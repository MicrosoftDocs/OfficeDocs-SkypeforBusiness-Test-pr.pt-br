---
title: 'Lync Server 2013: Enterprise Voice'
TOCTitle: Enterprise Voice
ms:assetid: c9da8099-6f4f-4346-ac67-f041bb96072c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg417163(v=OCS.15)
ms:contentKeyID: 49308109
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2015-04-08_

Com o Enterprise Voice, o Lync Server oferece um Protocolo Voz por Internet (VoIP) autônomo oferecendo melhoria ou substituição dos sistemas PBX tradicionais. Os usuários do Enterprise Voice podem ligar para colegas na sua rede VoIP da organização ou PBX e podem ligar para números tradicionais fora da organização. A solução do Enterprise Voice inclui recursos de ligação comuns como responder, encaminhar, transferir, manter, divergir, liberar e estacionar, e ligação 9-1-1 Avançado (E9-1-1) (E9-1-1 está disponível apenas nos Estados Unidos.) O Enterprise Voice também suporta uma ampla variedade de dispositivos USB e IPs atuais e antigos.

## Fazendo e recebendo chamadas

Usando o Lync, os usuários podem realizar chamadas digitando um nome ou número de telefone com o teclado ou usando o teclado na tela. Os usuários podem iniciar chamadas diretamente da sua lista de Contatos. Também é possível implantar dispositivos do Lync Phone Edition, que são dispositivos de telefone IP autônomos oferecidos pelos parceiros da Microsoft.

Os usuários podem ter diversos dispositivos telefônicos registrados no Lync Server e podem trocar entre eles com facilidade.

Os usuários são alertados sobre chamadas recebidas em todos seus dispositivos simultaneamente, com toques personalizados em telefones IP e uma notificação parecida com uma mensagem instantânea no PC.

Os usuários também podem definir um único número de telefone que fica conectado ao telefone de mesa, PC e celular, de modo que possam ser encontrados não importa onde estejam.

## Recursos básicos de chamada

Durante uma chamada, um usuário pode atender a outras chamadas ou iniciar chamadas de saída, e a chamada ativa atual é colocada automaticamente em espera. As chamadas podem ser transferidas de um usuário para outro, diretamente ou após o primeiro usuário falar em particular com o segundo usuário. Os usuários também podem transferir chamadas para outro dispositivo; por exemplo, eles podem transferir uma chamada ativa para seus celulares enquanto saem de seus escritórios.

## Comunicações mais ricas

Ao conversar com outro usuário com o Lync, os usuários pode adicionar texto, vídeo ou compartilhamento de área de trabalho à chamada. O recurso Não Incomodar é integrado às configurações de presença no Lync.

Com o Unificação de Mensagens (UM) do Exchange, Lync e integração do Lync Server com o Microsoft Exchange Server 2013 e Microsoft Outlook 2013. Os usuários podem ver se há novas caixas postais na janela do Lync e no e-mail. Enquanto estiverem no e-mail, podem clicar para reproduzir o áudio da caixa postal em uma mensagem de email ou exibir uma transcrição da mensagem de caixa postal.

## Recursos avançados de chamada

O Enterprise Voice também inclui diversos recursos avançados de chamada, como delegação, chamada em equipe, atendimento de chamadas em grupo e Grupos de Resposta.

A delegação permite que os usuários deleguem a manipulação de chamadas a um ou mais assistentes. O representante pode executar diversas tarefas de chamada em nome do usuário, incluindo camadas filtragem de chamadas, realização de chamadas e início de conferências.

A chamada em equipe permite que as chamadas em entrada de um usuário toquem simultaneamente nos telefones de colegas de sua equipe, para que qualquer membro dessa equipe possa atender a chamada.

Atendimento de chamadas em grupo, um novo recurso nas atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013, permite que os usuários atendam, utilizando seus próprios telefones, chamadas em entrada destinadas a seus colegas. Atendimento de chamadas em grupo é diferente de chamada em equipe primariamente porque uma chamada em entrada toca somente no telefone do destinatário, mas qualquer outro usuário pode optar por atendê-la discando um número de grupo de atendimento de chamadas.

Os Grupos de Resposta podem ser definidos para enfileiramento e roteamento inteligente de chamadas aos agentes designados. Entre os usos comuns estão assistência técnica de TI, linde atendimento dos recursos humanos e outros centros de contato internos.

## Administração do Enterprise Voice

O Lync Server usa interfaces padrão e publicadas para interoperar com a infraestrutura existente. Ele suporta as opções de gateway e SIP (como tronco SIP) para interconexão com sistemas IP PBX e as redes PSTN, de modo que você possa migrar os usuários para o Enterprise Voice com o tempo, minimizando as interrupções. O Lync Server suporta codecs tradicionais como G.711, G.722 e G.723.1 para interoperabilidade com soluções VoIP tradicionais.

Com o (controle de admissão de chamada), os administradores podem definir limites sobre a quantidade de tráfego de voz e vídeo do Lync Server transportado em links de rede restrita e especificar a ação a ser executada se uma nova chamada ultrapassasse o limite. As ações poderiam incluir roteamento por um caminho alternativo ou a recusa da chamada.

O Lync Server funciona com Dispositivos de Filial Persistente de terceiros para oferecer serviços de chamada e conexão ao PSTN em escritórios filiais, em caso de uma falha de WAN no local central.

