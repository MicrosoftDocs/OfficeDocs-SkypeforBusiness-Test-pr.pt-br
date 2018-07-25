---
title: 'Lync Server 2013: Introdução'
TOCTitle: Introdução ao Lync Server
ms:assetid: 99dd6b65-e591-421f-852b-ee9fe9588998
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398795(v=OCS.15)
ms:contentKeyID: 49307566
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Introdução ao Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Lync Server 2013 e seu software cliente, como o Lync 2013, permitem que os usuários se conectem de novas maneiras e permaneçam conectados, independentemente da localização físicas deles. O Lync e Lync Server reúnem em uma única interface de cliente as diferentes formas de comunicação entre as pessoas, são implantados como uma plataforma unificada e administrados por meio de uma infraestrutura de gerenciamento única.

Esta tabela e as seções a seguir ilustram os principais conjuntos de recursos, ou *cargas de trabalho* , que o Lync Server oferece para seus usuários.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Carga de Trabalho</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>IM e presença</p></td>
<td><p>Sistemas de mensagens instantâneas (IM) e de presença ajudam seus usuários a encontrar e se comunicar entre si de forma eficiente e efetiva.</p>
<p>O IM fornece uma plataforma de mensagens instantâneas com histórico de conversas e oferece suporte a conectividade pública de IM com usuários de redes públicas de IM, como MSN/Windows Live, Yahoo!, AOL e Google Talk.</p>

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li>
> </ul>

