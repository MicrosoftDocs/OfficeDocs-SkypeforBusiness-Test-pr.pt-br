---
title: 'Lync Server 2013: Relatório de Uso do Grupo de Resposta'
TOCTitle: Relatório de Uso do Grupo de Resposta
ms:assetid: 3248b320-a552-400a-8485-6891af4eb0f3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558632(v=OCS.15)
ms:contentKeyID: 49306310
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Uso do Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O aplicativo de Grupo de Resposta fornece uma maneira para que o Microsoft Lync Server 2013 responda e roteie chamadas telefônicas baseado no número que foi discado e, opcionalmente, nas respostas do chamador a uma série de perguntas. Geralmente, chamadas do Grupo de Resposta não são roteadas a uma pessoa específica, mas, em vez disso, para uma equipe de pessoas referidas como um grupo de agentes. Por exemplo, se alguém chamar o número de telefone de seu help desk, o Lync Server 2013 rotear automaticamente essa chamada ao primeiro agente disponível do help desk. Como alternativa, o Lync Server pode fazer uma série de perguntas ("Pressione 1 se tiver problemas de hardware. Pressione 2 se tiver problemas de software. Pressione 3 se tiver problemas de rede.") e depois rotear a chamada para o agente de help desk mais apropriado, dependendo das respostas a essas perguntas.

O Relatório de Uso de Grupo de Resposta oferece uma visão detalhada do número de chamadas telefônicas recebidas por todos os fluxos de trabalho do Grupo de Resposta e decompõe essas chamadas em categorias mais restritas, como Chamadas oferecidas, Chamadas respondidas e Chamadas abandonadas.

A chave para trabalhar com o Relatório de Uso do Grupo de Resposta é entender a diferença entre os tipos de chamada reportados:

  - **Chamadas recebidas**. Número total de chamadas recebidas por todas as instâncias do aplicativo Grupo de Resposta.

  - **Chamadas bem-sucedidas** . Número total de chamadas atendidas pelo aplicativo Grupo de Resposta.

  - **Chamadas oferecidas**. Número total de chamadas transferidas para um agente do Grupo de Resposta.

  - **Chamadas atendidas**. Número total de chamadas atendidas por um agente do Grupo de Resposta.

  - **Porcentagem de chamadas abandonadas**. Porcentagem de chamadas que foram recebidas pelo aplicativo Grupo de Resposta, mas que nunca foram atendidas por um agente. Este valor é calculado subtraindo as chamadas atendidas pelas chamadas recebidas e, então, dividindo esse valor pelo número de chamadas recebidas. Por exemplo, se 10 chamadas foram recebidas e 7 foram atendidas, você deve subtrair 7 de 10, restando 3 chamadas não atendidas. Esse valor deve ser dividido por 10, resultando em uma porcentagem de 30% de chamadas abandonadas.

  - **Chamadas transferidas**. Número total de chamadas do Grupo de Resposta transferidas devido a um tempo limite ou estouro de fila.

Se estiver analisando o Relatório de uso de Grupo de Resposta e não se lembrar da definição de qualquer um desses tipos de chamada, basta manter o mouse sobre a etiqueta do tipo de chamada apropriado. Uma dica de ferramenta será exibida oferecendo uma breve descrição do tipo de chamada.

O Relatório de Uso do Grupo de Resposta permite que você filtre em um URI de fluxo de trabalho (o endereço SIP associado a esse fluxo de trabalho). No entanto, os próprios URIs de fluxo de trabalho não são exibidos no relatório. Se quiser saber, por exemplo, quais fluxos de trabalho estão respondendo à maioria das chamadas ou quais estão recebendo a maioria das chamadas transferidas, clique na medida apropriada para abrir o Relatório de Lista de Chamadas do Grupo de Resposta para o período. Esse relatório lista os URIs de fluxo de trabalho.

## Acessando o Relatório de Uso do Grupo de Resposta

