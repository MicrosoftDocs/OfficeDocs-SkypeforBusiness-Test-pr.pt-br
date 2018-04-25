---
title: Cmdlets do servidor de borda
TOCTitle: Cmdlets do servidor de borda
ms:assetid: 1a5427f4-a0d1-4652-8135-91333158ffc8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg415635(v=OCS.15)
ms:contentKeyID: 49306039
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets do servidor de borda

 

_**Tópico modificado em:** 2016-12-08_

Os Servidores de borda fornecem uma maneira para você ampliar as capacidades do Microsoft Lync Server 2013 para pessoas não conectadas na sua rede interna. Por exemplo, se você possuir usuários remotos, usuários autenticados que efetuem logon no Lync Server 2013 através da Internet em vez da rede interna, será necessário configurar um Servidor de borda que execute o serviço de Borda de acesso ao Lync Server. Além disso, os Servidores de Borda são necessários se você deseja estabelecer a federação com outra organização ou se deseja fornecer aos seus usuários o direito de se comunicarem com pessoas que possuam contas em serviços públicos de mensagens instantâneas tais como o Yahoo\!, AOL ou MSN.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Gg425939.important(OCS.15).gif" title="important" alt="important" />Importante:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul>
<li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
<li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
<li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Cmdlets do Servidor de Borda

A lista a seguir contém os cmdlets diretamente relacionados ao gerenciamento dos Servidores de borda:

**Servidor de borda**

  -   
    [Get-CsAccessEdgeConfiguration](get-csaccessedgeconfiguration.md)

  -   
    [Set-CsAccessEdgeConfiguration](set-csaccessedgeconfiguration.md)

  -   
    [Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)

  -   
    [New-CsAVEdgeConfiguration](new-csavedgeconfiguration.md)

  -   
    [Remove-CsAVEdgeConfiguration](remove-csavedgeconfiguration.md)

  -   
    [Set-CsAVEdgeConfiguration](set-csavedgeconfiguration.md)

  -   
    [Test-CsAVEdgeConnectivity](test-csavedgeconnectivity.md)

  -   
    [Set-CsEdgeServer](set-csedgeserver.md)

## Consulte Também

#### Outros Recursos

[Blog do Lync Server PowerShell](http://go.microsoft.com/fwlink/?linkid=203150)

