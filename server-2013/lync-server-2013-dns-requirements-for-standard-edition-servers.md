---
title: Requisitos DNS para servidores do Standard Edition
TOCTitle: Requisitos DNS para servidores do Standard Edition
ms:assetid: 3d6bbe65-e7ce-491b-a0bd-d2f7197f240d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425900(v=OCS.15)
ms:contentKeyID: 49306461
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos DNS para servidores do Standard Edition

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve os registros DNS necessários para a implantação de servidores Standard Edition.

## Registros DNS para servidores Standard Edition

A tabela a seguir especifica os requisitos de DNS para a implantação do servidor Lync Server 2013 Standard Edition.

### Requisitos de DNS para um servidor Standard Edition

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cenário da implantação</th>
<th>Requisito de DNS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor Standard Edition</p></td>
<td><p>Um registro A interno que resolva o FQDN (nome de domínio totalmente qualificado) do servidor como o respectivo endereço IP.</p></td>
</tr>
<tr class="even">
<td><p>Entrada automática do cliente</p></td>
<td><p>Para cada domínio SIP aceito, um registro SRV para _sipinternaltls._tcp.<em>&lt;domínio&gt;</em> na porta 5061 que mapeie para o FQDN do servidor Standard Edition responsável por autenticar e redirecionar as solicitações de entrada dos clientes. Para obter detalhes, consulte <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">Requisitos DNS para conexão automática de clientes no Lync Server 2013</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Descoberta do serviço Web de Atualização de Dispositivo por dispositivos de UC (comunicações unificadas)</p></td>
<td><p>Um registro A interno com o nome ucupdates-r2.<em>&lt;domínio SIP&gt;</em> que se resolva como o endereço IP do servidor Standard Edition que hospeda o serviço Web de Atualização do Dispositivo. Na situação em que um dispositivo de UC esteja ativado, mas um usuário nunca tenha feito logon no dispositivo, o registro A permite que o dispositivo descubra o servidor que hospeda o serviço Web de Atualização de Dispositivo e obtenha atualizações. Caso contrário, os dispositivos obtêm as informações do servidor através do provisionamento em banda na primeira vez que um usuário faz logon.</p></td>
</tr>
<tr class="even">
<td><p>Um proxy reverso para dar suporte ao tráfego HTTP</p></td>
<td><p>Um registro A externo que resolva o FQDN da Web farm externa como o endereço IP externo do proxy reverso. Os clientes e os dispositivos de UC usam esse registro para se conectar ao proxy reverso. Para obter detalhes, consulte <a href="lync-server-2013-determine-dns-requirements.md">Determinar requisitios de DNS para Lync Server 2013</a> na documentação Planejamento.</p></td>
</tr>
</tbody>
</table>

