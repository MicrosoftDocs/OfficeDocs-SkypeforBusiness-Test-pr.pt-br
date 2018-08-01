---
title: 'Lync Server 2013: Relatório de Atividades do Usuário'
TOCTitle: Relatório de Atividades do Usuário
ms:assetid: 3aa6fef2-ea02-4f0f-93e8-fa2e0a953d79
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558638(v=OCS.15)
ms:contentKeyID: 49306427
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Atividades do Usuário no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Atividades do Usuário oferece uma lista detalhada das sessões ponto a ponto e de conferência realizadas pelos usuários em um determinado período. Diferente de muitos dos Relatórios de Monitoramento, o Relatório de Atividades do Usuário vincula cada chamada a usuários individuais. Por exemplo, as sessões ponto a ponto especificam URIs do SIP da pessoa que iniciou a chamada (o usuário de origem) e a pessoa que está sendo chamada (o usuário de destino). Se as informações forem ampliadas para uma conferência, será possível ver uma lista de todos os participantes da conferência e a função que desempenham na conferência.

O Relatório de Atividades do Usuário é referenciado algumas vezes como o relatório do "suporte técnico". Isso se deve ao fato de o relatório ser sempre usado pela equipe do suporte técnico para recuperar informações sobre a sessão para um usuário específico. É possível filtrar chamadas feitas para ou por um usuário individual simplesmente digitando o URI do SIP do usuário na caixa URI do usuário.

Se você fizer isso, o Relatório de atividades do usuário retornará informações sobre qualquer usuário cuja URI do SIP comece com a string especificada. Por exemplo, se você digitar **ken** na caixa URI, o Relatório de atividades do usuário localizará **Ken** .Myer@litwareinc.com. No entanto, ele localizará também esses usuários:

  - **ken** azi@litwareinc.com

  - **ken** burg@litwareinc.com

  - **Ken** .Sanchez@litwareinc.com

  - **Ken** nedy@litwareinc.com

Para garantir que somente informações sobre Ken Myer sejam retornadas, digite sua URI completa (Ken.Myer@litwareinc.com) na caixa de pesquisa ou, pelo menos, digite a URl do Ken o bastante para distingui-lo de outros usuários na organização. Por exemplo:

Ken.my

## Para acessar o Relatório de Atividades do Usuário

O Relatório de Atividades do Usuário é acessado pela home page dos Relatórios de Monitoramento. É possível acessar o Relatório de Atividades do Usuário clicando na medida URI do [Relatório de Inventário de Telefones IP no Lync Server 2013](lync-server-2013-ip-phone-inventory-report.md). No Relatório de Atividades do Usuário, ao clicar em URI da Conferência (para uma conferência), você será levado para o Relatório Detalhado de Conferências. Da mesma forma, ao clicar na medida Detalhes de uma chamada ponto a ponto, você será levado para o [Relatório de Detalhes de Sessão Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-session-detail-report.md).

## Fazendo o melhor uso do Relatório de Atividades do Usuário

Embora haja muitas informações relevantes no Relatório de Atividades do Usuário, essas informações podem, por vezes, ser difíceis de localizar. Por exemplo, toda a atividade de usuários que ocorre em sua organização durante um período específico está incluída no Relatório de Atividades do Usuário; isso significa que o relatório encerra informações sobre quais usuários realmente utilizaram o Microsoft Lync Server 2013 de alguma forma.


> [!WARNING]  
> Tecnicamente, é possível que algumas das atividades do usuário não sejam registradas: embora o Lync Server se esforce para manter as informações sobre todas as chamadas telefônicas, é possível que uma chamada tenha sido feita sem que as informações sobre ela fossem gravadas no banco de dados. O Lync Server foi projetado para oferecer uma visão extremamente precisa, porém não necessariamente perfeita de como o Lync Server 2013 está sendo usado. (O fato de não haver garantia de 100% de que todas as chamadas serão registradas explica por que o monitoramento do Lync Server não deve ser usado como sistema de faturamento.)<BR>Em segundo lugar, um Relatório de Monitoramento pode exibir apenas um máximo de 1.000 registros. Dependendo da quantidade de usuários que você tem e também de período com o qual está trabalhado, isso significa que sua consulta pode não retornar todos os dados realmente armazenados no banco de dados.



  - Quais usuários usaram realmente o sistema durante este período?

  - Quais dentre meus usuários foram os mais ativos durante este período?

  - Os usuários que fazem a maioria das chamadas são também aqueles que participam da maioria das sessões de mensagens instantâneas?

