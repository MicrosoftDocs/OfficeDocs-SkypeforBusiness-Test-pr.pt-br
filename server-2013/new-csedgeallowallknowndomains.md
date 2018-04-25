---
title: New-CsEdgeAllowAllKnownDomains
TOCTitle: New-CsEdgeAllowAllKnownDomains
ms:assetid: f9416909-c328-41b3-9215-7ebd091b0ca0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994088(v=OCS.15)
ms:contentKeyID: 52057774
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsEdgeAllowAllKnownDomains

 

_**Tópico modificado em:** 2015-03-09_

Habilita a federação do Microsoft Lync Online com todos os domínios, exceto para os domínios incluídos na lista de domínios bloqueados.

Este cmdlet pode ser usado apenas com o Skype for Business Online.

## Sintaxe

    New-CsEdgeAllowAllKnownDomains [-Verbose]

## Exemplos

## Exemplo 1

Os dois comandos mostrados no Exemplo 1 definem as configurações de federação do locatário com a identidade "bf19b7db-6960-41e5-a139-2aa373474354" para permitir todos os domínios conhecidos. Para fazer isso, o primeiro comando do exemplo usa o cmdlet **New-CsEdgeAllowAllKnownDomains** para criar uma instância do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowAllKnownDomains; essa instância é armazenada em uma variável chamada $x. No segundo comando, o cmdlet **Set-CsTenantFederationConfiguration** é chamado junto com o parâmetro AllowedDomains; o uso de $x como valor de parâmetro define as configurações de federação para permitir todos os domínios conhecidos.

    $x = New-CsEdgeAllowAllKnownDomains
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $x

## Exemplo 2

O Exemplo 2 demonstra como você pode configurar todos os locatários para permitir a comunicação com todos os domínios que não estão explicitamente exibidos na lista de domínios bloqueados. Para fazer isso, o primeiro comando no exemplo usa o cmdlet **New-CsEdgeAllowAllKnownDomains** para criar uma instância do objeto AllowAllKnownDomains, que é armazenado em uma variável chamada $x.

O segundo comando do exemplo usa o cmdlet **Get-CsTenant** para retornar uma coleção de todos os locatários disponíveis. Essa coleção é, então, conectada ao cmdlet **ForEach-Object**. O cmdlet **ForEach-Object**, por sua vez, executa o cmdlet **Set-CsTenantFederationConfiguration** em cada locatário da coleção, configurando a propriedade AllowedDomains para permitir todos os domínios conhecidos.

    $x = New-CsEdgeAllowAllKnownDomains
    Get-CsTenant | ForEach-Object {Set-CsTenantFederationConfiguration -Tenant $_.TenantID -AllowedDomains $x}

## Descrição detalhada

Federação é um serviço que permite aos usuários trocarem MI e informações de presença com os usuários de outros domínios. Com Lync Online, os administradores podem usar as definições de configuração da federação para controlar:

  - Se os usuários podem ou não se comunicar com pessoas de outros domínios e se puderem, com quais domínos eles têm permissão para a comunicação.

  - Se os usuários podem ou não se comunicar com pessoas que têm contas na MI pública e provedores de presença, como o Windows Live, AOL e Yahoo.

A federação é gerenciada, em parte, usando listas de domínios permitidos e de domínios bloqueados. A lista de domínios permitidos especifica os domínios com os quais os usuários têm permissão de se comunicar; a lista de domínios bloqueados especifica os domínios com os quais os usuários não têm permissão de se comunicar. Por padrão, os usuários podem se comunicar com qualquer domínio que não apareça na lista de bloqueados. Entretanto, os administradores podem modificar essa configuração padrão e limitar a comunicação com os domínios que estejam na lista de domínios permitidos.

O Lync Online não permite que você modifique diretamente a lista de permitidos ou a lista de bloqueados; por exemplo, não é possível usar um comando semelhante a esse, que passa um valor de cadeia de caracteres que representa um nome de domínio para a lista de domínios permitidos:

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains "fabrikam.com"

Em vez disso, você deve usar o cmdlet **New-CsEdgeAllowAllKnownDomains** ou **New-CsEdgeAllowList** para criar o objeto de domínio e passá-lo ao cmdlet **Set-CsTenantFederationConfiguration**. O cmdlet **New-CsEdgeAllowAllKnownDomains** será usado se você quiser permitir que os usuários se comuniquem com todos os domínios, exceto os expressamente especificados na lista de domínios bloqueados. O cmdlet N**ew-CsEdgeAllowList** será usado se você quiser limitar a comunicação do usuário a uma coleção especificada de domínios. Nesse caso, os usuários só poderão se comunicar com domínios que apareçam na lista de domínios permitidos.

Para configurar a federação com todos os domínios conhecidos, use um conjunto de comandos similar a este:

    $x = New-CsEdgeAllowAllKnownDomains
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $x

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
<td><p>Este cmdlet fornece apenas os parâmetros comuns do Windows PowerShell.</p></td>
<td><p>N/D</p></td>
<td><p>N/D</p></td>
<td><p>N/D</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **New-CsEdgeAllowAllKnownDomains** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **New-CsEdgeAllowAllKnownDomains** cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowAllKnownDomains.

## Consulte Também

#### Outros Recursos

[New-CsEdgeAllowList](new-csedgeallowlist.md)  
[New-CsEdgeDomainPattern](new-csedgedomainpattern.md)  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

