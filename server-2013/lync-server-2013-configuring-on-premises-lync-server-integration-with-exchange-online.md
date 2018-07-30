---
title: 'Lync Server 2013: Configurando integração local do Lync Server 2013 com o Exchange Online'
TOCTitle: Configurando integração local do Lync Server 2013 com o Exchange Online
ms:assetid: 95a20117-2064-43c4-94fe-cac892cadb6f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh533880(v=OCS.15)
ms:contentKeyID: 49307510
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando integração local do Lync Server 2013 com o Exchange Online

 

_**Tópico modificado em:** 2014-07-02_

Clientes que estiverem usando implantações locais do Lync Server 2013 podem configurar a interoperabilidade com o Microsoft Outlook Web App no Microsoft Exchange Online em um modo de implantação híbrido. Recursos de interoperabilidade incluem logon único, sistemas de mensagens instantâneas (IM) e integração de presença com a interface do Outlook Web App. Para habilitar esta integração, você deve configurar o Servidor de Borda em sua implantação local do Lync Server concluindo as seguintes tarefas:

  - Configurar um espaço de endereçamento SIP compartilhado

  - Configurar um provedor de hospedagem no Servidor de Borda

  - Verificar a replicação do Repositório de Gerenciamento Central atualizado

## Configurar um espaço de endereçamento SIP compartilhado

Para integrar o Lync Server 2013 local com o Exchange Online, você deve configurar um espaço de endereçamento SIP compartilhado. O mesmo espaço de endereçamento de domínio SIP é suportado pelo Lync Server e o serviço do Exchange Online.

Usando o Shell de Gerenciamento do Lync Server, configure o Servidor de Borda para federação executando o cmdlet **Set-CSAccessEdgeConfiguration** usando os parâmetros exibidos no exemplo a seguir:

    Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

  - O parâmetro **AllowFederatedUsers** especifica se usuários internos têm permissão para se comunicar com usuários de domínios federados. Esta propriedade também determina se usuários internos podem se comunicar com usuários em um cenário de espaço de endereçamento SIP compartilhado com o Lync Server e o Exchange Online.

Para detalhes sobre como usar o Shell de Gerenciamento do Lync Server, consulte [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Configurar um provedor de hospedagem no Servidor de Borda

Usando o Shell de Gerenciamento do Lync Server, configure um provedor de hospedagem no Servidor de Borda executando o cmdlet **New-CsHostingProvider**, com os parâmetros do exemplo a seguir:

    New-CsHostingProvider -Identity "Exchange Online" -Enabled $True -EnabledSharedAddressSpace $True -HostsOCSUsers $False -ProxyFqdn "exap.um.outlook.com" -IsLocal $False -VerificationLevel UseSourceVerification

> [!NOTE]  
> Se você estiver usando o Office 365 operado pela 21Vianet na China, substitua o valor do parâmetro <strong>ProxyFqdn</strong> neste exemplo (&quot;exap.um.outlook.com&quot;) pelo FQDN do serviço operado pela 21Vianet: &quot;exap.um.partner.outlook.cn&quot;.

  - **Identity** especifica um identificador de valor de cadeia de caracteres único para o provedor de hospedagem que está sendo criado (por exemplo "Exchange Online"). Valores que contêm espaços devem estar entre aspas duplas.

  - **Enabled** indica se a conexão de rede entre seu domínio e o provedor de hospedagem está habilitada. Deve ser definido como True.

  - **EnabledSharedAddressSpace** indica se o provedor de hospedagem será usado em um cenário de espaço de endereçamento SIP compartilhado. Deve ser definido como True.

  - **HostsOCSUsers** indica se o provedor de hospedagem será usado para hospedar o Office Communications Server ou Lync Server. Deve ser definido como False.

  - **ProxyFQDN** especifica o nome de domínio totalmente qualificado (FQDN) para o servidor de proxy usado pelo provedor de hospedagem. Para o Exchange Online, o FQDN é exap.um.outlook.com.

  - **IsLocal** indica se o servidor de proxy usado pelo provedor de hospedagem está contido em sua topologia do Lync Server. Deve ser definido como False.

  - **VerificationLevel** indica o nível de verificação permitido para mensagens enviadas para e a partir do provedor hospedado. Especifique **UseSourceVerification**, que depende do nível de verificação incluso em mensagens enviadas a partir do provedor hospedado. Se este nível não for especificado, a mensagem será rejeitada como sendo não-verificável.

## Verificar a replicação do Repositório de Gerenciamento Central Atualizado

As alterações realizadas usando os cmdlets nas seções anteriores são automaticamente aplicadas ao Servidor de Borda e geralmente levam menos de um minuto para serem replicadas. Você pode validar o status da replicação e confirmar se as alterações foram aplicadas ao seu Servidor de Borda usando os cmdlets a seguir.

Para verificar as atualizações de replicação em um servidor interno à sua implantação do Lync Server, execute o cmdlet a seguir:

    Get-CsManagementStoreReplicationStatus

Para confirmar que as alterações foram aplicadas, no Servidor de Borda, execute o cmdlet a seguir:

    Get-CsHostingProvider -LocalStore

## Consulte Também

#### Outros Recursos

[Fornecendo caixa postal a usuários do Lync Server 2013 no Exchange UM hospedado](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md)  
[Integração de Unificação de Mensagens do Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-unified-messaging-integration.md)

