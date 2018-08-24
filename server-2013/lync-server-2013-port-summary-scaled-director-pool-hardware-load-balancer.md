---
title: "Lync Server 2013: Res. de porta - Pool de Dir. em esc., balanc. de carga de hardware"
TOCTitle: Resumo de porta - Pool de Diretor em escala, balanceador de carga de hardware
ms:assetid: 6ae2f4ac-5b64-4e45-8253-133308f5812d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204983(v=OCS.15)
ms:contentKeyID: 49307007
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de porta - Pool de Diretor em escala, balanceador de carga de hardware no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos de porta de firewall de um Pool de diretores consistem nas portas que são usadas para estabelecer a comunicação com o Diretor da interface interna do Servidor de Borda ou da interface interna do proxy reverso. O Microsoft Lync Server 2013 por padrão espera que as portas HTTP/TCP 8080 e HTTPS/TCP 4443 estejam abertas do proxy reverso para o Diretor, bem como o Pool de Front-Ends e o Servidor Front-End. Além disso, deve haver comunicação SIP da interface interna do Servidor de Borda com o Diretor e com o Pool de Front-Ends e o Servidor Front-End. O protocolo SIP usa SIP/MTLS/TCP 5061 do Servidor de Borda para o Pool de Front-Ends e o Servidor Front-End. Uma regra que permita a comunicação SIP/MTLS/TCP 5061 do Diretor, do Pool de Front-Ends e do Servidor Front-End com a interface interna do Servidor de Borda também deve ser criada.

### Portas e protocolos do Diretor para definições de firewall

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
<td><p>Recebida inicialmente pelo lado externo do proxy reverso, a comunicação é enviada para o VIP do HLB do Diretor e os serviços Web do Servidores Front-End</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP 4443</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>VIP de balanceador de carga de hardware Diretor</p></td>
<td><p>Recebida inicialmente pelo lado externo do proxy reverso, a comunicação é enviada para o VIP do HLB do Diretor e os serviços Web do Servidores Front-End</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP 444</p></td>
<td><p>Diretor</p></td>
<td><p>Servidor Front-End ou Pool de Front-Ends</p></td>
<td><p>Comunicação entre servidores entre o VIP do HLB do Diretor e os Servidores Front-End</p></td>
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
<td><p>VIP de balanceador de carga de hardware Diretor</p></td>
<td><p>Comunicação SIP do Servidor de Borda para o Diretor e o Servidores Front-End.</p></td>
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