O Relatório de Uso do Grupo de Resposta é acessado pela home page Relatórios de Monitoramento. Você pode fazer busca detalhada no [Relatório de Lista de Chamadas do Grupo de Resposta no Lync Server 2013](lync-server-2013-response-group-call-list-report.md) clicando em qualquer uma das seguintes medidas:

  - Chamadas recebidas

  - Chamadas Bem-sucedidas

  - Chamadas oferecidas

  - Chamadas atendidas

  - Chamadas transferidas

## Fazendo o melhor uso do Relatório de Uso do Grupo de Resposta

Um dos usos mais interessantes do Relatório de Uso do Grupo de Resposta podem não estar imediatamente aparente: a capacidade de recuperar informações de uso de um fluxo de trabalho individual do Grupo de Resposta.


> [!WARNING]  
> Um fluxo de trabalho do Grupo de Resposta é basicamente um conjunto de instruções que determina o que o Lync Server faz quando um usuário disca para um determinado número de telefone. Para isso, cada fluxo de trabalho é associado exclusivamente a um número de telefone. Quando alguém liga para o número, o fluxo de trabalho determina como a chamada será tratada. Por exemplo, o fluxo de trabalho pode fazer com que a chamada seja roteada a uma série de perguntas de resposta interativa de voz (IVR), que solicitam que o chamador especifique informações adicionais ("Pressione 1 para suporte de hardware. Pressione 2 para suporte de software"). Como alternativa, o fluxo de trabalho pode fazer com que a chamada seja colocada em uma fila e o chamador colocado em espera até que um agente esteja disponível para atender a chamada. A disponibilidade dos agentes para atender chamadas também é determinada pelo fluxo de trabalho: eles são usados para configurar as horas comerciais (os dias da semana e as horas do dia em que os agentes estão disponíveis para atender chamadas) e feriados (dias em que nenhum agente está disponível para atender chamadas). Sempre que você liga para um número de telefone que pertence ao aplicativo Grupo de Resposta, você está essencialmente ligando para um fluxo de trabalho do Grupo de Resposta.



Embora os URIs de fluxo de trabalho não sejam exibidos no Relatório de Uso do Grupo de Resposta, ainda é possível exibir as estatísticas de uso de um fluxo de trabalho individual, algo que sempre é extremamente útil. Por exemplo, suponha que você tenha divulgado uma nova campanha publicitária e esteja curioso para saber se as pessoas estão ligando para se informar sobre o produto. Se o fluxo de trabalho do Grupo de Resposta tiver sido associado ao número de telefone dado na campanha publicitária, será possível verificar com facilidade quantas pessoas (se houverem) estão ligando para o número.

É possível também usar uma abordagem semelhante para medir o número de chamadas que estão sendo tratadas pelo suporte técnico interno ou pelo departamento de atendimento ao cliente.

Para revisar as estatísticas de uso de determinado fluxo de trabalho, insira o URI do fluxo de trabalho na caixa URI do Fluxo de Trabalho. Obviamente, como observado, os URIs do fluxo de trabalho (o endereço SIP associado a um fluxo de trabalho) não são exibidos no relatório. Isso significa que é preciso encontrar uma forma de determinar o URI de um fluxo de trabalho. Uma possibilidade é usar o Windows PowerShell e o Shell de Gerenciamento do Lync Server. Por exemplo, este comando retorna todos os URIs de todos os fluxos de trabalho do Grupo de Resposta:

    Get-CsRgsWorkflow | Select-Object Name, PrimaryUri

That will return data similar to this:

    Name                            PrimaryUri
    ----                            ----------
    Customer Support                sip:support@litwareinc.com
    Help Desk                       sip:helpdesk@litwareinc.com
    New Ad Campaign                 sip:newads@litwareinc.com

Este comando retorna informações sobre um fluxo de trabalho individual, cujo nome é Nova campanha publicitária:

    Get-CsRgsWorkflow -Name "New Ad Campaign" | Select-Object Name, PrimaryUri

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionado ou de exibir os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Uso do Grupo de Resposta permite que você veja os dados dos fluxos de trabalho de todos os seus Grupos de Resposta ou que veja os dados de um fluxo de trabalho individual. Também é possível escolher como os dados devem ser agrupados. Nesse caso, os usos são agrupados por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Uso do Grupo de Resposta.