<p>A presença estabelece e exibe a disponibilidade pessoal e vontade de um usuário de se comunicar através do uso de estados comuns, como <strong>Disponível</strong> ou <strong>Ocupado</strong> , além de estados mais detalhados, como <strong>Volto Logo</strong> e <strong>Não Incomodar</strong> . Essas informações valiosas de presença permitem que outros usuários façam escolhas de comunicação eficientes de forma imediata.</p></td>
</tr>
<tr class="even">
<td><p>Conferência</p></td>
<td><p>O Lync Server inclui suporte para conferência de IM, conferências via web, vídeo conferências e compartilhamento de aplicativos, para reuniões agendadas e improvisadas. Todos esses tipos de reunião são suportados com um único cliente. O Lync Server também oferece suporte a conferência discada para que os usuários de telefones da rede telefônica pública (PSTN) possam participar da parte de áudio de conferências.</p>
<p>Conferências podem mudar e crescer em tempo real sem problemas. Por exemplo, uma única conferência pode começar como mensagens instantâneas entre alguns usuários e crescer para uma conferência de áudio com compartilhamento de área de trabalho e audiência maior de forma instantânea, fácil e sem interromper o fluxo da conversa.</p></td>
</tr>
<tr class="odd">
<td><p>Enterprise Voice</p></td>
<td><p><em>Enterprise Voice</em> é a oferta de protocolo VoIP no Lync Server. Ele fornece uma opção de voz para aprimorar ou substituir sistemas de central privada de comutação telefônica (PBX). Além de completar recursos de telefonia de um IP PBX, o Enterprise Voice é integrado com presença avançada, IM, colaboração e reuniões. Recursos como atender, colocar em espera, reiniciar, transferir, encaminhar e desviar chamadas são suportados diretamente, enquanto teclas de discagem rápida são substituídas por listas de Contatos e o interfone automático é substituído pelo IM.</p>
<p>O Enterprise Voice oferece suporte a alta disponibilidade através do serviço de controle de admissão de chamadas (CAC), persistência de filial e opções avançadas para resiliência de dados.</p></td>
</tr>
<tr class="even">
<td><p>Suporte a usuários remotos</p></td>
<td><p>Você pode fornecer a funcionalidade completa do Lync Server para usuários que estão atualmente fora dos firewalls da sua organização, implantando servidores chamados <em>Servidores de Borda</em> para fornecer uma conexão para estes usuários remotos. Eles podem se conectar a conferências usando um computador pessoal com o Lync 2013 instalado, o telefone ou uma interface web.</p>
<p>Implantar Servidores de Borda também permite a <em>federação</em> com organizações fornecedoras ou parceiros. Uma relação federada permite que seus usuários coloquem usuários federados em suas listas de Contatos, troquem informações de presença e mensagens instantâneas com eles e os convidem para chamadas de áudio, de vídeo e conferências.</p></td>
</tr>
<tr class="odd">
<td><p>Suporte a clientes móveis</p></td>
<td><p>Além disso, com os serviços de mobilidade do Lync Server seus usuários podem acessar a funcionalidade do Lync ao usar dispositivos móveis suportados Apple iOS, Android, Windows Phone ou Nokia para realizar atividades como enviar e receber mensagens instantâneas, visualizar contatos e visualizar presença. Além disso, os dispositivos móveis suportam alguns recursos do Enterprise Voice, como clicar para participar de uma conferência, Chamada via Trabalho, acesso a único número, caixa postal e chamadas perdidas. Notificações de push são também suportadas para dispositivos móveis que não suportam aplicativos sendo executados em segundo plano.</p></td>
</tr>
<tr class="even">
<td><p>Integração com outros produtos</p></td>
<td><p>O Lync Server se integra com vários outros produtos para fornecer benefícios adicionais a seus usuários e administradores.</p>
<p>Ferramentas de reunião são integradas no Outlook para permitir aos organizadores agendar uma reunião ou iniciar uma conferência de última hora com um único clique e, da mesma forma, facilitar a entrada dos participantes.</p>
<p>Informações de presença são integradas no Outlook e SharePoint.</p>
<p>A Unificação de Mensagens do Exchange (UM) fornece vários recursos de integração. Os usuários podem ver se têm uma nova mensagem na caixa postal dentro do Lync Server. Eles podem clicar em um botão de reprodução na mensagem no Outlook para ouvir a mensagem de áudio ou exibir uma transcrição da mensagem de voz na mensagem de notificação.</p>
<p>Além disso, executar o Lync Server 2013 com Exchange 2013 permite vários novos recursos, como armazenamento de contatos unificado que pode ser acessado por clientes de ambos os produtos, assim como fotos de alta resolução que são armazenadas no banco de dados do Exchange 2013.</p></td>
</tr>
<tr class="odd">
<td><p>Implantação simples</p></td>
<td><p>Para ajudá-lo a planejar e implantar seus servidores e clientes, o Lync Server oferece o Construtor de Topologias.</p>
<p></p>
<p>O Construtor de Topologias é um componente de instalação do Lync Server. Use o Construtor de Topologias para criar, ajustar e publicar sua topologia planejada. Ele também valida sua topologia antes de você começar as instalações dos servidores. Ao instalar o Lync Server em servidores individuais, o programa de instalação implanta o servidor conforme orientado na topologia.</p></td>
</tr>
<tr class="even">
<td><p>Gerenciamento simples</p></td>
<td><p>Depois de implantar o Lync Server, ele oferece as poderosas e eficientes ferramentas de gerenciamento a seguir:</p>
<ul>
<li><p>Gerenciamento de configuração central, que permite gerenciar alterações forma centralizada e fazê-las replicar rapidamente para toda a implantação.</p></li>
<li><p>O Painel de Controle do Lync Server, uma nova interface gráfica do usuário baseada em web para administradores. Com esta IU baseada em web, os administradores do Lync Server podem gerenciar seus sistemas de qualquer lugar na rede corporativa, sem a necessidade de um software de gerenciamento especializado instalado em seus computadores.</p></li>
<li><p>A ferramenta de gerenciamento de linha de comando Shell de Gerenciamento do Lync Server, baseada no Interface da linha de comando do Windows PowerShell. Ela fornece um sofisticado conjunto de comandos para administração de todos os aspectos do produto e permite que administradores do Lync Server automatizem tarefas repetitivas usando uma ferramenta familiar.</p></li>
</ul></td>
</tr>
</tbody>
</table>


Embora os recursos de IM e presença sejam automaticamente instalados em toda implantação do Lync Server, você pode escolher se implantará conferências, Enterprise Voice e acesso de usuário remoto, para personalizar sua implantação de acordo com as necessidades da sua organização.

## Nesta seção

  - [IM e presença no Lync Server 2013](lync-server-2013-im-and-presence.md)

  - [Conferência no Lync Server 2013](lync-server-2013-conferencing.md)

  - [Enterprise Voice no Lync Server 2013](lync-server-2013-enterprise-voice.md)

  - [Escalabilidade com Lync Server 2013](lync-server-2013-scalability.md)

