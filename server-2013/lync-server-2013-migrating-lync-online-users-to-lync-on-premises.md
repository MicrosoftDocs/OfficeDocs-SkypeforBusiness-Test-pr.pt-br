---
title: Migração dos usuários do Lync Online para o Lync no local
TOCTitle: Migração dos usuários do Lync Online para o Lync no local
ms:assetid: 0e29605b-db2d-4cbf-b6a9-15db6b9fdabc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn689115(v=OCS.15)
ms:contentKeyID: 62247357
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migração dos usuários do Lync Online para o Lync no local

 

_**Tópico modificado em:** 2016-12-08_

> [!IMPORTANT]  
> Essas etapas são necessárias somente para migração de contas de usuários que foram originalmente habilitadas para Lync no Lync Online, antes de implantar o Lync local. Para mover os usuários que foram originalmente habilitados para Lync local e posteriormente movidos para o Lync Online, consulte <a href="lync-server-2013-administering-users-in-a-hybrid-deployment.md">Administrando usuários em uma implantação híbrida do Lync Server 2013</a>.<br />Além disso, todos os usuários que migrarem devem ter contas no Diretório Ativo local.

## Como migrar para o Lync local contas de usuários habilitadas originalmente no Lync Online

1.  Primeiro, certifique-se de que sua organização esteja configurada como híbrida.
    
      - Instale a Ferramenta de Sincronização do Windows Azure Active Directory. Para mais informações, consulte <http://social.technet.microsoft.com/wiki/contents/articles/19098.howto-install-the-windows-azure-active-directory-sync-tool.aspx>.
    
      - Para habilitar seus usuários a usar o login único para o Lync Online, instale os Serviços de Federação do Active Directory <http://social.technet.microsoft.com/wiki/contents/articles/1011.active-directory-federation-services-ad-fs-overview.aspx>.
    
      - Em suas implantações locais, no Shell de Gerenciamento do Lync Server, digite os cmdlets a seguir para criar o provedor de host para o Lync Online:
        
    ```
        Set-CSAccessEdgeConfiguration -AllowOutsideUsers 1 -AllowFederatedUsers 1 -UseDnsSrvRouting -EnablePartnerDiscovery $true
    ```
    ```        
        New-CSHostingProvider -Identity LyncOnline -Name LyncOnlin -ProxyFqdn "sipfed.online.lync.com" -Enabled $true -EnabledSharedAddressSpace $true -HostsOCSUsers $true -VerificationLevel UseSourceVerification -IsLocal $false -AutodiscoverUrl https://webdir.online.lync.com/Autodiscover/AutodiscoverService.svc/root
    ```

