---
title: Resumo de porta - SIP, federação XMPP e mensagens instantâneas públicas
TOCTitle: Resumo de porta - SIP, federação XMPP e mensagens instantâneas públicas
ms:assetid: ab05bdd6-e9b0-4b1b-9dd9-29ab88e8befe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618373(v=OCS.15)
ms:contentKeyID: 49307757
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de porta - SIP, federação XMPP e mensagens instantâneas públicas

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos de porta, protocolo e firewall para federação com Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server são semelhantes aos do Servidor de Borda implantado. Os clientes iniciam a comunicação com o Serviço de Borda de Acesso por TLS/SIP/TCP 443. No entanto os parceiros federados iniciarão as comunicações com o Serviço de Borda de Acesso por MTLS/SIP/TCP 5061.

Para configurar seu firewall para as portas e protocolos necessários para suportar a conectividade de mensagens instantâneas públicas, primeiro observe que o SIP/MTLS/TCP 5061 é bidirecional para a conta para a capacidade dos contatos do provedor de IMs públicas contatar clientes do Lync ou para o Lync contatar os contatos de IMs públicas.

O Windows Live Messenger pode participar das comunicações de áudio/vídeo com os clientes do Lync. Essas contas para a configuração de porta de firewall e protocolo muito similares que você geralmente teria no firewall para suportar os clientes do Lync como usuários externos.

> [!IMPORTANT]  
> Mais do que nunca, o Lync é uma ferramenta poderosa de conexão entre organizações e pessoas de todo o mundo. A federação com o Windows Live Messenger não exige licenças adicionais de usuário ou dispositivo além da CAL (licença de acesso para cliente) padrão do Lync. A federação com o Skype será adicionada a essa lista, permitindo que os usuários do Lync alcancem centenas de milhões de pessoas por meio de IM (mensagens instantâneas) e voz.<br />A federação com os contatos do cliente do Messenger terminará oficialmente em 15 de março de 2013, exceto para a China continental. O Skype se tornará o cliente de federação dos usuários federados que usavam o Messenger anteriormente.

As portas e os protocolos definidos para o proxy XMPP implantado no Servidor de Borda permitem comunicações do parceiro XMPP federado com o Servidor de Borda e também permitem a comunicação do seu Servidor de Borda com o parceiro XMPP federado. Uma regra também é definida no firewall interno do Servidor Front-End ou Pool de Front-Ends para o Servidor de Borda ou o Pool de borda.

## Resumo de firewall - Federação SIP


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
<td><p>Acessar/SIP(MTLS)/TCP/5061</p></td>
<td><p>Endereço IP público de Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Para conectividade federada e de IM público usando SIP</p></td>
</tr>
</tbody>
</table>


## Resumo de certificado – Conectividade de Mensagens Instantâneas Públicas


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
<th>Endereço IP fonte</th>
<th>Endereço IP de destino</th>
<th>Observações</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Parceiros de conectividade pública de IM</p></td>
<td><p>Interface de acesso do Servidor de Borda</p></td>
<td><p>Para conectividade a IM público e federado com SIP.</p></td>
</tr>
<tr class="even">
<td><p>Acesso/SIP(MTLS)/TCP/5061</p></td>
<td><p>Interface de acesso do Servidor de Borda</p></td>
<td><p>Parceiros de conectividade pública de IM</p></td>
<td><p>Para conectividade a IM público e federado com SIP.</p></td>
</tr>
<tr class="odd">
<td><p>Acesso/SIP(TLS)/TCP/443</p></td>
<td><p>Clientes</p></td>
<td><p>Interface de acesso do Servidor de Borda</p></td>
<td><p>Tráfego SIP do cliente ao servidor para o acesso do usuário externo.</p></td>
</tr>
<tr class="even">
<td><p>A/V/RTP/TCP/50.000-59.999</p></td>
<td><p>Interface de acesso do Servidor de Borda</p></td>
<td><p>Clientes do Live Messenger</p></td>
<td><p>Usado para sessões A/V com o Windows Live Messenger se a conectividade pública de IM estiver configurada.</p></td>
</tr>
<tr class="odd">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Interface de acesso do Servidor de Borda</p></td>
<td><p>Clientes do Live Messenger</p></td>
<td><p>Obrigatório para a conectividade de IM público com o Windows Live Messenger.</p></td>
</tr>
<tr class="even">
<td><p>A/V/STUN,MSTURN/UDP/3478</p></td>
<td><p>Clientes do Live Messenger</p></td>
<td><p>Interface de acesso do Servidor de Borda</p></td>
<td><p>Obrigatório para a conectividade de IM público com o Windows Live Messenger.</p></td>
</tr>
</tbody>
</table>


## Resumo de Firewall - Mensagens Extensíveis e Protocolo de Presença (XMPP)


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
<th>Fonte (endereço IP)</th>
<th>Destino (endereço IP)</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Qualquer um</p></td>
<td><p>endereço IP da interface do Serviço de Borda de Acesso</p></td>
<td><p>Porta padrão de comunicação entre servidores para XMPP. Permite comunicação do proxy XMPP do Servidor de Borda para parceiros XMPP federados</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Endereço IP da interface do Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Porta padrão de comunicação entre servidores para XMPP. Permite comunicação do proxy XMPP do Servidor de Borda para parceiros XMPP federados</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/23456</p></td>
<td><p>Qualquer um</p></td>
<td><p>IP Interno da Interface do Servidor de Borda</p></td>
<td><p>Tráfego XMPP interno do gateway XMPP na Servidor Front-End ou no Pool de Front-Ends para o Servidor de Borda</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)  

#### Outros Recursos

[Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

