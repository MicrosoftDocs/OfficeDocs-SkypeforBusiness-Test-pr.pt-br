---
title: Configuração do Enterprise Voice no Lync Server 2013
TOCTitle: Configuração do Enterprise Voice no Lync Server 2013
ms:assetid: 7df179fa-d3a2-4b23-a433-b750aedf980b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994041(v=OCS.15)
ms:contentKeyID: 52057663
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração do Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para implantar o Enterprise Voice, será necessário fazer as seguintes configurações:

  - Criar um tronco

  - Definir uma política de voz

  - Definir uma rota de voz

  - Habilitar usuários para o Enterprise Voice

## Criar um tronco

É necessário definir troncos na implementação do Enterprise Voice. Para roteamento baseado em locais, é necessário criar uma configuração de troncos por tronco. Use o Lync ServerConstrutor de Topologias para definir seus troncos e use o use comando do Lync ServerWindows PowerShell, New-CsTrunkConfiguration, ou Painel de Controle do Lync Server para definir as configurações de troncos correspondente. Obtenha mais informações sobre como habilitar o Roteamento com Base no Local nas configurações de troncos na seção, Habilitar o Roteamento com Base no Local para troncos, no tópico, [Habilitando o Roteamento com Base no Local no Lync Server 2013](lync-server-2013-enabling-location-based-routing.md). Para este exemplo, a tabela a seguir ilustra os troncos usados neste cenário.

Para obter mais informações, consulte [Definir troncos adicionais no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-additional-trunks-in-topology-builder.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome do tronco</th>
<th>Tipo de sistema</th>
<th>Nome</th>
<th>Local</th>
<th>Servidor de Mediação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tronco 1 DEL-GW</p></td>
<td><p>Gateway PSTN</p></td>
<td><p>DEL-GW</p></td>
<td><p>Délhi</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>Tronco 2 HYD-GW</p></td>
<td><p>Gateway PSTN</p></td>
<td><p>HYD-GW</p></td>
<td><p>Hiderabade</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="odd">
<td><p>Tronco 3 DEL-PBX</p></td>
<td><p>PBX</p></td>
<td><p>DEL-PBX</p></td>
<td><p>Délhi</p></td>
<td><p>MS1</p></td>
</tr>
<tr class="even">
<td><p>Tronco 4 HYD-PBX</p></td>
<td><p>PBX</p></td>
<td><p>HYD-PBX</p></td>
<td><p>Hiderabade</p></td>
<td><p>MS1</p></td>
</tr>
</tbody>
</table>



## Definir políticas de voz

É necessário definir políticas de voz para a implantação do Enterprise Voice. Definir uma Política de Voz para colocar em prática restrições de Roteamento com Base no Local a um subconjunto de usuários se apenas uma parte deles tiver de usar o Roteamento com Base no Local. Para este exemplo, a tabela a seguir ilustra as políticas de voz usadas neste cenário. Apenas configurações que são específicas para o Roteamento com Base no Local estão inclusas na tabela para fins de ilustração.

Para obter mais informações, consulte [Configurando políticas de voz e registros de uso de PSTN para autorizar recursos e privilégios de chamada no Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Política de voz 1</th>
<th>Política de voz 2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ID da política de voz</p></td>
<td><p>Política de voz de Délhi</p></td>
<td><p>Política de voz de Hiderabade</p></td>
</tr>
<tr class="even">
<td><p>Usos de PSTN</p></td>
<td><p>Uso de Délhi, uso de PBX Del, uso de PBX Hid</p></td>
<td><p>Uso de Hiderabade, uso de PBX Hid, uso de PBX Del</p></td>
</tr>
<tr class="odd">
<td><p>PreventPSTNTollBypass</p></td>
<td><p>Falso</p></td>
<td><p>Falso</p></td>
</tr>
</tbody>
</table>



## Definir rotas de voz

É necessário definir rotas de voz para a implantação do Enterprise Voice. Para este exemplo, a tabela a seguir ilustra as rotas de voz usadas neste cenário. Apenas configurações que são específicas para o Roteamento com Base no Local estão inclusas na tabela para fins de ilustração.

Para obter mais informações, consulte [Configurando rotas de voz para chamadas de saída no Lync Server 2013](lync-server-2013-configuring-voice-routes-for-outbound-calls.md).


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Rota de voz 1</th>
<th>Rota de voz 2</th>
<th>Rota de voz 3</th>
<th>Rota de voz 4</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome</p></td>
<td><p>Rota de Délhi</p></td>
<td><p>Rota de Hiderabade</p></td>
<td><p>Rota PBX Del</p></td>
<td><p>Rota PBX Hid</p></td>
</tr>
<tr class="even">
<td><p>Usos de PSTN</p></td>
<td><p>Uso de Délhi</p></td>
<td><p>Uso de Hiderabade</p></td>
<td><p>Uso de PBX Del</p></td>
<td><p>Uso de PBX Hid</p></td>
</tr>
<tr class="odd">
<td><p>Tronco</p></td>
<td><p>Tronco 1 DEL-GW</p></td>
<td><p>Tronco 2 HYD-GW</p></td>
<td><p>Tronco 3 DEL-PBX</p></td>
<td><p>Tronco 4 HYD-PBX</p></td>
</tr>
</tbody>
</table>



## Habilitar usuários para o Enterprise Voice

Habilite usuários para o Enterprise Voice e atribua a eles uma política de voz previamente definida. Para este exemplo, a tabela a seguir ilustra a atribuição usada neste cenário. Apenas configurações que são específicas para o Roteamento com Base no Local estão inclusas na tabela para fins de ilustração.

Para obter mais informações, consulte [Habilitar usuários para Enterprise Voice no Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md).


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Usuários em Délhi</th>
<th>Usuários em Hiderabade</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Política de voz pertinente</p></td>
<td><p>Política de voz de Délhi</p></td>
<td><p>Política de voz de Hiderabade</p></td>
</tr>
<tr class="even">
<td><p>Exemplos de usuários</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
</tbody>
</table>



## Consulte Também

#### Outros Recursos

[Configurando o Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-configuring-location-based-routing.md)

