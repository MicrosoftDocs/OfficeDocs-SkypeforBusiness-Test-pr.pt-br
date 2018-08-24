---
title: 'Lync Server 2013: Experiência do grupo de resposta durante falha no pool'
TOCTitle: Experiência do grupo de resposta durante falha no pool
ms:assetid: 4e00fb38-64b1-4fd9-903d-7639177bc303
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204886(v=OCS.15)
ms:contentKeyID: 49306664
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Experiência do grupo de resposta no Lync Server 2013 durante falha no pool

 

_**Tópico modificado em:** 2015-03-09_

Essa seção descreve em detalhes como a atividade do grupo de resposta é afetada nos seguintes estágios:

  - Uma interrupção ocorre no pool primário, mas o failover ainda não foi iniciado.

  - O serviço realizou um failover ao pool de backup.

  - O serviço realizou um failback ao pool primário.

## Experiência do usuário quando ocorre interrupção

Quando ocorre uma interrupção de um pool ou site, mas o administrador ainda não iniciou o failover, a atividade do grupo de resposta é manipulada como descrito na seguinte tabela.

> [!NOTE]  
> Durante a recuperação de desastre, as chamadas se comportam de forma diferente dependendo se os grupos de resposta do pool primário foram importados ao pool de backup durante a recuperação. Na tabela seguinte, as referências dos grupos de respostas importados significam que os grupos de respostas do pool primário foram importados ao pool de backup durante o modo de recuperação de desastre.

### Ocorre a interrupção

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de chamada ou ação do usuário</th>
<th>Durante a interrupção</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chamadas conectadas a um agente</p></td>
<td><ul><li><p>Chamadas normais permanecem conectadas.</p></li><li><p>Chamadas anônimas são desconectadas.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Chamadas em andamento ainda não conectadas a um agente</p></td>
<td><p>As chamadas são desconectadas.</p></td>
</tr>
<tr class="odd">
<td><p>Novas chamadas</p></td>
<td><ul><li><p>As chamadas são desconectadas.</p></li><li><p>Se um grupo de resposta for importado, as chamadas serão conectadas ao pool de backup, mas os agentes hospedados no pool primário serão inacessíveis.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Chamadas de agentes em nome do grupo de resposta</p></td>
<td><p>Recurso desabilitado durante esse estágio.</p></td>
</tr>
<tr class="odd">
<td><p>Entrada do agente e informações do agente</p></td>
<td><ul><li><p>Os grupos de agentes pertencentes ao pool primário podem ser exibidos no console do agente, mas os agentes não podem entrar.</p></li><li><p>Os grupos de agentes pertencentes ao pool de backup podem ser exibidos no console do agente e os agentes podem entrar.</p></li><li><p>Os grupos de agentes importados não são exibidos no console do agente.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Configuração do grupo de resposta</p></td>
<td><ul><li><p>Os grupos de resposta pertencentes ao pool primário podem ser exibidos, dependendo da disponibilidade do banco de dados back-end do pool primário, mas não podem ser modificados.</p></li><li><p>Os grupos de respostas pertencentes ao pool de backup podem ser exibidos e modificados.</p></li><li><p>Os grupos de respostas importados não podem ser exibidos com o Painel de Controle do Lync Server nem com o Ferramenta de Configuração de Grupo de Resposta, mas podem ser configurados por meio dos cmdlets Shell de Gerenciamento do Lync Server.</p></li></ul></td>
</tr>
</tbody>
</table>


## Experiência do usuário durante o failover

Quando um administrador chama um failover para um pool de backup, a atividade do grupo de resposta é manipulada durante e depois do failover, conforme descrito na tabela seguinte. A primeira coluna descreve o tipo de atividade que pode estar ocorrendo. A coluna do meio descreve como cada atividade é manipulada durante o breve período necessário para enviar o failover ao pool de backup. A última coluna descreve como a atividade é manipulada durante todo o período, após o processo de failover ser concluído e o pool de backup estar disponível para o pool primário.

