---
title: 'Lync Server 2013: Resumo do certificado - Diretor único'
TOCTitle: Resumo do certificado - Diretor único
ms:assetid: 1b769a76-cbf3-46e9-a955-f6cde5faff93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204720(v=OCS.15)
ms:contentKeyID: 49306046
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo do certificado - Diretor único no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Requisitos de certificado para um único Diretor consiste de um certificado padrão que possui um nome de assunto e nomes de assunto alternativos para serviços que o Diretor pode receber. Além disso, há um certificado OAuth Token para fins de autenticação servidor para servidor.

### Certificados do diretor

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente</th>
<th>Nome da entidade (SN)</th>
<th>Nomes de Entidade Alternativos (SAN)</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Padrão</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>dir01.contoso.net</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>lyncdiscoverinternal.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(Opcional) *.contoso.com</p></td>
<td><p>Certificados Diretor podem ser solicitados de uma Autoridade de Certificação (CA) interna ou uma CA pública.</p>
<p>O Diretor responde a solicitações do proxy reverso no perímetro ou do Servidor de Borda. Clientes internos não usarão o Diretor.</p>
<p>Ou, uma entrada curinga para os URLs simples</p></td>
</tr>
<tr class="even">
<td><p>OAuthTokenIssuer</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>Nenhuma entrada</p></td>
<td>

> [!IMPORTANT]  
> Observe que o comprimento mínimo de chave é 1024, mas você pode receber um aviso de que o comprimento de chave mínimo recomendado é 2048 bits.

<p>O certificado OAuthTokenIssuer é um certificado para o fim único de autenticar servidores em um ambiente de grande escala e pode ser solicitado de um CA interno ou público. O certificado é exigido.</p>
<p></p></td>
</tr>
</tbody>
</table>

