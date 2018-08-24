---
title: 'Lync Server 2013: Resumo de porta - Proxy reverso'
TOCTitle: Resumo de porta - Proxy reverso
ms:assetid: 59b9ac3c-3e6f-4776-b366-174f0dd1f2eb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204932(v=OCS.15)
ms:contentKeyID: 49306809
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de porta - Proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O proxy reverso tem requisitos mínimos de firewall e porta/protocolo.

  - Os requisitos do firewall externo são HTTPS/TCP/443 e HTTP/TCP/80 opcional. HTTPS é usado para comunicações seguras SSL e TLS por meio do proxy reverso. HTTP é usado se você escolher permitir acesso ao serviço de Descoberta Automática quando estiver modificando os certificados pode ser difícil ou ter custos não justificados.

  - Os clientes esperam entrar em contato com o Servidor Office Web Apps por HTTPS. O Servidor Office Web Apps espera se comunicar a partir dos clientes internos por HTTPS/TCP/443. A configuração recomendada é autorizar HTTPS/TCP/443 no proxy reverso do Servidor Office Web Apps.

  - A porta 8080 é usada para encaminhar tráfego da interface interna do proxy reverso para o VIP (IP virtual) do Servidor Front-End, do Pool de Front-Ends ou o VIP opcional do Diretor ou do Pool de diretores. A porta TCP 8080 é necessária para dispositivos móveis que executam o Lync para localizar o serviço Descoberta Automática em situações em que não se deseja modificar o certificado de regra de publicação de serviço Web externo (por exemplo, se houver um número grande de domínios SIP). Se você optar por adquirir novos certificados com as entradas de SAN necessárias, a porta TCP 8080 não será necessária e será opcional.

  - A porta 4443 é usada para tráfego da interface interna do proxy reverso para o VIP do Servidor Front-End, do Pool de Front-Ends ou o VIP opcional do Diretor ou do Pool de diretores
    
    ![Proxy Reverso e Serviços Web Externos](images/JJ204932.13142405-d5c9-45b7-a8b7-a8c89f09c97c(OCS.15).jpg "Proxy Reverso e Serviços Web Externos")  
    

    > [!CAUTION]  
    > Não confunda o tráfego da porta 4443 por TCP do proxy reverso para a implantação interna com o tráfego da porta 4443 por TCP do Standard Edition Server ou do Pool de Front-Ends que gerencia a função do Repositório de Gerenciamento Central.



## Detalhes de protocolo e porta

### Detalhes de firewall do servidor de proxy reverso: Interface externa

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/80</p></td>
<td><p>Qualquer um</p></td>
<td><p>Ouvinte do proxy reverso</p></td>
<td><p>(Opcional) Redirecionamento para HTTPS se o usuário inserir http:// <em>&lt;publishedSiteFQDN&gt;</em> .</p>
<p>Também é requerido se estiver usando o Office Web Apps para conferência e o serviço de Descoberta Automática para dispositivos móveis executando o Lync em situações nas quais a organização não deseja modificar o certificado de regra de publicação de serviço Web externo.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/443</p></td>
<td><p>Qualquer um</p></td>
<td><p>Ouvinte do proxy reverso</p></td>
<td><p>Downloads do Catálogo de Endereços, serviço de consulta à Web do Catálogo de Endereços, Descoberta Automática, atualizações de cliente, conteúdo da reunião, atualizações de dispositivo, expansão de grupo, Office Web Apps para conferência, conferência de discagem e reuniões.</p></td>
</tr>
</tbody>
</table>


### Detalhes de firewall do servidor de proxy reverso: Interface interna

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo/TCP ou UDP/Porta</th>
<th>Endereço IP de Origem</th>
<th>Endereço IP de Destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>HTTP/TCP/8080</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Servidor Front-End, Pool de Front-Ends, Diretor, Pool de diretores</p></td>
<td><p>Necessário se o serviço Descoberta Automática estiver sendo usado para dispositivos móveis que executam o Lync em situações nas quais a organização não deseja modificar o certificado de regra de publicação de serviço Web externo.</p>
<p>O tráfego enviado para a porta 80 na interface externa do proxy reverso é redirecionado para um pool na porta 8080 a partir da interface interna do proxy reverso, assim os serviços Web do pool podem diferenciá-lo do tráfego Web interno.</p></td>
</tr>
<tr class="even">
<td><p>HTTPS/TCP/4443</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Servidor Front-End, Pool de Front-Ends, Diretor, Pool de diretores</p></td>
<td><p>O tráfego enviado para a porta 443 na interface externa do proxy reverso é redirecionado para um pool na porta 4443 a partir da interface interna do proxy reverso, assim os serviços Web do pool podem diferenciá-lo do tráfego Web interno.</p></td>
</tr>
<tr class="odd">
<td><p>HTTPS/TCP/443</p></td>
<td><p>Interface interna do proxy reverso</p></td>
<td><p>Office Web Apps para conferências</p></td>
<td><p></p></td>
</tr>
</tbody>
</table>

