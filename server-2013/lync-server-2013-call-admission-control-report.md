---
title: 'Lync Server 2013: Relatório de Ccontrole de Admissão de Chamadas'
TOCTitle: Relatório de Ccontrole de Admissão de Chamadas
ms:assetid: ea4b0c9f-7f93-4b8a-b901-01e1636c44fb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615043(v=OCS.15)
ms:contentKeyID: 49308492
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Ccontrole de Admissão de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório de Controle de Admissão de Chamadas fornece informações sobre sessões de conferência e ponto a ponto que eram conduzidas sob restrições impostas pelo Controle de Admissão de Chamadas. O Controle de Admissão de Chamadas, introduzido no Microsoft Lync Server 2010, fornece uma maneira para que os administradores permitam (ou não) sessões de comunicação baseadas em limites de largura de banda. Por exemplo, os administradores podem criar políticas que impõe um limite na quantidade de banda disponível para chamadas de voz e vídeo. Caso o limite de banda tenha sido alcançado, novas chamadas de voz ou vídeo não poderão ser feitas até que uma das chamadas atuais termine e libere os recursos de rede necessários.

## Acessando o Relatório de Controle de Admissão de Chamadas

O Relatório de Controle de Admissão de Chamadas é acessado através da página de Relatórios de Monitoramento. A partir do Relatório de Controle de Admissão de Chamadas você pode buscar mais detalhes em um dos seguintes relatórios:

  - Relatório de Detalhes de Conferência - Para acessar este relatório, clique na métrica Detalhes em uma sessão de conferência.

  - Relatório de Detalhe de Sessão Ponto a Ponto - Para acessar este relatório, clique na métrica Detalhes para uma sessão ponto a ponto.

## Usando o Relatório de Controle de Admissão de Chamadas da melhor maneira possível

Para obter uma lista de chamadas que falharam por causa de largura de banda insuficiente, selecione Chamadas rejeitadas por causa do controle de admisssão de chamadas, na lista suspensa de categoria de Chamadas. A maioria das chamadas retornadas provavelmente terão a ID de diagnóstico 5:

Largura de banda insuficiente para estabelecer sessão. Tente reencaminhamento PSTN.

Isso indica que as limitações do Controle de Admissão de Chamadas estavam impedidndo a chamada de ser feita na rede VoIP.

## Filtros

Os filtros fornecem uma maneira de retornar um conjunto de dados mais direcionado ou de exibir os dados retornados de maneiras diferentes. Por exemplo, o Relatório de Controle de Admissão de Chamada permite que você filtre as chamadas de acordo com o usuário que iniciou a chamada ou com o usuário que está sendo chamado. Também é possível escolher como os dados devem ser agrupados. Nesse caso, as chamadas são agrupadas por hora, dia, semana ou mês.

A tabela a seguir lista os filtros que podem ser usados com o Relatório de Controle de Admissão de Chamada.

### Filtros do Relatório de Controle de Admissão de Chamadas

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
<p>17/7/012 13:00</p>
<p>Se você não inserir a hora de início, o relatório começará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>17/7/12</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>13/7/12</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="even">
<td><p><strong>Até</strong></p></td>
<td><p>Data/hora final de intervalo de tempo. Para ver os dados por horas, insira a data e hora final conforme segue:</p>
<p>17/7/012 13:00</p>
<p>Se você não inserir a hora final, o relatório terminará automaticamente à meia-noite do dia especificado. Para ver os dados por dia, insira somente a data:</p>
<p>17/7/12</p>
<p>Para exibir por semana ou mês, insira uma data dentro da semana ou mês que deseja exibir (não é necessário inserir o primeiro dia da semana ou mês):</p>
<p>13/7/12</p>
<p>As semanas sempre vão de domingo a sábado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>FQDN (Nome de domínio totalmente qualificado) do pool de Registradores ou Servidor de Borda. Você pode selecionar um pool individual ou clicar em <strong>[Tudo]</strong> para ver os dados de todos os pools. Essa lista suspensa é automaticamente preenchida para você com base nos registros no banco de dados.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de atividade</strong></p></td>
<td><p>Tipo de atividade. Selecione uma das seguintes atividades:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Ponto a ponto</p></li>
<li><p>Conferência</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>Categoria da chamada</strong></p></td>
<td><p>Indica o motivo de o CAC ter sido usado para a chamada. Selecione uma das seguintes opções:</p>
<ul>
<li><p>[Todos]</p></li>
<li><p>Chamada rejeitada devido ao controle de admissão de chamada</p></li>
<li><p>Chamadas reencaminhadas por PSTN devido ao controle de admissão de chamada</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Métricas para sessões ponto a ponto

A tabela a seguir lista as informações fornecidas no Relatório de Controle de Admissão de Chamada para sessões ponto a ponto (ou seja, sessões que envolvem apenas dois participantes).

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
<td><p>Quando você clica nesse item, o relatório mostra o Relatório de Detalhes da Sessão Ponto a Ponto para a sessão especificada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Usuário &quot;De&quot;</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Usuário &quot;Para&quot;</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP do usuário convidado para ingressar na sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Modalidades</strong></p></td>
<td><p>Sim</p></td>
<td><p>Modalidades de comunicação (como áudio e vídeo) usadas durante a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora do convite</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora de envio do convite inicial da sessão para o usuário De.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora da resposta</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora de recebimento da aceitação do convite.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora final</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora de encerramento da sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Sim</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho de diagnóstico-ms) anexado a uma mensagem SIP que fornece informações úteis sobre os erros de solução de problemas. Os cabeçalhos diagnósticos são opcionais (é possível ter sessões SIP que não os incluem), e os IDs diagnósticos são relatados somente para as sessões com algum tipo de problema.</p></td>
</tr>
</tbody>
</table>


## Métricas para sessões de conferência

A tabela a seguir lista as informações fornecidas no Relatório de Controle de Admissão de Chamada para sessões de conferência (ou seja, sessões que envolvem três ou mais participantes).

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
<td><p>Identificador exclusivo para a conferência. Quando você clica nesse item, o relatório mostra os participantes individuais da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Organizador</strong></p></td>
<td><p>Sim</p></td>
<td><p>Endereço SIP do usuário que organizou a conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Pool</strong></p></td>
<td><p>Sim</p></td>
<td><p>Servidor de Borda usado na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora inicial</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora de início da sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora final</strong></p></td>
<td><p>Sim</p></td>
<td><p>Data e hora em que a conferência terminou.</p></td>
</tr>
</tbody>
</table>


## Métricas para participantes individuais de conferência

A tabela a seguir lista as informações fornecidas no Relatório de Controle de Admissão de Chamada para participantes individuais da conferência.

### Métricas para participantes individuais de conferência

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
<td><p>Função (por exemplo, Apresentador) desempenhada pelo participante da conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Participante</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do participante de conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Conectividade</strong></p></td>
<td><p>Não</p></td>
<td><p>Conectividade de rede (normalmente Interna ou Externa) para o participante.</p></td>
</tr>
<tr class="even">
<td><p><strong>Modalidade</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de conferência (por exemplo, conferência A/V).</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora da entrada</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora de ingresso do participante na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora da saída</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora de saída do participante da conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho de diagnóstico-ms) anexado a uma mensagem SIP que fornece informações úteis sobre os erros de solução de problemas. Os cabeçalhos diagnósticos são opcionais (é possível ter sessões SIP que não os incluem), e os IDs diagnósticos são relatados somente para as sessões com algum tipo de problema.</p></td>
</tr>
</tbody>
</table>

