---
title: Get-CsNetworkInterface
TOCTitle: Get-CsNetworkInterface
ms:assetid: 06a5fedf-d87e-4469-9bd6-ad16c1f9a801
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398121(v=OCS.15)
ms:contentKeyID: 49305768
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsNetworkInterface

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre as interfaces de rede em uso em computadores executando os serviços do Lync Server ou as funções de servidor. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsNetworkInterface [-Identity <NetworkInterfaceIdentity>] <COMMON PARAMETERS>

    Get-CsNetworkInterface [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-ComputerFqdn <Fqdn>]

## Exemplos

## EXEMPLO 1

O Exemplo 1retorna informações para todas as interfaces de rede configuradas para uso na organização.

    Get-CsNetworkInterface

## EXEMPLO 2

O comando mostrado no Exemplo 2 retorna informações sobre uma única interface de rede: a interface que possui identidade igual a atl-cs-001.litwareinc.com.com/Primary/1.

    Get-CsNetworkInterface -Identity atl-cs-001.litwareinc.com/Primary/1

## EXEMPLO 3

No Exemplo 3, informações são retornadas para todas as interfaces de rede no domínio litwareinc.com. Para fazer isso, o parâmetro Filter foi incluído, com valor de filtro igual a "\*.litwareinc.com\*". Esse valor de filtro limita os dados retornados a interfaces que possuam identidade incluindo a cadeia de caracteres "litwareinc.com".

    Get-CsNetworkInterface -Filter "*.litwareinc.com*"

## EXEMPLO 4

O Exemplo 4 retorna informações sobre todas as interfaces de rede configuradas para o endereço IP 192.168.0.240. Para fazer isso, o comando chama primeiro o cmdlet **Get-CsNetworkInterface** sem nenhum parâmetro; isso retornará uma coleção de todas as interfaces de rede configuradas para uso na organização. Essa coleção é então canalizada para o cmdlet **Where-Object**, que seleciona somente aquelas interfaces cuja propriedade IPAddress seja igual a 192.168.0.240.

    Get-CsNetworkInterface | Where-Object {$_.IPAddress -eq "192.168.0.240"}

## EXEMPLO 5

O comando mostrado no Exemplo 5 é uma variação do comando mostrado no Exemplo 4; neste caso, as informações são retornadas para todas as interfaces de rede configuradas para a sub-rede "192.168.0.\*". Para fazer isso, é preciso recuperar uma coleção de todas as interfaces de rede, canalizar essa coleção para o cmdlet **Where-Object** e então selecionar somente aquelas interfaces cujo endereço IP comece pela cadeia de caracteres "192.168.0.".

    Get-CsNetworkInterface | Where-Object {$_.IPAddress -like "192.168.0.*"}

## EXEMPLO 6

O Exemplo 6 retorna todas as interfaces de rede que foram configuradas para acesso externo. Para fazer isso, é preciso primeiro chamar o cmdlet **Get-CsNetworkInterface** sem nenhum parâmetro; isso retornará uma coleção de todas as interfaces de rede atualmente em uso. Essa coleção é então canalizada para o cmdlet **Where-Object**, que seleciona somente aqueles itens cuja propriedade Interface seja igual a External.

    Get-CsNetworkInterface | Where-Object {$_.Interface -eq "External"}

## Descrição detalhada

Para que as informações sejam transmitidas de um computador para outro, os computadores precisam de interfaces de rede: conexões entre um computador e a rede. Os computadores executando os serviços do Lync Server ou funções de servidor precisam ter ao menos uma interface de rede ou não poderão se comunicar com outros computadores. No entanto, esses computadores podem ter várias interfaces de rede; por exemplo, um Servidor de Borda pode ter uma interface para conexão com a rede interna e outra para conexão com a Internet. O cmdlet **Get-CsNetworkInterface** oferece uma forma de os administradores retornarem informações sobre as interfaces de rede atualmente em uso em computadores executando os serviços do Lync Server ou funções de servidor.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsNetworkInterface** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsNetworkInterface"}

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
<td><p><em>ComputerFqdn</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN do computador para o qual a informação de interface de rede deverá ser retornada. Por exemplo, para retornar informação de interface de rede para o computador atl-cs-001.litwareinc.com (e somente para esse computador), use esta sintaxe: -ComputerFqdn atl-cs-001.litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite que você use caracteres curinga ao especificar a(s) interface(s) de rede a ser(em) retornada(s). Por exemplo, esta sintaxe retornará informações sobre a interface de rede principal usada em todos os seus computadores executando um serviço do Lync Server ou função de servidor: -Filter &quot;*/Primary/*&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.NetworkInterfaceIdentity</p></td>
<td><p>Identificador exclusivo para a interface de rede a ser retornada. A identidade de uma interface de rede contém três partes:</p>
<p>O FQDN (nome de domínio totalmente qualificado) do próprio computador (por exemplo, atl-cs-001.litwareinc.com).</p>
<p>O &quot;lado&quot; da interface de rede (Primary; Internal; External; rede telefônica pública comutada). O lado indica o tipo de tráfego para o qual a porta é usada.</p>
<p>O número da interface de rede para esse lado em particular.</p>
<p>Por exemplo: -Identity &quot;atl-cs-001.litwareinc.com/Primary/1&quot;.</p>
<p>Os parâmetros Identity, ComputerFqdn e Filter precisam ser usados separadamente; por exemplo, não é possível executar um comando que use ambos os parâmetros ComputerFqdn e Identity. Além disso, não é possível usar caracteres curinga ao especificar a identidade. Para usar caracteres curinga, use o parâmetro Filter.</p>
<p>Se nenhum dos parâmetros Identity, ComputerFqdn ou Filter forem usados, então o cmdlet <strong>Get-CsNetworkInterface</strong> retornará informações sobre todas as interfaces de rede atualmente em uso em seus computadores executando um serviço do Lync Server ou funções de servidor.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsNetworkInterface** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Get-CsNetworkInterface** retorna uma instância do objeto Microsoft.Rtc.Management.Xds.DisplayNetworkInterface.

## Consulte Também

#### Outros Recursos

[Get-CsComputer](get-cscomputer.md)

