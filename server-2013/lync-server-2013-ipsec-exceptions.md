---
title: Exceções Ipsec no Lync Server 2013
TOCTitle: Exceções Ipsec no Lync Server 2013
ms:assetid: 241f1eca-6f2f-44de-90b1-2cb659cbe27c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425719(v=OCS.15)
ms:contentKeyID: 49306141
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exceções Ipsec no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Nas redes corporativas em que o protocolo IPsec (consulte a RFC 4301-4309 da IETF) foi implantado, o protocolo IPsec deverá ser desabilitado no intervalo de portas usado para a entrega de áudio, vídeo e vídeo panorama. A recomendação vem da necessidade de evitar qualquer atraso na alocação das portas de mídia por causa da negociação IPsec.

A tabela a seguir explica as configurações de exceções recomendadas do IPsec.

### Exceções recomendadas do IPsec

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome da regra</th>
<th>IP de origem</th>
<th>IP de destino</th>
<th>Protocolo</th>
<th>Porta de origem</th>
<th>Porta de destino</th>
<th>Requisito de autenticação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Entrada interna do Servidor de Borda A/V</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Interno do Servidor de Borda A/V</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Entrada externa do Servidor de Borda A/V</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Externo do Servidor de Borda A/V</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Saída interna do Servidor de Borda A/V</p></td>
<td><p>Interno do Servidor de Borda A/V</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Saída externa do Servidor de Borda A/V</p></td>
<td><p>Externo do Servidor de Borda A/V</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Entrada do Servidor de Mediação</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Mediação</p>
<p>Servidor(es)</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Saída do Servidor de Mediação</p></td>
<td><p>Mediação</p>
<p>Servidor(es)</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Entrada do Atendedor de Conferência</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Servidor Front End executando o Atendedor de Conferência</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Saída do Atendedor de Conferência</p></td>
<td><p>Servidor Front End executando o Atendedor de Conferência</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Entrada de Conferência A/V</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Servidores Front-End</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Saída de Conferência A/V</p></td>
<td><p>Servidores Front-End</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Entrada do Exchange</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Unificação de Mensagens do Exchange</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Entrada dos Servidores de Compartilhamento de Aplicativo</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Servidores de Compartilhamento de Aplicativos</p></td>
<td><p>TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Saída do Servidor de Compartilhamento de Aplicativos.</p></td>
<td><p>Servidores de Compartilhamento de Aplicativos</p></td>
<td><p>Qualquer uma</p></td>
<td><p>TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="even">
<td><p>Saída do Exchange</p></td>
<td><p>Unificação de Mensagens do Exchange</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP e TCP</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
<tr class="odd">
<td><p>Clientes</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Qualquer uma</p></td>
<td><p>UDP</p></td>
<td><p>Intervalo especificado de portas de mídia</p></td>
<td><p>Qualquer uma</p></td>
<td><p>Não autenticar</p></td>
</tr>
</tbody>
</table>

