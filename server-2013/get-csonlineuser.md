---
title: Get-CsOnlineUser
TOCTitle: Get-CsOnlineUser
ms:assetid: 2bfafd70-a7d9-4308-a353-5ecf44249b53
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994026(v=OCS.15)
ms:contentKeyID: 52057589
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsOnlineUser

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os usuários que têm contas hospedadas no Microsoft Lync Online. Este cmdlet só pode ser usado com o Skype for Business Online.

## Sintaxe

    Get-CsOnlineUser [[-Identity] <UserIdParameter>] [-Filter <String>] [-LdapFilter <String>] [-OnOfficeCommunicationServer] [-OnLyncServer] [-UnAssignedUser] [-OU <OUIdParameter>] [-DomainController <Fqdn>] [-Credential <PSCredential>] [-ResultSize <Unlimited`1>] [-Verbose]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 retorna informações de todos os usuários configurados como usuários online.

    Get-CsOnlineUser

## Exemplo 2

As informações do Exemplo 2 são retornadas para um único usuário online: o usuário com o endereço SIP "sip:kenmyer@litwareinc.com".

    Get-CsOnlineUser -Identity "sip:kenmyer@litwareinc.com"

## Exemplo 3

O comando mostrado no Exemplo 3 retorna informações de todos os usuários online que foram habilitados para o Lync Online, mas não foram atribuídos a um pool do Registrador Avançado.

    Get-CsOnlineUser -UnassignedUser

## Exemplo 4

O Exemplo 4 usa o parâmetro Filter para limitar os dados retornados aos usuários online que receberam a política de arquivamento por usuário RedmondArchiving. Para fazer isso, o valor de filtro {ArchivingPolicy -eq "RedmondArchiving"} é utilizado; essa sintaxe limita os dados retornados aos usuários em que a propriedade ArchivingPolicy é igual a (-eq) "RedmondArchiving".

    Get-CsOnlineUser -Filter {ArchivingPolicy -eq "RedmondArchiving"}

## Exemplo 5

O Exemplo 5 retorna informações somente de contas de usuário que foram configuradas para que a conta não apareça na lista de endereços do Microsoft Exchange. (Ou seja, o atributo msExchHideFromAddressLists do Active Directory é True.) Para realizar essa tarefa, o parâmetro Filter é incluído junto com o valor de filtro {HideFromAddressLists -eq $True}.

    Get-CsOnlineUser -Filter {HideFromAddressLists -eq $True}

## Exemplo 6

O comando mostrado no Exemplo 6 retorna informações de todos os usuários online atribuídos ao locatários com a TenantID "bf19b7db-6960-41e5-a139-2aa373474354". Para realizar a tarefa, o comando inclui o parâmetro Filter junto com o valor de filtro {TenantId –eq "bf19b7db-6960-41e5-a139-2aa373474354"}. Esse filtro limita os dados retornados aos usuários online atribuídos ao locatário "bf19b7db-6960-41e5-a139-2aa373474354".

    Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}

## Descrição detalhada

O cmdlete **Get-CsOnlineUser** retorna informações sobre usuários que têm contas hospedadas em Microsoft Lync Online. As informações retornadas incluem os dados padrão da conta do Active Directory (como departamento em que o usuário trabalha, seu endereço e número de telefone etc.), bem como informações específicas do Lync Server: o cmdlet **Get-CsOnlineUser** informa, por exemplo, se o usuário está ou não habilitado para o Enterprise Voice e quais políticas por usuário (se houver alguma) foram atribuídas ao usuário.

Observe que o cmdlet **Get-CsOnlineUser** não tem um parâmetro TenantId; isso significa que você não pode usar um comando similar a esse para limitar os dados retornados aos usuários que têm contas com um locatário específico do Lync Online:

    Get-CsOnlineUser -TenantId "bf19b7db-6960-41e5-a139-2aa373474354"

No entanto, se você tem vários locatários do Lync Online, poderá retornar usuários de um locatário especificado usando o parâmetro Filter e um comando similar a este:

    Get-CsOnlineUser -Filter {TenantId -eq "bf19b7db-6960-41e5-a139-2aa373474354"}

Esse comando limitará os dados retornados às contas de usuário que pertencem ao locatário com a TenantId "bf19b7db-6960-41e5-a139-2aa373474354". Se você não conhecer usas IDs de locatário, use este comando para retornar essas informações:

    Get-CsTenant

Se você tiver uma implantação híbrida ou de "domínio dividido" (ou seja, uma implantação em que alguns usuários tenham contas hospedadas em Lync Online, enquanto outros usuários têm contas hospedadas em uma versão local do Lync Server, tenha em mente que o cmdlet **Get-CsOnlineUser** retornará apenas informações de usuários do Lync Online. No entanto, o cmdlet [Get-CsUser](get-csuser.md) retornará informações de usuários do Lync Online de usuários Lync Server local. Se você quiser excluir os usuários do Lync Online dos dados retornados pelo cmdlet **Get-CsUser**, use o seguinte comando:

    Get-CsUser -Filter {TenantId -eq "00000000-0000-0000-0000-000000000000"}

Por definição, os usuários hospedados na versão local do Lync Server sempre terão uma TenantId igual a 00000000-0000-0000-0000-000000000000. Os usuários hospedados no Lync Online terão uma TenantId igual a algum valor diferente de 00000000-0000-0000-0000-000000000000.

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
<td><p><em>Credential</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Permite a você executar o cmdlet <strong>Get-CsOnlineUser</strong> usando credenciais alternativas. Isso pode ser necessário se a conta que você usou para fazer logon no Windows não tiver os privilégios necessários para se trabalhar com objetos de usuário.</p>
<p>Para usar o parâmetro Credential, primeiro crie um objeto PSCredential usando o cmdlet <strong>Get-Credential</strong>. Para obter mais detalhes, consulte o tópico de Ajuda do cmdlet <strong>Get-Credential</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Permite que você se conecte a um controlador de domínio especificado para recuperar informações de usuário. Para conectar-se a um controlador de domínio em particular, inclua o parâmetro DomainController seguido do FQDN (nome de domínio totalmente qualificado) (por exemplo, atl-cs-001.litwareinc.com).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite que você limite os dados retornados filtrando atributos específicos do Lync Server. Por exemplo, você pode limitar os dados retornados aos usuários que receberam uma política de voz específica ou aos usuários que não receberam uma política de voz específica.</p>
<p>O parâmetro Filter usa a mesma sintaxe de filtragem do Windows PowerShell usada pelo cmdlet Where-Object. Por exemplo, um filtro que retorna somente usuários habilitados para o Enterprise Voice teria a seguinte aparência, com EnterpriseVoiceEnabled representando o atributo do Active Directory, -eq representando o operador de comparação (igual a) e $True (uma variável interna do Windows PowerShell) representando o valor de filtro:</p>
<p>{EnterpriseVoiceEnabled -eq $True}</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Indica a identidade da conta de usuário a ser recuperada. As identidades de usuários podem ser especificadas usando um de quatro formatos: 1) O endereço SIP do usuário; 2) o nome UPN do usuário; 3) o nome de domínio do usuário e nome de logon, na forma domínio\logon (por exemplo, litwareinc\kenmyer); e, 4) o nome de exibição do Active Directory do usuário (por exemplo, Ken Myer). Também é possível fazer referência a uma conta de usuário com o nome diferenciado do Active Directory.</p>
<p>Você pode usar o caractere curinga asterisco (*) ao usar o nome para exibição como identidade do usuário. Por exemplo, a identidade &quot;* Smith&quot; retornaria todos os usuários com nome para exibição que termine com &quot; Smith&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite limitar os dados retornados filtrando atributos genéricos do Active Directory (ou seja, atributos que não são específicos do Lync Server). Por exemplo, você pode limitar os dados retornados aos usuários que trabalham em um departamento específico ou aos usuários que têm um gerente ou cargo específico.</p>
<p>O parâmetro LDAPFilter usa o idioma de consulta LDAP ao criar filtros. Por exemplo, um filtro que retorna somente os usuários que trabalham na cidade de Redmond seria assim: &quot;l=Redmond&quot;, onde &quot;l&quot; (L minúsculo) representa o atributo do Active Directory (localidade); &quot;=&quot; representa o operador de comparação (igual a); e &quot;Redmond&quot; representa o valor do filtro.</p></td>
</tr>
<tr class="even">
<td><p><em>OnLyncServer</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retorna uma coleção de usuários hospedados no Lync Server. Usuários com contas em versões anteriores do software não serão retornados quando você usar esse parâmetro.</p></td>
</tr>
<tr class="odd">
<td><p><em>OnOfficeCommunicationServer</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retorna uma coleção de usuários hospedados em uma versão anterior do Lync Server (por exemplo, Microsoft Office Communications Server 2007 R2). Usuários com contas na versão corrente do software não serão retornados quando você usar esse parâmetro.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Permite retornar informações sobre contas de usuário de uma unidade organizacional (OU) ou contêiner específicos. O parâmetro OU retorna dados da OU especificada e de qualquer de suas OUs filhas. Por exemplo, se a OU Finance tiver duas OUs filhas, AccountsPayable e AccountsReceivable, os dados retornados incluirão usuários de cada uma dessas três OUs.</p>
<p>Ao especificar uma OU, use o DN (nome diferenciado) do contêiner em questão; por exemplo: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;. Para retornar contas de usuário do contêiner Usuários, use esta sintaxe:</p>
<p>-OU &quot;cn=Users,dc=litwareinc,dc=com&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>Permite limitar o número de registros retornados pelo cmdlet. Por exemplo, para retornar sete usuários (independentemente do número de usuários existentes em sua floresta), inclua o parâmetro ResultSize e defina seu valor como 7. Observe que não há como garantir quais serão os sete usuários retornados.</p>
<p>O tamanho do resultado pode ser definido com qualquer número inteiro entre 0 e 2147483647, inclusive. Se for definido com 0, o comando será executado mas nenhum dado será retornado. Se você definir o ResultSize com 7, mas tiver apenas três usuários em sua floresta, o comando retornará esses três usuários e, em seguida, será concluído sem erros.</p></td>
</tr>
<tr class="even">
<td><p><em>UnassignedUser</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Permite que você retorne uma coleção de todos os usuários que foram habilitados para o Lync Online, mas não estão atribuídos ao pool de um Registrador Avançado. Os usuários não têm permissão para fazer logon, a menos que recebam o pool de um Registrador Avançado.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

O cmdlet **Get-CsOnlineUser** aceita instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADUser que entram em pipeline, bem como valores de cadeia de caracteres que representam uma identidade de conta de usuário válida (por exemplo, "sip:kenmyer@litwareinc.com").

## Tipos de retorno

O cmdlet **Get-CsOnlineUser** retorna instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.ADOCOnlineUser.

## Consulte Também

#### Outros Recursos

[Get-CsUser](get-csuser.md)

