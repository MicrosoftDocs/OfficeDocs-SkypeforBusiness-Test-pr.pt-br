---
title: Atribuir políticas de presença por usuário no Lync Server 2013
TOCTitle: Atribuir políticas de presença por usuário no Lync Server 2013
ms:assetid: fd1097b7-248d-4b78-8c43-456b03257c18
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182614(v=OCS.15)
ms:contentKeyID: 49308708
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir políticas de presença por usuário no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Uma política de presença é um conjunto de limites e restrições que afetam a presença. A tabela a seguir descreve as configurações de política de presença disponíveis no Lync Server 2013.

### Configurações da Política de Presença

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
<th>Nome XML</th>
<th>Nome de exibição</th>
<th>Descrição</th>
<th>Tipo</th>
<th>Valor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CategorySubscriptions</p></td>
<td><p>Número máximo de inscrições de categoria do assinante</p></td>
<td><p>Limita o número de inscrições de categoria do assinante. Por exemplo, quando o Communicator se inscreve para a presença de um usuário, ele obtém uma inscrição de categoria para cada cartão de contato, dados de calendário, notas, serviços e categorias de estado.</p>
<p>Uma configuração 0 significa que o objeto de usuário ou contato não pode ser inscrito por outros.</p>

> [!NOTE]  
> Essa configuração pode ter um impacto significativo no desempenho se for definida para um número alto e o usuário médio tem um grande número de usuários inscrevendo para sua presença.

</td>
<td><p>Inteiro</p></td>
<td><p>0-3000</p></td>
</tr>
<tr class="even">
<td><p>PromptedSubscribers</p></td>
<td><p>Número máximo de alertas de inscrição de presença na fila</p></td>
<td><p>Limita o número de entradas na tabela de inscritos solicitados. Essa configuração determina o número máximo de solicitações que podem ser enfileiradas para um determinado usuário. Por exemplo, quando um usuário A se inscreve para a presença do usuário B, o usuário B recebe um prompt de que o usuário A agora está inscrito para o usuário B e um prompt de confirmação é criado na tabela de inscritos solicitados do usuário B. Após o usuário B aceitar ou confirmar a inscrição, o prompt de confirmação é removido da tabela de inscritos solicitados do usuário B.</p>
<p>Uma configuração 0 significa que o usuário não é solicitado quando alguém se inscreve para sua presença.</p></td>
<td><p>Inteiro ou símbolo</p></td>
<td><p>0-500</p></td>
</tr>
</tbody>
</table>


Por padrão, as políticas de presença **Política padrão** e **Serviço: Médio** são instaladas ao implantar o Lync Server. A tabela a seguir descreve as configurações específicas de duas políticas de presença.

### Políticas de presença

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome da política</th>
<th>Descrição</th>
<th>CategorySubscriptions</th>
<th>PromptedSubscribers</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Política padrão</p></td>
<td><p>Política para usuários comuns. Esta é a política de presença padrão.</p></td>
<td><p>1000</p></td>
<td><p>200</p></td>
</tr>
<tr class="even">
<td><p>Serviço: Médio</p></td>
<td><p>Política para aplicativos que exigem mais usuários para se inscrever na presença do objeto.</p></td>
<td><p>1000</p></td>
<td><p>0</p></td>
</tr>
</tbody>
</table>

