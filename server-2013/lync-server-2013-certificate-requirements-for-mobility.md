---
title: 'Lync Server 2013: Requisitos de certificado para mobilidade'
TOCTitle: Requisitos de certificado para mobilidade
ms:assetid: bb0e97af-cf60-4271-a0ab-654429d884ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690044(v=OCS.15)
ms:contentKeyID: 49307944
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de certificado para mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Se você implantar o recurso de mobilidade e suportar a descoberta automática para clientes móveis, será necessário incluir determinadas entradas de nome de entidade alternativo nos certificados a fim de suportar conexões seguras de clientes móveis.

É necessário incluir entradas de nome de entidade alternativo para a descoberta automática nos certificados a seguir:

  - Pool de diretores

  - Pool de Front-Ends

  - Proxy reverso

Esta seção descreve as entradas de nome de entidade alternativo necessárias em seus certificados para descoberta automática.

> [!NOTE]  
> A reemissão de certificados usando uma autoridade de certificação interna é normalmente um processo simples, mas a adição de múltiplas entradas de nome de entidade alternativo aos certificados públicos usados pelo proxy reverso pode ser cara. Se você tiver muitos domínios SIP, tornando a adição de nomes de entidade alternativos muito cara, será possível configurar o proxy reverso para usar HTTP para a solicitação do Serviço de Descoberta Automática, em vez de usar HTTPS (a configuração padrão). Para obter detalhes, consulte <a href="lync-server-2013-technical-requirements-for-mobility.md">Requisitos técnicos para mobilidade no Lync Server 2013</a>.

### Requisitos de certificado do Pool de Diretores

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Entrada de nome de entidade alternativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL interna do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscoverinternal.&lt;sipdomain&gt;</p></td>
</tr>
<tr class="even">
<td><p>URL de Serviço Descoberta Automática Externo</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Como alternativa, é possível usar SAN=*.&lt;sipdomain&gt;

### Requisitos de certificado do pool Front-End

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Entrada de nome de entidade alternativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL interna do serviço de Descoberta Automática</p></td>
<td><p>SAN=lyncdiscoverinternal.&lt;sipdomain&gt;</p></td>
</tr>
<tr class="even">
<td><p>URL de Serviço Descoberta Automática Externo</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Como alternativa, é possível usar SAN=*.&lt;sipdomain&gt;

### Requisitos de certificado de proxy reverso (CA pública)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Entrada de nome de entidade alternativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>URL de Serviço Descoberta Automática Externo</p></td>
<td><p>SAN=lyncdiscover.&lt;sipdomain&gt;</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Atribua esse SAN ao certificado atribuído ao Ouvinte de SSL no proxy reverso.

> [!NOTE]  
> Seu ouvinte de proxy reverso terá nomes alternativos de entidade para seu(s) URL(s) de serviços Web externos (por exemplo, SAN=lyncwebextpool01.contoso.com e dirwebexternal.contoso.com se tiver implantado o Diretor opcional).
