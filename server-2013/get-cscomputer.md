---
title: Get-CsComputer
TOCTitle: Get-CsComputer
ms:assetid: 493931a9-1670-4a76-abba-7d3c7723d2e1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425959(v=OCS.15)
ms:contentKeyID: 49306613
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsComputer

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os computadores que executam funções de serviço na infraestrutura do Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsComputer [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsComputer [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Local <SwitchParameter>] [-Pool <String>]

## Exemplos

## EXEMPLO 1

No Exemplo 1, o cmdlet **Get-CsComputer** é utilizado para retornar informações sobre todos os computadores que executarem funções de serviço na infraestrutura do Lync Server.

    Get-CsComputer

## EXEMPLO 2

O comando apresentado no Exemplo 2 utiliza o parâmetro Filter, para retornar apenas os computadores de funções de serviço que fizerem parte do domínio litwareinc.com. A cadeia de caracteres curinga \*.litwareinc.com restringe as informações retornadas a computadores cujo FQDN termine com o valor de cadeia de caracteres ".litwareinc.com".

    Get-CsComputer -Filter "*.litwareinc.com"

## EXEMPLO 3

No Exemplo 1, o parâmetro Identity é utilizado para limitar os dados retornados a um computador cujo nome de domínio totalmente qualificado for atl-cs-001.litwareinc.com.

    Get-CsComputer -Identity "atl-cs-001.litwareinc.com"

## EXEMPLO 4

No Exemplo 4, o parâmetro Pool é usado para retornar informações sobre todos os computadores encontrados no pool atl-cs-001.litwareinc.com.

    Get-CsComputer -Pool "atl-cs-001.litwareinc.com"

## Descrição detalhada

O cmdlet **Get-CsComputer** possibilita identificar rapidamente os computadores que estiverem executando funções de serviços ou de servidor do Lync Server. Chamado sem nenhum parâmetro, o cmdlet **Get-CsComputer** retorna uma coleção de todos os computadores que estiverem executando funções de serviço ou de servidor do Lync Server. Essa coleção inclui a Identidade, o nome do pool e o nome de domínio totalmente qualificado (FQDN) de cada computador. É possível utilizar parâmetros opcionais como Identity, Filter ou Pool para limitar os dados retornados a um único computador ou a um grupo de computadores.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsComputer** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins e RTCUniversalReadOnlyAdmins.

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
<td><p>Permite utilizar caracteres curinga ao se especificar a identidade do computador (ou computadores) a ser retornada. Por exemplo, este comando retorna informações sobre todos os computadores cuja identidade começar com o valor da cadeia de caracteres &quot;atl-&quot;: -Filter &quot;atl-*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>FQDN do computador a ser retornado. Por exemplo: -Identity &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>Se esse parâmetro não for especificado, serão retornados todos os computadores que estiverem executando o Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p><em>Local</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando presente, retorna informações apenas para o computador local.</p></td>
</tr>
<tr class="even">
<td><p><em>Pool</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>FQDN de um pool do Lync Server. Ao se utilizar esse parâmetro, serão retornadas informações sobre todos os computadores no pool especificado.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Get-CsComputer** não aceita a entrada canalizada.

## Tipos de retorno

O cmdlet **Get-CsComputer** retorna instâncias do objeto Microsoft.Rtc.Management.Deploy.Internal.Machine.

## Consulte Também

#### Outros Recursos

[Disable-CsComputer](disable-cscomputer.md)  
[Enable-CsComputer](enable-cscomputer.md)  
[Test-CsComputer](test-cscomputer.md)