> [!NOTE]  
> Durante a recuperação de desastre, as chamadas se comportam de forma diferente dependendo se os grupos de resposta do pool primário foram importados ao pool de backup durante a recuperação. Na tabela seguinte, as referências dos grupos de respostas importados significam que os grupos de respostas do pool primário foram importados ao pool de backup durante o modo de recuperação de desastre.

### O failover é iniciado

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de chamada ou ação do usuário</th>
<th>Durante o failover</th>
<th>Após a conclusão do failover</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chamadas conectadas a um agente</p></td>
<td><ul><li><p>Chamadas normais permanecem conectadas.</p></li><li><p>Chamadas anônimas são desconectadas.</p></li></ul></td>
<td><ul><li><p>Chamadas normais permanecem conectadas.</p></li><li><p>Para grupos de respostas importados, as chamadas anônimas que alcançaram o pool de backup permanecem conectadas.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Chamadas em andamento ainda não conectadas a um agente</p></td>
<td><p>As chamadas são desconectadas.</p></td>
<td><ul><li><p>Se os grupos de respostas não forem importados, nenhuma chamada estará nesse status.</p></li><li><p>Para grupos de chamadas importados, as chamadas que alcançaram o pool de backup permanecem conectadas.</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Novas chamadas</p></td>
<td><ul><li><p>As chamadas são desconectadas.</p></li><li><p>Para grupos de respostas importados, as chamadas se conectam ao pool de backup, mas os agentes hospedados no pool primário são inalcançáveis.</p></li></ul></td>
<td><ul><li><p>Se os grupos de resposta não forem importados, as chamadas serão desconectadas.</p></li><li><p>Para grupos de respostas importados, as chamadas são conectadas ao pool de backup.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Chamadas de agentes em nome do grupo de resposta</p></td>
<td><p>O recurso é desabilitado durante esse estágio</p></td>
<td><ul><li><p>Se os grupos de resposta não forem importados, as chamadas falham.</p></li><li><p>Para grupos de resposta importados, as chamadas são bem-sucedidas.</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Entrada do agente e informações do agente</p></td>
<td><ul><li><p>Os grupos de agentes pertencentes ao pool primário podem ser exibidos no console do agente, mas os agentes não podem entrar.</p></li><li><p>Os grupos de agentes pertencentes ao pool de backup podem ser exibidos no console do agente e os agentes podem entrar.</p></li><li><p>Os grupos de agentes importados são exibidos no console do agente e os agentes podem entrar.</p></li></ul></td>
<td><ul><li><p>Os grupos de agentes pertencentes ao pool primário podem ser exibidos no console do agente, mas os agentes não podem entrar.</p></li><li><p>Os grupos de agentes pertencentes ao pool de backup podem ser exibidos no console do agente e os agentes podem entrar.</p></li><li><p>Os grupos de agentes importados são exibidos no console do agente e os agentes podem entrar.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Configuração do grupo de resposta</p></td>
<td><ul><li><p>Os grupos de resposta pertencentes ao pool primário podem ser exibidos, dependendo da disponibilidade do banco de dados back-end do pool primário, mas não podem ser modificados.</p></li><li><p>Os grupos de respostas pertencentes ao pool de backup podem ser exibidos e modificados.</p></li><li><p>Os grupos de respostas importados não podem ser exibidos com o Painel de Controle do Lync Server nem com o Ferramenta de Configuração de Grupo de Resposta, mas podem ser configurados por meio dos cmdlets Shell de Gerenciamento do Lync Server.</p></li></ul></td>
<td><ul><li><p>Os grupos de resposta pertencentes ao pool primário podem ser exibidos, dependendo da disponibilidade do banco de dados back end, mas não podem ser modificados.</p></li><li><p>Os grupos de respostas pertencentes ao pool de backup podem ser exibidos e modificados.</p></li><li><p>Os grupos de respostas importados não podem ser exibidos com o Painel de Controle do Lync Server nem com o Ferramenta de Configuração de Grupo de Resposta, mas podem ser configurados por meio dos cmdlets Shell de Gerenciamento do Lync Server.</p></li></ul></td>
</tr>
</tbody>
</table>


## Experiência do usuário durante failback

Quando um administrador chama o failback para o pool primário, a atividade do grupo de resposta é manipulada durante e após o failback, conforme descritos na tabela seguinte.

