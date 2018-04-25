---
title: Get-CsPool
TOCTitle: Get-CsPool
ms:assetid: e0911c68-9a0a-461a-88d6-c610c6cd996c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398992(v=OCS.15)
ms:contentKeyID: 49308367
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPool

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os pools utilizados na implantação do Lync Server. Os pools são coleções de computadores em um local onde todos executam o mesmo conjunto de serviços do Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsPool [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPool [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Site <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 retorna todos os pools encontrados na implantação do Lync Server.

    Get-CsPool

## EXEMPLO 2

O Exemplo 2 exibe informações detalhadas sobre os computadores encontrados em cada um de seus pools. Isso é feito chamando o cmdlet **Get-CsPool** e canalizando os dados retornados ao cmdlet **Select-Object**. O parâmetro ExpandProperty é usado então para "expandir" o valor da propriedade Computers. A propriedade Computers é uma matriz de objetos que representam cada computador do pool. Ao expandir a propriedade Computers, você recebe informações detalhadas sobre cada um desses computadores.

    Get-CsPool | Select-Object -ExpandProperty Computers

## EXEMPLO 3

No exemplo 3, utiliza-se o parâmetro Identity para restringir os dados retornados ao pool cuja Identidade for atl-cs-001.litwareinc.com.

    Get-CsPool -Identity atl-cs-001.litwareinc.com

## EXEMPLO 4

O Exemplo 4 retorna todos os pools encontrados no site de Redmond. Para fazer isso, o comando usa o parâmetro Site. O valor de parâmetro "Redmond" limita os dados retornados aos pools cuja propriedade Site for igual a Redmond.

    Get-CsPool -Site "Redmond"

## EXEMPLO 5

O comando mostrado no Exemplo 5 retorna uma coleção de todos os pools que não possuem um serviço do Lync Server instalado. Para realizar esta tarefa, o comando chama primeiro o cmdlet **Get-CsPool** sem nenhum parâmetro. Isto retorna uma coleção de todos os pools em atualmente uso na organização. Esta coleção é então canalizada ao cmdlet **Where-Object**, que seleciona todos os pools cuja propriedade Services.Count é igual a 0. Se Count for igual 0, não haverá serviços do Lync Server configurados para esse pool.

    Get-CsPool | Where-Object {$_.Services.Count -eq 0}

## Descrição detalhada

No Lync Server, um pool consiste em um ou mais computadores no mesmo local que estiverem executando o mesmo conjunto de serviços. Por exemplo: se houver um servidor executando o serviço do Servidor de Mediação no site de Redmond, este pool do Servidor de Mediação consistirá em um único computador. Se houver dois computadores executando o Servidor de Mediação no site de Redmond, este pool do Servidor de Mediação consistirá em dois computadores. O número de pools usados na organização depende do número de servidores e dos diferentes serviços executados por esses servidores.

O cmdlet **Get-CsPool** permite recuperar informações sobre cada pool em uso na organização, inclusive informações sobre os serviços em execução em cada pool.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsPool** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins e RTCUniversalReadOnlyAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPool"}

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
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite utilizar caracteres curingas ao especificar a Identidade do pool (ou pools) a ser retornada. Por exemplo, essa sintaxe retorna todos os pools que possuírem uma Identidade que termine com o valor de cadeia de caracteres &quot;.fabrikam.com&quot;: -Filter &quot;*.fabrikam.com&quot;.</p>
<p>Observe que não é possível utilizar os parâmetros Filter e Identity no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Nome do domínio totalmente qualificado (FQDN) do pool a ser retornado. Por exemplo: -Identity atl-cs-001.litwareinc.com.</p>
<p>Se esse parâmetro não estiver presente, serão retornados todos os pools da organização.</p></td>
</tr>
<tr class="odd">
<td><p><em>Site</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Retorna todos os pool localizados no site especificado. Observe que a referência ao site em questão deve utilizar o DisplayName do site (Redmond, por exemplo) em vez da Identidade do site (site:Redmond, por exemplo). Por exemplo: -Site &quot;Redmond&quot;. É possível recuperar os nomes de exibição dos sites executando-se esse comando:</p>
<p>Get-CsSite | Select-Object Identity, DisplayName</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsPool** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsPool** retorna as instâncias do objeto Microsoft.Rtc.Management.Deploy.Internal.Cluster.

## Consulte Também

#### Outros Recursos

[Get-CsSite](get-cssite.md)  
[Get-CsTopology](get-cstopology.md)

