---
title: "Res. de Porta - Mens. Extensíveis e Feder. de Protocolo de Presença (XMPP)"
TOCTitle: "Res. de Porta - Mens. Extensíveis e Feder. de Protocolo de Presença (XMPP)"
ms:assetid: 62e98fab-7add-4983-a3fa-dbe74e1c3849
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618371(v=OCS.15)
ms:contentKeyID: 49306908
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de Porta - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)

 

_**Tópico modificado em:** 2015-03-09_

As portas e os protocolos definidos para o proxy XMPP implantado no Servidor de Borda permitem comunicações do parceiro XMPP federado com o Servidor de Borda e também permitem a comunicação do seu Servidor de Borda com o parceiro XMPP federado. Uma regra também é definida no firewall interno do Servidor Front-End ou do Pool de Front-Ends para o Servidor de Borda ou o Pool de borda.

## Resumo do firewall para o protocolo XMPP


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
<th>Origem (endereço IP)</th>
<th>Destino (endereço IP)</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Qualquer um</p></td>
<td><p>Endereço IP da interface do Serviço de Borda de Acesso</p></td>
<td><p>Porta de comunicação servidor a servidor padrão para XMPP. Permite a comunicação com o proxy XMPP do Servidor de Borda de parceiros XMPP federados</p></td>
</tr>
<tr class="even">
<td><p>XMPP/TCP/5269</p></td>
<td><p>Endereço IP da interface do Serviço de Borda de Acesso</p></td>
<td><p>Qualquer um</p></td>
<td><p>Porta de comunicação servidor a servidor padrão para XMPP. Permite a comunicação do proxy XMPP do Servidor de Borda com parceiros XMPP federados</p></td>
</tr>
<tr class="odd">
<td><p>XMPP/MTLS/23456</p></td>
<td><p>Qualquer um</p></td>
<td><p>IP da interface interna do Servidor de Borda</p></td>
<td><p>Tráfego XMPP interno do gateway XMPP no Servidor Front-End ou no Pool de Front-Ends com o Servidor de Borda</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Tarefas

[Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### Outros Recursos

[Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

