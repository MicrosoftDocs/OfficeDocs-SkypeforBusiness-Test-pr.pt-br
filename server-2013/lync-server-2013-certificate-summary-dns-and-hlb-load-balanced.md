---
title: 'Lync Server 2013: Resumo de certificado - Cargas de DNS e de HLB balanceadas'
TOCTitle: Resumo de certificado - Cargas de DNS e de HLB balanceadas
ms:assetid: 8318a1a4-b423-47b7-95e6-9541adfad391
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205047(v=OCS.15)
ms:contentKeyID: 49307311
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de certificado - Cargas de DNS e de HLB balanceadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

As exigências de certificado para um Diretor com balanceamento de carga de DNS e um balanceador de carga de hardware usarão um certificado padrão que tenha nome da entidade e nomes alternativos da entidade para serviços que o Diretor possa receber. Um certificado é solicitado para cada Diretor no pool. É importante lembrar que o balanceador de carga de hardware equilibra somente o tráfego do proxy reverso. Ademais, há um certificado OAuth Token para fins de autenticação entre servidores instalado em cada servidor.

### Certificador para Diretor

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

<p>O certificado OAuthTokenIssuer é um certificado para o fim único de autenticar servidores em um ambiente de grande escala e pode ser solicitado de um CA interno ou público. O certificado é exigido.</p></td>
</tr>
</tbody>
</table>

