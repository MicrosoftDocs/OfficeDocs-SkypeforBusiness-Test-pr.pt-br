---
title: 'Lync Server 2013: Relatório de Distribuição de Falha'
TOCTitle: Relatório de Distribuição de Falha
ms:assetid: 365c7beb-24d4-40f5-92e7-4978b9688916
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558635(v=OCS.15)
ms:contentKeyID: 49306368
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Distribuição de Falha no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Distribuição de Falhas classifica sessões com falha nas seguintes categorias:

  - Principais motivos diagnósticos

  - Principais modalidades

  - Principais pools

  - Principais fontes

  - Principais componentes

  - Principais usuários de origem

  - Principais usuários de destino

  - Principal usuário de origem

É possível usar essas categorias para determinar exatamente onde está ocorrendo um problema e, em alguns casos, porque o problema está ocorrendo. Por exemplo, suponha que você tenha registrado 242 sessões de áudio/vídeo com falha durante um determinado dia. Se você observar o Relatório de Distribuição de Falhas, ele poderá mostrar que 237 das sessões com falha ocorreram no pool de Dublin. Isso fornece um ótimo ponto inicial para rastrear e diagnosticar as causas por trás dessas falhas. Se você clicar no pool de Dublin na categoria **Principais pools** , você verá um Relatório de Distribuição de Falhas exclusivo desse pool. Será possível então começar a analisar por que o pool de Dublin enfrentou tantas dificuldades.

## Exibindo o Relatório de Distribuição de Falhas

É possível acessar o Relatório de Distribuição de Falhas a partir de qualquer um dos seguintes relatórios clicando nas medidas **Volume de falhas esperado** ou **Volume de falhas não esperado** :

  - [Relatório das principais falhas no Lync Server 2013](lync-server-2013-top-failures-report.md)

  - [Relatório de Diagnósticos da Conferência no Lync Server 2013](lync-server-2013-conference-diagnostic-report.md)

  - [Relatório de Diagnóstico de Atividade Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-activity-diagnostic-report.md)

No Relatório de Distribuição de Falhas, é possível clicar em qualquer uma das seguintes medidas para exibir o [Relatório de lista de falhas no Lync Server 2013](lync-server-2013-failure-list-report.md):

  - Top diagnostic reasons (sessions)

  - Top modalities (sessions)

  - Top pools (sessions)

  - Top sources (sessions)

  - Top components (sessions)

  - Top from users (sessions)

  - Top to users (sessions)

  - Top from user agents (sessions)

## Usando o Relatório de Distribuição de Falhas

Dependendo do tamanho de seu monitor e da resolução da tela, é possível que alguns dos dados apresentados no Relatório de Distribuição de Falhas sejam truncados que exibidos na tela. Por exemplo, um agente de usuário com o nome "UCCAPI/4.0.7400.0 OC/4.0.7400.0 (Microsoft Lync 2013)" poderá aparecer apenas parcialmente na tela:

UCCAPI/4.0.7400.0 OC/4.0.7400.0 (Microsoft Ly...

Felizmente, é possível ver o nome completo mantendo o mouse sobre o valor truncado.

Um medida interessante que pode ser filtrada usando o Relatório de Distribuição de Falhas é o ID do diagnóstico. Se vir o mesmo ID do diagnóstico surgir em outros relatórios, será possível filtrar esse ID no Relatório de Distribuição de Falhas e obter uma visão bastante detalhada de exatamente onde e com que frequência esse ID foi reportado durante uma sessão com falha.

## Filtros

O filtro é uma maneira de retornar um conjunto de dados mais refinado e direcionado, ou ver os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Falha na Distribuição permite filtrar itens como tipo de atividade (sessão ponto a ponto ou de conferência) ou pelo ID diagnóstico que acompanha cada sessão com falha.

A tabela a seguir lista os filtros que você pode usar com o Relatório de Falha na Distribuição.

### Filtros do Relatório de Falha na Distribuição.

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
<td><p>Data/hora de início para o intervalo de tempo. Para ver os dados por horas, insira a data e hora de início conforme segue:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora de início, o relatório começará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data/hora final de intervalo de tempo. Para ver os dados por horas, insira a data e hora final conforme segue:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/7/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/3/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>FQDN (Nome de domínio totalmente qualificado) do Pool de registradores ou Servidor de Borda. Você pode selecionar um pool individual ou clicar em <strong>[Todos]</strong> para ver os dados de todos os pools. Essa lista suspensa é automaticamente preenchida para você com base nos registros no banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de atividade</strong></p></td>
<td><p>Tipo de atividade para filtrar. Selecione uma das seguintes opções:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Ponto a ponto</p></li>
<li><p>Conferência</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Categoria da sessão</strong></p></td>
<td><p>Indica se a atividade em questão teve sucesso ou falhou. Selecione uma das seguintes opções:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Sucesso</p></li>
<li><p>Falha esperada</p></li>
<li><p>Falha inesperada</p></li>
</ul>
<p>Uma &quot;falha esperada&quot; é aquela que se espera que ocorra. Por exemplo, se um usuário tiver definido seu status como Não incomodar, é esperado que toda chamada encaminhada para esse usuário falhe. &quot;Falha inesperada&quot; é uma falha que ocorre em um sistema que parecia estar em bom estado.Por exemplo, uma chamada não deve ser finalizada se o chamador é colocado em espera. Se isso ocorrer, a situação será sinalizada como falha inesperada.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho de diagnóstico-ms) anexado a uma mensagem SIP que fornece informações úteis sobre os erros de solução de problemas. Os cabeçalhos diagnósticos são opcionais (é possível ter sessões SIP que não os incluem), e os IDs diagnósticos são relatados somente para as sessões com algum tipo de problema.</p></td>
</tr>
</tbody>
</table>