Se precisar responder a essas perguntas, será possível exportar os dados recuperados pelos Relatórios de Monitoramento para uma planilha do Excel. Utilize essa planilha e/ou um arquivo de valores separados por vírgulas para analisar os dados como faz o Relatório de Atividades do Usuário. Por exemplo, suponha que os dados do relatório tenham sido exportados para o Excel e depois para um arquivo de valores separados por vírgulas. Neste ponto, é possível importar os dados do arquivo .CSV para o Windows PowerShell usando um comando semelhante a esse:

    $x = Import-Csv -Path "C:\Data\User_Activity_Report.csv"

Depois que os dados forem importados, utilize os comandos do Windows PowerShell para ajudar a responder a suas perguntas. Por exemplo, este comando retorna uma lista de usuários exclusivos que atuaram como "usuário de origem" em pelo menos uma sessão.

    $x | Group-Object "From user" | Select Name | Sort-Object Name

Em outras palavras:

    Name
    ----
    David.Ahs@litwareinc.com
    Gilead.Amosnino@litwareinc.com
    Henrik.Jensen@litwareinc.com
    Ken.Myer@litwareinc.com
    Pilar.Ackerman@litwareinc.com

Este comando lista os usuários exclusivos (com base no número total de sessões das quais participaram:

    $x | Group-Object "From user" | Select Count, Name | Sort-Object Count -Descending

Este retorna dados semelhantes a estes:

    Count    Name
    -----    ----
      523    Ken.Myer@litwareinc.com
       63    David.Ahs@litwareinc.com
       29    Pilar.Ackerman@litwareinc.com
       17    Gilead.Amosnino@litwareinc.com
       10    Henrik.Jensen@litwareinc.com

Este comando limita as sessões reportadas àquelas que incluíram áudio como modalidade:

    $x | Where-Object {$_.Modalities -match "audio"} | Group-Object "From user" | Select Count, Name | Sort-Object Count -Descending

Se você pousar o mouse sobre qualquer ID do diagnóstico mostrado no relatório, uma dica de ferramenta será exibida descrevendo o ID.

## Filtros

O filtro é uma maneira de retornar um conjunto de dados mais refinado e direcionado, ou ver os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Atividades do Usuário permite filtrar os dados retornados com base em itens como tipo de atividade (isto é, sessão ponto a ponto ou de conferência) ou pelo endereço SIP do usuário (permitindo exibir as atividades para um usuário). Você também pode escolher como os dados serão agrupados; neste caso, os usos são agrupados por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que você pode usar com o Relatório de Atividades do Usuário.

### Filtros do Relatório de Atividades do Usuário

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
<p>7/17/2012 1:00 PM</p>
<p>Se você não inserir a hora de início, o relatório começará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/17/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/13/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data/hora final de intervalo de tempo. Para ver os dados por horas, insira a data e hora final conforme segue:</p>
<p>7/17/2012 1:00 PM</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>7/17/2012</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>7/13/2012</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de atividade</strong></p></td>
<td><p>Tipo de atividade. Selecione uma das seguintes opções:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Ponto a ponto</p></li>
<li><p>Conferência</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Modalidade</strong></p></td>
<td><p>A Modalidade disponível para você varia de acordo com o Tipo de Atividade selecionado. Se o Tipo de Atividade for Ponto a Ponto, você poderá selecionar Mensagem Instantânea; Transferência de Arquivo; Compartilhamento de Aplicativos; Voz; ou Vídeo como a modalidade.</p>
<p>Se o Tipo de Atividade for Conferência, você poderá selecionar conferência Telefônica de Mensagem Instantânea; conferência da Web; Compartilhamento de Aplicativos; conferência de Voz/Vídeo; ou conferência Telefônica.</p></td>
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
<p>Uma &quot;falha esperada&quot; é uma falha prevista; por exemplo, se um usuário configurou seu status para Não Perturbe, é previsto que qualquer chamada para ele irá falhar. Uma &quot;falha inesperada&quot; ocorre em um sistema que parecia saudável. Por exemplo, uma chamada não deveria ser terminada se o chamador for colocado em espera. Se isso ocorrer, será sinalizado como uma falha inesperada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Prefixo de URI do usuário</strong></p></td>
<td><p>Endereço SIP para o usuário. Para exibir registros somente para o usuário Ken Myer, digite o endereço SIP de Ken Myer. Por exemplo:</p>
<p>sip:kenmyer@litwareinc.com</p></td>
</tr>
</tbody>
</table>


## Métricas para sessões ponto a ponto

A tabela a seguir lista as informações fornecidas no Relatório de Atividades do Usuário para a sessões ponto a ponto (isto é, as que envolvem apenas dois participantes).

### Métricas para sessões ponto a ponto

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
<td><p><strong>Detalhe</strong></p></td>
<td><p>Não</p></td>
<td><p>Quando você clica neste item, é mostrado o Relatório de Detalhes de Sessão Ponto a Ponto para a sessão selecionada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Usuário &quot;De&quot;</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP do usuário que iniciou a sessão ponto a ponto.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Usuário &quot;Para&quot;</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP do usuário que entrou na sessão ponto a ponto.</p></td>
</tr>
<tr class="even">
<td><p><strong>Modalidades</strong></p></td>
<td><p>Sim</p></td>
<td><p>Tipo de comunicação usado na sessão. Por exemplo, IM, áudio ou transferência de arquivo.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora do convite</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora em que o convite inicial para entrar na sessão ponto a ponto foi enviado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora da resposta</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora em que o usuário &quot;Para&quot; aceitou o convite para a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora final</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora em que a sessão ponto a ponto terminou.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Sim</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho de diagnóstico-ms) anexado a uma mensagem SIP que fornece informações úteis sobre os erros de solução de problemas. Os cabeçalhos diagnósticos são opcionais (é possível ter sessões SIP que não os incluem), e os IDs diagnósticos são relatados somente para as sessões com algum tipo de problema.</p></td>
</tr>
</tbody>
</table>


