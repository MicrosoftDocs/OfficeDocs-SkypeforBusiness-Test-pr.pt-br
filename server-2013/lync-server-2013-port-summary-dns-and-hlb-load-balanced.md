---
title: 'Lync Server 2013: Resumo de porta - cargas de DNS e de HLB balanceadas'
TOCTitle: Resumo de porta - cargas de DNS e de HLB balanceadas
ms:assetid: b07c37e4-820e-46ee-a678-1da95d1b87af
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205179(v=OCS.15)
ms:contentKeyID: 49307809
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de porta - cargas de DNS e de HLB balanceadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos de porta de firewall para um único Diretor consistem nas portas que são usadas para estabelecer comunicações com o Diretor da interface ou rede interna do proxy reverso. Por padrão, o Microsoft Lync Server 2013 espera que as portas HTTP/TCP 8080 e HTTPS/TCP 4443 sejam abertas no proxy reverso Diretor, bem como o Pool de Front-Ends e o Servidor Front-End. Além disso, deve haver uma comunicação de protocolo de inicialização de sessão (SIP) da interface interna do Servidor de Borda para o Diretor, bem como para o Pool de Front-Ends e o Servidor Front-End. O protocolo SIP usa SIP/MTLS/TCP 5061 do Servidor de Borda para o Pool de Front-Ends e o Servidor Front-End. Também é necessário criar uma regra que permite a comunicação SIP/MTLS/TCP 5061 do Diretor, do Pool de Front-Ends e do Servidor Front-End com a interface interna do Servidor de Borda.

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
<td><p>VIP de balanceador de carga de hardware Diretor</p></td>
<td><p>Recebido inicialmente pelo lado externo no proxy reverso, as comunicações são enviadas para o VIP HLB Diretor e os serviços Web Servidor Front-End.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP 4443</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>VIP de balanceador de carga de hardware Diretor</p></td>
<td><p>Recebido inicialmente pelo lado externo no proxy reverso, as comunicações são enviadas para o VIP HLB Diretor e os serviços Web Servidor Front-End.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 444</p></td>
<td><p>Diretor</p></td>
<td><p>Pool de Front-Ends ou Servidor Front-End</p></td>
<td><p>Comunicação de servidores entre o VIP HLB do Diretor e o Servidor Front-End ou Servidores Front-End.</p></td>
</tr>
<tr class="even">
<td><p>HTTP/TCP 80</p></td>
<td><p>Clientes internos</p></td>
<td><p>VIP de balanceador de carga de hardware Diretor</p></td>
<td><p>O Diretor fornece serviços Web para clientes internos e externos.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 443</p></td>
<td><p>Clientes internos</p></td>
<td><p>VIP de balanceador de carga de hardware Diretor</p></td>
<td><p>O Diretor fornece serviços Web para clientes internos e externos.</p></td>
</tr>
<tr class="even">
<td><p>SIP/MTLS/TCP 5061</p></td>
<td><p>Interface interna do Servidor de Borda</p></td>
<td><p>Diretor</p></td>
<td><p>Comunicação SIP do Servidor de borda com o Diretor, bem como o Servidores Front-End.</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50001</p></td>
<td><p>Qualquer um</p></td>
<td><p>Diretor</p></td>
<td><p>Comandos e coleção de logs do controlador (ClsController.exe) ou do agente (ClsAgent.exe) de Serviço de Log Centralizado</p></td>
</tr>
<tr class="even">
<td><p>MTLS/TCP/50002</p></td>
<td><p>Qualquer um</p></td>
<td><p>Diretor</p></td>
<td><p>Comandos e coleção de logs do controlador (ClsController.exe) ou do agente (ClsAgent.exe) de Serviço de Log Centralizado</p></td>
</tr>
<tr class="odd">
<td><p>MTLS/TCP/50003</p></td>
<td><p>Qualquer um</p></td>
<td><p>Diretor</p></td>
<td><p>Comandos e coleção de logs do controlador (ClsController.exe) ou do agente (ClsAgent.exe) de Serviço de Log Centralizado</p></td>
</tr>
</tbody>
</table>