> [!NOTE]  
> Durante a recuperação de desastre, as chamadas se comportam de forma diferente dependendo se os grupos de resposta do pool primário foram importados ao pool de backup durante a recuperação. Na tabela seguinte, as referências dos grupos de respostas importados significam que os grupos de respostas do pool primário foram importados ao pool de backup durante o modo de recuperação de desastre.

### Administração de chamada no Failback

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de chamada ou ação do usuário</th>
<th>Durante o failback</th>
<th>Após a conclusão do failback</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Chamadas conectadas a um agente</p></td>
<td><ul><li><p>Chamadas normais permanecem conectadas.</p></li><li><p>Se os grupos de respostas não forem importados, nenhuma chamada anônima estará nesse status.</p></li><li><p>Para grupos de resposta importados, as chamadas anônimas permanecem conectadas.</p></li></ul></td>
<td><ul><li><p>Chamadas normais permanecem conectadas.</p></li><li><p>Se os grupos de respostas não forem importados, nenhuma chamada anônima estará nesse status.</p></li><li><p>Para grupos de resposta importados, as chamadas anônimas permanecem conectadas.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Chamadas em andamento ainda não conectadas a um agente</p></td>
<td><ul><li><p>Se os grupos de respostas não forem importados, nenhuma chamada estará nesse status.</p></li><li><p>Para grupos de respostas importados, as chamadas serão desconectadas.</p></li></ul></td>
<td><ul><li><p>Se os grupos de respostas não forem importados, nenhuma chamada estará nesse status.</p></li><li><p>Para grupos de respostas importados, as chamadas serão desconectadas.</p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Novas chamadas</p></td>
<td><p>Chamadas conectadas ao pool primário, mas os agentes hospedados no pool primário são inacessíveis.</p></td>
<td><p>Chamadas conectadas ao pool primário.</p></td>
</tr>
<tr class="even">
<td><p>Chamadas de agentes em nome do grupo de resposta</p></td>
<td><p>Recurso desabilitado durante esse estágio.</p></td>
<td><p>Chamadas bem-sucedidas.</p></td>
</tr>
<tr class="odd">
<td><p>Entrada do agente e informações do agente</p></td>
<td><ul><li><p>Os grupos de agentes pertencentes ao pool primário podem ser exibidos no console do agente, mas os agentes não podem entrar.</p></li><li><p>Os grupos de agentes pertencentes ao pool de backup podem ser exibidos no console do agente e os agentes podem entrar.</p></li><li><p>Os grupos de agentes importados são exibidos no console do agente e os agentes podem entrar.</p></li></ul></td>
<td><ul><li><p>Os grupos de agente pertencentes ao pool primário podem ser exibidos no console do agente e os agentes podem entrar.</p></li><li><p>Os grupos de agentes pertencentes ao pool de backup podem ser exibidos no console do agente e os agentes podem entrar.</p></li><li><p>Os grupos de agentes importados não são exibidos no console do agente.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Configuração do grupo de resposta</p></td>
<td><ul><li><p>Os grupos de resposta pertencentes ao pool primário podem ser exibidos, dependendo da disponibilidade do banco de dados back-end do pool primário, mas não podem ser modificados.</p></li><li><p>Os grupos de respostas pertencentes ao pool de backup podem ser exibidos e modificados.</p></li><li><p>Os grupos de respostas importados não podem ser exibidos com o Painel de Controle do Lync Server nem com o Ferramenta de Configuração de Grupo de Resposta, mas podem ser configurados por meio dos cmdlets Shell de Gerenciamento do Lync Server.</p></li></ul></td>
<td><ul><li><p>Os grupos de respostas pertencentes ao pool primário podem ser exibidos e modificados.</p></li><li><p>Os grupos de respostas pertencentes ao pool de backup podem ser exibidos e modificados.</p></li><li><p>Os grupos de respostas importados não podem ser exibidos com o Painel de Controle do Lync Server nem com o Ferramenta de Configuração de Grupo de Resposta, mas podem ser configurados por meio dos cmdlets Shell de Gerenciamento do Lync Server.</p></li></ul></td>
</tr>
</tbody>
</table>

