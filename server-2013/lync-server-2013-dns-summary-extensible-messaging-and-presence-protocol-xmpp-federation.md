---
title: Resumo DNS - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)
TOCTitle: Resumo DNS - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)
ms:assetid: 0f720a2a-8ab5-43cc-882a-ab595ed3cec7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618368(v=OCS.15)
ms:contentKeyID: 49305900
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo DNS - Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)

 

_**Tópico modificado em:** 2015-03-09_

Para configurar o protocolo XMPP para sua implantação, crie dois registros de sistema de nome de domínio (DNS) em um servidor DNS externo que resolverá os registros no Serviço de Borda de Acesso do seu Servidor de Borda ou Pool de borda.

## Resumo do DNS para o protocolo XMPP


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Localização/TIPO/Porta</th>
<th>FQDN</th>
<th>Endereço IP/registro de host do FQDN</th>
<th>Mapeia para/Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS Externo/SRV/5269</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>Interface externa do proxy XMPP no Serviço de Borda de Acesso ou Pool de borda. Repetir conforme o necessário para todos os domínios SIP internos com usuários habilitados para o Lync, onde o contato com contatos XMPP é permitido através da configuração da Política de Acesso Externo, via uma política global, política de site onde o usuário está localizado ou política de usuário aplicada ao usuário habilitado para Lync. Um domínio XMPP permitido também deve ser configurado na política de Parceiros Federados XMPP. Consulte os tópicos em <strong>Veja também</strong> para detalhes adicionais</p></td>
</tr>
<tr class="even">
<td><p>DNS Externo/A</p></td>
<td><p>xmpp.contoso.com (for example)</p></td>
<td><p>Endereço IP do Serviço de Borda de Acesso em seu Servidor de Borda ou Pool de borda que estiver hospedando o proxy XMPP</p></td>
<td><p>Aponta para o Serviço de Borda de Acesso ou Pool de borda que hospeda o serviço do proxy XMPP. Normalmente, o registro SRV que você criar apontará para este registro de host (A ou AAAA)</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Tarefas

[Configurando federação de XMPP no Lync Server 2013](lync-server-2013-setting-up-xmpp-federation.md)  

#### Conceitos

[Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)