## Métricas para os principais motivos diagnósticos

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base no ID diagnóstico relatado com mais frequência.

### Métricas para os principais motivos diagnósticos

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa das sessões com falha, com base no ID diagnóstico, que é um identificador exclusivo (na forma de um cabeçalho de diagnóstico-ms) anexado a uma mensagem SIP que fornece informações úteis sobre os erros de solução de problemas.</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais motivos diagnósticos</strong></p></td>
<td><p>Não</p></td>
<td><p>ID diagnóstico gerado em uma sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha em que ID diagnóstico especificado foi gerado.</p></td>
</tr>
</tbody>
</table>


## Métricas para as principais modalidades

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base nas modalidades de sessão que apresentaram mais falhas.

### Métricas para as principais modalidades

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa com base na sessão com falha baseada no tipo de sessão (por exemplo, conferência de áudio/vídeo ou sessão de transferência de arquivo ponto a ponto).</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais modalidades</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha envolvendo a modalidade especificada.</p></td>
</tr>
</tbody>
</table>


## Métricas para os principais pools

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base nos pools que apresentaram mais falhas.

### Métricas para os principais pools

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa de sessões com falha com base no Pool de registradores ou no Servidor de Borda no qual a sessão foi conduzida.</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais pools</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome do Pool de registradores ou do Servidor de Borda.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha por Pool de registradores ou por Servidor de Borda.</p></td>
</tr>
</tbody>
</table>


## Métricas para as principais fontes

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base nos computadores que apresentaram mais falhas.

### Métricas para as principais fontes

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa das sessões com falha por computador.</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais fontes</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome do computador envolvido na sessão com falha.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha por computador.</p></td>
</tr>
</tbody>
</table>


## Métricas para os principais componentes

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base nos componentes do Microsoft Lync Server 2010 que apresentaram mais falhas.

### Métricas para os principais componentes

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa das sessões com falha com base no componente do Lync Server 2010 (por exemplo, ExumRouting, GroupChat ou MediationServer).</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais componentes</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome do componente envolvido na sessão com falha.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha por componente.</p></td>
</tr>
</tbody>
</table>


## Métricas para os principais usuários "Para"

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base nos usuários que apresentaram mais falhas quando tentaram chamar alguém (conhecidos como usuários "De").

### Métricas para os principais usuários "Para"

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa das sessões com falha, com base no usuário convidado a entrar na sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais usuários &quot;Para&quot;</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário convidado para entrar na sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha por usuário.</p></td>
</tr>
</tbody>
</table>


## Métricas para os principais usuários

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base nos usuários que apresentaram mais falhas quando o outro usuário tentou chamá-los (conhecidos como usuários "Para").


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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa das sessões com falha, com base no usuário que iniciou a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais usuários &quot;Para&quot;</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha por usuário.</p></td>
</tr>
</tbody>
</table>


## Métricas para os principais agentes do usuário

A tabela a seguir lista as informações fornecidas no Relatório de Falha de Distribuição, com base no software de ponto de extremidade que apresentou mais falhas.

### Métricas para os principais agentes do usuário

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
<td><p><strong>Classificação</strong></p></td>
<td><p>Não</p></td>
<td><p>Classificação relativa de sessões com falha, com base no agente do usuário (software) envolvido na sessão. Por exemplo: RTCC/4.0.0.0 Inbound Routing/4.0.0.0.</p></td>
</tr>
<tr class="even">
<td><p><strong>Principais agentes do usuário</strong></p></td>
<td><p>Não</p></td>
<td><p>Nome do agente do usuário envolvido na sessão com falha.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Sessões</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de sessões com falha por agente do usuário.</p></td>
</tr>
</tbody>
</table>

