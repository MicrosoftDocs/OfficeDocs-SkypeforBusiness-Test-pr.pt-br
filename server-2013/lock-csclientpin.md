---
title: Lock-CsClientPin
TOCTitle: Lock-CsClientPin
ms:assetid: 81a9895f-96e3-43c9-9dac-8129358e446a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398650(v=OCS.15)
ms:contentKeyID: 49307288
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lock-CsClientPin

 

_**Tópico modificado em:** 2015-03-09_

Permite a um administrador evitar que um usuário utilize a autenticação por número de identificação pessoal (PIN). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Lock-CsClientPin -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

No Exemplo 1, utiliza-se o cmdlet **Lock-CsClientPin** para bloquear o PIN que pertence ao usuário kenmyer@litwareinc.com.

    Lock-CsClientPin -Identity "kenmyer@litwareinc.com"

## EXEMPLO 2

O Exemplo 2 utiliza o cmdlet **Lock-CsClientPin** para bloquear os PINs de todos os usuários que tiverem um PIN. Isto é feito utilizando-se o cmdlet **Get-CsUser** para retornar uma coleção de todos os usuários que tiverem sido habilitados para o Lync Server. Esta coleção será canalizada para o cmdlet **Get-CsClientPinInfo**, que é utilizado em conjunto com o cmdlet **Where-Object**, para retornar uma coleção de usuários cuja propriedade IsPinSet for igual a True. Essa coleção filtrada será então canalizada para o cmdlet **Lock-CsClientPin**, que bloqueará o PIN de cada usuário na coleção.

    Get-CsUser | Get-CsClientPinInfo | Where-Object {$_.IsPinSet -eq $True} | Lock-CsClientPin

## EXEMPLO 3

No Exemplo 3, utiliza-se o cmdlet **Lock-CsClientPin** para bloquear todos os usuários cujos PINs tiverem expirado. Para realizar essa tarefa, chama-se primeiramente o cmdlet **Get-CsUser**, para retornar uma coleção de todos os usuários que estiverem habilitados para o Lync Server. Esta coleção será canalizada para o cmdlet **Get-CsClientPinInfo**, que é utilizado em conjunto com o cmdlet **Where-Object** para limitar a coleção aos usuários cujos PINs tiverem expirado. Para determinar quais usuários possuem PINs expirados, o cmdlet **Where-Object** verifica as contas nas quais a propriedade PinExpirationTime (que indica a data em que o PIN expira) for menor do que a data atual. (a data atual é obtida utilizando-se o cmdlet **Get-Date**.) Se a data de expiração (por exemplo, 1º de setembro de 2010) for menor do que a data atual (por exemplo, 2 de setembro de 2010), o PIN expirou. Depois disso, utiliza-se o cmdlet **Lock-CsClientPin** para bloquear cada um dos PINs expirados.

    Get-CsUser | Get-CsClientPinInfo | Where-Object {$_.PinExpirationTime -lt (Get-Date)} | Lock-CsClientPin

## Descrição detalhada

O Lync Server permite que os usuários se conectem ao sistema ou participem de conferências da rede telefônica pública comutada (PSTN) pelo telefone. Normalmente, o logon no sistema ou a participação de uma conferência exige que o usuário digite um nome de usuário ou uma senha. No entanto, a digitação de um nome de usuário e uma senha pode ser um problema, se você estiver usando um telefone que não possua um teclado alfanumérico. Por isso, o Lync Server permite fornecer aos usuários PINs exclusivamente numéricos. Quando solicitados, os usuários podem fazer o logon no sistema ou participar de uma conferência, digitando o PIN, em vez do nome de usuário e da senha.

Como medida de segurança, o Lync Server permite bloquear o PIN de um usuário. Quando um PIN for bloqueado, o usuário não conseguirá mais utilizá-lo para acessar o sistema ou entrar em uma conferência. (entretanto, esse usuário ainda conseguirá acessar o sistema e entrar em conferências utilizando um aplicativo como o Lync 2013 e fornecendo um nome de usuário e uma senha.) Depois que um PIN tiver sido bloqueado, a única forma de restaurá-lo (e os privilégios de acesso do usuário) envolve o seu desbloqueio, por um administrador. Isso pode ser feito utilizando-se o cmdlet **Unlock-CsClientPin**.

O cmdlet **Lock-CsClientPin** permite aos administradores impedirem temporariamente um usuário de acessar o sistema utilizando a autenticação por PIN. Os PINs também podem ser bloqueados pelo sistema: se um usuário falhar repetidamente em fazer o logon no sistema, o seu PIN será bloqueado automaticamente e, novamente, necessitará do desbloqueio por um administrador.

Observe que, por padrão, não se habilitam as exceções de firewall do SQL Server Express ao se instalar a Standard Edition do Lync Server. Isso significa que será possível executar o cmdlet **Lock-CsClientPin** em uma instância remota do Windows PowerShell porque o comando não conseguirá atravessar o firewall e acessar o banco de dados do SQL Server Express. (no entanto, ainda será possível executar o cmdlet localmente no próprio servidor Standard Edition). Para executar o cmdlet **Lock-CsClientPin** remotamente, será necessário habilitar manualmente as exceções do firewall para o SQL Server Express.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Lock-CsClientPin** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Lock-CsClientPin"}

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Identidade da conta do usuário cujo PIN deverá ser bloqueado. As identidades de usuário podem ser especificadas usando-se um dos quatro formatos a seguir: 1) O endereço SIP do usuário, 2) o UPN (nome principal de usuário), 3) o nome de domínio e nome de logon do usuário, na forma domínio\logon (por exemplo: litwareinc\kenmyer) e 4) o nome de exibição do usuário no Active Directory (por exemplo: Ken Myer). Também é possível fazer referência às Identidades de usuário utilizando-se o nome diferenciado do usuário no Active Directory.</p>
<p>Além disso, é possível utilizar o caractere curinga asterisco (*) ao utilizar o nome de exibição como identidade do usuário. Por exemplo: a identidade &quot;* Smith&quot; retornará todos os usuários com nome de exibição que terminarem com o valor da cadeia de caracteres &quot; Smith&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Valor de cadeia de caracteres ou objeto Microsoft.Rtc.Management.ADConnect.Schema.ADUser. O cmdlet **Lock-CsClientPin** aceita entradas canalizadas de valores de cadeia de caracteres que representam a Identidade de uma conta de usuário. O cmdlet também aceita entradas canalizadas de objetos de usuário.

## Tipos de retorno

O cmdlet **Lock-CsClientPin** não retorna um valor ou objeto. Em vez disso, o cmdlet configura uma ou mais instâncias do objeto Microsoft.Rtc.Management.UserPinService.PinInfoDetails.

## Consulte Também

#### Outros Recursos

[Get-CsClientPinInfo](get-csclientpininfo.md)  
[Set-CsClientPin](set-csclientpin.md)  
[Unlock-CsClientPin](unlock-csclientpin.md)

