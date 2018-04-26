---
title: New-CsEdgeAllowList
TOCTitle: New-CsEdgeAllowList
ms:assetid: 21a6d546-9e03-485c-b7ec-9deb778f2b01
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994023(v=OCS.15)
ms:contentKeyID: 52057578
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsEdgeAllowList

 

_**Tópico modificado em:** 2015-03-09_

Permite que os administradores especifiquem os domínios com que seus usuários poderão se comunicar. O cmdlet **New-CsEdgeAllowList**, que só pode ser usado com o Microsoft Lync Online, deve ser usado em conjunto com o cmdlet **New-CsEdgeDomainPattern** e o cmdlet **Set-CsTenantFederationConfiguration**.

## Sintaxe

    New-CsEdgeAllowList [-AllowedDomain <PSListModifier>] [-Verbose]

## Exemplos

## Exemplo 1

Os comandos mostrados no Exemplo 1 atribuem o domínio fabrikam.com aos domínios permitidos para o locatário para a TenantId "bf19b7db-6960-41e5-a139-2aa373474354". Para fazer isso, o primeiro comando no exemplo usa o cmdlet **New-CsEdgeDomainPattern** para criar um objeto de domínio para fabrikam.com; esse objeto é armazenado em uma variável chamada $x. Depois que o objeto de domínio tiver sido criado, o cmdlet **New-CsEdgeAllowList** será usado para criar uma nova lista permitida contendo somente o domínio fabrikam.com.

Com a lista de domínios permitidos criada, o comando final no exemplo poderá então usar o cmdlet **Set-CsTenantFederationConfiguration** para configurar fabrikam.com como o único domínio na lista de domínios permitidos para o locatário especificado.

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

Observe que o parâmetro Locatário só será necessário em um ambiente híbrido. Se você estiver conectado somente ao Skype for Business Online, então o parâmetro Locatário poderá ser omitido.

## Exemplo 2

O Exemplo 2 mostra como você pode adicionar vários domínios a uma lista de domínios permitidos. Isso é feito chamando o cmdlet **New-CsEdgeDomainPattern** várias vezes (uma para cada domínio adicionado à lista) e armazenando os objetos do domínio resultante em variáveis separadas. Cada uma dessas variáveis pode então ser adicionada à lista de permissões criada pelo cmdlet **New-CsEdgeAllowList** simplesmente usando o parâmetro AllowedDomain e separando o nome das variáveis usando vírgulas:

$newAllowList = New-CsEdgeAllowList -AllowedDomain $x,$y

    $x = New-CsEdgeDomainPattern -Domain "contoso.com"
    $y = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x,$y
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

## Exemplo 3

No Exemplo 3, todos os domínios são removidos da lista de domínios permitidos. Para fazer isso, o primeiro comando no exemplo usa o cmdlet **New-CsEdgeAllowList** para criar uma lista em branco de domínios permitidos; isso é realizado por meio da configuração da propriedade AllowedDomain como um valor nulo ($Null). A referência de objeto resultante ($newAllowList) será então usada em conjunto com o cmdlet **Set-CsTenantFederationConfiguration** para remover todos os domínios da lista de domínios permitidos para o locatário com a TenantId "bf19b7db-6960-41e5-a139-2aa373474354".

    $newAllowList = New-CsEdgeAllowList -AllowedDomain $Null
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

## Descrição detalhada

A federação é um serviço que permite aos usuários trocar informações de IM e de presença com usuários de outros domínios. Com o Lync Online, os administradores podem usar as configurações de federação para controle:

  - Se os usuários podem ou não se comunicar com pessoas de outros domínios e, se puderem, com que domínios eles têm permissão de se comunicar.

  - Se os usuários podem ou não se comunicar com pessoas com contas em provedores de IM e presença públicos como o Windows Live, AOL e Yahoo

A federação é gerenciada, em parte, usando listas de domínios permitidos e de domínios bloqueados. A lista de domínios permitidos especifica os domínios com os quais os usuários têm permissão de se comunicar; a lista de domínios bloqueados especifica os domínios com os quais os usuários não têm permissão de se comunicar. Por padrão, os usuários podem se comunicar com qualquer domínio que não apareça na lista de bloqueados. Entretanto, os administradores podem modificar essa configuração padrão e limitar a comunicação com os domínios que estejam na lista de domínios permitidos.

O Lync Online não permite que você modifique diretamente a lista de permitidos ou a lista de bloqueados; por exemplo, não é possível usar um comando semelhante a esse, que passa um valor de cadeia de caracteres que representa um nome de domínio para a lista de domínios permitidos:

    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains "fabrikam.com"

Em vez disso, você deverá usar o cmdlet **New-CsEdgeAllowAllKnownDomains** ou o cmdlet **New-CsEdgeAllowList** para criar um objeto de domínio e então passar esse objeto de domínio para o cmdlet **Set-CsTenantFederationConfiguration**. O cmdlet **New-CsEdgeAllowAllKnownDomains** será usado caso você queira permitir que usuários se comuniquem com todos os domínios, exceto por aqueles expressamente especificados na lista de domínios bloqueados. O cmdlet **New-CsEdgeAllowList** será usado caso você queira limitar a comunicação do usuário a uma coleção de domínios especificada. Nesse caso, os usuários só poderão se comunicar com domínios que apareçam na lista de domínios permitidos.

Para adicionar um único domínio (fabrikam.com) à lista de domínios permitidos, será necessário usar um conjunto de comandos semelhante a este:

    $x = New-CsEdgeDomainPattern -Domain "fabrikam.com"
    $newAllowList = New-CsEdgeAllowList -AllowedDomain $x
    Set-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -AllowedDomains $newAllowList

Quando a execução deste comando for concluída, os usuários só poderão se comunicar com usuários do domínio fabrikam.com.

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
<td><p><em>AllowedDomain</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.PSListModifier</p></td>
<td><p>A referência de objeto para o novo domínio (ou conjunto de domínios) a ser adicionada à lista de domínios permitidos. As referências de objeto de domínio devem ser criadas usando o cmdlet <strong>New-CsEdgeDomainPattern</strong>. Vários objetos de domínio podem ser adicionados por meio da separação das referências de objeto usando vírgulas. Por exemplo:</p>
<p>-AllowedDomain $x,$y</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **New-CsEdgeAllowList** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **New-CsEdgeAllowList** cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.AllowList.

## Consulte Também

#### Outros Recursos

[New-CsEdgeAllowAllKnownDomains](new-csedgeallowallknowndomains.md)  
[New-CsEdgeDomainPattern](new-csedgedomainpattern.md)  
[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

