---
title: 'Lync Server 2013: Planejamento de capacidade para Grupo de Resposta'
TOCTitle: Planejamento de capacidade para Grupo de Resposta
ms:assetid: a2459a69-1f45-4f2f-bca5-d4f442708e44
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412754(v=OCS.15)
ms:contentKeyID: 49307662
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de capacidade para Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir descreve o modelo de usuário do Grupo de Resposta que pode ser usado como base para requisitos de planejamento de capacidade.

> [!NOTE]  
> Os números na tabela a seguir assumem que arquivos de 16 kHz, mono, Wave (.wav) de 16 bits sejam usados para todos os arquivos de áudio do grupo de resposta. Se você usa outros formatos de arquivo, como Windows Media Audio (.wma), os números podem variar.

> [!IMPORTANT]  
> Tenha em mente que para planejar a capacidade de recuperação de desastres, cada pool de um pool pareado deve poder lidar com cargas de trabalho de todos os grupos de resposta, em ambos os pools.

### Modelo de Usuário do Grupo de Resposta

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Indicador</th>
<th>Por pool Enterprise Edition (Com 8 Servidores Front End)</th>
<th>Por servidor Standard Edition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chamadas de entrada por segundo</p></td>
<td><p>16</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>Chamadas concorrentes conectadas ao IVR ou MoH</p></td>
<td><p>480</p></td>
<td><p>60</p></td>
</tr>
<tr class="odd">
<td><p>Sessões anônimas concorrentes (sem IM)</p></td>
<td><p>224</p></td>
<td><p>28</p></td>
</tr>
<tr class="even">
<td><p>Sessões anônimas concorrentes (com IM)</p></td>
<td><p>64</p></td>
<td><p>8</p></td>
</tr>
<tr class="odd">
<td><p>Operadores ativos (formais e informais)</p></td>
<td><p>1200</p></td>
<td><p>1200</p></td>
</tr>
<tr class="even">
<td><p>Número de grupos de busca</p></td>
<td><p>400</p></td>
<td><p>400</p></td>
</tr>
<tr class="odd">
<td><p>Número de grupos IVR (usa reconhecimento de fala)</p></td>
<td><p>200</p></td>
<td><p>200</p></td>
</tr>
</tbody>
</table>

