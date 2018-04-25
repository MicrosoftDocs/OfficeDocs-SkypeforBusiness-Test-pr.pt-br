---
title: Get-CsTenant
TOCTitle: Get-CsTenant
ms:assetid: 7b642117-5ca7-4a5b-bca7-16b0ae694ae2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994044(v=OCS.15)
ms:contentKeyID: 52057640
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenant

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os locatátios do Skype for Business Online que foram configuradas para serem usadas na sua organização. Os locatários representam os grupos de usuários online. Em muitos casos, você talvez precise apenas de um locatário. No entanto, se diferentes grupos de usuários tiverem diferentes necessidades de gerenciamento, o Skype for Business Online oferecerá suporte para que uma única organização tenha vários locatários.

Get-CsTenant só pode ser usado com o Skype for Business Online.

## Sintaxe

    Get-CsTenant [[-Identity] <OUIdParameter>] [-Filter <String>] [-ResultSize <Unlimited`1>] [-Verbose]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 retorna informações sobre todos os locatários configurados para uso na organização.

    Get-CsTenant

## Exemplo 2

No Exemplo 2, são retornadas informações de um único locatário: o locatário com a identidade "bf19b7db-6960-41e5-a139-2aa373474354".

    Get-CsTenant -Identity "bf19b7db-6960-41e5-a139-2aa373474354"

## Exemplo 3

O comando anterior mostra uma forma alternativa de retornar informações sobre um único locatário; neste exemplo, isso é feito com a inclusão do parâmetro Filter e do valor de filtro {DisplayName –eq "Fabrikam"}. Essa sintaxe retorna informações somentre do locatário que tem o nome de exibição Fabrikam.

    Get-CsTenant -Filter {DisplayName -eq "Fabrikam"}

## Exemplo 4

O comando mostrado no Exemplo 4 retorna informações de todos os locatários que têm ServiceInstance igual a "LitwareincCommunicationsOnline/San Antonio". Para fazer isso, o comando inclui o parâmetro Filter e o valor de filtro {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}. Esse valor de filtro limita os dados retornados a locatários que têm a propriedade ServiceInstance igual a (-eq) "LitwareincCommunicationsOnline/San Antonio".

    Get-CsTenant -Filter {ServiceInstance -eq "LitwareincCommunicationsOnline/San Antonio"}

## Exemplo 5

O Exemplo 5 retorna informações de todos os locatários que têm um nome de exibição de país ou região igual a Austrália. Isso é feito usando o parâmetro Filter e o valor de parâmetro {CountryOrRegionDisplayName -eq "Austrália"}.

    Get-CsTenant -Filter {CountryOrRegionDisplayName -eq "Australia"}

## Descrição detalhada

No Skype for Business Online, os locatários representam grupos de usuários que têm contas hospedadas no serviço. Muitas organizações exigirão um único locatário, no qual serão hospedadas todas as suas contas de usuário. No entanto, o gerenciamento do Skype for Business Online é geralmente realizado por locatário; isso significa que todos os usuários do mesmo locatário terão a mesma política de voz, as mesmas configurações de federação etc. Se você precisar gerenciar alguns usuários de uma forma e outros usuários de outra forma, é recomendável o uso de vários locatários, cada um com sua própria coleção de políticas e configurações.

Independentemente do número de locatários que você tem, use o cmdlet **Get-CsTenant** para retornar informações sobre esses locatários.

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite que você retorne dados usando os atributos do Active Directory, sem precisar especificar o nome diferenciado completo do Active Directory. Por exemplo, para recuperar um locatário usando o nome de exibição de locatário, use uma sintaxe semelhante a esta:</p>
<p>Get-CsTenant –Filter {DisplayName –eq &quot;FabrikamTenant&quot;}</p>
<p>Para retornar todos os locatários que usam o domínio Fabrikam, use esta sintaxe:</p>
<p>Get-CsTenant –Filter {Domains –like &quot;*fabrikam*&quot;}</p>
<p>O parâmetro Filter usa a mesma sintaxe de filtragem do Windows PowerShell usada pelo cmdlet Where-Object.</p>
<p>Não é possível usar os parâmetros Filter e Identity no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.AD.OUIdParameter</p></td>
<td><p>O nome diferenciado do Active Directory do locatário. Por exemplo:</p>
<p>-Identity &quot;OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=litwareinc,dc=com&quot;</p>
<p>Se você não incluir a identidade ou o parâmetro Filter, o cmdlet <strong>Get-CsTenant</strong> retornará informações sobre todos os seus locatários.</p></td>
</tr>
<tr class="odd">
<td><p><em>ResultSize</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.ADConnect.Core.Unlimited`1</p></td>
<td><p>Permite limitar o número de registros retornados por um cmdlet. Por exemplo, para retornar sete locatários (independentemente do número de locatários que estão na sua floresta), inclua o parâmetro ResultSize e defina o valor de parâmetro para 7. Observe que não há nenhum modo de garantir quais sete usuários serão retornados.</p>
<p>O tamanho do resultado pode ser definido por qualquer número inteiro entre 0 e 2147483647, inclusive. Se o número for definido como 0, o comando será executado, mas nenhum dado será retornado. Se você definir os locatários como 7, mas tiver somente três contatos na floresta, o comando retornará esses três locatários e será concluído sem erros.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

O cmdlet **Get-CsTenant** aceita instâncias em pipeline do objeto Microsoft.Rtc.Management.ADConnect.Schema.TenantObject, bem como valores de cadeia de caracteres representando a identidade de um locatário Skype for Business Online (por exemplo, "OU=bf19b7db-6960-41e5-a139-2aa373474354,OU=OCS Tenants,dc=vdomain,dc=com").

## Tipos de retorno

O cmdlet **Get-CsTenant** retorna instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.TenantObject.

## Consulte Também

#### Outros Recursos

[Get-CsOnlineUser](get-csonlineuser.md)

