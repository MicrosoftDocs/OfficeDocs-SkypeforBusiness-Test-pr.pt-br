---
title: 'Lync Server 2013: Resumo de certificado - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT'
TOCTitle: Resumo de certificado - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT
ms:assetid: 41677dbd-3d07-498a-8591-df255b606647
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425921(v=OCS.15)
ms:contentKeyID: 49306516
ms.date: 12/17/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de certificado - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-15_

O Microsoft Lync Server 2013 usa certificados para autenticar mutuamente outros servidores e para criptografar dados de servidor para servidor e de servidor para cliente. Certificados requerem a correspondência dos nomes dos registros de DNS (sistema de nome de domínio) associados aos servidores e o SN (nome de entidade) e SAN (nome alternativo de entidade) no certificado. Para mapear os servidores, entradas de certificados e registros DNS com êxito, você deve planejar cuidadosamente seus nomes desejados de domínio totalmente qualificados de servidor, do mesmo modo que está registrado no SN e nas entradas de SN e SAN no certificado.

O certificado atribuído às interfaces externas do Servidor de Borda foi solicitado pela autoridade de certificação pública (CA). As CAs públicas obtiveram êxito no fornecimento de certificados para os fins de Comunicações Unificadas que estão listados no artigo a seguir: [http://go.microsoft.com/fwlink/p/?linkid=3052\&kbid=929395](http://go.microsoft.com/fwlink/p/?linkid=3052%26kbid=929395) Ao solicitar o certificado, é possível usar a solicitação do certificado gerada pelo Assistente de Implantação do Lync Server ou criar a solicitação manualmente ou através do processo fornecido pela CA pública. Ao atribuir o certificado, ele foi atribuído à interface do Serviço de Borda de Acesso, Serviço de Borda de Webconferência, e ao serviço de Autenticação de Áudio/Vídeo. O serviço de Autenticação de Áudio/Vídeo não deve ser confundido com o Serviço de Borda A/V que não usa um certificado para criptografar os fluxos de áudio e vídeo. A interface interna do Servidor de Borda pode usar um certificado de uma CA interna (à sua organização) ou um certificado de uma CA pública. O certificado de interface interna usa apenas o SN e não precisa de entradas SAN nem as usa.

> [!NOTE]  
> A tabela a seguir exibe uma segunda entrada SIP (sip.fabrikam.com) na lista de nomes alternativos de entidade como referência. Para cada domínio SIP em sua organização, você precisa adicionar um FQDN correspondente listado na lista de nome alternativo de entidade do certificado.

## Borda consolidada dimensionada, DNS com carga balanceada com endereços IP privados usando NAT


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
<th>Nomes alternativos de entidade (SAN)/Ordem</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Borda consolidada dimensionada (Borda externa)</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>O certificado deve ser de uma AC Pública, e deve possuir o EKU de servidor e de cliente se a conectividade de mensagens instantâneas pública com AOL será implantada. Além disso, para Servidores de Borda dimensionadas, a chave privada do certificado deve ser exportável e a chave privada e o certificado copiados para cada Servidor de Borda. O certificado é atribuído às interfaces de Borda externa para:</p><ul><li><p>Borda de Acesso</p></li><li><p>Borda de Conferência</p></li><li><p>Borda A/V</p></li></ul>
<p>Observe que os SANs são adicionados automaticamente ao certificado, com base em suas definições no Construtor de Topologia. Você pode adicionar entradas de SAN conforme necessário para domínios SIP adicionais e outras entradas às quais você precisa dar suporte. O nome da entidade é replicado no SAN e deve ser apresentado para a operação correta.</p></td>
</tr>
<tr class="even">
<td><p>Borda consolidada dimensionada (Borda interna)</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>Nenhum SAN necessário</p></td>
<td><p>O certificado pode ser emitido por uma AC pública ou privada, e deve conter o EKU do servidor. O certificado é atribuído à interface de Borda interna.</p></td>
</tr>
</tbody>
</table>


## Resumo de certificado - Conectividade pública de mensagens instantâneas


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
<th>Nomes alternativos de entidade (SAN)/Ordem</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Borda de acesso/externa</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>sip.fabrikam.com</p></td>
<td><p>O certificado deve ser de uma AC Pública, e deve possuir o EKU de servidor e de cliente se a conectividade de mensagens instantâneas pública com AOL será implantada. O certificado é atribuído às interfaces de Borda externa para:</p><ul><li><p>Borda de Acesso</p></li><li><p>Borda de Conferência</p></li><li><p>Borda A/V</p></li></ul>
<p>Observe que os SANs são adicionados automaticamente ao certificado, com base em suas definições no Construtor de Topologia. Você pode adicionar entradas de SAN conforme necessário para domínios SIP adicionais e outras entradas às quais você precisa dar suporte. O nome da entidade é replicado no SAN e deve ser apresentado para a operação correta.</p></td>
</tr>
</tbody>
</table>


## Resumo de Certificado para Protocolo de Presença e Mensagem Extensível


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
<th>Nomes alternativos de entidade (SAN)/Ordem</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Atribuir para Serviço de Borda de Acesso de Servidor de Borda ou Pool de borda</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>webcon.contoso.com</p>
<p>sip.contoso.com</p>
<p>sip.fabrikam.com</p>
<p>xmpp.contoso.com</p>
<p><strong>*.contoso.com</strong></p></td>
<td><p>As três primeiras entradas SAN são as entradas SAN normais para uma Servidor de Borda completa. A contoso.com é a entrada exigida para federação com o parceiro XMPP no nível de domínio raiz. Essa entrada habilitará XMPP para todos os domínios com sufixo *.contoso.com.</p></td>
</tr>
</tbody>
</table>

