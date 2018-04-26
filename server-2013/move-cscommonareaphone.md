---
title: Move-CsCommonAreaPhone
TOCTitle: Move-CsCommonAreaPhone
ms:assetid: af5f832c-1be9-4495-ba1a-c10ca50d7b29
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412837(v=OCS.15)
ms:contentKeyID: 49307794
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Move-CsCommonAreaPhone

 

_**Tópico modificado em:** 2015-04-02_

Move um ou mais telefones de área comum para um novo pool de Registrador. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Move-CsCommonAreaPhone -Identity <UserIdParameter> -Target <Fqdn> [-Confirm [<SwitchParameter>]] [-DomainController <Fqdn>] [-Force <SwitchParameter>] [-IgnoreBackendStoreException <SwitchParameter>] [-PassThru <SwitchParameter>] [-ProxyPool <Fqdn>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 move o telefone de área comum com Identidade CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com para o pool de registradores atl-cs-001.litwareinc.com.

    Move-CsCommonAreaPhone -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -Target atl-cs-001.litwareinc.com

## EXEMPLO 2

No Exemplo 2, o telefone de área comum com o nome para exibição no Active Directory "Building 31 Cafeteria" é movido para o pool de registradores atl-cs-001.litwareinc.com. Para isso, o cmdlet **Get-CsCommonAreaPhone** é chamado primeiro, sem nenhum parâmetro, para retornar um conjunto de todos os telefones de área comum atualmente em uso na organização. Em seguida, esse conjunto é direcionado para o cmdlet **Where-Object**, que seleciona apenas os telefones nos quais o atributo DisplayName é igual a "Building 31 Cafeteria". Em seguida, o conjunto filtrado é direcionado para o cmdlet **Move-CsCommonAreaPhone**, que move cada telefone do conjunto para atl-cs-001.litwareinc.com.

    Get-CsCommonAreaPhone | Where-Object {$_.DisplayName -eq "Building 31 Cafeteria"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com

## EXEMPLO 3

O Exemplo 3 move todos os telefones de área comum hospedados no pool de registradores dublin-cs-001.litwareinc.com para o pool de registradores atl-cs-001.litwareinc.com. Para executar esta tarefa, o comando primeiro chama o cmdlet **Get-CsCommonAreaPhone** sem nenhum parâmetro; isso retorna um conjunto de todos os telefones de área comum configurados para uso na organização. Em seguida, esse conjunto é direcionado para o cmdlet **Where-Object**, que seleciona todos os telefones de área comum nos quais RegistrarPool é igual a dublin-cs-001.litwareinc.com. Em seguida, esse conjunto é direcionado para o cmdlet **Move-CsCommonAreaPhone**, que move cada telefone na coleção para o novo pool de registradores atl-cs-001.litwareinc.com.

    Get-CsCommonAreaPhone | Where-Object {$_.RegistrarPool -match "dublin-cs-001.litwareinc.com"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com

## EXEMPLO 4

O Exemplo 4 é uma variação do comando exibido no Exemplo 3; neste caso, porém, os telefones de área comum não apenas são movidos para um novo pool de registradores, como também são atribuídos a uma nova diretiva de voz por usuário. Para isso, o parâmetro PassThru é incluído ao chamar o cmdlet **Move-CsCommonAreaPhone**; isso é necessário para passar os objetos do telefone de área comum pela pipeline (por padrão, o cmdlet **Move-CsCommonAreaPhone** não passa objetos pela pipeline). Depois de mover os telefones, os objetos de telefone são direcionados para o cmdlet **Grant-CsVoicePolicy**, que atribui a diretiva de voz AtlantaVoicePolicy a todos os telefones recém-movidos.

    Get-CsCommonAreaPhone | Where-Object {$_.RegistrarPool -match "dublin-cs-001.litwareinc.com"} | Move-CsCommonAreaPhone -Target atl-cs-001.litwareinc.com -PassThru | Grant-CsVoicePolicy -PolicyName AtlantaVoicePolicy

## Descrição detalhada

Telefones de área comum são telefones IP que não estão associados a um usuário individual. Em vez de estarem localizados no escritório de alguém, esses telefones geralmente estão localizados em lobbies de edifícios, cafeterias, lounges para funcionários, salas de reuniões e outros locais que possam receber um grande número de pessoas. Isso é um desafio de gerenciamento para os administradores: o uso de um telefone no Lync Server geralmente é mantido usando várias diretivas de voz e planos de discagem, atribuídos a usuários individuais. Os telefones de área comum não são atribuídos a usuários individuais.

A solução é criar objetos de contato do Active Directory para todos os seus telefones de área comum (esses objetos de contato podem ser criados com o cmdlet **New-CsCommonAreaPhone**). Assim como as contas de usuário, esses objetos de contato podem ser atribuídos a diretivas e planos de voz. Com isso, é possível manter o controle sobre os telefones de área comum mesmo que não estejam associados a um usuário individual. Por exemplo, se você não quiser que as pessoas possam transferir ou estacionar chamadas em um telefone de área comum, crie uma diretiva de voz que proíba a transferência e o estacionamento de chamadas e atribua essa diretiva ao telefone de área comum (ou, o que seria mais correto, atribua essa diretiva ao objeto de contato que representa o telefone de área comum).

O cmdlet **Move-CsCommonAreaPhone** permite mover um telefone de área comum existente para um novo pool de registradores.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Move-CsCommonAreaPhone** localmente: RTCUniversalUserAdmins. Permissões para executar este cmdlet para sites específicos ou UOs (unidades organizacionais) do Active Directory específicas podem ser atribuídas com o cmdlet **Grant-CsOUPermission**. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Move-CsCommonAreaPhone"}

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
<td><p>Identificador exclusivo do telefone de área comum. Os telefones de área comum são identificados usando o nome diferenciado do Active Directory do objeto de contato associado. Por padrão, telefones de área comum usam um GUID (identificador global exclusivo) como nome comum; ou seja, os telefones geralmente terão uma Identidade semelhante a esta: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.</p></td>
</tr>
<tr class="even">
<td><p><em>Target</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>O FQDN (nome de domínio totalmente qualificado) do pool de registradores para o qual o telefone de área comum deve ser movido; por exemplo: atl-cs-001.litwareinc.com. Além de um pool de registradores, o Target pode ser também o FQDN de um provedor de hospedagem.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Permite sua conexão ao controlador de domínio especificado para mover o telefone de área comum. Para se conectar a um determinado controlador de domínio, inclua o parâmetro DomainController seguido pelo nome do computador (por exemplo, atl-cs-001) ou por seu FQDN (por exemplo, atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Se presente, move o telefone de área comum mas exclui quaisquer dados associados (como diretivas que foram atribuídas ao dispositivo). Se não estiver presente, o telefone é movido junto com quaisquer dados associados.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreBackendStoreException</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, instrui o computador a ignorar quaisquer erros que possam ocorrer com o banco de dados de back-end e tentar mover o telefone de área comum apesar desses erros.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Permite passar um objeto de usuário através da pipeline que representa a conta de usuário que está sendo movida. Por padrão, o cmdlet <strong>Move-CsCommonAreaPhone</strong> não passa objetos pela pipeline.</p></td>
</tr>
<tr class="even">
<td><p><em>ProxyPool</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Este parâmetro é usado somente para o Lync Online. Não deve ser usado com uma implementação local do Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

String. O cmdlet **Move-CsCommonAreaPhone** aceita um valor de cadeia de caracteres por pipeline que representa a Identidade do telefone de área comum.

## Tipos de retorno

Por padrão, o cmdlet **Move-CsCommonAreaPhone** não retorna nenhum objeto ou valor. No entanto, se o parâmetro PassThru for incluído, o cmdlet retornará instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact.

## Consulte Também

#### Outros Recursos

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

