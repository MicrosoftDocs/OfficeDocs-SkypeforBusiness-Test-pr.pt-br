---
title: 'Lync Server 2013: Configuração de federação do Lync'
TOCTitle: Configuração de federação do Lync
ms:assetid: 374ddc43-26f9-499d-be68-a5158adfa49c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204800(v=OCS.15)
ms:contentKeyID: 49306375
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração de federação do Lync no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Se o servidor de borda já foi implantado nos servidores, a adição dos recursos de cenários federados é o próximo passo. Se os servidores de borda ainda não foram definidos, faça isso primeiro. Para obter detalhes, consulte: [Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md) na documentação de planejamento e [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de implantação.

> [!NOTE]  
> Se você pretende instalar uma combinação de federação XMPP, federação do Lync ou uma conectividade pública de mensagens instantâneas, é possível implantá-las simultaneamente ou uma de cada vez. Se configurar as opções com o Construtor de Topologias e o shell de gerenciamento do Lync Server e executar o Assistente de implantação no servidor de borda depois de configurar as opções para um, dois ou todos os três tipos de federação, será possível reduzir o número de etapas necessárias.

## Instalando a federação do Lync no Construtor de Topologias e o Assistente de implantação

1.  Em um servidor front-end, abra o Construtor de Topologias. Expanda os pools de borda e clique com o botão direito do mouse no servidor de borda ou pool de servidores de borda. Selecione Editar propriedades.

2.  Em Editar propriedades, em Geral, selecione Habilitar federação para esse pool de borda (porta 5061). Clique em OK.

3.  Clique em Ação, selecione Topologia e, depois, Publicar. Quando for consultado sobre a publicação da topologia, clique em Avançar. Quando a publicação estiver concluída, clique em Concluir.

4.  No servidor de borda, abra o assistente Implantação do Lync Server. Clique em Instalar ou Atualizar Sistema do Lync Server e, então, clique em Instalar ou Remover Componentes do Lync Server. Clique em Executar Novamente.

5.  Em Instalar Componentes do Lync Server, clique em Avançar. A tela de resumo mostrará as ações conforme forem executadas. Depois que a implantação estiver concluída, clique em Exibir Log para exibir os arquivos de log disponíveis. Clique em Concluir para concluir a implantação.
    
    > [!IMPORTANT]  
    > É possível selecionar esta opção, mas apenas um pool de borda ou servidor de borda de sua organização pode ser publicado externamente para federação. Todo o acesso de usuários federados, inclusive usuários públicos de IM (mensagens instantâneas), atravessa o mesmo pool de borda ou servidor de borda único. Por exemplo, se sua implantação contém um pool de borda ou servidor de borda único implantado em Nova Iorque e outro implantado um Londres e você habilita o suporte à federação no pool de borda ou servidor de borda único de Nova Iorque, o tráfego do sinal para os usuários federados atravessará o pool de borda ou servidor de borda único de Nova Iorque. Isso é verdadeiro até mesmo para comunicações com os usuários de Londres, embora um usuário interno de Londres que liga para um usuário federado do Nova Iorque use um pool ou servidor de borda de Londres para o tráfego de áudio/vídeo.

## Configurando a federação com parceiros

1.  Para instalar uma federação bem-sucedida com outro Microsoft Lync Server 2013, Lync Server 2010, Office Communications Server 2007 R2 ou Office Communicator 2007, selecione o tipo de federação da tabela a seguir e defina os registros SRV de DNS, o host DNS (A ou AAAA para IPv6) e configure as políticas aplicáveis ao tipo de federação:    
    
<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de federação</th>
<th>Registros DNS</th>
<th>Definição de política</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Domínio do parceiro descoberto</p></td>
<td><p>Configure o registro SRV de formato _sipfederationtls._tcp.&lt;nome do domínio externo&gt; em que o valor da porta do registro SRV é TCP 5061 e o <strong>Host que oferece esse serviço</strong> é definido como sip. &lt;nome do domínio externo&gt; - o FQDN de seu Serviço de Borda de Acesso. Consulte <a href="lync-server-2013-configure-dns-for-edge-support.md">Configurar DNS para suporte à borda no Lync Server 2013</a> para obter detalhes sobre a criação do registro SRV</p></td>
<td>      
<ul>   
<li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></li>   
<li><p><a href="lync-server-2013-enable-or-disable-discovery-of-federation-partners.md">Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013</a></p></li></ul></td>
<td><p>As versões anteriores se referiam a esse tipo de federação como <strong>Federação avançada aberta</strong>. A criação do registro SRV é obrigatória para esse tipo de federação e serve para permitir que outros parceiros descubram sua federação.</p></td>
</tr>
<tr class="even">
<td><p>Domínio de parceiro permitido</p></td>
<td><p>Configure o registro SRV de formato _sipfederationtls._tcp.&lt;nome do domínio externo&gt; em que o valor da porta do registro SRV é TCP 5061 e o <strong>Host que oferece esse serviço</strong> é definido como sip. &lt;nome do domínio externo&gt; - o FQDN de seu Serviço de Borda de Acesso. Consulte <a href="lync-server-2013-configure-dns-for-edge-support.md">Configurar DNS para suporte à borda no Lync Server 2013</a> para obter detalhes sobre a criação do registro SRV</p></td>
<td><ul>    
<li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></li>    </ul></td>
<td><p>As versões anteriores se referiam a esse tipo de federação como <strong>Federação avançada</strong>. A criação do registro SRV é opcional para esse tipo de federação e serve para permitir que outros parceiros descubram sua federação. Isso é obviamente uma <strong>Federação avançada aberta</strong> ou um <strong>Domínio de parceiro descoberto</strong></p></td>
</tr>
<tr class="odd">
<td><p>Servidor de parceiro permitido</p></td>
<td><p>Configure o nome do domínio SIP e o FQDN de parceiro do Servidor de Borda como um parceiro de federação em Políticas</p></td>
<td><ul>    
<li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></li>    
<li><p><a href="lync-server-2013-configure-support-for-allowed-external-domains.md">Configurar suprote para domínios externos permitidos no Lync Server 2013</a></p></li>    
<li><p><a href="lync-server-2013-configure-support-for-blocked-external-domains.md">Configurar suporte para domínios externos bloqueados no Lync Server 2013</a></p></li>    </ul></td>
<td><p>Esse tipo de federação é a definição de uma relação um-para-um e não permite a descoberta de outros parceiros de federação. Cada parceiro de federação é configurado explicitamente. Nas versões anteriores, isso era conhecido como <strong>Federação direta</strong></p></td>
</tr>
<tr class="even">
<td><p>Hospedando provedor e provedor de IM público</p></td>
<td><p>Nenhum requisito específico de DNS é definido para esse tipo de federação</p></td>
<td><ul>    
<li><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></li>    
<li><p><a href="lync-server-2013-create-or-edit-public-sip-federated-providers.md">Criar ou editar fornecedores SIP públicos federados no Lync Server 2013</a></p></li>    
<li><p><a href="lync-server-2013-create-or-edit-hosted-sip-federated-providers.md">Criar ou editar provedores hospedados federados SIP no Lync Server 2013</a></p></li>   </ul></td>
    <td><p>Esse tipo de federação define os provedores de serviços e hospedagem que você deseja configurar para seus usuários. Os usos mais comuns incluem a configuração de provedores de IM públicos como Windows Live Messenger, Yahoo! e AOL, bem como provedores de hospedagem, como Lync Online e Office 365</p>
    <div class="alert">
    > [!IMPORTANT]  
    > <ul>    
<li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>    
<li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>    
<li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li>    </ul>

</div></td>
</tr>
</tbody>
</table>


2.  Defina e configure todos os hosts DNS exigidos (A ou AAAA para IPv6) e registros SRV de DNS

3.  Defina e configure todas as políticas usando o Painel de Controle do Lync Server ou o Shell de Gerenciamento do Lync Server e os cmdlets apropriados. Para obter detalhes sobre os cmdlets do Shell de Gerenciamento do Lync Server, consulte [Cmdlets de federação e acesso externo no Lync Server 2013](https://docs.microsoft.com/en-us/powershell/module/skype/)
    
    > [!NOTE]  
    > O Lync Room System (LRS) não mostra o botão Ingressar para reuniões enviadas pelos organizadores em parceiros federados do Lync. Para que o link Ingressar de uma reunião apareça no LRS, a organização remetente deverá habilitar o TNEF usando o seguinte cmdlet:<br />    <br />    <code>New-RemoteDomain -DomainName Contoso.com -Name Contoso</code><br />    <code>Set-RemoteDomain -Identity Contoso -TNEFEnabled $true</code><br />    Observe que isso não é específico do LRS. O Outlook e o Lync também não mostrarão links Ingressar nesse caso, pois as propriedades MAPI não são transportadas, mas no caso do Outlook, o usuário pode abrir o convite para reunião e clicar na URL da reunião. Quando TNEFEnabled está definido como true, o Exchange 2013 não remove as propriedades MAPI, inclusive OnlineMeetingExternalLink, e o botão Ingressar será mostrado no lembrete.

## Consulte Também

#### Outros Recursos

[Planejamento para SIP, federação XMPP e mensagens instantâneas públicas no Lync Server 2013](lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md)  
[Gerenciando de federação e acesso externo ao Lync Server 2013](lync-server-2013-managing-federation-and-external-access-to-lync-server-2013.md)

