---
title: 'Lync Server 2013: Recursos de mobilidade'
TOCTitle: Recursos de mobilidade
ms:assetid: 12517a88-2531-44a5-bea5-d8884aff53eb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh689983(v=OCS.15)
ms:contentKeyID: 49305950
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recursos de mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

O recurso de mobilidade no Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013 suporta a funcionalidade de clientes móveis Lync 2010 Mobile e Lync 2013. Ao implantar o Serviço de Mobilidade do Lync Server 2013, os usuários podem usar os dispositivos móveis suportados Apple iOS, Android, Windows Phone ou Nokia Symbian para realizar atividades como enviar e receber mensagens instantâneas, visualizar contatos e visualizar presença. Além disso, os dispositivos móveis suportam alguns recursos do Enterprise Voice, como clicar para participar de uma conferência, Chamada via Trabalho, acesso a único número, caixa postal e chamadas perdidas. Novos recursos introduzidos pelas Atualizações Cumulativas para Lync Server: Fevereiro de 2013 incluem o recurso VoIP e vídeo (H264) para participante de reunião.

O recurso de mobilidade apresentado nas Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013 suporta a funcionalidade de cliente móvel Lync 2013. As Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013 instalam a API Web de Comunicações Unificadas, ou UCWA. A UCWA é o componente usado para clientes móveis Lync 2013. No Lync Server 2013, o Mcx é usado para clientes Lync 2010 Mobile. As Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013 apresentam o UCWA como um novo ponto de entrada para serviços de mobilidade. Lync Server 2013, ao mesmo tempo, implementa o Serviço de mobilidade (Mcx), introduzido no Atualizações Cumulativas para Lync Server 2010: Novembro de 2011, e fornece suporte para Lync 2010 Mobile. Ao implantar as Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013, os usuários podem usar os dispositivos suportados Apple iOS, Android e Windows Phone para efetuar as seguintes atividades:

> [!IMPORTANT]  
> Recursos suportados pelo Serviço de Mobilidade do Atualizações Cumulativas para Lync Server 2010: Novembro de 2011 estão marcadas com (Mcx). Todos os recursos listados são suportados pela UCWA, apresentados na Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

  - Enviar e receber mensagens instantâneas (Mcx)

  - Visualizar presença (Mcx)

  - Visualizar contatos (Mcx)

  - Clicar para participar de uma conferência (Mcx)

  - Chamada via Trabalho (Mcx)

  - Acesso a número único (Mcx)

  - Mensagem por voz (Mcx)

  - Notificação de chamada perdida (Mcx)

  - Voz sobre IP (VoIP)

  - Vídeo de participante (H.264)

> [!NOTE]  
> O Lync 2010 Mobile forneceu um cliente para dispositivos Nokia Symbian. O Lync 2013 móvel não possui um cliente para dispositivos com base em Nokia Symbian.

Usuários do Apple iPad terão acesso a recursos avançados. Depois de entrar em uma reunião usando retorno de chamada de áudio, um usuário do iPad poderá visualizar apresentações do Microsoft PowerPoint carregadas dentro de uma reunião, compartilhar aplicativos e áreas de trabalho, visualizar a lista de participantes da reunião e receber notificações de outros tipos de conteúdo que estiverem sendo compartilhados dentro da reunião.


> [!TIP]
> Com o acesso a único número, um usuário recebe chamadas feitas de um telefone móvel que discou para o número do trabalho. Com o Chamada via Trabalho, o usuário estabelece uma chamada de saída de um cliente Lync Mobile usando o número de telefone do trabalho em vez do número do celular. Com a discagem, o cliente envia uma solicitação ao Mcx ou UCWA (com base na versão Lync Mobile) para chamar. O servidor inicia a chamada e depois retorna a chamada no celular do usuário. Quando o usuário atende, o servidor completa a chamada discando para a outra parte. Usando o Chamada via Trabalho, os usuários podem manter sua identidade de trabalho durante uma chamada, o que significa que o destinatário da chamada não visualiza o número de celular do chamador, e este evita incorrer em tarifas da chamada de saída.



> [!NOTE]  
> Nem todos os recursos funcionam exatamente da mesma forma em dispositivos móveis. Para obter informações sobre os recursos suportados nos dispositivos móveis, consulte Tabelas de comparação do cliente móvel em <a href="http://go.microsoft.com/fwlink/p/?linkid=234777">http://go.microsoft.com/fwlink/p/?LinkId=234777</a>. Para obter informações sobre os dispositivos suportados e os sistemas operacionais, consulte os tópicos de requisitos em <a href="lync-server-2013-planning-for-mobile-clients.md">Planejamento para clientes móveis no Lync Server 2013</a>.

Quando você usa o Serviço de Descoberta Automática do Lync Server 2013, os aplicativos móveis podem localizar automaticamente os Serviços da Web do Lync Server 2013 sem solicitar que os usuários insiram manualmente as URLs em suas configurações dos dispositivos. A inserção manual de URLs nas configurações do dispositivo móvel também é suportada, principalmente para fins de solução de problemas.

> [!IMPORTANT]  
> O Mcx e a UCWA são serviços complementares e implantados para fornecer suporte a clientes móveis Lync 2010 Mobile e Lync 2013. O Lync 2013 móvel não pode entrar em implantações Lync Server 2010. Lync 2010 Mobile e Lync 2013 móveis poderão usar uma implantação Lync Server 2013 com Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013 aplicada.

O recurso de mobilidade também dá suporte às *notificações por push* para dispositivos móveis que não suportam os aplicativos executados em segundo plano. Uma notificação por push é um aviso enviado a um dispositivo móvel sobre um evento que ocorre enquanto o aplicativo está inativo. Por exemplo, um convite de mensagem instantânea pode resultar em uma notificação por push.

O Mcx, UCWA, Serviço de Descoberta Automática e o suporte a notificações por push são fornecidos no Lync Server 2013. Recursos de clientes atualizados, capacidades e o uso do UCWA como ponto de entrada de mobilidade são introduzidos no Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

