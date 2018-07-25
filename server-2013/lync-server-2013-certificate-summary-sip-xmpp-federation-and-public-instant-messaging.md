---
title: Resumo de certificado - SIP, federação XMPP e mensagens instantâneas públicas
TOCTitle: Resumo de certificado - SIP, federação XMPP e mensagens instantâneas públicas
ms:assetid: 933d6351-cfa6-4432-b3ed-1aff3ac92065
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ618372(v=OCS.15)
ms:contentKeyID: 49307473
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de certificado - SIP, federação XMPP e mensagens instantâneas públicas

 

_**Tópico modificado em:** 2015-03-09_

Os certificados que são necessários para a federação com o Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server serão atendidos geralmente pelos certificados que você configurar, solicitar e atribuir a seu Servidor de Borda.

Os requisitos de certificado para ativar e estabelecer comunicações com mensagens extensíveis e parceiros de protocolo de presença (XMPP) requerem o registro adicional de seus domínios XMPP. O registro incluído no certificado como um nome alternativo da entidade (SAN) será o domínio que pode participar das comunicações XMPP. O domínio pode ser o domínio no nível raiz (por exemplo, contoso.com) se você deseja habilitar XMPP para o domínio inteiro ou pode ser determinados domínios filho (por exemplo, corp.contoso.com, finance.contoso.com) se estiver habilitando XMPP para um subconjunto de usuários.

Para configurar certificados para conectividade de Mensagem Instantânea pública, você deve primeiro observar que não há nada diferente de outros tipos de federação SIP ou mesmo certificados padrão do Servidor de Borda exceto que a America Online (AOL) exige o certificado ou certificados (no caso de um Pool de borda) para também conter o cliente EKU. O cliente EKU é uma adição ao certificado e faz parte do certificado público externo atribuído a seu Servidor de Borda.

Para confirmar que você atende aos requisitos de certificado corretos da sua implantação do Servidor de Borda, revise os tópicos listados na seção intitulada **Consulte Também**.



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
<th>Nomes de Entidade Alternativos (SAN)</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Borda de acesso/externa</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>sip.contoso.com</p>
<p>webcon.contoso.com</p>
<p>contoso.com</p>

> [!NOTE]  
> Para suportar o namespace do XMPP do contoso.com

<p>sip.fabrikam.com</p>

> [!NOTE]  
> Para dar suporte ao namespace do SIP do fabrikam.com

<p>fabrikam.com</p>

> [!NOTE]  
> Para dar suporte ao namespace do XMPP do fabrikam.com

</td>
<td><p>O certificado deve ser de uma CA pública e deve ter o EKU do servidor e o EKU do cliente se a conectividade de IM pública com a AOL ainda esteja para ser implementada. O certificado é atribuído para as interfaces externas do Servidor de Borda para:</p>
<ul>
<li><p>Serviço de Borda de Acesso</p></li>
<li><p>Serviço de Borda de Webconferência</p></li>
<li><p>Serviço de Borda A/V</p></li>
</ul>

> [!NOTE]  
> Tecnicamente, um certificado não é atribuído à Borda A/V Edge. A comunicação e autenticação seguras são gerenciadas por meio do Serviço de Autenticação de Media Relay (MRAS). O MRAS usa o certificado atribuído à interface interna do Servidor de Borda.

<p>Observe que os SANs são adicionados automaticamente ao certificado, com base em suas definições no Construtor de Topologia. Você pode adicionar entradas de SAN conforme necessário para domínios SIP adicionais e outras entradas às quais você precisa dar suporte. O nome da entidade é replicado no SAN e deve ser apresentado para a operação correta.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Tarefas

[Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk](lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md)  

#### Conceitos

[Planejar certificados do Servidor de Borda no Lync Server 2013](lync-server-2013-plan-for-edge-server-certificates.md)  
[Resumo de certificado - única borda consolidada com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-certificate-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)  
[Resumo de certificado - Única borda consolidada com endereços IP públicos no Lync Server 2013](lync-server-2013-certificate-summary-single-consolidated-edge-with-public-ip-addresses.md)  
[Resumo de certificado - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)  
[Resumo de certificado - Borda consolidade em escala, balanceamento de carga de DNS com endereços IP públicos no Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)  
[Resumo de certificado - Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

