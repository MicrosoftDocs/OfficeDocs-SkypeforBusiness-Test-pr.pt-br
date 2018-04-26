---
title: 'Lync Server 2013: Relatório de Lista de Chamadas do Grupo de Resposta'
TOCTitle: Relatório de Lista de Chamadas do Grupo de Resposta
ms:assetid: a2d3e08b-511b-4507-abba-8ff71aa27c8e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615443(v=OCS.15)
ms:contentKeyID: 49307657
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Lista de Chamadas do Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O aplicativo de Grupo de Resposta fornece uma maneira para que o Microsoft Lync Server 2013 responda e roteie chamadas telefônicas baseado no número que foi discado e, opcionalmente, nas respostas do chamador a uma série de perguntas. Geralmente, chamadas do Grupo de Resposta não são roteadas a uma pessoa específica, mas, em vez disso, para uma equipe de pessoas referidas como um grupo de agentes. Por exemplo, se alguém chamar o número de telefone de seu help desk, o Lync Server 2013 rotear automaticamente essa chamada ao primeiro agente disponível do help desk. Como alternativa, o Lync Server pode fazer uma série de perguntas ("Pressione 1 se tiver problemas de hardware. Pressione 2 se tiver problemas de software. Pressione 3 se tiver problemas de rede.") e depois rotear a chamada para o agente de help desk mais apropriado, dependendo das respostas a essas perguntas.

O Relatório de lista de chamadas do grupo de resposta representa uma coleção de chamadas feitas por um período específico de tempo e para um tipo específico de chamada. O Relatório de uso de grupo de resposta (que deve ser aberto primeiro, antes de abrir o Relatório de lista de chamadas do grupo de resposta) reconhece os seguintes tipos de chamadas:

  - **Chamadas recebidas**. Número total de chamadas recebidas por todas as instâncias do aplicativo Grupo de Resposta.

  - **Chamadas bem-sucedidas**. Número total de chamadas atendidas pelo aplicativo Grupo de Resposta.

  - **Chamadas oferecidas** . Número total de chamadas transferidas para um agente do Grupo de Resposta.

  - **Chamadas atendidas** . Número total de chamadas atendidas por um agente do Grupo de Resposta.

  - Porcentagem de chamadas abandonadas. Porcentagem de chamadas recebidas pelo aplicativo Grupo de Resposta, mas que nunca foram atendidas por um agente. Esse valor é calculado subtraindo as Chamadas atendidas das Chamadas recebidas e dividindo esse valor pelo número de chamadas recebidas. Por exemplo, se você receber 10 chamadas recebidas e 7 forem respondidas, subtraia 7 de 10, deixando 3 chamadas não respondidas. Esse valor seria dividido por 10, proporcionando uma porcentagem de chamadas abandonadas de 30%.

  - **Chamadas transferidas** . Número total de chamadas do Grupo de Resposta transferidas devido a um tempo limite ou estouro de fila.

## Como acessar o Relatório de Lista de Chamadas de Grupo de Resposta

O Relatório de Lista de Chamadas de Grupo de Resposta pode ser acessado apenas clicando em uma das seguintes métricas encontradas no [Relatório de Uso do Grupo de Resposta no Lync Server 2013](lync-server-2013-response-group-usage-report.md):

  - Chamadas recebidas

  - Chamadas Bem-sucedidas

  - Chamadas oferecidas

  - Chamadas atendidas

  - Chamadas transferidas

## Como usar melhor o Relatório de Lista de Chamadas de Grupo de Resposta

O Relatório de Lista de Chamadas de Grupo de Resposta permite que você limite os dados exibidos para chamadas que envolvem um fluxo de trabalho específico de Grupo de Resposta. Para fazer isso, você precisa inserir o URI do fluxo de trabalho (o endereço SIP do fluxo de trabalho) na caixa do URI do fluxo de trabalho. Antes que você possa fazer isso, no entanto, é necessário realmente poder ver a caixa do URI do fluxo de trabalho. Para exibir as opções de filtragem do Relatório de Lista de Chamadas de Grupo de Resposta, clique no botão Exibir/Ocultar Parâmetros, na parte superior esquerda da janela do relatório.

