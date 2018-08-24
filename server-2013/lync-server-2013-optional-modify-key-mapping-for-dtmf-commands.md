---
title: 'Lync Server 2013: (Opcional) Modificar mapeamento principal de comandos DTMF'
TOCTitle: (Opcional) Modificar mapeamento principal de comandos DTMF
ms:assetid: d753b78d-400c-4df2-957f-e7576b2019c2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398943(v=OCS.15)
ms:contentKeyID: 49308262
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Modificar mapeamento principal de comandos DTMF no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Os usuários de conferência discada podem pressionar teclas no teclado do telefone para executar comandos DTMF (multifrequência de tom dual). Comandos DTMF permitem que os usuários que discam para uma conferência controlem as configurações da conferência (como ativar ou desativar o próprio microfone, ou bloquear e desbloquear a conferência) pelo teclado do telefone. É possível usar cmdlets para modificar as teclas usadas para os comandos DTMF. Essa etapa é opcional.

> [!NOTE]  
> Para obter detalhes sobre esses cmdlets e as possíveis opções de DTMF, consulte a documentação do Shell de Gerenciamento do Lync Server ou a Ajuda da linha de comando do Shell de Gerenciamento do Lync Server.

## Para modificar o mapeamento principal dos comandos DTMF

1.  Faça logon no computador como membro do grupo **RTCUniversalServerAdmins** ou como membro da função **Cs-ServerAdministrator** ou **CsAdministrator** .

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o seguinte no prompt de comando:
    
        Get-CsDialinConferencingDtmfConfiguration
    
    Esse cmdlet retorna as configurações de DTMF usadas para conferência discada.

4.  Execute o seguinte cmdlet e especifique a tecla a ser pressionada para cada opção que você deseja alterar:
    
        Set-CsDialinConferencingDtmfConfiguration [-Identity <global or site collection to be changed>]
        [-AdmitAll <default key is 8>] [-AudienceMuteCommand <default key is 4>]
        [-CommandCharacter <* (default) | #>] [-EnableDisableAnnouncementsCommand <default key is 9>]
        [-HelpCommand <default key is 1>] [-LockUnlockConferenceCommand <default key is 7>]
        [-MuteUnmuteCommand <default key is 6>] [-PrivateRollCallCommand <default key is 3>]
    
    Esse cmdlet modifica as configurações de DTMF usadas para conferência discada.
    
    Por exemplo:
    
        Set-CsDialinConferencingDtmfConfiguration -EnableDisableAnnouncementsCommand 4 -AudienceMuteCommand 9
    
    Esse exemplo troca a tecla pressionada para habilitar ou desabilitar os anúncios e a tecla pressionada para ativar ou desativar o opção Mudo de todos os participantes. Como nenhuma Identidade é especificada, essas alterações se aplicam às configurações DTMF globais.

5.  (Opcional) Para criar conjuntos adicionais de comandos DTMF para sites específicos, use o cmdlet **New-CsDialinConferencingDtmfConfiguration** com uma identidade de site. Ao criar novas configurações DTMF para sites, as configurações do site têm precedência sobre as configurações globais. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server ou a Ajuda da linha de comando do Shell de Gerenciamento do Lync Server.

