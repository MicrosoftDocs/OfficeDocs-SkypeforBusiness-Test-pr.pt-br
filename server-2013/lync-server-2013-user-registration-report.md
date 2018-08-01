---
title: 'Lync Server 2013: Relatório de Registro de Usuário'
TOCTitle: Relatório de Registro de Usuário
ms:assetid: 151d5cc9-cc1b-4cfa-be9c-55ebe321f7a4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558614(v=OCS.15)
ms:contentKeyID: 49305977
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Registro de Usuário no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Registro de Usuário fornece uma visão geral da atividade de logon de usuário, principalmente informações sobre o número de usuários que fizeram logon no Microsoft Lync Server 2013 dura um período de tempo especificado (por hora, dia, semana ou mês). Lembre-se de que o relatório mostra apenas quantas pessoas fizeram logon. Ele não mostra *quais* pessoas fizeram logon. Os Relatórios de Monitoramento não fornecem informações sobre quais usuários específicos estão usando o Lync Server 2013 (e quais não estão). No entanto, você pode obter uma estimativa aproximada de informações de usuário usando o Relatório de Atividades de Usuário.

Ao fornecer informações sobre logons de usuários, o Relatório de Registro de Usuário faz duas distinções importantes. Primeiro, ele desdobra os logons em duas categorias primárias: logons internos e logons externos. Logons internos representam usuários que fizeram logon de dentro da firewall de sua organização (isto é, enquanto conectados à rede corporativa). Logons externos representam usuários que fizeram logon de fora da firewall, através de uma Servidor de Borda (por exemplo, um usuário que fez logon a partir de um Internet Café conta como um logon externo). Caso precise saber quantas de seus usuários estão fazendo logon de fora da firewall, o Relatório de Registro de Usuário pode fornecer essa informação a você.

Além disso, o Relatório de Registro de Usuário indica quantos usuários *ativos* estavam presentes durante um dado período de tempo. Um usuário ativo é um usuário que fez parte de uma sessão de IM (mensagens instantâneas), participou de uma Reunião do Lync, fez ou recebeu uma chamada telefônica, ou usou o Lync Server de qualquer outra maneira durante este período de tempo. Isso é diferente de um usuário que fez logon mas nunca realmente usou o sistema.

## Acessando o Relatório de Registro de Usuário

Você acessa o Relatório de Registro de Usuário apenas a partir da página inicial de Relatórios de Monitoramento. O Relatório de Registro de Usuário não leva a qualquer outro relatório.

## Usando o Relatório de Registro de Usuário da melhor maneira possível

Após ter implantado o Lync Server uma pergunta frequentemente feita é esta: como posso saber se meus usuários estão realmente usando essa nova tecnologia? Embora tenha algumas limitações neste sentido, o Relatório de Registro de Usuário pode ajudar você a responder esta pergunta. Para determinar se os usuários estão usando o Lync Server ou não, você precisa de duas coisas. Primeiro, obtenha o valor da métrica de Usuários de logon exclusivos, do Relatório de Registro de Usuário. Esse valor diz a você quantos indivíduos distintos fizeram logon no Lync Server.

Por comparação, a métrica Total de logons mostra quantas vezes no total alguém fez logon no Lync Server. Por exemplo, suponha que Ken Myer fez logon no Lync Server cinco vezes em um mesmo dia. Nesse caso, Ken Myer contaria como cinco sessões de logon separadas para a métrica de Total de logons, mas como apenas um usuário de logon para a métrica de Usuários de logon exclusivos. Do mesmo modo, não é incomum que um usuário faça logon de vários dispositivos ou locais. Por exemplo, um usuário pode fazer logon usando seu PC, seu laptop e ele pode ter um telefone IP que faz logon automaticamente no Lync Server. Neste exemplo, existe um usuário exclusivo com três logons.

Para explicar de modo mais aprofundado a diferença entre total de logons e logons exclusivos, considere os logons para um dado período de tempo na tabela a seguir.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Usuário</th>
<th>Horário de logon</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>João Casqueiro</p></td>
<td><p>7/7/2012 8:45 AM</p></td>
</tr>
<tr class="even">
<td><p>João Casqueiro</p></td>
<td><p>7/7/2012 8:46 AM</p></td>
</tr>
<tr class="odd">
<td><p>Paula Bento</p></td>
<td><p>7/7/2012 9:17 AM</p></td>
</tr>
<tr class="even">
<td><p>João Casqueiro</p></td>
<td><p>7/7/2012 9:22 AM</p></td>
</tr>
<tr class="odd">
<td><p>Paula Bento</p></td>
<td><p>7/7/2012 9:31 AM</p></td>
</tr>
</tbody>
</table>


Observe que há um total de cinco logons; no entanto, existem apenas dois usuários de logon exclusivos: Ken Myer (que fez logon três vezes) e Pilar Ackerman (que fez logon duas vezes). Essa é a diferença entre logons e usuários de logon exclusivos.

Além de saber o número de logons exclusivos, você precisa saber o número total de usuários que foram habilitados para o Lync Server. Esse valor pode ser obtido abrindo o Shell de Gerenciamento do Lync Server 2013 e executando o seguinte comando do Windows PowerShell:

    (Get-CsUser).Count

