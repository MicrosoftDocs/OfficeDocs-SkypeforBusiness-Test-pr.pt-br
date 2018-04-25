---
title: Gerenciar as reuniões e as conferências do Lync Online
TOCTitle: Gerenciar as reuniões e as conferências do Lync Online
ms:assetid: a4d0c070-4df2-47df-a1e2-6ce62600a287
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362833(v=OCS.15)
ms:contentKeyID: 56270457
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar as reuniões e as conferências do Lync Online

 

_**Tópico modificado em:** 2015-06-22_

Os seguintes cmdlets podem ser usados para gerenciar as configurações de conferência e reunião:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="disable-csmeetingroom.md">Disable-CsMeetingRoom</a><br />
<a href="enable-csmeetingroom.md">Enable-CsMeetingRoom</a><br />
<a href="get-csmeetingroom.md">Get-CsMeetingRoom</a><br />
<a href="set-csmeetingroom.md">Set-CsMeetingRoom</a></p></td>
<td><p>Gerencia dispositivos de ponto de extremidade para salas de reuniões.</p>
<p>No Skype for Business Online, salas de reunião são appliances de computador autocontidos que estão instalados nas salas de conferência e fornecem recursos de reunião avançados. Para gerenciar estes novos dispositivos de ponto de extremidade, você deve, entre outras coisas, criar e habilitar uma conta de caixa de correio de recurso do Exchange para o dispositivo e, em seguida, habilitar a conta de recurso para o Skype for Business Online.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csaudioconferencingprovider.md">Get-CsAudioConferencingProvider</a></p></td>
<td><p>Retorna informações sobre os provedores de audioconferência com os quais sua organização assinou contrato.</p>
<p>Um provedor de audioconferência é uma empresa terceirizada que fornece às organizações serviços de conferência, incluindo serviços de alta tecnologia como a tradução instantânea, transcrição e assistência em tempo real ao operador por conferência.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csmeetingconfiguration.md">Get-CsMeetingConfiguration</a><br />
<a href="set-csmeetingconfiguration.md">Set-CsMeetingConfiguration</a></p></td>
<td><p>Controla o tipo de reuniões que os usuários podem criar e determina como as reuniões lidam com usuários anônimos e usuários de conferência discada.</p>
<p>As reuniões (também chamadas de conferências) são parte integrante do Skype for Business Online. Com esses cmdlets, por exemplo, você pode configurar as reuniões para que usuários de discagem não sejam admitidos automaticamente à reunião, mas que sejam encaminhados para o lobby de reunião. Esses usuários de discagem permanecem em espera no lobby até que um apresentador os admita à reunião.</p></td>
</tr>
</tbody>
</table>


Você também pode gerenciar um pequeno subconjunto de propriedades de configuração da reunião usando o centro de administração do Skype for Business Online:

![Propriedades de opções gerais do centro de administração do Lync](images/Dn362833.acf90793-7ee4-4faf-b791-f149dd5df2a5(OCS.15).png "Propriedades de opções gerais do centro de administração do Lync")

## Consulte Também

#### Conceitos

[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)  
[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

