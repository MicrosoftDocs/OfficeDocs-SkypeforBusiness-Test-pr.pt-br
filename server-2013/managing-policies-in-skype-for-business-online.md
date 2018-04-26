---
title: Gerenciar políticas
TOCTitle: Gerenciar políticas
ms:assetid: 91372888-a96e-44db-a0dc-d08facbfce87
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362826(v=OCS.15)
ms:contentKeyID: 56270445
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar políticas

 

_**Tópico modificado em:** 2015-06-22_

Os seguintes cmdlets gerenciam políticas Skype for Business Online. As políticas ajudam a determinar as capacidades Skype for Business Online que estão disponíveis para os usuários e para a organização como um todo.


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
<td><p><a href="get-csclientpolicy.md">Get-CsClientPolicy</a><br />
<a href="grant-csclientpolicy.md">Grant-CsClientPolicy</a></p></td>
<td><p>As políticas de cliente são usadas para determinar os recursos do cliente Lync que estão disponíveis para os usuários. Por exemplo, você pode dar a alguns usuários a capacidade de transferir arquivos, mas não a outros.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csconferencingpolicy.md">Get-CsConferencingPolicy</a><br />
<a href="grant-csconferencingpolicy.md">Grant-CsConferencingPolicy</a></p></td>
<td><p>As políticas de conferência determinam os recursos e as capacidades que podem ser usados ​​em uma conferência. Isso inclui tudo, desde se a conferência pode incluir áudio e vídeo IP ao número máximo de pessoas que podem participar de uma reunião.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csexternalaccesspolicy.md">Get-CsExternalAccessPolicy</a><br />
<a href="grant-csexternalaccesspolicy.md">Grant-CsExternalAccessPolicy</a></p></td>
<td><p>As políticas de acesso externo são usadas ​​para determinar se os usuários têm permissão para se comunicar com usuários de domínios federados, e/ou se os usuários têm permissão para se comunicar com usuários que têm contas em provedores públicos de mensagens instantâneas, como o Windows Live ou AOL.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csvoicepolicy.md">Get-CsVoicePolicy</a><br />
<a href="grant-csvoicepolicy.md">Grant-CsVoicePolicy</a><br />
<a href="remove-csvoicepolicy.md">Remove-CsVoicePolicy</a></p></td>
<td><p>As políticas de voz são usadas ​​para gerenciar recursos do Enterprise Voice, como toques simultâneos (a capacidade de ter um segundo toque do telefone toda vez que alguém ligar para o telefone do escritório) e encaminhamento de chamadas.</p></td>
</tr>
</tbody>
</table>


Você também pode gerenciar as configurações de política de conferência selecionadas usando o centro de administração Skype for Business Online:

![Propriedades de opções gerais do centro de administração do Lync](images/Dn362833.acf90793-7ee4-4faf-b791-f149dd5df2a5(OCS.15).png "Propriedades de opções gerais do centro de administração do Lync")

Você também pode gerenciar as configurações da política de acesso externo usando o centro de administração Skype for Business Online:

![Opções de comunicação externa do centro de administração](images/Dn362826.e5cfb159-b096-463e-b1ef-2b42eb29168a(OCS.15).png "Opções de comunicação externa do centro de administração")

## Consulte Também

#### Conceitos

[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)  
[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