### Filtros do Relatório de Uso do Grupo de Resposta

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
<td><p><strong>Intervalo</strong></p></td>
<td><p>Intervalo de tempo. Selecione uma das seguintes opções:</p>
<ul>
<li><p>Por hora (é possível exibir no máximo 25 horas)</p></li>
<li><p>Diariamente (é possível exibir no máximo 31 dias)</p></li>
<li><p>Semanalmente (é possível exibir no máximo 12 semanas)</p></li>
<li><p>Mensalmente (é possível exibir no máximo 12 meses)</p></li>
</ul>
<p>Se as datas de início e término excederem o número máximo de valores permitidos para o intervalo selecionado, somente o número máximo de valores (a partir da data de início) será exibido. Por exemplo, se você selecionar o intervalo Diariamente com data de início em 7/7/2012 e data de término de 2/28/2012, os dados serão exibidos do dia 8/7/2012 12:00 AM, até o dia 9/7/2012 12:00 AM (ou seja, um total de 31 dias de dados).</p></td>
</tr>
<tr class="even">
<td><p><strong>URI do Fluxo de trabalho</strong></p></td>
<td><p>Permite limitar os dados retornados ao fluxo de trabalho do Grupo de Resposta especificado. Para usar este filtro, insira o endereço SIP do Fluxo de Trabalho. Por exemplo:</p>
<p>sip:helpdesk@litwareinc.com</p></td>
</tr>
</tbody>
</table>


## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Uso do Grupo de Resposta.

### Métricas do Relatório de Uso do Grupo de Resposta

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
<td><p>Indica o intervalo de tempo selecionado. Quando aplicável, você pode clicar em um dado intervalo de tempo para exibir informações detalhadas para aquele intervalo. Por exemplo, se estiver usando um intervalo por dia e clicar em 7/7/2012, você verá uma divisão por hora das atividades de registro do usuário para aquela data.</p></td>
</tr>
<tr class="even">
<td><p><strong>Chamadas recebidas</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas recebidas por todas as instâncias do aplicativo Grupo de Resposta. Quando você clica nesse item, o relatório mostra o relatório de Lista de Chamadas do Grupo de Resposta para o período de tempo selecionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Chamadas Bem-sucedidas</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas atendidas pelo aplicativo Grupo de Resposta. Quando você clica nesse item, o relatório mostra o relatório de Lista de Chamadas do Grupo de Resposta para o período de tempo selecionado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Chamadas oferecidas</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas transferidas para um agente do Grupo de Resposta. Quando você clica nesse item, o relatório mostra o relatório de Lista de Chamadas do Grupo de Resposta para o período de tempo selecionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Chamadas atendidas</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas atendidas por um agente do Grupo de Resposta. Quando você clica nesse item, o relatório mostra o relatório de Lista de Chamadas do Grupo de Resposta para o período de tempo selecionado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Porcentagem de chamadas abandonadas</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas recebidas pelo aplicativo Grupo de Resposta, mas que nunca foram atendidas por um agente. Isso é calculado subtraindo as Chamadas atendidas das Chamadas recebidas e dividindo esse valor pelo número de chamadas recebidas. Por exemplo, se você tiver 10 chamadas recebidas e sete respondidas, subtraia sete de 10, deixando três chamadas não respondidas. Esse valor seria dividido por 10, proporcionando uma porcentagem de chamadas abandonadas de 30%.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Duração média em minutos de chamada por representante</strong></p></td>
<td><p>Não</p></td>
<td><p>Duração média que um agente do Grupo de Resposta gasta em uma chamada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Chamadas transferidas</strong></p></td>
<td><p>Não</p></td>
<td><p>Número total de chamadas do Grupo de Resposta transferidas devido a um tempo limite ou estouro de fila. Ao clicar nesse item, o relatório mostra o relatório Lista de Chamadas do Grupo de Resposta para o período selecionado.</p></td>
</tr>
</tbody>
</table>

