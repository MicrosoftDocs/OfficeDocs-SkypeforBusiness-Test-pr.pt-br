---
title: Requisitos de DNS para servidores de chat persistente
TOCTitle: Requisitos de DNS para servidores de chat persistente
ms:assetid: f7531374-d7ed-4b63-ae81-02294cb4496a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205391(v=OCS.15)
ms:contentKeyID: 49308640
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de DNS para servidores de chat persistente

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve os registros do Sistema de Nomes de Domínio (DNS) necessários para implantar o Servidores de Chat Persistente.

## Registros DNS para servidores de chat persistente

A tabela a seguir especifica os requisitos de DNS para a implantação do Servidor de Chat Persistente.

### Requisitos de DNS para um servidor de chat persistente

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
<td><p>Um Servidor de Chat Persistente</p></td>
<td><p>Um registro A interno que resolve o nome de domínio totalmente qualificado (FQDN) do servidor ao seu endereço IP.</p></td>
</tr>
<tr class="even">
<td><p>Pool de Chat Persistente</p></td>
<td><p>Um registro A interno que resolve o nome de domínio totalmente qualificado (FQDN) dos servidores aos seus endereços IP.</p>
<p><strong>Exemplo</strong></p>
<p>PersistentChatServer01.contoso.com     10.10.10.1</p>
<p>PersistentChatServer02.contoso.com     10.10.10.2</p>
<p>Um registro A interno que resolve o nome de domínio totalmente qualificado (FQDN) dos servidores aos seus endereços IP.</p>
<p><strong>Exemplo</strong></p>
<p>PersistentChatPool.contoso.com    10.10.10.1</p>
<p>PersistentChatPool.contoso.com    10.10.10.2</p></td>
</tr>
</tbody>
</table>

