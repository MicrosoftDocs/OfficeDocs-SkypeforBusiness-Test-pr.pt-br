---
title: 'Lync Server 2013: Processo de implantação para Roteamento Baseado em Local'
TOCTitle: Processo de implantação para Roteamento Baseado em Local
ms:assetid: 9e923e72-83fc-4a4f-8937-28a55739ed3e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994055(v=OCS.15)
ms:contentKeyID: 52057692
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação para Roteamento Baseado em Local no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Este tópico oferece uma visão geral do processo envolvido na configuração do Roteamento com Base no Local. É preciso implantar o Lync ServerEnterprise Edition ou o Standard Edition com Enterprise Voice antes de configurar o Roteamento com Base no Local. Os componentes necessários ao Roteamento com Base no Local já estarão instalados e habilitados quando você implantar o Enterprise Voice.

### Processo de Implantação de Roteamento com Base no Local

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Grupos e funções necessários</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Implantar o Enterprise Voice</p></td>
<td><ul>
<li><p>Configurar troncos</p></li>
<li><p>Criar políticas de voz</p></li>
<li><p>Definir rotas de voz</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p>Implantando o Enterprise Voice</p></td>
</tr>
<tr class="even">
<td><p>Verificar sua implantação do Enterprise Voice</p></td>
<td><p></p></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td> </td>
</tr>
<tr class="odd">
<td><p>Configurar regiões de rede, sites e sub-redes</p></td>
<td><ul>
<li><p>Criar regiões de rede</p></li>
<li><p>Criar sites de rede</p></li>
<li><p>Associa sub-redes a sites de rede</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p>Sobre regiões de rede, sites e sub-redes<br />
Criar ou modificar uma região de rede<br />
Criar ou modificar um site de rede<br />
Associar uma sub-rede a um site de rede</p></td>
</tr>
<tr class="even">
<td><p>Configurar o Roteamento com Base no Local</p></td>
<td><ul>
<li><p>Criar políticas de roteamento de voz</p></li>
<li><p>Definir a configuração de tronco separada por tronco</p></li>
<li><p>Modificar políticas de voz</p></li>
<li><p>Habilitar a configuração de Roteamento com Base no Local</p></li>
</ul></td>
<td><p>CSVoiceAdmins<br />
CsAdministrator<br />
CsServerAdministrator</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


## Implantação de exemplo

A implantação a seguir é usada para ilustrar ainda mais os mecanismos habilitados pelo Roteamento com Base no Local.

![Topologia do Roteamento Baseado na Localização](images/JJ994055.e1bd2230-44da-4784-b359-24572b6ce02d(OCS.15).png "Topologia do Roteamento Baseado na Localização")

## Chamadas de PSTN de entrada

Um administrador pode habilitar o tronco definido para rotear chamadas para o "Gateway do Site 1" para Roteamento com Base no Local e associar o "Gateway do Site 1" ao site 1. Uma vez habilitadas, as chamadas roteadas por meio do "Gateway do Site 1" só serão roteadas para usuários localizados no site 1. Todas as chamadas roteadas por meio do tronco "Gateway do Site 1" destinado a usuários em um site diferente, como o site 2 será bloqueado para impedir o desvio de chamadas tarifadas de PSTN.

Todas as chamadas de PSTN de entrada feitas por meio do "Gateway do Site 1" só poderão ser roteadas para pontos de extremidade localizados no site 1. Por exemplo, quando o "Usuário 1 do Lync" viajar para o site 2, todas as chamadas de PSTN de entrada feitas por meio do "Gateway do Site 1" não serão roteadas para pontos de extremidade do "Usuário 1 do Lync" localizados no site 2. A mesma regra de roteamento se aplicará se o "Usuário 1 do Lync" viajar para um site de rede desconhecido onde a localização do usuário não pode ser determinado.

A tabela a seguir descreve a experiência do usuário do "Usuário 1 do Lync" neste contexto.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Pontos de extremidade do Usuário 1 do Lync localizados no site de rede 1</th>
<th>Pontos de extremidade do Usuário 1 do Lync localizados no site de rede 2</th>
<th>Pontos de extremidade do Usuário 1 do Lync localizados em site de rede desconhecido</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chamadas de PSTN de entrada para o Usuário 1 do Lync</p></td>
<td><p>As chamadas são roteadas para pontos de extremidade neste local</p></td>
<td><p>As chamadas não são roteadas para pontos de extremidade neste local</p></td>
<td><p>As chamadas não são roteadas para pontos de extremidade neste local</p></td>
</tr>
</tbody>
</table>


## Chamadas de PSTN de saída

As rotas de voz são referenciadas em ambas as Políticas de Voz atribuídas diretamente a usuários e as Políticas de Roteamento de Voz atribuídas a sites de rede. Ambas as políticas contêm referências a rotas, que podem ser usadas para rotear uma chamada de forma diferente. Por exemplo, um administrador pode definir uma Política de Roteamento de Voz para todos os usuários localizados no site de rede 1 para rotear todas as chamadas de saída por meio do "Gateway do Site 1", enquanto a Política de Voz de alguns usuários define uma rota para todas as chamadas de saída por meio do "Gateway do Site 2". Embora esses usuários estejam localizados no site de rede 1, suas chamadas de saída serão roteadas por meio do "Gateway do Site 1".

