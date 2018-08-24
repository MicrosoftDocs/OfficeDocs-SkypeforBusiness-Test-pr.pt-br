---
title: Resumo do Porta – conectividade para redes públicas de mensagens instantâneas
TOCTitle: Resumo do Porta – conectividade para redes públicas de mensagens instantâneas
ms:assetid: f46756ec-1401-4ca2-a4a4-5cd28bcfdc7f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618376(v=OCS.15)
ms:contentKeyID: 49308597
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo do Porta – conectividade para redes públicas de mensagens instantâneas

 

_**Tópico modificado em:** 2015-03-09_

Para configurar seu firewall para as portas e os protocolos necessários a fim de oferecer suporte à conectividade do sistema de mensagens instantâneas públicas, observe primeiro que SIP/MTLS/TCP 5061 é bidirecional para permitir que os contatos no provedor de IM (mensagens instantâneas) público entrem em contato com clientes do Lync ou para que o Lync entre em contato com os contatos de IM público

O Windows Live Messenger pode participar de comunicações por áudio/vídeo com clientes do Lync. Isso permite que cada configuração de protocolo e porta de firewall geralmente presentes no firewall ofereça suporte aos clientes do Lync como usuários externos.

> [!IMPORTANT]  
> Mais do que nunca, o Lync é uma ferramenta poderosa de conexão entre organizações e pessoas de todo o mundo. A federação com o Windows Live Messenger não exige licenças adicionais de usuário ou dispositivo além da CAL (licença de acesso para cliente) padrão do Lync. A federação com o Skype será adicionada a essa lista, permitindo que os usuários do Lync alcancem centenas de milhões de pessoas por meio de IM (mensagens instantâneas) e voz.<br />A federação com os contatos do cliente do Messenger terminará oficialmente em 15 de março de 2013, exceto para a China continental. O Skype se tornará o cliente de federação dos usuários federados que usavam o Messenger anteriormente.

## Resumo do firewall – Conectividade pública de mensagens instantâneas


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
<th>Endereço IP de origem</th>
<th>Endereço IP de destino</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Parceiros de conectividade pública de IM</p></td>
<td><p>Interface de acesso Servidor de Borda</p></td>
<td><p>Para conectividade a IM público e federando com SIP.</p></td>
</tr>
<tr class="even">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Interface de acesso Servidor de Borda</p></td>
<td><p>Parceiros de conectividade pública de IM</p></td>
<td><p>Para conectividade a IM público e federado com SIP.</p></td>
</tr>
<tr class="odd">
<td><p>Acesso/SIP(TLS)/TCP/443</p></td>
<td><p>Clientes</p></td>
<td><p>Interface de acesso Servidor de Borda</p></td>
<td><p>Tráfego SIP do cliente ao servidor para o acesso do usuário externo.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50,000-59,999</p></td>
<td><p>Interface de acesso Servidor de Borda</p></td>
<td><p>Clientes Live Messenger</p></td>
<td><p>Usado para sessões A/V com o Windows Live Messenger se a conectividade pública de IM estiver configurada.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Interface de acesso Servidor de Borda</p></td>
<td><p>Clientes Live Messenger</p></td>
<td><p>Obrigatório para a conectividade de IM público com o Windows Live Messenger.</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Clientes Live Messenger</p></td>
<td><p>Interface de acesso Servidor de Borda</p></td>
<td><p>Obrigatório para a conectividade de IM público com o Windows Live Messenger.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

