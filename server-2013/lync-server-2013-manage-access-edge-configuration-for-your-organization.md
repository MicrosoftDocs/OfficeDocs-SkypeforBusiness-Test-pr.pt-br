---
title: 'Lync Server 2013: Gerenciar configuração da borda de acesso para sua organização'
TOCTitle: Gerenciar configuração da borda de acesso para sua organização
ms:assetid: 0145eb08-984f-4ecd-bf9c-364817619c2a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ552443(v=OCS.15)
ms:contentKeyID: 49305668
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar configuração da borda de acesso para sua organização no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Esta documentação é preliminar e está sujeita a alterações. Os tópicos em branco são incluídos como espaços reservados.

Após a implantação de um ou mais Servidores de Borda, é necessário habilitar os tipos de domínio externo ou acesso de provedor, acesso de usuário remoto e acesso de usuário anônimo às conferências por meio do Servidores de Borda que será suportado em sua organização.

Essas opções incluem os seguintes tipos de acesso que podem ser configurados por meio da página **Configuração de Borda de Acesso** :

  - **Habilitar Federação e conectividade a Redes Públicas de IM**    Habilite essa opção se quiser suportar acesso do usuário a domínios de parceiro federado. Essa configuração se aplica à federação SIP e à federação XMPP configuradas para escopos global, site ou usuário na página **Política de Acesso Externo** . Para aplicar as configurações de federação, é necessário configurar o suporte à federação em ambas as páginas.
    
    Há duas configurações opcionais para o modo como os parceiros federados são descobertos, e se os avisos de isenção de arquivamento (notificação a contatos federados com os quais você se comunica de que sua implantação tem o arquivamento habilitado e de que os detalhes das comunicações serão arquivados) serão enviados aos contatos
    
      - **Habilitar descoberta de domínios de parceiros**    Selecionar essa opção habilita a descoberta automática de domínios com os quais é possível federar. O Lync Server 2013 usa registros DNS (Sistema de Nome de Domínio) para tentar descobrir domínios não listados na lista de domínios permitidos, avaliando automaticamente o tráfego de entrada de parceiros federados descobertos e limitando ou bloqueando esse tráfego com base no nível de confiança, quantidade de tráfego e configurações de administrador. Se você não selecionar essa opção, o acesso do usuário federado será habilitado somente para usuários nos domínios que você incluir na lista de domínios permitidos. Mesmo que você não selecione essa opção, poderá especificar o bloqueio ou permissão de domínios individuais, incluindo a restrição do acesso a servidores específicos, executando o serviço Borda de Acesso no domínio federado. Para obter detalhes, consulte [Configurar suprote para domínios externos permitidos no Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md).
    
      - **Enviar aviso de isenção de responsabilidade de arquivamento para parceiros federados**    A seleção dessa opção habilita o envio de uma mensagem de isenção de responsabilidade do arquivamento aos parceiros federados que os orienta de que os detalhes das comunicações foram registrados. Se você arquivar comunicações externas com domínios de parceiro federados, deverá habilitar a notificação de aviso de isenção de responsabilidade de arquivamento a fim de avisar os parceiros de que suas mensagens e comunicações estão sendo arquivadas por sua implantação. Para obter detalhes sobre o arquivamento, consulte [Definindo seus requisitos para Arquivamento no Lync Server 2013](lync-server-2013-defining-your-requirements-for-archiving.md).

  - **Habilitar acesso de usuário remoto**    Habilite essa opção se quiser que os usuários em sua organização que estiverem fora de seu firewall, como usuários remotos e em viagem, possam se conectar ao Lync Server. Para obter detalhes, consulte [Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013](lync-server-2013-enable-or-disable-remote-user-access.md).

  - **Habilitar usuários anônimos para acessar conferências**    Habilite essa opção se quiser que os usuários internos convidem usuários anônimos externos para conferências que organizam. A habilitação dessa configuração permite apenas usuários anônimos para conferências. Para configurar a experiência de conferência e opções que definirão como e o que seus usuários podem fazer com as conferências e para a inclusão de usuários anônimos, consulte detalhes em [Criar ou modificar a experiência do usuário de conferência para um local ou grupo de usuários](https://technet.microsoft.com/pt-br/library/gg429715\(v=ocs.15\)) e [Referência das configurações da política de conferência para Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md).

> [!NOTE]  
> Além de permitir o suporte ao acesso de usuário externo, você também configura políticas para controlar o uso do acesso de usuário remoto em sua organização antes de qualquer tipo de acesso de usuário externo ficar disponível para os usuários. Para obter detalhes sobre como criar, configurar e aplicar políticas de acesso para usuário externo, consulte <a href="lync-server-2013-manage-external-access-policy-for-your-organization.md">Gerenciar política de acesso externo no Lync Server 2013</a>.

**Exibindo as informações de configuração da Borda de Acesso utilizando os cmdlets Windows PowerShell**

  - As informações de configuração da Borda de Acesso podem ser exibidas utilizando os cmdlets Windows PowerShell e **Get-CsAccessEdgeConfiguration**. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    Para exibir informações sobre todas suas configurações de Borda de Acesso, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsAccessEdgeConfiguration
    
    Isso retornará informações parecidas com:
    
        Identity                               : Global
        AllowAnonymousUsers                    : False
        AllowFederatedUsers                    : False
        AllowOutsideUsers                      : True
        BeClearingHouse                        : False
        EnablePartnerDiscovery                 : False
        EnableArchivingDisclaimer              : False
        EnableUserReplicator                   : True
        KeepCrlsUpToDateForPeers               : True
        MarkSourceVerifiableOnOutgoingMessages : True
        OutgoingTlsCountForFederatedPartners   : 4
        DiscoveredPartnerStandardRate          : 20
        EnableDiscoveredPartnerContactsLimit   : True
        MaxContactsPerDiscoveredPartner        : 1000
        DiscoveredPartnerReportPeriodMinutes   : 60
        MaxAcceptedCertificatesStored          : 1000
        MaxRejectedCertificatesStored          : 500
        CertificatesDeletedPercentage          : 20
        RoutingMethod                          : UseDnsSrvRouting

## Nesta seção

  - [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

  - [Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md)

  - [Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados no Lync Server 2013](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md)

  - [Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013](lync-server-2013-enable-or-disable-remote-user-access.md)

  - [Habilitar ou desabilitar acesso de usuário anônimo no Lync Server 2013](lync-server-2013-enable-or-disable-anonymous-user-access.md)

  - [Atribuir políticas de conferência para suporte de usuários anônimos no Lync Server 2013](lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md)