Quando um usuário estiver localizado em um site de rede configurado para o Roteamento com Base no Local, a rota da Política de Roteamento de Voz do site de rede substituirá a rota da Política de Voz do usuário. Essa regra é particularmente útil para usuários que se movem temporariamente para outro site. Nesse caso em particular, um usuário sempre usará um gateway local em sua localização; se o "Usuário 3 do Lync" estiver localizado no "Site 2", todas suas chamadas de saída serão roteadas via "Gateway do Site 2", mas se ele viajar para o site 1, todas as chamadas de saída feitas enquanto ele estiver no site 1 serão roteadas por meio do "Gateway do Site 1".

A tabela a seguir ilustra a experiência do usuário do Usuário 1 do Lync fazendo uma chamada de saída dos sites de rede a seguir.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Site de rede 1</th>
<th>Site de rede 2</th>
<th>Site de rede desconhecido ou não habilitado para Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Autorização de chamadas de saída</p></td>
<td><p>Política de voz de usuário 1 do Lync</p></td>
<td><p>Política de voz de usuário 1 do Lync</p></td>
<td><p>Política de voz de usuário 1 do Lync</p></td>
</tr>
<tr class="even">
<td><p>Roteamento de chamadas de saída</p></td>
<td><p>Política de roteamento de voz de Site 1</p></td>
<td><p>Política de roteamento de voz de Site 2</p></td>
<td><p>Política de voz do usuário e somente para sistemas não habilitados para Roteamento com Base no Local</p></td>
</tr>
</tbody>
</table>


## Transferências e encaminhamentos de chamada

Quando chamadas são transferidas ou encaminhadas, o roteamento de chamadas é afetado pelo Roteamento com Base no Local.

A tabela a seguir representa o Usuário 1 do Lync transferindo ou encaminhando uma chamada de PSTN para outro usuário do Lync.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Usuário iniciando transferência ou encaminhamento de chamada</th>
<th>Usuário 2 do Lync</th>
<th>Usuário 4 do Lync</th>
<th>Usuário do Lync em site de rede não habilitado para Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuário 1 do Lync</p></td>
<td><p>Encaminhamento ou transferência de chamada permitido</p></td>
<td><p>Encaminhamento ou transferência de chamada não permitido</p></td>
<td><p>Encaminhamento ou transferência de chamada não permitido</p></td>
</tr>
</tbody>
</table>

  
A tabela a seguir ilustra como o Roteamento com Base no Local afeta como a chamada é roteada no local do usuário do Lync transferido (Usuário 2 do Lync, Usuário 4 do Lync etc.) para um ponto de extremidade PSTN


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Ponto de extremidade para onde a chamada é transferida ou encaminhada</th>
<th>Usuário 2 do Lync</th>
<th>Usuário 4 do Lync</th>
<th>Usuário do Lync em site de rede não habilitado para Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ponto de extremidade do PSTN</p></td>
<td><p>Encaminhamento ou transferência de chamada é roteada por meio da política de roteamento de voz do site 1 e com saída via Gateway do Site 1</p></td>
<td><p>Encaminhamento ou transferência de chamada é roteada por meio da política de roteamento de voz do site 2 e com saída via Gateway do Site 2</p></td>
<td><p>Encaminhamento ou transferência de chamada é roteado por meio da política de voz de usuário do Lync e com saída via um gateway não habilitado para roteamento com base no local (se disponível)</p></td>
</tr>
</tbody>
</table>


## Toque simultâneo

Uma vez que o roteamento com base no local é configurado na topologia de exemplo, as interações a seguir são impostas.

A tabela a seguir ilustra se o Roteamento com Base no Local permite o toque simultâneo para usuários do Lync diferentes (isto é, usuário 2 do Lync, usuário 4 do Lync etc).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Destino de chamada PSTN de entrada</th>
<th>Usuário 2 do Lync</th>
<th>Usuário 4 do Lync</th>
<th>Usuário do Lync em site de rede não habilitado para Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuário 1 do Lync</p></td>
<td><p>O toque simultâneo é permitido</p></td>
<td><p>O toque simultâneo não é permitido</p></td>
<td><p>O toque simultâneo não é permitido</p></td>
</tr>
</tbody>
</table>

  
A tabela a seguir ilustra se o Roteamento com Base no Local permite o toque simultâneo para um ponto de extremidade PSTN de usuários do Lync diferentes (isto é, usuário 2 do Lync, usuário 4 do Lync etc).


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Destino de toque simultâneo</th>
<th>Usuário 2 do Lync</th>
<th>Usuário 4 do Lync</th>
<th>Usuário do Lync em site de rede não habilitado para Roteamento com Base no Local</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Telefone celular do usuário 1 do Lync (ponto de extremidade PSTN)</p></td>
<td><p>Chamada roteada por meio da política de roteamento de voz do site 1 da rede e com saída via gateway do site 1</p></td>
<td><p>Chamada roteada por meio da política de roteamento de voz do site 2 da rede e com saída via gateway do site 2</p></td>
<td><p>Chamada roteada por meio da política de voz do chamador e terá saída via gateway PSTN não habilitado para Roteamento com Base no Local</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Outros Recursos

[Planejamento de Roteamento Baseado em Local no Lync Server 2013](lync-server-2013-planning-for-location-based-routing.md)

