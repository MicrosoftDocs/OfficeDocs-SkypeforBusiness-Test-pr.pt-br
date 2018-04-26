---
title: Eventos do UCWA
TOCTitle: Eventos do UCWA
ms:assetid: 26cb409d-f4e4-43c7-873f-b694702d491d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945621(v=OCS.15)
ms:contentKeyID: 52057573
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Eventos do UCWA

 

_**Tópico modificado em:** 2015-03-09_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

O Lync Server 2013 usa a API Web de Comunicação Unificada (UCWA) para diversos propósitos, desde acessar o Microsoft Exchange para pesquisas de contato até a atualização de presença para clientes móveis.

A UCWA gravará registros de comportamento operacional como tipos de evento Informacional, Aviso e Erro. A tabela a seguir descreve tais eventos que podem ser gravados com componentes da UCWA.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>ID do evento</th>
<th>Tipo de evento</th>
<th>Resumo</th>
<th>Causa e resolução</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>20001</p></td>
<td><p>Informativo</p></td>
<td><p>UCWA inicializado</p></td>
<td><p>N/D</p>
<p>N/D</p></td>
</tr>
<tr class="even">
<td><p>20002</p></td>
<td><p>Erro</p></td>
<td><p>A UCWA encontrou uma exceção inesperada durante a inicialização</p></td>
<td><p>Ocorreu um erro inesperado durante a inicialização</p>
<p>Examine os detalhes da exceção na entrada de log do evento associado para determinar a possível causa</p></td>
</tr>
<tr class="odd">
<td><p>20003</p></td>
<td><p>Erro</p></td>
<td><p>A UCWA encontrou uma exceção não manipulada</p></td>
<td><p>Ocorreu uma exceção não manipulada</p>
<p>Reinicie o servidor. Se o problema persistir, entre em contato com o suporte do produto</p></td>
</tr>
<tr class="even">
<td><p>20004</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível acessar o Exchange para foto HD</p></td>
<td><p>A conexão com o Exchange não está disponível</p>
<p>Certifique-se de que a conexão com o Exchange está disponível</p></td>
</tr>
<tr class="odd">
<td><p>20005</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de uma falha ao acessar o Exchange para foto HD</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="even">
<td><p>20006</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível acessar o Exchange para pesquisa de contato</p></td>
<td><p>A conexão com o Exchange não está disponível</p>
<p>Certifique-se de que a conexão com o Exchange está disponível</p></td>
</tr>
<tr class="odd">
<td><p>20007</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de uma falha em pesquisar contato no Exchange</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="even">
<td><p>20008</p></td>
<td><p>Aviso</p></td>
<td><p>Tente assinar mais de uma assinatura de presença permitida por aplicativo</p></td>
<td><p>Tente assinar mais de uma assinatura de presença permitida por aplicativo</p>
<p>Verifique se os clientes possuem assinaturas desnecessárias</p></td>
</tr>
<tr class="odd">
<td><p>20009</p></td>
<td><p>Aviso</p></td>
<td><p>Tente assinar mais de uma assinatura de presença permitida por lote</p></td>
<td><p>Tente assinar mais de uma assinatura de presença permitida por lote</p>
<p>Verifique se os clientes possuem assinaturas desnecessárias</p></td>
</tr>
<tr class="even">
<td><p>20010</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível recuperar os dados inband</p></td>
<td><p>Não é possível recuperar os dados inband</p>
<p>Se o problema persistir entre em contato com o suporte do produto</p></td>
</tr>
<tr class="odd">
<td><p>20011</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível assinar a presença</p></td>
<td><p>Não é possível assinar a presença</p>
<p>Se o problema persistir entre em contato com o suporte do produto</p></td>
</tr>
<tr class="even">
<td><p>20012</p></td>
<td><p>Erro</p></td>
<td><p>Falha ao registrar o ponto de extremidade</p></td>
<td><p>Falha ao registrar o ponto de extremidade</p>
<p>Se o problema persistir entre em contato com o suporte do produto</p></td>
</tr>
<tr class="odd">
<td><p>20013</p></td>
<td><p>Erro</p></td>
<td><p>A MCU de IM não está disponível</p></td>
<td><p>A MCU de IM não está disponível</p>
<p>Consulte se a MCU de IM está sendo executada</p></td>
</tr>
<tr class="even">
<td><p>20014</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de uma falha ao conectar ao MCU de IM</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="odd">
<td><p>20015</p></td>
<td><p>Erro</p></td>
<td><p>A MCU de AV não está disponível</p></td>
<td><p>A MCU de AV não está disponível</p>
<p>Consulte se a MCU de AV está sendo executada</p></td>
</tr>
<tr class="even">
<td><p>20016</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de uma falha ao conectar ao MCU de AV</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="odd">
<td><p>20017</p></td>
<td><p>Erro</p></td>
<td><p>A MCU de AS não está disponível</p></td>
<td><p>A MCU de AS não está disponível</p>
<p>Consulte se a MCU de AS está sendo executada</p></td>
</tr>
<tr class="even">
<td><p>20018</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de uma falha ao conectar ao MCU de AS</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="odd">
<td><p>20019</p></td>
<td><p>Erro</p></td>
<td><p>A MCU de Dados não está disponível</p></td>
<td><p>A MCU de Dados não está disponível</p>
<p>Consulte se a MCU de Dados está sendo executada</p></td>
</tr>
<tr class="even">
<td><p>20020</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de uma falha ao conectar ao MCU de dados</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="odd">
<td><p>20021</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível participar da MCU de IM</p></td>
<td><p>Não é possível participar da MCU de IM</p>
<p>Consulte se a MCU de IM está sendo executada</p></td>
</tr>
<tr class="even">
<td><p>20022</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível participar da MCU de AV</p></td>
<td><p>Não é possível participar da MCU de AV</p>
<p>Consulte se a MCU de AV está sendo executada</p></td>
</tr>
<tr class="odd">
<td><p>20023</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível participar da MCU de AS</p></td>
<td><p>Não é possível participar da MCU de AS</p>
<p>Consulte se a MCU de AS está sendo executada</p></td>
</tr>
<tr class="even">
<td><p>20024</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível participar da MCU de Dados</p></td>
<td><p>Não é possível participar da MCU de Dados</p>
<p>Consulte se a MCU de Dados está sendo executada</p></td>
</tr>
<tr class="odd">
<td><p>20025</p></td>
<td><p>Erro</p></td>
<td><p>Não é possível acessar o diretório ativo para foto</p></td>
<td><p>A conexão com o diretório ativo não está disponível</p>
<p>Certifique-se de que a conexão com o diretório ativo está disponível</p></td>
</tr>
<tr class="even">
<td><p>20026</p></td>
<td><p>Informativo</p></td>
<td><p>Recuperação de falha ao acessar o diretório ativo para foto</p></td>
<td><p>N/D</p></td>
</tr>
<tr class="odd">
<td><p>20027</p></td>
<td><p>Aviso</p></td>
<td><p>Não é possível desserializar</p></td>
<td><p>Não é possível desserializar</p>
<p>Se o problema persistir entre em contato com o suporte do produto</p></td>
</tr>
</tbody>
</table>