Observe que a lista de chamadas do grupo de resposta não exibe informações sobre o código de Resposta nem do ID do Diagnóstico se você manter o mouse sobre uma dessas métricas. Se você precisar de mais informações, você poderá anotar o código de Resposta e/ou o ID do Diagnóstico, e depois pesquisar esses valores no [Relatório das principais falhas no Lync Server 2013](lync-server-2013-top-failures-report.md).

uma pergunta como esta: "Qual é o fluxo de trabalho individual que recebeu a maioria das chamadas?", é possível fazer o seguinte:

1.  No Relatório de uso do grupo de resposta, defina o período desejado de tempo e depois clique na métrica Chamadas Recebidas. Isso abrirá o Relatório de lista de chamadas do grupo de resposta.

2.  Exporte os dados exibidos no Relatório de lista de chamadas do grupo de resposta. Por exemplo, você poderá exportar os dados em formato Microsoft Excel, e depois usar o Excel para converter esses dados a um arquivo de valores separados por vírgula.

3.  Execute suas análises usando o Windows PowerShell.

Por exemplo, se você salvou os dados para um arquivo chamado C:\\Data\\Response\_Group\_Call\_List\_Report.csv, você pode depois usar o seguinte comando para retornar o número total de chamadas recebidas para cada fluxo de trabalho listado no relatório:

    $calls = Import-Csv -Path "C:\ Data\Response_Group_Call_List_Report.csv"
    $calls | Group-Object Workflow | Select-Object Count, Name | Sort-Object Count -Descending

As informações serão similares a essas:

    Count    Name
    -----    ----
      160    Redmond Help Desk
       47    Dublin Help Desk
       31    North America Customer Support
       16    EMEA Customer Support
       14    Employment Opportunities

## Filtros

Filtros fornecem uma forma de retornar um conjunto de dados mais focado ou exibir os dados retornados de diferentes formas. A tabela a seguir lista os filtros que podem ser usados com o Relatório de Lista de Chamadas de Grupo de Resposta.

### Filtros do Relatório de Lista de Chamadas de Grupo de Respostas

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
<p>07.07.12</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>03.07.12</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data/hora final de intervalo de tempo. Para ver os dados por horas, insira a data e hora final conforme segue:</p>
<p>7/7/2012 1:00 PM</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>07.07.12</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>03.07.12</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>URI do Fluxo de trabalho</strong></p></td>
<td><p>Permite limitar os dados retornados ao fluxo de trabalho do Grupo de Resposta especificado. Para usar este filtro, insira o endereço SIP do Fluxo de Trabalho. Por exemplo:</p>
<p>sip:helpdesk@litwareinc.com</p></td>
</tr>
<tr class="even">
<td><p><strong>Chamadas</strong></p></td>
<td><p>Você pode selecionar um dos seguintes tipos de chamadas:</p>
<ul>
<li><p>Chamadas Recebidas</p></li>
<li><p>Chamadas com Êxito</p></li>
<li><p>Chamadas Oferecidas</p></li>
<li><p>Chamadas Atendidas</p></li>
<li><p>Chamadas Transferidas</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Lisa de Chamadas de Grupo de Resposta para cada chamada recebida pelo aplicativo do Grupo de Resposta.

### Métricas do Relatório de Lista de Chamadas de Grupo de Resposta

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
<td><p><strong>Chamador</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do chamador.</p></td>
</tr>
<tr class="even">
<td><p><strong>Fluxo de trabalho</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do fluxo de trabalho do Grupo de Resposta.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora inicial</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e horário em que a chamada teve início.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora final</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e horário em que a chamada terminou.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Código da resposta</strong></p></td>
<td><p>Não</p></td>
<td><p>Código da resposta SIP enviado quando a sessão falhou.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho ms-diagnostics) anexado a uma mensagem SIP que frequentemente fornece informações úteis para solução de erros.</p></td>
</tr>
</tbody>
</table>

