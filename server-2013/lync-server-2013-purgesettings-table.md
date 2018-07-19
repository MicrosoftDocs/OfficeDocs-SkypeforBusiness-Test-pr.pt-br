---
title: Tabela PurgeSettings no Lync Server 2013
TOCTitle: Tabela PurgeSettings no Lync Server 2013
ms:assetid: 9ff2c8fc-4ae8-4f22-96a8-1f4d5eecbf2d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205121(v=OCS.15)
ms:contentKeyID: 49307630
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabela PurgeSettings no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela PurgeSettings contém informações que especificam se (e quando) registros de detalhes de chamada desatualizados serão excluídos automaticamente do banco de dados CRD. Observe que as informações relacionadas à limpeza podem ser também obtidas no Shell de Gerenciamento do Microsoft Lync Server 2013, executando o seguinte comando:

    Get-CsCdrConfiguration

Os administradores devem tratar a tabela PurgeSettings como somente para leitura: alterações às configurações de limpeza de detalhes de chamada devem ser feitas apenas usando os cmdlets [New-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsCdrConfiguration) ou [Set-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCdrConfiguration).

Esta tabela foi introduzida no Microsoft Lync Server 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Coluna</th>
<th>Tipo de dados</th>
<th>Chave/índice</th>
<th>Detalhes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Id</strong></p></td>
<td><p>int</p></td>
<td><p>Primário</p></td>
<td><p>Identificador exclusivo para coleção de definições de limpeza do CDR.</p></td>
</tr>
<tr class="even">
<td><p><strong>EnablePurge</strong></p></td>
<td><p>bit</p></td>
<td><p></p></td>
<td><p>Quando definido como Verdadeiro (1), o Microsoft Lync Server 2013 limpará periodicamente registros desatualizados do banco de dados CRD. A limpeza ocorrerá todos os dias no tomo especificado pela configuração PurgeHour. Se definido como Falso (0), os registros não serão limpos automaticamente do banco de dados. O valor padrão é Verdadeiro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>KeepCallDetailForDays</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Especifica a idade dos registros CRD (em dias) que serão limpos do banco de dados: se a limpeza estiver ativada, os registros CDR mais velhos que esse valor serão removidos do banco de dados. O valor padrão é 60 dias.</p></td>
</tr>
<tr class="even">
<td><p><strong>KeepErrorReportForDays</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Especifica a idade dos registros de relatórios de erro (em dias) que serão limpos do banco de dados: se a limpeza estiver ativada, os registros de relatórios de erro mais velhos que esse valor serão removidos do banco de dados. O valor padrão é 60 dias.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PurgeHour</strong></p></td>
<td><p>int</p></td>
<td><p></p></td>
<td><p>Especifica a hora local do dia em que ocorrerá a limpeza. O horário é especificado utilizando-se um relógio de 24 horas, onde 0 representa a meia-noite (00:00) e 23 representa 11:00 da noite. Observe que é possível especificar apenas a hora do dia: o valor 10 (indicando 10:00 da manhã) é permitido, mas um valor 10:30 de 10,5 (indicando 10:30 da manhã) não é permitido. O valor padrão é 2 (2:00 da manhã).</p></td>
</tr>
</tbody>
</table>

