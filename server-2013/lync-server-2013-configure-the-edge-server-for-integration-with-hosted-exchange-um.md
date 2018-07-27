---
title: 'Lync Server 2013: Configurar Servidor de Borda para integração com o Exchange UM hospedado'
TOCTitle: Configurar Servidor de Borda para integração com o Exchange UM hospedado
ms:assetid: ede3f2f9-f412-418e-a705-8d8ec98176c5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399075(v=OCS.15)
ms:contentKeyID: 49308531
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar Servidor de Borda para integração com o Exchange UM hospedado

 

_**Tópico modificado em:** 2015-01-23_

Para oferecer recursos de caixa postal aos usuários do Lync Server 2013 no Unificação de Mensagens (UM) do Exchange hospedado, realize as seguintes tarefas de configuração no Servidor de Borda:

  - Configure o Servidor de Borda para federação.

  - Replique os dados do Repositório de Gerenciamento Central para o Servidor de Borda e verifique a replicação.

  - Crie um provedor de hospedagem no Servidor de Borda.

Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server sobre os seguintes cmdlets:

  - [Set-CsAccessEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsAccessEdgeConfiguration)

  - [New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider)

> [!IMPORTANT]  
> É necessário criar um registro DNS SRV para o serviço Exchange de hospedagem antes de você executar essas etapas. Para obter detalhes, consulte <a href="lync-server-2013-create-a-dns-srv-record-for-integration-with-hosted-exchange-um.md">Criar um registro DNS SRV para integração com Exchange UM hospedado</a>.

## Para configurar o Servidor de Borda para federação

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsAccessEdgeConfiguration para configurar o servidor para federação. Por exemplo, execute:
    
        Set-CsAccessEdgeConfiguration -UseDnsSrvRouting -AllowFederatedUsers 1 -EnablePartnerDiscovery 0
    
    O exemplo anterior define os seguintes parâmetros:
    
      - **UseDnsSrvRouting** especifica se os Servidores de Borda dependerão dos registros DNS SRV ao enviar e receber solicitações de federação.
    
      - **AllowFederatedUsers** especifica se os usuários internos têm permissão para se comunicar com usuários de domínios federados. Essa propriedade também determina se os usuários internos podem se comunicar com usuários em uma situação de divisão de domínios.
    
      - **EnablePartnerDiscovery** especifica se o Lync Server usará os registros DNS para tentar descobrir domínios parceiros não listados na lista de domínios permitidos do Active Directory. Se for configurado como Falso, o Lync Server 2013 irá federar somente com domínios encontrados na lista de domínios permitidos. Esse parâmetro é obrigatório caso se esteja utilizando o roteamento de serviço de DNS. Na maioria das implantações, o valor é definido como falso para evitar abrir a federação a todos os parceiros.

## Para replicar os dados para o Servidor de Borda e verificar a replicação

  - Verifique se a replicação para o Servidor de Borda está completa. Para obter o procedimento, consulte [Verificar conectividade entre servidores internos e Servidores de Borda no Lync Server 2013](lync-server-2013-verify-connectivity-between-internal-servers-and-edge-servers.md).

## Para criar um provedor de hospedagem no Servidor de Borda

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet **New-CsHostingProvider** para configurar o provedor de hospedagem. Por exemplo, execute:
    
        New-CsHostingProvider -Identity Fabrikam.com -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFQDN "proxyserver.fabrikam.com" -IsLocal $False -VerificationLevel UseSourceVerification
    
    O exemplo anterior define os seguintes parâmetros:
    
      - **Identidade** especifica um identificador exclusivo de valor de cadeia de caracteres para o provedor de hospedagem que você está criando, neste exemplo, **Fabrikam.com** . Observe que o comando falhará se um provedor existente já tiver sido configurado com essa identidade.
    
      - **Habilitado** indica se a conexão de rede entre seu domínio e o provedor de hospedagem está habilitado. As mensagens não podem ser trocadas entre as duas organizações até que esse valor seja definido como **Verdadeiro** .
    
      - **EnabledSharedAddressSpace** indica se o provedor de hospedagem está sendo usado em um cenário de espaço de endereço SIP compartilhado (domínio dividido).
        
        > [!NOTE]  
        > Antes de definir <code>EnableSharedAddressSpace</code> como True, tente resolver o registro SRV de Federação internamente. Se esse registro não puder ser resolvido internamente, você precisará criar os registros, _sipfederationtls._tcp.&lt;domain&gt; e _sip._tls.&lt;domain&gt; no DNS interno. Esses registros devem apontar para o endereço IP externo da Interface de Acesso do Servidor de Borda.    
      - **HostsOCSUsers** indica se o provedor de hospedagem é usado para hospedar contas do Lync Server 2013. Se estiver definido como **Falso** , o provedor hospedará outros tipos de conta, como contas do Microsoft Exchange.
    
      - **ProxyFQDN** especifica o FQDN (nome de domínio totalmente qualificado) para o servidor proxy usado pelo provedor de hospedagem, neste exemplo, **proxyserver.fabrikam.com** . Esse valor não pode ser modificado. Se o provedor de hospedagem alterar o seu servidor proxy, será necessário excluir e recriar a entrada desse provedor.
    
      - **IsLocal** indica se o servidor proxy usado pelo provedor de hospedagem está contido dentro de sua topologia do Lync Server 2013.
    
      - **VerficationLevel** indica o nível de verificação permitido para mensagens enviadas para e do provedor de hospedagem. Especifique **UseSourceVerification**, que depende do nível de verificação incluído nas mensagens enviadas do provedor de hospedagem. Se este nível não for especificado, a mensagem será rejeitada como sendo não-verificável.

## Consulte Também

#### Tarefas

[Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md)  

#### Conceitos

[Verificar conectividade entre servidores internos e Servidores de Borda no Lync Server 2013](lync-server-2013-verify-connectivity-between-internal-servers-and-edge-servers.md)  

#### Outros Recursos

[New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider)

