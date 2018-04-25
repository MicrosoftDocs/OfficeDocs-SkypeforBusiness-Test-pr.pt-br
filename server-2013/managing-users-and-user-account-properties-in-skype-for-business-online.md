---
title: Gerenciamento de Usuários e Propriedades da Conta de Usuário
TOCTitle: Gerenciamento de Usuários e Propriedades da Conta de Usuário
ms:assetid: 5d13ab15-0e12-4bd0-a970-f130de980404
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362790(v=OCS.15)
ms:contentKeyID: 56270393
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciamento de Usuários e Propriedades da Conta de Usuário

 

_**Tópico modificado em:** 2015-06-22_

Os seguintes cmdlets gerenciam Skype for Business Online as contas de usuários.


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
<td><p><a href="get-csonlineuser.md">Get-CsOnlineUser</a></p></td>
<td><p>Devolve informações sobre os usuários que têm contas hospedads em seu Skype for Business Online locatário.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-csuseracp.md">Get-CsUserAcp</a><br />
<a href="remove-csuseracp.md">Remove-CsUserAcp</a><br />
<a href="set-csuseracp.md">Set-CsUserAcp</a></p></td>
<td><p>Permite que você atribua, modifique ou não atribua um provedor de audioconferência para usuários individuais.</p>
<p>Um provedor de audioconferência é uma empresa de terceiros que oferece organizações com serviços para conferências, incluindo serviços de alta qualidade, como tradução simultânea, transcrição e assistência ao operador na conferência.</p>
<p>Esses cmdlets não devolvem as informações sobre os fornecedores de áudio disponíveis que são atribuídos a esses usuários. Para essa informação, execute este comando:</p>
<pre><code>Get-CsAudioConferencingProvider</code></pre></td>
</tr>
</tbody>
</table>



> [!WARNING]
> O Set-CsUser cmdlet também está incluído no conjunto de cmdlets disponíveis para os administradores Skype for Business Online. No entanto, o Set-CsUser não pode ser usado gerenciado atualmente.Skype for Business Online, exceto para a configuração do parâmetro AudioVideoDisabled. Se você tentar executar o cmdlet com outro parâmetro, ele falhará com uma mensagem de erro similar a esta:<BR>Impossível definir o “SipAddress”. Este parâmetro é restrito com o Locatário Remoto PowerShell.



Os provedores de audioconferências podem também ser atribuídos a (ou nã atribuídos) contas de usuários, usando o Skype for Business Online centro do administrador:

![Propriedades de conferência de discagem do centro de administração do Lync](images/Dn362790.0c61f0c2-8aef-4020-a0a8-02580d43092a(OCS.15).png "Propriedades de conferência de discagem do centro de administração do Lync")

## Consulte Também

#### Conceitos

[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)  
[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

