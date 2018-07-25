---
title: 'Lync Server 2013: Resumo de certificado - pool Certificate summary - pool de diretores em escala, balanceador de carga de hardware'
TOCTitle: Resumo de certificado - pool Certificate summary - pool de diretores em escala, balanceador de carga de hardware
ms:assetid: 45940add-8027-418d-b79a-9033b494762f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204846(v=OCS.15)
ms:contentKeyID: 49306581
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de certificado - pool Certificate summary - pool de diretores em escala, balanceador de carga de hardware no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos de certificado para um Diretor com balanceador de carga de hardware utilizará o certificado padrão que possui o nome de entidade e nomes alternativos de entidade para serviços o qual o Pool de diretores pode receber. Um certificado é solicitado para cada Diretor no pool. Adicionalmente, há um certificado OAuth Token para propósitos de autenticação servidor para servidor que é instalado em cada servidor.

### Certificados para um Diretor escalado utilizando um balanceador de carga de hardware

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
<td><p>dirpool01.contoso.net</p></td>
<td><p>dirpool01.contoso.net</p>
<p>dir01.contoso.net</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>lyncdiscoverinternal.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(Opcional) *.contoso.com</p></td>
<td><p>Certificados Diretor podem ser solicitados de uma Autoridade de Certificação (CA) interna ou uma CA pública.</p>
<p>O Diretor responde a solicitações do proxy reverso no perímetro ou do Servidor de Borda.</p>
<p>Ou, uma entrada curinga para os URLs simples</p></td>
</tr>
<tr class="even">
<td><p>OAuthTokenIssuer</p></td>
<td><p>dir01.contoso.net</p></td>
<td><p>Nenhuma entrada</p></td>
<td>

> [!IMPORTANT]  
> Observe que o comprimento mínimo de chave é 1024, mas você pode receber um aviso de que o comprimento de chave mínimo recomendado é 2048 bits.

<p>O certificado OAuthTokenIssuer é um certificado para o fim único de autenticar servidores em um ambiente de grande escala e pode ser solicitado de um CA interno ou público. O certificado é exigido.</p></td>
</tr>
</tbody>
</table>

