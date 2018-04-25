---
title: 'Lync Server 2013: Registros de uso de PSTN'
TOCTitle: Registros de uso de PSTN
ms:assetid: b5f624aa-abe8-455b-a8e3-c228be230463
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412878(v=OCS.15)
ms:contentKeyID: 49307871
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Registros de uso de PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O planejamento dos registros de uso de PSTN consiste principalmente em listar todas as permissões de chamadas em uso na organização, desde o CEO até os funcionários temporários, os consultores e a equipe contingente. Esse processo também oferece uma oportunidade de reexaminar as permissões de chamadas existentes e revisá-las. Você pode criar registros de uso de PSTN somente para as permissões de chamada que se aplicam aos usuários previstos do Enterprise Voice, mas uma solução melhor e de longo alcance pode ser criar registros de PSTN para todas as permissões de chamadas, ainda que algumas delas não se apliquem no momento ao grupo de usuários que será habilitado para o Enterprise Voice. Se as permissões de chamada forem alteradas ou novos usuários com permissões de chamada diferentes forem adicionados, você já terá criado os registros de uso de PSTN necessários.

A tabela a seguir mostra um quadro típico de uso do PSTN.

### Registros de uso de PSTN

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Atributo do telefone</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Local</p></td>
<td><p>Chamadas locais</p></td>
</tr>
<tr class="even">
<td><p>Interurbano</p></td>
<td><p>Chamadas interurbanas</p></td>
</tr>
<tr class="odd">
<td><p>Internacional</p></td>
<td><p>Chamadas internacionais</p></td>
</tr>
<tr class="even">
<td><p>Délhi</p></td>
<td><p>Funcionários de Délhi em tempo integral</p></td>
</tr>
<tr class="odd">
<td><p>Redmond</p></td>
<td><p>Funcionários de Redmond em tempo integral</p></td>
</tr>
<tr class="even">
<td><p>RedmondTemps</p></td>
<td><p>Funcionários temporários de Redmond</p></td>
</tr>
<tr class="odd">
<td><p>Zurique</p></td>
<td><p>Funcionários de Zurique em tempo integral</p></td>
</tr>
</tbody>
</table>


Sozinhos, os registros de uso do PSTN não fazem nada. Para que funcionem, é necessário associá-los ao seguinte:

  - Políticas de voz, que são atribuídas a usuários.

  - Rotas, que são atribuídas a números de telefone.

Para obter detalhes sobre políticas de voz e rotas, consulte [Políticas de voz no Lync Server 2013](lync-server-2013-voice-policies.md) and [Rotas de voz no Lync Server 2013](lync-server-2013-voice-routes.md). Para obter detalhes sobre como criar e configurá-las, consulte [Configurando rotas de voz para chamadas de saída no Lync Server 2013](lync-server-2013-configuring-voice-routes-for-outbound-calls.md).

