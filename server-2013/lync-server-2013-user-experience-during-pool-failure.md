---
title: 'Lync Server 2013: Experiência do usuário durante falha do pool'
TOCTitle: Experiência do usuário durante falha do pool
ms:assetid: b224b0d0-87e3-4cac-ae87-f45f54fabb49
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205184(v=OCS.15)
ms:contentKeyID: 49307828
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Experiência do usuário durante falha do pool no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Se ocorrer um failover de pool, todos os usuários do pool afetado são forçados a sair e entrar no pool de backup. Por um curto período os usuários que entram no pool de backup podem estar no modo de resiliência. No modo Resiliência, os usuários não conseguem executar tarefas que causariam uma mudança persistente no Lync Server, como adicionar um contato. Após a conclusão do failover, todos os usuários podem obter todos os serviços do pool de backup.

Quaisquer sessões que um usuário tem quando o pool falha são interrompidas, sendo necessário estabelecer essas sessões depois do failover para continuar.

Os usuários não são hospedados novamente durante o failover ou o failback. Os usuários que são hospedados em um pool que falha serão atendidos temporariamente pelo pool de backup. Quando o pool de hospedagem é restaurado, o administrador pode efetuar o failback desses usuários para que sejam atendidos pelo pool de hospedagem original.

Observe que no Lync 2013, o banco de dados do Servidor de informações de local não é replicado no pool de backup. Como prática recomendada, o administrador deve efetuar regularmente o backup do banco de dados LIS e usar a cópia de backup mais recente para restaurar o banco de dados LIS no pool de backup depois do failover.

## Experiência do usuário durante o failover

Quando um usuário está em um pool que falha, o usuário é desconectado. Qualquer sessão de ponto a ponto na qual o usuário estava participando é terminada, bem como conferências organizadas por esse usuário. o usuário não pode se conectar até o temporizador de resiliência do registrador expirar ou o administrador iniciar procedimentos de failover, o que ocorrer primeiro. Quando o usuário entrar novamente, isso ocorrerá no pool de backup. Se entrarem antes da conclusão do failover, estarão no modo Resiliência até a conclusão do failover. Somente então o usuário poderá estabelecer novas sessões ou estabelecer novamente sessões anteriores.

## Experiência do usuário durante failback

O failback de pool pode ocorrer enquanto um usuário afetado é conectado ao pool de backup e o usuário permanece conectado e trabalhando durante o failback. Observe que o processo de failback leva vários minutos para terminar.  Para referência, a expectativa é de até 60 minutos para um pool de 20.000 usuários.

As seguintes tabelas mostram detalhes sobre como um usuário com um cliente do Lync 2013 ou do Microsoft Lync 2010 é afetado durante, bem como depois do failback e também como os usuários em outros pools veem e interagem com um usuário em um pool que sofre failback. Os usuários com clientes do Microsoft Office Communicator 2007 R2 não conseguem se conectar até o pool de front-end sofre o failback total).

O termo *usuários afetado* se refere a qualquer usuário que sofreu failover no pool de hospedagem e está sendo atendido pelo pool de backup. Por definição, qualquer usuário hospedado originalmente no pool de backup não é um usuário afetado.

### Experiência do usuário para um usuário afetado em um pool failback

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Estado ou tarefa do usuário</th>
<th>Durante o failback</th>
<th>Depois da conclusão do failback</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Estado do usuário já conectado</p></td>
<td><p>O usuário permanece registrado e conectado ao pool de backup. Em algum momento o usuário será desconectado e conectado ao pool de hospedagem original, no modo Resiliência.</p></td>
<td><p>O usuário permanece conectado e entra no modo normal.</p></td>
</tr>
<tr class="even">
<td><p>Conexão de novo usuário</p></td>
<td><p>O usuário pode se conectar no pool de hospedagem no modo Resiliência.</p></td>
<td><p>O usuário pode se conectar no pool de hospedagem original no modo normal.</p></td>
</tr>
<tr class="odd">
<td><p>Conferências em andamento organizadas pelo usuário afetado</p></td>
<td><p>Todas as modalidades de conferência são concluídas. O botão Reingressar aparecerá, mas nenhum usuário pode reingressar enquanto o usuário afetado está no modo Resiliência.</p></td>
<td><p>Todas as modalidade funcionam agora. Cada participante precisa clicar para reingressar na conferência.</p></td>
</tr>
<tr class="even">
<td><p>Conferências em andamento organizadas pelo usuário não afetado</p></td>
<td><p>A conferência continua e o usuário afetado pode permanecer na conferência. O usuário afetado está restrito ao que ele/ela pode executar no modo Resiliência.</p></td>
<td><p>A conferência continua e o usuário afetado pode permanecer na conferência e todas as modalidades funcionam depois que o usuário sair do modo Resiliência.</p></td>
</tr>
<tr class="odd">
<td><p>Agendando ou modificando reuniões programadas, criando conferências ad-hoc</p></td>
<td><p>Não é possível enquanto o usuário está no modo Resiliência.</p></td>
<td><p>Disponível para todas as modalidades.</p></td>
</tr>
<tr class="even">
<td><p>Presença como vista por outros usuários no mesmo pool</p></td>
<td><p>Presença desconhecida enquanto o usuário está conectado ao pool de backup durante o modo Resiliência.</p></td>
<td><p>Mostra o último estado de presença definido pelo usuário e as alterações de presença serão refletidas a partir de agora.</p></td>
</tr>
<tr class="odd">
<td><p>Disponibilidade da lista de contatos e do serviço de Catálogo de endereços</p></td>
<td><p>Não disponível</p></td>
<td><p>Disponível</p></td>
</tr>
<tr class="even">
<td><p>Todas as sessões e modalidades ponto a ponto</p></td>
<td><p>Disponível</p></td>
<td><p>Disponível</p></td>
</tr>
</tbody>
</table>


### Experiência do usuário para um usuário hospedado em um pool não afetado durante o failback de outro pool

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tarefa do usuário</th>
<th>Durante o failback</th>
<th>Depois da conclusão do failback</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Exibindo a presença do usuário afetado</p></td>
<td><p>Mostra o último estado de presença definido pelo usuário afetado.</p></td>
<td><p>Trabalhando. Os usuário não afetados visualizam atualizações efetuadas pelos usuário afetados.</p></td>
</tr>
<tr class="even">
<td><p>Conferências em andamento organizadas pelo usuário afetado</p></td>
<td><p>Todas as modalidade de conferência são concluídas.</p></td>
<td><p>Todas as modalidade funcionam agora. Cada participante precisa clicar para reingressar na conferência.</p></td>
</tr>
<tr class="odd">
<td><p>Conferências em andamento organizadas pelo usuário não afetado</p></td>
<td><p>A conferência continua e o usuário afetado pode continuar na conferência, com todas as modalidades funcionando.</p></td>
<td><p>A conferência continua e o usuário afetado pode continuar na conferência, com todas as modalidades funcionando.</p></td>
</tr>
<tr class="even">
<td><p>Todas as sessões e modalidades ponto a ponto</p></td>
<td><p>Disponível</p></td>
<td><p>Disponível</p></td>
</tr>
</tbody>
</table>

