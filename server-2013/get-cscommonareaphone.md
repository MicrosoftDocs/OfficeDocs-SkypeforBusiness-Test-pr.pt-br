---
title: Get-CsCommonAreaPhone
TOCTitle: Get-CsCommonAreaPhone
ms:assetid: bfb7927b-49a7-4637-a9ff-fd68897efb45
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412934(v=OCS.15)
ms:contentKeyID: 49307986
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCommonAreaPhone

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os telefones de área comum gerenciados, usando o Lync Server. Os telefones de área comum são telefones que estão localizados nos saguões dos edifícios, na área de descanso dos funcionários ou em outras áreas onde provavelmente são usados por diversas pessoas e para diferentes usos. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsCommonAreaPhone [-Identity <UserIdParameter>] [-Credential <PSCredential>] [-DomainController <Fqdn>] [-Filter <String>] [-LdapFilter <String>] [-OU <OUIdParameter>] [-ResultSize <Unlimited>]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 retorna informações sobre todos os telefones de área comum configurados para uso na organização. Isso é feito chamando o cmdlet **Get-CsCommonAreaPhone** sem qualquer parâmetro.

    Get-CsCommonAreaPhone

## EXEMPLO 2

No Exemplo 2, o telefone de área comum cujo nome de exibição no Active Directory é "Building 14 Lobby" é retornado. Essa tarefa é realizada incluindo o parâmetro Filter e o valor de filtro {DisplayName -eq "Building 14 Lobby"}. Esse valor de filtro limita os objetos retornados a telefones de área comum cuja propriedade DisplayName é igual a "Building 14 Lobby".

    Get-CsCommonAreaPhone -Filter {DisplayName -eq "Building 14 Lobby"}

## EXEMPLO 3

O Exemplo 3 retorna todos os telefones de área comum com o nome de exibição no Active Directory que comece com os caracteres "Building 14". Para isso, o cmdlet **Get-CsCommonAreaPhone** é chamado com o parâmetro Filter e o valor de filtro {DisplayName -like "Building 14\*"}. O valor de filtro utiliza o operador -like e a cadeia de caracteres curinga "Building 14\*" para limitar os dados retornados aos telefones cuja propriedade DisplayName comece com "Building 14" (por exemplo, "Building 14 Lobby", "Building 14 Cafeteria", etc.).

    Get-CsCommonAreaPhone  -Filter {DisplayName -like "Building 14*"}

## EXEMPLO 4

No Exemplo 4, é retornado um único telefone de área comum: o telefone que possui a propriedade LineUri igual a "tel:+14255551234". Como LineUris devem ser exclusivas, este comando nunca retornará mais do que um único item.

    Get-CsCommonAreaPhone  -Filter {LineUri -eq "tel:+14255551234"}

## EXEMPLO 5

O comando exibido no Exemplo 5 retorna informações sobre todos os telefones de área comum aos quais não tiver sido atribuído um plano de discagem. Isso é realizado usando o parâmetro Filter e o valor de filtro {DialPlan -eq $Null}, que limita os dados retornados aos telefones cuja propriedade DialPlan for igual a um valor nulo. Se um plano de discagem não tiver sido atribuído explicitamente a um telefone de área comum, o telefone usará automaticamente o plano de discagem global ou, se existir, o plano de discagem atribuído ao site.

    Get-CsCommonAreaPhone -Filter {DialPlan -eq $Null}

## EXEMPLO 6

O Exemplo 6 retorna uma coleção de todos os telefones de área comum que tiverem um objeto de contato na UO Telecommunications do Serviços de Domínio Active Directory. Para isso, o **Get-CsCommonAreaPhone** é chamado com o parâmetro OU. O valor do parâmetro limita os objetos retornados aos telefones que tiverem objetos de contato na UO cujo nome diferenciado for ou=Telecommunications,dc=litwareinc,dc=com.

    Get-CsCommonAreaPhone -OU "ou=Telecommunications,dc=litwareinc,dc=com"

## Descrição detalhada

Os telefones de área comum são telefones IP que não estão associados a um usuário específico. Em vez de estarem localizados no escritório de alguém, os telefones de área comum estão normalmente localizados nos saguões dos edifícios, cafeterias, áreas de descanso dos funcionários, salas de reunião e outros locais em que uma grande quantidade de pessoas costuma se reunir. Isso apresenta aos administradores um desafio de gerenciamento; isso ocorre porque o uso do telefone no Lync Server normalmente é mantido usando políticas de voz e planos de discagem que são atribuídos a usuários específicos. Os telefones de área comum não possuem usuários específicos atribuídos a eles.

A solução para esse desafio é criar objetos de contato no Active Directory em todos os telefones de área comum (esses objetos de contato podem ser criados usando o cmdlet **New-CsCommonAreaPhone**). Como no caso das contas de usuários, é possível atribuir políticas e planos de voz a esses objetos de contato. Como resultado, será possível manter o controle sobre os telefones de área comum, mesmo se não estiverem associados a um usuário específico. Por exemplo: se você não quiser que as pessoas transfiram ou estacionem chamadas de um telefone de área comum, basta criar uma política de voz que proíba as transferências e os estacionamentos de chamadas e, em seguida, atribuir essa política ao telefone de área comum (ou, mais corretamente, ao objeto de contato que representa o telefone de área comum). Por exemplo, esse comando atribui a política de voz CommonAreaPhoneVoicePolicy a todos os telefones de área comum:

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