## Métricas para sessões de conferência

A tabela a seguir lista as informações fornecidas no Relatório de Atividades do Usuário para a sessões de conferência (isto é, as que envolvem três ou mais participantes).

### Métricas para sessões de conferência

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
<td><p><strong>URI de conferência</strong></p></td>
<td><p>Sim</p></td>
<td><p>Identificador exclusivo da conferência. Quando você clica neste item, é mostrado o Relatório de Detalhes da Conferência para a sessão selecionada. Quando você expande esse item, o relatório mostra as informações sobre os participantes. Para obter os detalhes, consulte &quot;Métricas para participantes da conferência&quot;, mais adiante neste tópico.</p></td>
</tr>
<tr class="even">
<td><p><strong>Organizador</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP do usuário que organizou a conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>Sim</p></td>
<td><p>Nome do Servidor de Borda (se houver) usado na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora inicial</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora em que a conferência começou.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora final</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora em que a conferência terminou.</p></td>
</tr>
</tbody>
</table>


## Métricas para participantes da conferência

A tabela a seguir lista as informações fornecidas no Relatório de Atividades do Usuário para cada participante de uma conferência.

### Métricas para participantes da conferência

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
<td><p><strong>Função</strong></p></td>
<td><p>Não</p></td>
<td><p>Função do usuário na conferência (por exemplo, Apresentador).</p></td>
</tr>
<tr class="even">
<td><p><strong>Participante</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Conectividade</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de conexão da rede. Por exemplo, &quot;De Interno&quot; para conexão interna ou &quot;De PSTN&quot; os usuários discados.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora da entrada</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora em que o usuário entrou na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora da saída</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora em que o usuário saiu da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho de diagnóstico-ms) anexado a uma mensagem SIP que fornece informações úteis sobre os erros de solução de problemas. Os cabeçalhos diagnósticos são opcionais (é possível ter sessões SIP que não os incluem), e os IDs diagnósticos são relatados somente para as sessões com algum tipo de problema.</p></td>
</tr>
</tbody>
</table>