2.  Confirme se, nos Servidores de Borda locais, você possui a cadeia de certificados que possibilita a conexão ao Lync Online, conforme mostra a tabela a seguir. A tabela está disponível para download aqui: [https://corp.sts.microsoft.com/Onboard/ADFS\_Onboarding\_Pack/corp\_sts\_certs.zip](https://corp.sts.microsoft.com/onboard/adfs_onboarding_pack/corp_sts_certs.zip) .
    
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Certificado</th>
    <th>Repositório de Certificado</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Raiz do Baltimore CyberTrust</p></td>
    <td><p>AC Raiz Confiável</p></td>
    </tr>
    <tr class="even">
    <td><p>Microsoft Internet Authority (novo certificado CA)</p></td>
    <td><p>CA Intermediário</p></td>
    </tr>
    <tr class="odd">
    <td><p>MSIT Machine Auth CA2 (nova emissão de CA2)</p></td>
    <td><p>CA intermediário</p></td>
    </tr>
    </tbody>
    </table>


3.  Em seu Active Directory local, habilite as contas de usuário afetadas para o Lync local. Essa ação é possível para usuários individuais digitando o cmdlet a seguir:
    
        Enable-CsUser
        -Identity "username" 
        -SipAddress "sip: username@contoso.com"
        -HostingProviderProxyFqdn "sipfed.online.lync.com"
    
    Você também pode criar um script que lê os nomes de usuário a partir de um arquivo e os oferece como input ao cmdlet Enable-CsUser:
    
        Enable-CsUser
        -Identity $Identity 
        -SipAddress $SipAddress 
        -HostingProviderProxyFqdn "sipfed.online.lync.com"

4.  Execute o DirSync para sincronizar os usuários do Lync Online com os usuários atualizados do Lync local.

5.  Atualize alguns registros DNS para direcionar todos os tráfegos SIP ao Lync local:
    
      - Atualize o **lyncdiscover.contoso.com** Um registro para apontar ao FQDN do servidor de proxy reverso do local.
    
      - Atualize o registro SRV ***\_sip*.\_tls.contoso.com** para solucionar o endereço VIP ou IP público do serviço de Borda de Acesso do Lync local.
    
      - Atualize o registro SRV ***\_sipfederationtls*.\_tcp.contoso.com** para solucionar o endereço VIP ou IP público do serviço de Borda de Acesso do Lync local.
    
      - Se sua organização usa DNS divididos (conhecidos como “split-brain DNS”), certifique-se de que os usuários que solucionam nomes por meio da zona DNS interna sejam direcionados ao Pool de Front-ends.

6.  Digite o cmdlet `Get-CsUser` para verificar algumas propriedades sobre os usuários que serão movidos. Certifique-se de que o HostingProviderProxyFQDN esteja definido como `"sipfed.online.lync.com"` e que os endereços SIP estejam definidos corretamente.

7.  Mova os usuários do Lync Online para o Lync local.
    
    Para mover um único usuário, digite:
    
    ```
        $cred = Get-Credential
    ```
    ```    
        Move-CsUser -Identity <username>@contoso.com -Target "<fe-pool>.contoso.com" -Credential $cred -HostedMigrationOverrideURL <URL>
    ```
    
    Você pode mover usuários únicos por meio do cmdlet **Get-CsUSer** com o parâmetro –Filtro para selecionar os usuários com determinada propriedade. Por exemplo, você pode selecionar todos os usuários do Lync Online filtrando por {Provedor de Hospedagem – eq “sipfed.online.lync.om”}. Em seguida, poderá canalizar os usuários retornados para o cmdlet **Move-CsUSer**, como mostra abaixo.
    
    ```
        Get-CsUser -Filter {Hosting Provider -eq "sipfed.online.lync.com"} | Move-CsUser -Target "<fe-pool>.contoso.com" -Credential $creds -HostedMigrationOverrideURL <URL>
    ```
    
    O formato da URL específica para o parâmetro **HostedMigrationOverrideUrl** deve ser a URL para o pool no qual o serviço de migração hospedada está sendo executado, no seguinte formato: *Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc*.
    
    Você pode identificar a URL do serviço de migração hospedada visualizando a URL do Painel de Controle do Lync Online da sua conta de locatário do Office 365.
    
    ## Para identificar a URL do Serviço de Migração Hospedada do seu locatário do Office 365
    
    1.  Faça logon no seu locatário do Office 365 como um administrador.
    
    2.  Abra o **Centro de administração do Lync**.
    
    3.  Com o **Centro de administração do Lync** exibido, selecione e copie a URL na barra de endereço no **lync.com**. Uma URL de exemplo seria parecida com esta:
        
        `https://webdir0a.online.lync.com/lscp/?language=en-US&tenantID=`
    
    4.  Substitua **webdir** na URL por **admin**, o que resulta no seguinte:
        
        `https://admin0a.online.lync.com`
    
    5.  Anexe a cadeia de caracteres a seguir à URL: **/HostedMigration/hostedmigrationservice.svc**.
        
        A URL resultante, que tem o valor de **HostedMigrationOverrideUrl**, deverá ser parecida com esta:
        
        `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`
    
    > [!NOTE]  
    > O tamanho máximo padrão para arquivos de registro de transação do banco de dados rtcxds é 16 GB. Este tamanho pode não ser suficiente caso você esteja movendo uma grande quantidade de usuários de uma só vez, especialmente se o espelhamento estiver ativado. Para contornar a situação, aumente o tamanho de arquivo ou faça backup dos arquivos de registro regularmente. Para obter mais informações, consulte <a href="http://support.microsoft.com/kb/2756725" class="uri">http://support.microsoft.com/kb/2756725</a>.

8.  Esta etapa é opcional. Caso precise fazer a integração com o Exchange 2013 Online, será necessário utilizar um provedor de hospedagem adicional. Para obter mais detalhes, consulte [Configurando integração local do Lync Server 2013 com o Exchange Online](lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md).

9.  Os usuários foram movidos. Para verificar se um usuário possui os valores corretos dos atributos exibidos na tabela a seguir, digite este cmdlet:
    
        Get-CsUser | fl DisplayName,HostingProvider,SipAddress,Enabled
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Atributo do Active Directory</th>
    <th>Nome do atributo</th>
    <th>Valor correto para usuário do Lync Online</th>
    <th>Valor correto para usuários do Lync local</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>msRTCSIP-DeploymentLocator</p></td>
    <td><p>HostingProvider</p></td>
    <td><p>sipfed.online.lync.com</p></td>
    <td><p>SRV:</p></td>
    </tr>
    <tr class="even">
    <td><p>msRTCSIP-PrimaryUserAddress</p></td>
    <td><p>SIPAddress</p></td>
    <td><p>sip:userName@contoso.com</p></td>
    <td><p>sip:userName@contoso.com</p></td>
    </tr>
    <tr class="odd">
    <td><p>sRTCSIP-UserEnabled</p></td>
    <td><p>Habilitado</p></td>
    <td><p>Verdadeiro</p></td>
    <td><p>Verdadeiro</p></td>
    </tr>
    </tbody>
    </table>


10. Cada usuário movido precisará fazer logout do Lync e fazer login novamente. Ao fazer login, deverão verificar a lista de contatos e adicionar, caso seja necessário.
    
    Observe que as reuniões agendadas não são migradas do Lync Online para o Lync local. Os usuários precisarão reagendar as reuniões depois de serem movidos.
    
    Depois que os registros de DNS forem atualizados e todos os usuários forem direcionados ao Lync local, o atributo HostingProvider direciona o usuário do Lync para utilizar os registros SRV ou para o provedor Online “sipfed.online.lync.com.”

