---
title: Gerenciando a Unificação de Mensagens do Exchange e a caixa-postal hospedada
TOCTitle: Gerenciando a Unificação de Mensagens do Exchange e a caixa-postal hospedada
ms:assetid: 844bf8d5-e093-4dcd-abcf-48dc70e8c73c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362822(v=OCS.15)
ms:contentKeyID: 56270438
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando a Unificação de Mensagens do Exchange e a caixa-postal hospedada

 

_**Tópico modificado em:** 2015-06-22_

Os seguintes cmdlets podem ser usados para gerenciar as políticas de Unificação de Mensagens (UM) e caixa-postal hospedada do Exchange:


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
<td><p><a href="get-csexumcontact.md">Get-CsExUmContact</a></p>
<p><a href="new-csexumcontact.md">New-CsExUmContact</a></p>
<p><a href="remove-csexumcontact.md">Remove-CsExUmContact</a></p>
<p><a href="set-csexumcontact.md">Set-CsExUmContact</a></p></td>
<td><p>Cria e gerencia objetos de contato usados para os serviços de Atendedor Automático e Acesso do Assinante, quando o UM do Exchange é um serviço hospedado.</p>
<p>O Skype for Business Online funciona com o UM do Exchange para fornecer diversos recursos relacionados à voz, incluindo Atendedor Automático e Acesso do Assinante. O Atendedor Automático fornece uma maneira de as chamadas serem atendidas automaticamente e roteadas para a pessoa correta. O Acesso do Assinante permite que os usuários se conectem ao UM do Exchange e recuperem emails, mensagens de voz, contatos e informações do calendário.</p>
<p>Quando o UM do Exchange é fornecido como um serviço hospedado, é necessário criar objetos de contato usados para os serviços de Atendedor Automático e Acesso do Assinante, usando o Windows PowerShell. Esses objetos são criados e gerenciados usando os cmdlets CsExUmContact.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cshostedvoicemailpolicy.md">Get-CsHostedVoicemailPolicy</a></p>
<p><a href="grant-cshostedvoicemailpolicy.md">Grant-CsHostedVoicemailPolicy</a></p></td>
<td><p>Gerencia as políticas de caixa-postal hospedada usadas na organização. As políticas de caixa-postal hospedada especificam como chamadas não atendidas são roteadas para o serviço de UM do Exchange. Essas políticas afetam apenas usuários que foram habilitados para a caixa-postal hospedada do UM do Exchange. Para confirmar se um usuário está habilitado para caixa-postal hospedada, execute um comando semelhante a este no prompt do Windows PowerShell:</p>
<pre><code>Get-CsOnlineUser -Identity &quot;kenmyer@litwareinc.com&quot; | Select-Object HostedVoiceMail</code></pre></td>
</tr>
</tbody>
</table>


Não é possível gerenciar configurações de UM do Exchange e políticas de caixa-postal hospedada usando o Centro de administração do Skype for Business Online.

## Consulte Também

#### Conceitos

[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)  
[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

