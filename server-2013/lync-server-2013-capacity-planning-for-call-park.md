---
title: 'Lync Server 2013: Planejamento de capacidade para Estacionamento de Chamada'
TOCTitle: Planejamento de capacidade para Estacionamento de Chamada
ms:assetid: 75520310-760a-4b1b-bcc1-4d724d13f87a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg416493(v=OCS.15)
ms:contentKeyID: 49307138
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de capacidade para Estacionamento de Chamada no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir descreve o modelo de usuário do Estacionamento de Chamada que pode ser usado como base para requisitos de planejamento de capacidade.

> [!IMPORTANT]  
> Tenha em mente que para o planejamento de capacidade de recuperação de desastres, cada pool de um par deve ser capaz de manipular cargas de trabalho de serviços do Estacionamento de Chamada nos dois pools.

### Modelo de usuário do estacionamento de chamada Park

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Indicador</th>
<th>Por Pool de Front-Ends (com 8 servidores Front-End)</th>
<th>Por Servidor Standard Edition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Taxa de estacionamento</p></td>
<td><p>8 por minuto</p></td>
<td><p>1 por minuto</p></td>
</tr>
<tr class="even">
<td><p>Recuperar a taxa de chamada estacionada</p></td>
<td><p>8 por minuto</p></td>
<td><p>1 por minuto</p></td>
</tr>
<tr class="odd">
<td><p>Duração média do estacionamento</p></td>
<td><p>60 segundos</p></td>
<td><p>60 segundos</p></td>
</tr>
</tbody>
</table>