O cmdlet **Get-CsCommonAreaPhone** permite recuperar informações sobre os telefones de área comum configurados para uso na organização. Se o cmdlet **Get-CsCommonAreaPhone** for chamado sem parâmetros, retornará informações sobre todos os telefones de área comum. Os parâmetros opcionais fornecem diversas formas de filtragem da informação. Por exemplo, é possível retornar todos os telefones de área comum com objetos de contato em uma unidade organizacional (UO) específica, ou todos os objetos de contato localizados em um edifício específico.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsCommonAreaPhone** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins e RTCUniversalReadOnlyAdmins. É possível atribuir permissões para executar esse cmdlet em sites específicos ou UOs específicas do Active Directory, usando o cmdlet **Grant-CsOUPermission**. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCommonAreaPhone"}

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
<td><p>Permite executar o cmdlet <strong>Get-CsCommonAreaPhone</strong> com credenciais alternativas. Isto pode ser necessário se a conta usada para fazer logon no Windows não tiver os privilégios necessários para trabalhar com objetos de contato.</p>
<p>Para usar o parâmetro Credential, primeiro um objeto PSCredential deve ser criado usando o cmdlet <strong>Get-Credential</strong>. Para mais detalhes, consulte o tópico da Ajuda referente ao cmdlet <strong>Get-Credential</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Permite que você se conecte ao controlador de domínio especificado, para recuperar as informações de contato. Para se conectar a um determinado controlador de domínio, inclua o parâmetro DomainController, seguido do nome de domínio totalmente qualificado (FQDN) desse computador (atl-cs-001.litwareinc.com, por exemplo).</p></td>
</tr>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite limitar os dados retornados, filtrando atributos específicos do Lync Server. Por exemplo, é possível limitar os dados retornados a objetos de contato do telefone de área comum aos quais tenha sido atribuída uma política de voz específica, ou a contatos aos quais não tenha sido atribuída uma política de voz específica.</p>
<p>O parâmetro Filter usa a mesma sintaxe de filtragem do Windows PowerShell utilizada pelo cmdlet <strong>Where-Object</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Identificador exclusivo do telefone de área comum. Os telefones de área comum são identificados mediante o uso de um nome diferenciado do objeto de contato associado no Active Directory. Por padrão, os telefones de área comum usam um identificador global exclusivo (GUID) como seu nome comum. Isso significa que os telefones normalmente terão uma identidade semelhante a essa: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.</p></td>
</tr>
<tr class="odd">
<td><p><em>LdapFilter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite limitar os dados retornados, filtrando atributos genéricos do Active Directory (ou seja, atributos que não são específicos do Lync Server). Por exemplo, é possível limitar os dados retornados a objetos de contato aos quais tenha sido atribuído um departamento específico ou que estejam localizados em um edifício específico.</p>
<p>Ao criar filtros, o parâmetro LdapFilter usa a linguagem de consulta LDAP. Por exemplo, um filtro que retorna apenas objetos de contato representando telefones de área comum na cidade de Redmond poderia ter a seguinte aparência:</p>
<p>-LDAPFilter &quot;l=Redmond&quot;</p>
<p>No filtro anterior, &quot;l&quot; (a letra L minúscula) representa o atributo do Active Directory (localidade); &quot;=&quot;, o operador de comparação (igual a) e &quot;Redmond&quot;, o valor de filtro.</p></td>
</tr>
<tr class="even">
<td><p><em>OU</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>Permite retornar objetos de contato de uma unidade organizacional (UO) específica do Active Directory. O parâmetro OU retorna dados da UO especificada e de qualquer uma de suas UOs filhas. Por exemplo: se a UO Finance tiver duas UOs filhas, AccountsPayable e AccountsReceivable, serão retornadas informações sobre telefones de área comum de cada uma das UOs.</p>
<p>Especificando um OU, use o nome diferenciado daquele contêiner; por exemplo: -OU &quot;OU=Finance,dc=litwareinc,dc=com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited</p></td>
<td><p>Permite limitar o número de registros retornados por um comando. Por exemplo: para retornar sete telefones de área comum (independente de quantos telefones de área comum existam na floresta), inclua o parâmetro ResultSize e defina o valor de parâmetro como 7. Observe que não há como garantir quais serão os sete telefones retornados. Se você definir o ResultSize como 7, mas só houver três telefones de área comum na floresta, o comando retornará os três telefones e, em seguida, concluirá sem erro.</p>
<p>O tamanho do resultado pode ser definido por qualquer número inteiro entre 0 e 2147483647, inclusive. Se o número for definido como 0, o comando será executado, mas nenhum dado será retornado.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

String. O cmdlet **Get-CsCommonAreaPhone** aceita um valor direcionado de cadeia de caracteres, que representa a Identidade do telefone de área comum.

## Tipos de retorno

O cmdlet **Get-CsCommonAreaPhone** retorna instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact.

## Consulte Também

#### Outros Recursos

[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)  
[Set-CsCommonAreaPhone](set-cscommonareaphone.md)

