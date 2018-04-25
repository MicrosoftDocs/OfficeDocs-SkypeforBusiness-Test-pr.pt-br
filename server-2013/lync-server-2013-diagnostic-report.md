---
title: 'Lync Server 2013: Relatório de diagnósticos'
TOCTitle: Relatório de diagnósticos
ms:assetid: b389dbd9-f2e8-4184-93d0-2e504796ac16
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615445(v=OCS.15)
ms:contentKeyID: 49307840
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de diagnósticos no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Relatório de diagnóstico fornece diagnósticos e informações para a solução de problemas de uma sessão com falha. Essas informações incluem a ID de diagnóstico e o cabeçalho de Diagnóstico que foram importados quando a sessão falhou. A ID de diagnóstico é um identificador exclusivo (na forma de um cabeçalho ms-diagnostics) que é anexado a uma mensagem SIP, enquanto a cabeçalho de Diagnóstico fornece uma descrição da ID de diagnóstico. O relatório também pode conter detalhes importantes para a solução de problemas e que são conhecidos pelo componente de relatório. Por exemplo:

  - O código de motivo fornecido pelo gateway da PSTN que gerou a falha. Quando uma chamada de saída falha na rede PSTN, um código de causa ISUP (parte de usuário ISDN, em inglês) é gerado automaticamente. Por exemplo, um gateway PSTN pode enviar o código de causa 34 para indicar que nenhum circuito ou canal estava disponível para completar a chamada.

  - FQDN do par, porta e erros de Winsock para falhas de conectividade.

  - Nomes pesquisados por falhas de resolução de DNS. A resolução DNS ocorre sempre que um cliente entra em contato com um servidor de nomes e solicita o endereço IP que corresponde ao nome de dispositivo especificado.

## Acessando o relatório de diagnósticos

O Relatório de diagnósticos pode ser acessado clicando na métrica Relatório de diagnósticos (Detalhe) no [Relatório de Detalhes de Sessão Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-session-detail-report.md) no Relatório de detalhes de conferência.

## Filtros

Nenhum. Não é possível filtrar o Relatório de Diagnóstico.

## Métricas

A tabela a seguir lista as informações fornecidas no Relatório de Diagnóstico para cada sessão.

### Métricas do Relatório de Diagnóstico

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
<td><p><strong>Hora do relatório</strong></p></td>
<td><p>Não</p></td>
<td><p>Data e hora do registro do relatório.</p></td>
</tr>
<tr class="even">
<td><p><strong>Código da resposta</strong></p></td>
<td><p>Não</p></td>
<td><p>Código da resposta SIP enviado quando a sessão falhou.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Tipo de solicitação</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de solicitação SIP que falhou. Por exemplo, CONVIDAR, ATÉ LOGO ou SERVIÇO.</p></td>
</tr>
<tr class="even">
<td><p><strong>Origem</strong></p></td>
<td><p>Não</p></td>
<td><p>Origem do erro.</p></td>
</tr>
<tr class="odd">
<td><p><strong>URI do usuário de origem</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="even">
<td><p><strong>Representante do usuário de origem</strong></p></td>
<td><p>Não</p></td>
<td><p>Software usado pelo ponto de extremidade do usuário que iniciou a sessão.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ID do Diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Identificador exclusivo (na forma de um cabeçalho ms-diagnostics) anexado a uma mensagem SIP que frequentemente fornece informações úteis para solução de erros.</p></td>
</tr>
<tr class="even">
<td><p><strong>Tipo de conteúdo</strong></p></td>
<td><p>Não</p></td>
<td><p>Tipo de conteúdo de mídia que falhou. Por exemplo, um tipo de conteúdo comum é Application/sdp. SDP (Protocolo de descrição de sessão) é um protocolo padrão de Internet usado para anúncios de sessão, convites de sessão e outras formas de início de sessão multimídia.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Aplicativo</strong></p></td>
<td><p>Não</p></td>
<td><p>Aplicativo envolvido no erro.</p></td>
</tr>
<tr class="even">
<td><p><strong>URI do usuário de destino</strong></p></td>
<td><p>Não</p></td>
<td><p>Endereço SIP do usuário convidado para a sessão.</p></td>
</tr>
<tr class="odd">
<td><p>Hora de ingresso de conferência (ms)</p></td>
<td><p>Não</p></td>
<td><p>Tempo (em milissegundos) que o usuário precisou para ingressar na conferência.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cabeçalho do diagnóstico</strong></p></td>
<td><p>Não</p></td>
<td><p>Descrição do ID de diagnóstico.</p></td>
</tr>
</tbody>
</table>


Uma lista de erros de diagnóstico pode ser encontrada na [página Cabeçalho Ms-Diagnostics](http://msdn.microsoft.com/en-us/library/gg132446\(v=office.12\).aspx).

