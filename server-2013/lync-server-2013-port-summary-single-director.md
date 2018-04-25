---
title: 'Lync Server 2013: Resumo de porta - Diretor único'
TOCTitle: Resumo de porta - Diretor único
ms:assetid: 079c1414-723f-4499-b7d4-a0d7121c1626
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204648(v=OCS.15)
ms:contentKeyID: 49305791
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de porta - Diretor único no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos de porta de firewall para um único Diretor são compostos pelas portas usadas para estabelecer comunicação com o Diretor a partir da interface interna ou da rede interna do proxy reverso. Por padrão, o Microsoft Lync Server 2013 espera que as portas HTTP/TCP 8080 e HTTPS/TCP 4443 estejam abertas para o proxy reverso para o Diretor, assim como para o Pool de Front-Ends e o Servidor Front-End. Além disso, é necessário haver comunicação SIP (session initiation protocol) da interface interna do Servidor de Borda para o Diretor e o Pool de Front-Ends e Servidor Front-End. O protocolo SIP usa SIP/MTLS/TCP 5061 do Servidor de Borda para o Pool de Front-Ends e o Servidor Front-End. Também é necessário criar uma regra que permite a comunicação SIP/MTLS/TCP 5061 do Diretor, Pool de Front-Ends e Servidor Front-End com a interface interna do Servidor de Borda.

### Portas e protocolos únicos do Diretor para definições de firewall

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Função/Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP 8080</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Diretor</p></td>
<td><p>Recebido inicialmente pelo lado externo do proxy reverso, a comunicação é enviada aos serviços Web do Diretor e do Servidor Front-End</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP 4443</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Diretor</p></td>
<td><p>Recebido inicialmente pelo lado externo do proxy reverso, a comunicação é enviada aos serviços Web do Diretor e do Servidor Front-End</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 444</p></td>
<td><p>Diretor</p></td>
<td><p>Servidor Front-End ou pool de Front-Ends</p></td>
<td><p>Comunicação entre servidores entre o Diretor e o Servidor Front-End</p></td>
</tr>
<tr class="even">
<td><p>HTTP/TCP 80</p></td>
<td><p>Clientes internos</p></td>
<td><p>Serviços Web do Diretor</p></td>
<td><p>O Diretor fornece serviços Web para clientes internos e externos.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 443</p></td>
<td><p>Clientes internos</p></td>
<td><p>Serviços Web do Diretor</p></td>
<td><p>O Diretor fornece serviços Web para clientes internos e externos.</p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP 5061</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Diretor</p></td>
<td><p>Comunicação SIP do Servidor de Borda para o Diretor, e o Servidor Front-End.</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Controlador Serviço de Log Centralizado (ClsController.exe) ou comandos e conjunto de log do agente (ClasAgent.exe)</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Controlador Serviço de Log Centralizado (ClsController.exe) ou comandos e conjunto de log do agente (ClasAgent.exe)</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>Qualquer um</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Controlador Serviço de Log Centralizado (ClsController.exe) ou comandos e conjunto de log do agente (ClasAgent.exe)</p></td>
</tr>
</tbody>
</table>

