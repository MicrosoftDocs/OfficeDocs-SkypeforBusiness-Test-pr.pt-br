---
title: "Res. do Certificado – conectividade para redes públicas de mens. instantâneas"
TOCTitle: "Res. do Certificado – conectividade para redes públicas de mens. instantâneas"
ms:assetid: 2b3687ee-50c2-4c1c-880e-8dcf8bd4f309
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618370(v=OCS.15)
ms:contentKeyID: 49306218
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo do Certificado – conectividade para redes públicas de mensagens instantâneas

 

_**Tópico modificado em:** 2015-03-09_

Para configurar certificados para conectividade de Mensagem Instantânea pública, você deve primeiro observar que não há nada diferente de outros tipos de federação SIP ou mesmo certificados padrões do Servidor de Borda, exceto que o America Online (AOL) exige uma configuração de certificado exclusiva. Além do uso de chave avançada do servidor normal (EKU), o America Online exige o certificado ou certificados (no caso de um Pool de borda) para também conter o cliente EKU. O cliente EKU é uma adição ao certificado e faz parte do certificado público externo atribuído ao seu Servidor de Borda.

## Resumo do certificado – Conectividade de mensagem instantânea pública


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
<th>Nome do assunto</th>
<th>Nomes alternativos do assunto (SAN)/Pedido</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Borda de Acesso/Externo</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>O certificado deve ser um CA público e deve ter um EKU do servidor e um EKU do cliente se a conectividade de IM pública com a AOL for implantada. O certificado é atribuído para as interfaces externas do Servidor de Borda para:</p>
<ul>
<li><p>Serviço de Borda de Acesso</p></li>
<li><p>Serviço de Borda de Webconferência</p></li>
<li><p>Serviço de Borda A/V</p></li>
</ul>
<p>Observe que os SANs são adicionados automaticamente ao certificado com base nas suas definições no Construtor de Topologia. É possível adicionar entradas SAN conforme necessário para domínios SIP adicionais e outras enteadas que precisam de suporte. O nome do assunto é replicado no SAN e deve estar presente para a operação correta.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)

