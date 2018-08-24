---
title: Configurar o suporte de federação para um domínio do Lync Online
TOCTitle: Configurar o suporte de federação para um domínio do Lync Online
ms:assetid: 19d5d5be-cd7f-47b8-b6c5-651a3191def7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202166(v=OCS.15)
ms:contentKeyID: 49306036
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o suporte de federação para um domínio do Lync Online

 

_**Tópico modificado em:** 2012-11-01_

A federação com um cliente Microsoft Lync Online 2010 requer que você conclua as seguintes etapas:

  - Configurar e suportar o domínio do cliente Lync Online 2010 (por exemplo, contoso.onmicrosoft.com). Conforme especificado na sessão [Pré-requisitos para federação com um cliente do Lync Online](lync-server-2013-prerequisites-for-federating-with-a-lync-online-customer.md) desta documentação, sua organização já deve estar habilitada para a federação. A habilitação da federação exige a especificação do método a ser usado para controlar o acesso dos domínios federados. Caso tenha configurado sua organização para usar a descoberta, a inclusão do domínio na sua lista de organizações permitidas é opcional. Se você não habilitar a descoberta de domínio, será necessário adicionar o nome do domínio do cliente Lync Online à sua lista de domínios permitidos. Você pode adicionar um nome de domínio usando o Painel de Controle do Lync Server ou executando o cmdlet **New-CSAllowedDomain**. Para obter mais detalhes sobre o uso do Painel de Controle do Lync Server, incluindo a habilitação de descoberta de domínios, consulte [Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md) na documentação de Operações. Para mais detalhes sobre o uso do cmdlet **New-CSAllowedDomain** para adicionar um domínio, consulte [New-CsAllowedDomain](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAllowedDomain) na documentação de Operações.
    
    > [!NOTE]  
    > Um cliente Lync Online pode ter vários domínios. Caso deseje federar com mais de um dos domínios, você deve configurar o suporte para cada domínio individual com o qual você deseja ter suporte federado e o administrador do cliente Lync Online deve habilitar a federação para cada um dos domínios a serem federados.

  - Configurar o suporte para o provedor de hospedagem do domínio do cliente Lync Online 2010 com o qual você deseja ser federado. Use os procedimentos desta seção para configurar o suporte ao provedor de hospedagem.
    
    > [!NOTE]  
    > Esta etapa é necessária somente para a federação com um domínio de um cliente Lync Online, não é necessária para a federação com qualquer domínio implantado localmente no parceiro federado.

## Configurar o suporte para um provedor de hospedagem

1.  A partir de um Servidor Front-End, Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet **New-CsHostingProvider** para criar e configurar um provedor de hospedagem. Por exemplo, execute:
    
        New-CsHostingProvider -Identity LyncOnline -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification -Enabled $True -EnabledSharedAddressSpace $False -HostsOCSUsers $False -IsLocal $False
    
    O exemplo anterior define os seguintes parâmetros:
    
      - **Identidade** especifica um identificador de valor exclusivo de cadeia de caracteres para o provedor de hospedagem que você está criando. Observe que o comando não funcionará casa haja um provedor existente já configurado com aquela Identity.
    
      - **ProxyFQDN** especifica o FQDN (nome de domínio totalmente qualificado) para o servidor proxy usado pelo provedor de hospedagem. Este valor não pode ser modificado. Se o provedor de hospedagem alterar seu servidor proxy, será necessário que você exclua e recrie a entrada para aquele provedor.
    
      - **VerificationLevel** especifica como (ou se) as mensagens enviadas de um provedor de hospedagem são verificados para garantir que sejam enviados a partir daquele provedor.
    
      - **Enabled** indica se a conexão de rede entre o seu domínio e o provedor de hospedagem está ativada. As mensagens não podem ser trocadas entre as duas organizações até que este valor seja definido como **True**.
    
      - **EnabledSharedAddressSpace** indica se o provedor de hospedagem está sendo usado em um cenário compartilhado de espaço de endereço SIP (divisão de domínios).
    
      - **HostsOCSUsers** indica se o provedor de hospedagem é usado para hospedar as contas do Lync Server. Caso seja **False**, o provedor hospeda outros tipos de conta, tais como as contas do Microsoft Exchange.
    
      - **IsLocal** indica se o servidor proxy usado pelo provedor de hospedagem está contido na sua topologia Lync Server.
    
    Para obter detalhes sobre o uso deste cmdlet, consulte [New-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsHostingProvider) na documentação de Operações.

