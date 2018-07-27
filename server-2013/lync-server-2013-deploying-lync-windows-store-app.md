---
title: Implantar o Lync Windows Store App no Lync Server 2013
TOCTitle: Implantar o Lync Windows Store App no Lync Server 2013
ms:assetid: 9e00aaf4-15f9-4356-9ed7-5a58a2bfa043
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ822971(v=OCS.15)
ms:contentKeyID: 52057691
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar o Lync Windows Store App no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Antes de disponibilizar o Aplicativo Lync Windows Store aos usuários, verifique se a implantação atende aos [Requisitos do Aplicativo Lync da Windows Store para Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md). Para obter mais detalhes sobre como configurar o Lync Server 2013 para oferecer suporte a Aplicativo Lync Windows Store, consulte o artigo do Blog NextHop, "Descoberta Automática do Lync Server e o Lync Windows Store App," no [http://go.microsoft.com/fwlink/?LinkId=271966](http://go.microsoft.com/fwlink/?linkid=271966). Quando seu ambiente de servidor estiver configurado corretamente, pode direcionar os usuários para baixar o aplicativo Lync da Windows Store procurando por "Lync."

## Habilitar a autenticação multifator para Aplicativo Lync Windows Store

Atualizações acumulativas para Lync Server 2013: junho de 2013 adiciona a autenticação multifator para clientes do Aplicativo Lync Windows Store. Além do nome de usuário e senha, você pode precisar de métodos de autenticação adicionais, como cartões inteligentes ou PINs, para autenticar usuários externos quando eles entrarem em reuniões do Lync. Para ativar a autenticação multifator, implante o servidor de federação do Serviço de Federação do Active Directory (AD FS) e habilite a autenticação passiva no Lync Server 2013. Após a configuração do AD FS, usuários externos que tentarem ingressar em reuniões do Lync visualizam uma página da Web de autenticação multifator do AD FS que contém o desafio de nome de usuário e senha junto com todos os métodos de autenticação adicionais que você configurou.

> [!IMPORTANT]  
> Veja a seguir considerações importantes se você pretende configurar o AD FS para autenticação multifator para o Aplicativo Lync Windows Store:<ul>
> <li><p>Lync Server 2013 com Atualizações acumulativas para Lync Server 2013: junho de 2013 é necessário, no mínimo. Clientes de desktop Lync 2013 não requerem Atualizações acumulativas para Lync Server 2013: junho de 2013, por isso pode parecer que a autenticação passiva está funcionando porque os clientes do Lync 2013 conseguem se autenticar. No entanto, o processo de autenticação para clientes do Aplicativo Lync Windows Store não será concluído e nenhuma mensagem de notificação ou de erro será exibida.</p></li>
> <li><p>O servidor deve ser configurado para que a autenticação passiva seja o único tipo de autenticação oferecido.</p></li>
> 
> <li><p>Se você usa balanceadores de carga de hardware, habilite a persistência de cookie nos balanceadores de carga para que todas as solicitações do cliente do Aplicativo Lync Windows Store sejam manipuladas pelo mesmo cookie de Servidor front-end.</p></li>
> 
> 
> <li><p>Ao estabelecer uma parte confiável entre os servidores do Lync Server e do AD FS, atribua uma vida de token longa o suficiente para considerar a duração máxima de suas reuniões do Lync. Normalmente, uma vida de token de 240 minutos é suficiente.</p></li></ul>


**Configurar a autenticação multifator**

1.  Instale uma função de servidor de federação AD FS. Para obter detalhes, consulte o Guia de implantação do Active Directory Federation Services 2.0 no <http://go.microsoft.com/fwlink/p/?linkid=267511>.

2.  Crie certificados para AD FS. Para obter mais informações, consulte a seção "Certificados do servidor da federação" do tópico Planejar para e implementar AD FS para uso com o logon único em [http://go.microsoft.com/fwlink/p/?LinkId=285376](http://go.microsoft.com/fwlink/p/?linkid=285376).

3.  A partir da interface de linha de comando do Windows PowerShell, execute o seguinte comando:
    
        add-pssnapin Microsoft.Adfs.powershell

4.  Estabeleça uma parceria executando o seguinte comando:
    
        Add-ADFSRelyingPartyTrust -Name ContosoApp -MetadataURL https://lyncpool.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  Defina as seguintes regras de confiabilidade de parte:
    
```
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.contoso.com/authorization/claims/permit", Value = "true");'$IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.contoso.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
```
```    
        Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
```
```    
        Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
```

## Problemas conhecidos que podem evitar o logon

## A data e a hora não estão definidas com precisão no dispositivo executando o Aplicativo Lync Windows Store

A hora no dispositivo deve estar sincronizada com o hora do servidor. Isto é particularmente importante para dispositivos como o Microsoft Surface, e outros dispositivos que executam o Windows RT que não são parte de um domínio. Para definir a hora nesses dispositivos automaticamente a partir de um servidor de horário, execute o seguinte comando em um prompt de comando elevado no dispositivo:

    w32tm /resync

## Aplicativo Lync Windows Store o servidor nem os serviços do Lync

Aplicativo Lync Windows Store pode não conseguir acessar o servidor nem os serviços do Lync por meio de adaptadores de rede, como modems 4G LTE USB, que não estão registrados no Windows 8 como dispositivos físicos. Aplicativo Lync Windows Store pode ter este problema, mesmo quando os aplicativos e navegadores de desktop conseguem acessar outros servidores e sites.

## O aplicativo Lync Windows Store não consegue fazer logon no Lync Server 2010 e no Office Communications Server 2007 R2 Edge Server

Se a sua topologia consiste em Lync Server 2010 com Office Communications Server 2007 R2 Edge Server, você terá que executar a versão atualizada do Construtor de Topologias disponível na atualização cumulativa para Lync Server 2010: julho de 2013. Versões anteriores do Construtor de Topologias não criam o mapeamento necessário para Office Communications Server 2007 Edge Server, por isso os clientes do aplicativo Lync Windows Store não conseguem fazer logon. As seguintes etapas são necessárias:

1.  Instale a atualização cumulativa para Lync Server 2010: julho de 2013 nos pools do Lync Server 2010 e diretores do Lync Server 2010.

2.  Atualize a configuração da Descoberta Automática do Lync para indicar que o ponto de entrada SIP externo é o endereço do servidor de borda, fazendo o seguinte:
    
    1.  Abrir o Shell de Gerenciamento do Lync Server.
    
    2.  Execute o seguinte comando:
        
            Set-CsAutodiscoverConfiguration -ExternalSipClientAccessFqdn <FQDN of server used for external client access> -ExternalSipClientAccessPort 443

## O Aplicativo Windows Store do Lync não pode se conectar devido a uma falha de validação do nome do certificado

Um problema de conexão pode ocorrer para usuários do Office 365 que não estão executando a versão mais recente do Aplicativo Lync Windows Store. Esse problema geralmente ocorre ao utilizar vários domínios (por exemplo, quando o URL do SIP for **userA@domainZ.com**, exceto o Servidor de Borda for **sip.domainX.com**). Para resolver o problema, os usuários devem instalar a versão mais recente da última versão do Aplicativo Lync Windows Store, que necessita do Windows 8.1.

## Use os logs do Aplicativo Lync Windows Store para solucionar problemas

Você pode usar os logs gerados no dispositivo para solucionar problemas. Os logs são armazenados na seguinte pasta:

%LocalAppData%\\Packages\\Microsoft.LyncMX\_8wekyb3d8bbwe\\LocalState\\Tracing

Antes de obter os logs de um usuário, certifique-se que o registro em log esteja ligado, e em seguida peça para o usuário salvar os logs, de modo que todas as informações armazenadas na memória também sejam salvas em arquivos no disco rígido.

**Para ativar o registro em log**

1.  Abra Aplicativo Lync Windows Store no dispositivo.

2.  Passe o dedo a partir do lado direito da tela. Se você estiver usando um mouse, aponte para o canto superior direito da tela e em seguida mova o ponteiro do mouse para baixo.

3.  Selecione **Configurações**, **Opções** e defina **Logs de diagnóstico** como **Ligado**.

4.  Se os **Logs de diagnóstico** estavam desligados em anteriormente, você deve reiniciar o Lync. Para reiniciar o Lync, siga um dos seguintes passos:
    
      - Reinicie o dispositivo.
    
      - Finalize a tarefa do Lync e inicie o aplicativo novamente. Para terminar a tarefa, abra o Gerenciador de Tarefas do Windows, selecione **Lync**, e toque em **Finalizar tarefa**. Se o Lync não estiver listado, toque em **Mais detalhes** e procure pelo Lync em **Processos em segundo plano**.

**Para salvar os logs**

1.  Abra Aplicativo Lync Windows Store no dispositivo.

2.  Tente fazer logon.

3.  Passe o dedo a partir do lado direito da tela. Se você estiver usando um mouse, aponte para o canto superior direito da tela e em seguida mova o ponteiro do mouse para baixo.

4.  Selecione **Configurações**, selecione **Sobre** e selecione **Salvar logs**.

