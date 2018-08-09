---
title: "Lync Server 2013: (Opc.) Hab. e desab. comunic. de ingresso e saída de confer."
TOCTitle: (Opcional) Habilitar e desabilitar comunicados de ingresso e saída de conferência
ms:assetid: c9529568-e66c-48d8-aef2-9072f9c336ff
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398834(v=OCS.15)
ms:contentKeyID: 49308102
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Habilitar e desabilitar comunicados de ingresso e saída de conferência no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Quando usuários discados ingressam em uma conferência ou saem dela, o Aplicativo Comunicado de Conferência pode anunciar sua entrada ou saída reproduzindo um tom ou dizendo seus nomes. Você pode alterar o funcionamento de comunicados executando cmdlets. Esta etapa é opcional.

## Para modificar o comportamento de anúncio de ingresso e saída de conferência

1.  Faça logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-ServerAdministrator** ou **CsAdministrator** .

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o seguinte no prompt de comando:
    
        Get-CsDialinConferencingConfiguration
    
    Este cmdlet recupera as informações sobre se os participantes precisam registrar seus nomes ao ingressar em uma conferência como o Lync Server responde quando os participantes ingressam ou saem de uma conferência discada.

4.  Execute o seguinte no prompt de comando:
    
        Set-CsDialinConferencingConfiguration -Identity <identity of dial-in conferencing settings to be modified>
        [-EnableNameRecording <$true | $false>]
        [-EntryExitAnnouncementsEnabledByDefault <$true | $false>]
        [-EntryExitAnnouncementsType <UseNames | ToneOnly]
    
    **EnableNameRecording**   Determina se os participantes anônimos devem receber uma solicitação para registrar seus nomes antes de entrar na conferência. O valor padrão é "$true", que significa que os participantes receberão essa solicitação. (Os participantes autenticados não registram seus nomes, pois em vez disso exibem seus nomes de exibição.)
    
    **EntryExitAnnouncementsEnabledByDefault**   Indica se os anúncios estão ativados ou desativados por padrão. O valor padrão é "$false", que significa que, por padrão, não anúncios quando os participantes ingressam ou saem de uma conferência. O organizador da reunião pode substituir essa configuração ao agendar uma reunião.
    
    **EntryExitAnnouncementsType**   Indica a ação a ser executada sempre que um participante ingressa ou sai de uma conferência para a qual os anúncios estão habilitados. O valor padrão é "UseNames", que significa que há um anúncio parecido com o seguinte: "Ken Myer ingressou na conferência" quando os anúncios estão ativados.
    
    É possível definir essas configurações no escopo global ou no escopo do site. As configurações definidas no escopo do site têm precedência sobre as configurações definidas no escopo global.
    
    Por exemplo:
    
        Set-CsDialinConferencingConfiguration -Identity site:Redmond
        -EnableNameRecording $false
        -EntryExitAnnouncementsEnabledByDefault $true
        -EntryExitAnnouncementsType ToneOnly
    
    Neste exemplo, as configurações estão definidas no escopo do site para Redmond. Os anúncios estão ativados, mas os participantes não recebem uma solicitação para inserir seus nomes quando ingressam em uma conferência. Um tom é reproduzido quando os participantes entram e saem de uma conferência.

