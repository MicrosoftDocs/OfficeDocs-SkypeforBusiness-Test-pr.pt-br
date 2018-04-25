---
title: New-CsEdgeDomainPattern
TOCTitle: New-CsEdgeDomainPattern
ms:assetid: 653bc148-c22b-4ad4-afdd-17aaeaa299d2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994040(v=OCS.15)
ms:contentKeyID: 52057648
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsEdgeDomainPattern

 

_**Tópico modificado em:** 2015-03-09_

Usado para especificar um domínio que será adicionado ou removido do conjunto de domínios habilitados para federação ou do conjunto de domínios desabilitados para federação. Você deve usar o cmdlet **New-CsEdgeDomainPattern** ao modificar as listas de domínios bloqueados ou permitidos. Os valores de cadeia de caracteres (como "fabrikam.com") não podem ser passados diretamente para os cmdlets usados para gerenciar qualquer uma dessas listas.

O cmdlet **New-CsEdgeDomainPattern** pode ser usado apenas com Skype for Business Online.

## Sintaxe

    New-CsEdgeDomainPattern -Domain <String> [-Verbose]

## Exemplos

## Exemplo 1

O Exemplo 1 demonstra como você pode atribuir um único domínio à lista de domínios bloqueados para um locatário especificado. Para fazer isso, o primeiro comando no exemplo cria um objeto para o domínio fabrikam.com; isso é feito chamando o cmdlet **New-CsEdgeDomainPattern** e salvando o objeto de domínio resultante em uma variável chamada $x. O segundo comando usa o cmdlet **Set-CsTenantFederationConfiguration** e o parâmetro BlockedDomains para configurar fabrikam.com como único domínio bloqueado pelo locatário com a TenantId "bf19b7db-6960-41e5-a139-2aa373474354".

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $x

## Descrição detalhada

Federação é um serviço que permite aos usuários trocarem MI e informações de presença com os usuários de outros domínios. Com Skype for Business Online, os administradores podem usar as definições de configuração da federação para controlar:

  - Se os usuários podem ou não se comunicar com pessoas de outros domínios e se puderem, com quais domínos eles têm permissão para a comunicação.

  - Se os usuários podem ou não se comunicar com pessoas que têm contas na MI pública e provedores de presença, como o Windows Live, AOL e Yahoo.

A federação é gerenciada, em parte, usando listas de domínios permitidos e de domínios bloqueados. A lista de domínios permitidos especifica os domínios com os quais os usuários têm permissão de se comunicar; a lista de domínios bloqueados especifica os domínios com os quais os usuários não têm permissão de se comunicar. Por padrão, os usuários podem se comunicar com qualquer domínio que não apareça na lista de bloqueados. Entretanto, os administradores podem modificar essa configuração padrão e limitar a comunicação com os domínios que estejam na lista de domínios permitidos.

O Skype for Business Online não permite que você modifique diretamente a lista de domínios permitidos ou a lista de domínios bloqueados; por exemplo, você não pode usar um comando similar a esse, que passa um valor de cadeia de caracteres que representa um nome de domínio para a lista de domínios bloqueados:

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains "fabrikam.com"

Em vez disso, você deve criar um objeto de domínio usando o cmdlet **New-CsEdgeDomainPattern**, armazenar esse objeto de domínio em uma variável (neste exemplo, $x) e passar o nome da variável para a lista de domínios bloqueados:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -BlockedDomains $x

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
<td><p><em>Domain</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Nome de domínio totalmente qualificado do domínio a ser adicionado à lista de domínios permitidos. Por exemplo:</p>
<p>-Domain &quot;fabrikam.com&quot;</p>
<p>Observe que você não pode usar caracteres curinga ao especificar um nome de domínio.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **New-CsEdgeDomainPattern** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **New-CsEdgeDomainPattern** cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DomainPattern.

## Consulte Também

#### Outros Recursos

[New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)  
[New-CsEdgeAllowList](new-csedgeallowlist.md)  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

