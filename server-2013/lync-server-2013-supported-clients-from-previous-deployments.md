---
title: 'Lync Server 2013: Clientes com suporte de implantações anteriores'
TOCTitle: Clientes com suporte de implantações anteriores
ms:assetid: 69d427f8-57a5-4244-b2ed-f2eb7600285e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398499(v=OCS.15)
ms:contentKeyID: 49306993
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Clientes com suporte de implantações anteriores no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Em um cenário de coexistência, clientes do Lync Server 2013 podem interagir com clientes de versões anteriores do Lync Server e do Office Communications Server. Diferentemente das versões anteriores, o Lync Server 2010 oferece suporte aos novos clientes do Lync 2013. Isso permite que organizações que estão atualizando do Lync Server 2010 implantem novos clientes independentemente das atualizações do Lync Server.

## Combinações de servidor e cliente com suporte

A tabela a seguir mostra as combinações com suporte das versões de cliente e de servidor. O Lync Server 2013 oferece suporte a duas versões de cliente anteriores e o Lync Server 2010 oferece suporte ao novo cliente do Lync 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Cliente</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App 2013</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendant</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Chat de Grupo do Lync 2010</p></td>
<td><p>Não aplicável</p></td>
<td><p>Com suporte1</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App 2010</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Attendee</p></td>
<td><p>Sem suporte2</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>Interoperável3</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="odd">
<td><p>Microsoft Office Communications Server 2007 R2 Attendant</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="even">
<td><p>Office Communicator 2007</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="odd">
<td><p>Office Live Meeting 2007</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
</tbody>
</table>


1No Microsoft Lync Server 2010, a funcionalidade de chat em grupo era possível com o Servidor de chat de grupo, um aplicativo confiável de terceiro para Lync Server 2010. Clientes do Lync 2013 não são compatíveis com o Lync Server 2010, Chat de Grupo.

2O Lync Web App 2013 agora fornece uma experiência de reuniões completa, incluindo áudio e vídeo do computador, e é considerado o substituto do Lync 2010 Attendee.

3A aparência e os recursos de IM no Office Communicator 2007 R2 são compatíveis com o Lync Server 2013, mas os recursos de conferência não são. Durante a migração do Office Communications Server 2007 R2, o Office Communicator 2007 R2 é ideal para a aparência e interoperabilidade de IM, mas os usuários devem usar o Lync Web App 2013 para fazer parte das reuniões do Lync Server 2013.

> [!NOTE]  
> Para obter detalhes sobre a capacidade dos clientes do Lync Server 2013 de coexistir e interagir com clientes de versões anteriores do Lync Server e do Office Communications Server, consulte <a href="lync-server-2013-client-interoperability-in-lync-2013.md">Interoperabilidade do Cliente no Lync 2013</a> na documentação de planejamento.
