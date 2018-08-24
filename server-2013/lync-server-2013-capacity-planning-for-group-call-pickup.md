---
title: Planejamento de capacidade para o recebimento de chamadas em grupo
TOCTitle: Planejamento de capacidade para o recebimento de chamadas em grupo
ms:assetid: 0d654a19-6cf0-4118-903d-ec2c4e519253
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ984297(v=OCS.15)
ms:contentKeyID: 52057553
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de capacidade para o recebimento de chamadas em grupo

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir descreve o modelo de usuário de Recebimento de chamada de grupo que pode ser usado como base para requisitos de planejamento de capacidade.

> [!IMPORTANT]  
> O Recebimento de chamada de grupo baseia-se no Aplicativo de Estacionamento de Chamada. Tenha em mente que, para planejamento de capacidade de recuperação de desastres, cada pool do pool pareado deve poder lidar com cargas de trabalho para serviçso do Estacionamento de Chamada, incluindo o Recebimento de chamada de grupo, em ambos pools.

### Modelo de usuário de Recebimento de chamada de grupo

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
<td><p>Número recomendado de usuários por grupo</p></td>
<td><p>50</p></td>
<td><p>50</p></td>
</tr>
<tr class="even">
<td><p>Número recomendado de grupos</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>Número máximo de usuários por pool ativado para Recebimento de chamada de grupo</p></td>
<td><p>25.000</p></td>
<td><p>3.000</p></td>
</tr>
<tr class="even">
<td><p>Taxa máxima de chamadas recebidas para o total de usuários habilitados para Recebimento de chamada de grupo por pool por minuto</p></td>
<td><p>500</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>Taxa máxima de chamadas recuperadas por usuários com Recebimento de chamada de grupo por pool por minuto</p></td>
<td><p>200</p></td>
<td><p>25</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> <ul>
> 
> <li><p>Para os Pools de Front-Ends que possuem menos que oito Servidores Front-End, calcule as métricas linearmente. Por exemplo, se o Pool de Front-Ends possuir um Servidor Front-End, calcule a carga máxima para 1/8 dos valores exibidos na tabela.</p></li>
> 
> 
> <li><p>Você pode aumentar ou diminuir o número recomendado de usuários por grupo e número de grupos desde que você não exceda o número máximo de usuários por pool. por exemplo, seu Servidor Standard Edition pode ter 120 grupos com 25 usuários por grupo porque o número de usuários para Recebimento de chamada de grupo ainda está no máximo do modelo (isto é, 120 grupos vezes 25 usuários, 3.000 usuários habilitados para Recebimento de chamada por grupo.</p></li></ul>