Se o comando anterior retorna um valor de 1.236 e a métrica de Usuários de logon exclusivos retorna um valor médio de 667, isso sugere que um pouco mais da metade de seus usuários habilitados para o Lync estão realmente fazendo logon no sistema a cada dia (isso é, 667 dividido por 1.236, que é aproximadamente 54%).


> [!WARNING]  
> Lembre-se de que as métricas de logon registram usuários que realmente fizeram logons durante o período de tempo especificado. Elas não rastreiam os usuários que já estão logados no sistema. Por exemplo, se a sua métrica de Usuários de logon exclusivos mostra 667 logons e você possui 1.236 usuários, isso sugere que quase a metade de seus usuários estão fazendo logon no sistema. No entanto, suponha que 300 usuários já estavam logados no sistema no momento em que você começou a verificar os dados de logon. Isso significaria que você tinha na verdade quase 1.000 usuários logados no Lync Server, o que significaria que cerca de 80% de seus usuários estavam logados.



Você também deve comparar o valor de Usuários de logon exclusivos com o valor da métrica de Usuários ativos exclusivos. A métrica de Usuários ativos exclusivos mostra a você quantos usuários exclusivos realmente usaram o Lync Server: eles fizeram uma chamada telefônica, eles ingressaram em uma Reunião do Lync, ou participaram de uma sessão de mensagens instantâneas. Essas informações são úteis, pois o Microsoft Lync 2013 pode ser configurado para iniciar automaticamente a cada vez que um usuário inicia o Windows. Por causa disso, você pode ter um número grande de usuários que fazem logon automaticamente no Lync ao fazerem logon no Windows a cada dia, mas nunca realmente usam o Lync Server durante esse período de tempo.

A métrica de Usuários ativos exclusivos também fornece mais dados significativos em uma organização onde os usuários normalmente não fazem logoff do Windows no fim do dia. Ao invés disso, eles simplesmente bloqueiam seus computadores e deixam o Windows e o Lync sendo executados. Em uma situação assim, você pode acabar com poucos logons por dia, pois seus usuários fizeram logon vários dias atrás e nunca fizeram o logoff. No entanto, Usuários ativos exclusivos mostra a você se os usuários estão ativamente usando o Lync ou outro cliente do Lync Server.

## Filtros

Os filtros oferecem uma forma de você retornar um conjunto de dados com o destino mais bem ajustado ou visualizar os dados retornados de formas diferentes. Por exemplo, o Relatório de registro do usuário permite que você visualize os dados de todos os seus Pool de registradores e Servidores de Borda ou visualize os dados de um pool individual. Você também pode escolher como os dados devem ser agrupados. Nesse caso, registros agrupados por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que você pode usar com o Relatório de registro do usuário.

### Filtros do Relatório de registro do usuário

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>De</strong></p></td>
<td><p>Data e hora inicial para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora inicial como a seguir:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora de início, o relatório começará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data e hora final para o intervalo de tempo. Para exibir os dados por hora, insira a data e hora final como a seguir:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Intervalo</strong></p></td>
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diariamente (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanalmente (é possível exibir no máximo 12 semanas)</p></li>
<li><p>Mensalmente (é possível exibir no máximo 12 meses)</p></li>
</ul>
<p>Se as datas de início e término excedem o número máximo de valores permitidos para o intervalo selecionado, apenas o número máximo de valores (começando pela data de início) será exibido. Por exemplo, se você selecionar o intervalo Diário com a data de início 7/7/2012 e a data de término 2/28/2012, os dados serão exibidos para o intervalo de 8/7/2012 12:00 AM a 9/7/2012 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>Pool</strong></p></td>
<td><p>O nome de domínio totalmente qualificado (FQDN) do Pool de registradores ou do Servidor de Borda. Você pode tanto selecionar um pool individual ou escolher <strong>[Todos]</strong> para visualizar os dados de todos os pools. Essa lista suspensa é automaticamente preenchida por você com base nos registros no banco de dados.</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de registro do usuário.

### Métrica do Relatório de registro do usuário

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Você pode classificar este item?</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Por hora</strong></p>
<p><strong>Diário</strong></p>
<p><strong>Semanal</strong></p>
<p><strong>Mensal</strong></p></td>
<td><p>Não</p></td>
<td><p>Indica o intervalo de tempo selecionado na barra de ferramentas de filtro. Quando aplicável, é possível clicar em determinado intervalo de tempo para exibir informações detalhadas sobre ele. Por exemplo, se você estiver usando o intervalo Diário e clicar em 7/7/2012, verá um detalhamento por hora da atividade de registro do usuário para a data em questão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Total de logons</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões de logon bem-sucedidas.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Logons internos</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de logons dentro da rede interna.</p></td>
</tr>
<tr class="even">
<td><p><strong>Logons externos</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total logons de fora da rede interna, usando o Servidor de Borda.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Usuários de logon exclusivo</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de usuário com ao menos uma sessão de logon. Um usuário com várias sessões de logon conta como um usuário, da mesma forma que uma pessoa que teve uma única sessão de logon.</p></td>
</tr>
<tr class="even">
<td><p><strong>Usuários ativos exclusivos</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de usuários envolvidos em uma sessão ponto a ponto ou de conferência. Um usuário com várias sessões de logon conta como um usuário, da mesma forma que uma pessoa que teve uma única sessão.</p></td>
</tr>
</tbody>
</table>

