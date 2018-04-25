---
title: 'Lync Server 2013: Relatório de Detalhes de Sessão Ponto a Ponto'
TOCTitle: Relatório de Detalhes de Sessão Ponto a Ponto
ms:assetid: 6be1d676-68f7-4a53-a72a-de73296c5571
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558659(v=OCS.15)
ms:contentKeyID: 49307014
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de Detalhes de Sessão Ponto a Ponto no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Relatório Detalhado de Sessão Ponto a Ponto retorna informações detalhadas sobre uma sessão ponto a ponto. Por exemplo, se você selecionar uma sessão de mensagens instantâneas, o relatório informará o número de mensagens enviadas por cada um dos dois usuários na seção.

## Acessando o Relatório Detalhado de Sessão Ponto a Ponto

O Relatório Detalhado de Sessão Ponto a Ponto pode ser acessado a partir de qualquer um dos relatórios a seguir (todos os quais podem ser acessados a partir da home page Relatórios de Monitoramento):

  - Relatório de inventário de telefones IP

  - Relatório de atividades do usuário

  - Relatório de controle de admissão de chamadas

  - Relatório de lista de falhas

A partir do Relatório Detalhado de Sessão Ponto a Ponto, você pode acessar o [Relatório de diagnósticos no Lync Server 2013](lync-server-2013-diagnostic-report.md) clicando na métrica Relatório de Diagnóstico (Detalhes). Você também pode acessar o Relatório das Principais Falhas clicando em uma destas duas métricas:

  - Resposta

  - ID do Diagnóstico

## Usando o Relatório Detalhado de Sessão Ponto a Ponto da melhor maneira possível

O Relatório Detalhado de Sessão Ponto a Ponto inclui um grande número de métricas, muitas das quais os administradores de sistemas podem desconhecer. Muitas vezes, porém, você pode exibir uma dica de ferramenta que oferece uma breve descrição da métrica. Para isso, basta manter o cursor do mouse sobre o rótulo da métrica.

Observe que as métricas mostradas em determinado relatório dependerão do tipo de sessão ponto a ponto selecionada. Uma sessão de áudio/vídeo mostrará um conjunto de métricas diferente de uma sessão de mensagens instantâneas.

Você também pode manter o cursor do mouse sobre as métricas Código de resposta e ID de diagnóstico para obter uma descrição desses valores:

## Filtros

Nenhum. Não é possível filtrar o relatório de Detalhes de Sessão Ponto a Ponto.

## Métricas de informações da sessão

A tabela a seguir lista as informações fornecidas no relatório de Detalhes de Sessão Ponto a Ponto para cada sessão.

### Métricas de informações da sessão

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
<td><p><strong>FQDN do pool</strong></p></td>
<td><p>Nome de domínio totalmente qualificado (FQDN) do pool de Registradores ou Servidor de Borda envolvido na sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora do convite</strong></p></td>
<td><p>Data e hora em que o convite de sessão foi originalmente enviado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora da resposta</strong></p></td>
<td><p>Data e hora de recebimento da aceitação do convite.</p></td>
</tr>
<tr class="even">
<td><p><strong>Usuário &quot;De&quot;</strong></p></td>
<td><p>Endereço SIP do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Representante do usuário de origem</strong></p></td>
<td><p>Software usado pelo ponto de extremidade do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>É Usuário interno de origem</strong></p></td>
<td><p>Indica se o usuário que iniciou a sessão estava conectado à rede interna.</p></td>
</tr>
<tr class="odd">
<td><p><strong>É Usuário de origem integrado ao telefone de mesa</strong></p></td>
<td><p>Indica se o ponto de extremidade usado pelo usuário que iniciou a sessão está integrado ao seu telefone de mesa.</p></td>
</tr>
<tr class="even">
<td><p><strong>Prioridade da Sessão</strong></p></td>
<td><p>Prioridade atribuída à sessão. As prioridades válidas são: Desconhecida; Não Urgente; Normal; Urgente; e Emergência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Código da resposta</strong></p></td>
<td><p>Código da resposta SIP enviado quando a sessão falhou.</p></td>
</tr>
<tr class="even">
<td><p><strong>Front-End</strong> .</p></td>
<td><p>Nome do Servidor Front-End usado na conferência.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Hora da captura</strong></p></td>
<td><p>Data e hora em que a sessão de informações foi gravada.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora final</strong></p></td>
<td><p>Data e hora em que a sessão foi encerrada.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Usuário &quot;Para&quot;</strong></p></td>
<td><p>Endereço SIP do usuário convidado para a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Para o agente do usuário</strong></p></td>
<td><p>Software usado pelo ponto de extremidade do usuário que foi convidado para a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>É Usuário interno de destino</strong></p></td>
<td><p>Indica se o usuário que foi convidado para a sessão estava conectado à rede interna.</p></td>
</tr>
<tr class="even">
<td><p><strong>É Usuário de destino integrado ao telefone de mesa</strong></p></td>
<td><p>Indica se o ponto de extremidade usado pelo usuário que foi convidado para a sessão está integrado ao seu telefone de mesa.</p></td>
</tr>
<tr class="odd">
<td><p><strong>É sessão repetida</strong></p></td>
<td><p>Indica se a sessão é uma tentativa para repetir uma sessão que falhou anteriormente.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Identificador exclusivo (no formato de um cabeçalho ms-diagnostics) anexado a uma mensagem SIP que frequentemente oferece informações úteis para resolução de erros. Mantenha o mouse sobre o número de identificação para exibir informações adicionais sobre essa identificação.</p></td>
</tr>
</tbody>
</table>


## Métricas para modalidades

A tabela a seguir lista as informações fornecidas no relatório de Detalhes de Sessão Ponto a Ponto para cada sessão de modalidade.

### Métricas para modalidades

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
<td><p><strong>Modalidades</strong></p></td>
<td><p>Não</p></td>
<td><p>Modalidades usadas na sessão. Por exemplo, mensagens instantâneas ou transferência de arquivo.</p></td>
</tr>
<tr class="even">
<td><p><strong>Mensagens do usuário de origem</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de mensagens enviadas pelo usuário que iniciou a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Mensagens do usuário de destino</strong></p></td>
<td><p>Não</p></td>
<td><p>Número de mensagens enviadas pelo usuário que foi convidado para a sessão.</p></td>
</tr>
</tbody>
</table>


## Métricas para relatórios de diagnóstico

A tabela a seguir lista as informações fornecidas no relatório de Detalhes de Sessão Ponto a Ponto para cada relatório de diagnóstico.

### Métricas para relatórios de diagnóstico

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
<td><p>Quando você clica nesse item, o relatório mostra o Relatório de Diagnóstico da sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Hora do relatório</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora do registro do relatório.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Solicitação</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de solicitação SIP. Por exemplo, INVITE ou BYE.</p></td>
</tr>
<tr class="even">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho ms-diagnostics) anexado a uma mensagem SIP que frequentemente fornece informações úteis para solução de erros.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de conteúdo</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de conteúdo de mídia usado na conferência. Por exemplo, um tipo de conteúdo comum é Application/sdp. O protocolo SDP é um protocolo padrão de Internet usado para comunicados de sessão, convites de sessão e outras formas de início de sessão multimídia.</p></td>
</tr>
<tr class="even">
<td><p><strong>Relatado por</strong></p></td>
<td><p>Não</p></td>
<td><p>Computador (isso é, o cliente ou servidor) que relatou o problema.</p></td>
</tr>
</tbody>
</table>

