---
title: 'Lync Server 2013: Resumo de certificado - Proxy reverso'
TOCTitle: Resumo de certificado - Proxy reverso
ms:assetid: f2b9a53f-aead-413d-81e9-4a294a010fbb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205381(v=OCS.15)
ms:contentKeyID: 49308591
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de certificado - Proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Requisitos de certificado para proxy reverso são muito mais simples que para os Servidores de Borda. O fluxograma fornecido apresenta os requisitos necessários. A tabela ao lado apresenta o nome de entidade típico do certificado e nomes de entidade alternativos relacionados aos cenários analisados nas discussões da Servidor de Borda. Para obter mais informações sobre os cenários da Servidor de Borda, consulte [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

**Fluxograma de certificados para proxy reverso**

![Fluxograma de Certificados para Servidor de Borda](images/JJ205381.026045d7-1b4b-4651-b32f-2d43a7161198(OCS.15).jpg "Fluxograma de Certificados para Servidor de Borda")

### Proxy Reverso: Interface Externa

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
<th>Nome da entidade</th>
<th>Ordem/Nome de entidade alternativo (SAN)</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Proxy reverso</p></td>
<td><p>webext.contoso.com</p></td>
<td><p>webext.contoso.com</p>
<p>webdirext.contoso.com</p>
<p>dialin.contoso.com</p>
<p>meet.contoso.com</p>
<p>officewebapps01.contoso.com</p>
<p>lyncdiscover.contoso.com</p>
<p>(Opcional): *.contoso.com</p></td>
<td><p>O certificado deve ser emitido por uma AC (autoridade de certificação) pública e com o EKU (uso avançado de chave) do servidor. Os serviços abrangem o Serviço de Catálogo de Endereços, os Office Web Apps de expansão do grupo de distribuição para conferências e as regras de publicação de dispositivo IP do Lync. O nome alternativo da entidade inclui:</p>
<ul>
<li><p>FQDN de Serviços Web Externos para Servidor Front-End ou Pool de Front-Ends</p></li>
<li><p>FQDN de Serviços Web Externos para Diretor ou Pool de diretores</p></li>
<li><p>Conferência Discada</p></li>
<li><p>Regra de publicação da reunião online</p></li>
<li><p>Office Web Apps para conferências</p></li>
<li><p>Lyncdiscover (Descoberta automática)</p></li>
</ul>
<p>O curinga opcional substitui o SAN discado e reunião</p></td>
</tr>
</tbody>
</table>

