---
title: 'Lync Server 2013: Requisitos de DNS para servidor Standard Edition'
TOCTitle: Requisitos de DNS para servidor Standard Edition
ms:assetid: 5d1daf54-6e60-4ce0-9254-7d57a0835fa4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204936(v=OCS.15)
ms:contentKeyID: 49306847
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de DNS para servidor Standard Edition no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve os registros DNS necessários para a implantação de servidores Standard Edition.

## Registros DNS para servidores Standard Edition

A tabela a seguir especifica os requisitos de DNS para a implantação do servidor Lync Server 2013 Standard Edition.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cenário da implantação</th>
<th>Requisitos de DNS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor Standard Edition</p></td>
<td><p>Um registro A interno que resolve o nome de domínio totalmente qualificado (FQDN) do servidor ao seu endereço IP.</p></td>
</tr>
<tr class="even">
<td><p>Entrada automática do cliente</p></td>
<td><p>Para cada domínio SIP com suporte, um registro SRV para _sipinternaltls._tcp.&lt;domain&gt; pela porta 5061 que mapeia o FQDN do servidor Standard Edition que autentica e redireciona as solicitações de cliente para entrada. Para obter detalhes, consulte <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">Requisitos DNS para conexão automática de clientes no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Descoberta do Serviço Web de Atualização de Dispositivo por dispositivos UC (comunicações unificadas)</p></td>
<td><p>Um registro A interno com o nome ucupdates-r2.&lt;SIP domain&gt; que seja resolvido como o endereço IP do servidor Standard Edition que hospeda o serviço Web de Atualização de Dispositivo. Na situação em que um dispositivo UC está ligado, mas o usuário nunca fez logon no dispositivo, o registro A permite que o dispositivo descubra o servidor que hospeda o serviço Web de Atualização de Dispositivo e obtenha atualizações. Caso contrário, os dispositivos obtêm as informações de servidor por meio do provisionamento em banda na primeira vez que um usuário faz logon. Para detalhes, consulte <a href="lync-server-2013-device-update-web-service.md">Serviço Web de Atualização de Dispositivo no Lync Server 2013</a> na documentação de Operações.</p></td>
</tr>
<tr class="even">
<td><p>Um proxy reverso para suportar o tráfego HTTP</p></td>
<td><p>Um registro A externo que resolve o FQDN da web farm externa para o endereço IP externo do proxy reverso. Dispositivos clientes e UC usam esse registro para se conectar ao proxy reverso. Para obter detalhes, consulte <a href="lync-server-2013-determine-dns-requirements.md">Determinar requisitios de DNS para Lync Server 2013</a> na documentação Planejamento.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Requisitos DNS para conexão automática de clientes no Lync Server 2013](lync-server-2013-dns-requirements-for-automatic-client-sign-in.md)  
[Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  

#### Outros Recursos

[Serviço Web de Atualização de Dispositivo no Lync Server 2013](lync-server-2013-device-update-web-service.md)

