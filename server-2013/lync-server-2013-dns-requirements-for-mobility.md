---
title: Requisitos DNS para mobilidade
TOCTitle: Requisitos DNS para mobilidade
ms:assetid: df6962bc-2a16-440e-a333-022ebd14f957
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690040(v=OCS.15)
ms:contentKeyID: 49308346
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos DNS para mobilidade

 

_**Tópico modificado em:** 2015-03-09_

Ao implantar o recurso de mobilidade do Lync Server 2013, é possível usar novas URLs disponíveis com o Serviço de Auto-descoberta do Microsoft Lync Server 2013 ou pode usar suas URLs do Web Services existentes. Se você usar suas URLs existentes, os usuários precisam inserir manualmente as URLs nas configurações de dispositivo móvel. Esta opção é geralmente usada para resolver problemas. Ao usar as novas URLs, os clientes móveis podem descobrir automaticamente os recursos do Lync Server 2013. Ao suportar a descoberta automática, é necessário adicionar registros DNS. Esta seção descreve os registros DNS necessários para descoberta automática.

Para suportar a descoberta automática, é necessário criar os seguintes registros DNS para cada domínio SIP:

  - Um registro DNS interno para suportar usuários móveis que se conectam a partir da rede de sua organização

  - Um registro DNS externo ou público para suportar usuários móveis que se conectam a partir da Internet

A URL de descoberta automática interna não deve ser endereçável de fora de sua rede. A URL de descoberta automática externa não deve ser endereçável de dentro de sua rede. No entanto, se não for possível atender a esse requisito para a URL externa, a funcionalidade de cliente móvel não deverá ser afetada.

Os registros DNS podem ser registros CNAME ou registros A (host).

**Registros DNS internos**

Você precisa criar um dos seguintes registros DNS internos:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de registro</th>
<th>Nome do host ou definição SRV</th>
<th>Resolve para</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscoverinternal.<em>&lt;sipdomain&gt;</em></p></td>
<td><p>FQDN (nome de domínio totalmente qualificado) dos Serviços Web internos para seu Pool de diretores, se você tiver um, ou para seu Pool de Front-Ends se você não tiver um Diretor</p></td>
</tr>
<tr class="even">
<td><p>A (host)</p></td>
<td><p>lyncdiscoverinternal.<em>&lt;sipdomain&gt;</em></p></td>
<td><p>Endereço IP (VIP [IP virtual], se você usar um balanceador de carga) dos Serviços Web internos de seu Pool de diretores, se você tiver um, ou de seu Pool de Front-Ends se você não tiver um Diretor</p></td>
</tr>
</tbody>
</table>


**Registros DNS externos**

Você precisa criar um dos seguintes registros DNS externos:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de registro</th>
<th>Nome do host</th>
<th>Resolve para</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CNAME</p></td>
<td><p>lyncdiscover. <em>&lt;sipdomain&gt;</em></p></td>
<td><p>FQDN dos Serviços Web externos para seu Pool de diretores, se você tiver um, ou para seu Pool de Front-Ends se você não tiver um Diretor</p></td>
</tr>
<tr class="even">
<td><p>A (host)</p></td>
<td><p>lyncdiscover. <em>&lt;sipdomain&gt;</em></p></td>
<td><p>Endereço IP externo ou público (endereço VIP se você usar um balanceador de carga) do proxy reverso</p></td>
</tr>
<tr class="odd">
<td><p>SRV</p></td>
<td><p>_sipfederationtls._tcp. <em>&lt;sipdomain&gt;</em></p>
<p>Resolve para hospedar o registro (A ou AAAA) do Serviço de Borda de Acesso</p></td>
<td><p>Para suportar o Serviços de Notificação por Push e Serviços de Notificação por Push da Apple, você cria um registro SRV para cada domínio SIP que possui clientes do Microsoft Lync Mobile.</p>
<div class="alert">
> [!IMPORTANT]  
> Este requisito é aplicável somente aos clientes do Microsoft Lync Mobile em dispositivos móveis baseados em Apple ou Microsoft. Dispositivos Android e Nokia Symbian não usam notificação de push.
</div></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Lyncdiscover, também conhecido como descoberta automática; o tráfego passa pelo proxy reverso. O registro SRV aponta para um registro que é resolvido pelo Serviço de Borda de Acesso.
