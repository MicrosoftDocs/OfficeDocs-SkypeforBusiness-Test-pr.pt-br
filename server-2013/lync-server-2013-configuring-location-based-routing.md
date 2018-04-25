---
title: 'Lync Server 2013: Configurando o Roteamento Baseado em Local'
TOCTitle: Configurando o Roteamento Baseado em Local
ms:assetid: 63cdc474-e80f-43b1-a237-9d9ed673300a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994036(v=OCS.15)
ms:contentKeyID: 52057621
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Roteamento Baseado em Local no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O CU1 do Lync Server 2013, Roteamento com Base no Local é um recurso do Enterprise Voice. O Roteamento com Base no Local é um recurso de gerenciamento de chamadas que controla como as chamadas são roteadas pelo CU1 do Lync Server 2013. Ele aplica as restrições quanto ao fato das chamadas poderem ser roteadas para destinos de PBX ou PSTN com base no local de quem está realizando a chamada do Lync. O Roteamento com Base no Local aplica as regras de autorização de chamada às chamadas de PSTN com base no local da rede de quem realiza a chamada. O local de quem realiza a chamada é determinado com base no local da rede associado à sub-rede da rede à qual quem realiza a chamada está conectado. A configuração do Roteamento com Base no Local requer primeiro a implementação do Enterprise Voice e, em seguida, a configuração de regiões de rede, locais e sub-redes. Isso configura a base para a habilitação do Roteamento com Base no Local.

Antes de implementar o Roteamento com Base no Local, você deve implementar o Enterprise Voice e configurar as regiões da rede, locais e subredes de redes associadas a seus locais de rede. Uma vez feito isso, você poderá configurar o Roteamento com Base no Local. Para etapas de como configurar as regiões da rede, locais e sub-redes, consulte [Implantando recursos avançados de Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

Esta seção fornece orientação para a configuração do Roteamento com Base no Local utilizando o exemplo a seguir como ilustração.

![Exemplo de roteamento baseado em local do Enterprise Voice](images/JJ994036.b6ef5afc-36ac-406f-8ec2-a87532b20612(OCS.15).png "Exemplo de roteamento baseado em local do Enterprise Voice")

  
A tabela a seguir representa os usuários definidos neste exemplo.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de Ponto de Extremidade</th>
<th>Local</th>
<th>Usuários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync</p></td>
<td><p>Escritório corporativo de Délhi</p></td>
<td><p>DEL-LYNC-1,DEL-LYNC-2,DEL-LYNC-3</p></td>
</tr>
<tr class="even">
<td><p>Lync</p></td>
<td><p>Escritório corporativo de Hiderabade</p></td>
<td><p>HYD-LYNC-1, HYD-LYNC-2, HYD-LYNC-3</p></td>
</tr>
<tr class="odd">
<td><p>Lync</p></td>
<td><p>Desconhecido (ou seja, hotel)</p></td>
<td><p>UNK-LYNC-1</p></td>
</tr>
<tr class="even">
<td><p>PBX</p></td>
<td><p>Escritório corporativo de Délhi</p></td>
<td><p>DEL-PBX-1, DEL-PBX-2</p></td>
</tr>
<tr class="odd">
<td><p>PBX</p></td>
<td><p>Escritório corporativo de Hiderabade</p></td>
<td><p>HYD-PBX-1, HYD-PBX-2</p></td>
</tr>
<tr class="even">
<td><p>PSTN</p></td>
<td><p>Desconhecido</p></td>
<td><p>PSTN-1, PSTN-2, PSTN-3</p></td>
</tr>
</tbody>
</table>

  

A tabela a seguir representa os sistemas ilustrados no ambiente deste exemplo.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Sistema</th>
<th>Local</th>
<th>Nome</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Pool do CU1 do Lync Server 2013</p></td>
<td><p>qualquer um</p></td>
<td><p>LS-PL1</p></td>
</tr>
<tr class="even">
<td><p>CU1 do Lync Server 2013, Servidor de Mediação</p></td>
<td><p>qualquer um</p></td>
<td><p>MS-PL1</p></td>
</tr>
<tr class="odd">
<td><p>Gateway PSTN 1</p></td>
<td><p>Délhi</p></td>
<td><p>DEL-GW</p></td>
</tr>
<tr class="even">
<td><p>Gateway PSTN 2</p></td>
<td><p>Hiderabade</p></td>
<td><p>HYD-GW</p></td>
</tr>
<tr class="odd">
<td><p>PBX 1</p></td>
<td><p>Délhi</p></td>
<td><p>DEL-PBX</p></td>
</tr>
<tr class="even">
<td><p>PBX 2</p></td>
<td><p>Hiderabade</p></td>
<td><p>RED-PBX</p></td>
</tr>
</tbody>
</table>


## Nesta seção

  - [Configuração do Enterprise Voice no Lync Server 2013](lync-server-2013-configuring-enterprise-voice.md)

  - [Implantação de regiões de rede, sites e sub-redes no Lync Server 2013](lync-server-2013-deploying-network-regions-sites-and-subnets.md)

  - [Habilitando o Roteamento com Base no Local no Lync Server 2013](lync-server-2013-enabling-location-based-routing.md)

## Consulte Também

#### Outros Recursos

[Implantando recursos avançados de Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)

