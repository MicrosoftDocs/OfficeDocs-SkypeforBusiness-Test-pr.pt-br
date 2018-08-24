---
title: 'Lync Server 2013: Novidades para clientes'
TOCTitle: Novidades para clientes
ms:assetid: 5c144677-4d58-4fc3-8445-74b76c9fcf07
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204933(v=OCS.15)
ms:contentKeyID: 49306835
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novidades para clientes no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Microsoft Lync 2013 traz uma interface do usuário reformulada e importantes novos recursos. Para administradores, o cliente agora vem incluído no programa de instalação do Office, fornecendo uma abordagem simplificada para a implantação do Office e a personalização dos clientes na sua organização.

> [!NOTE]  
> Para obter uma visualização ilustrada das atualizações da interface do usuário do Lync 2013, consulte “Novidades do Lync 2013” em <a href="http://go.microsoft.com/fwlink/?linkid=273885">http://go.microsoft.com/fwlink/?LinkId=273885</a>.

## Integração com a instalação do Office

O cliente do Lync 2013 e o Suplemento de Reunião Online para Lync 2013, que oferece suporte ao gerenciamento de reuniões a partir do cliente de colaboração e mensagens do Outlook agora vêm ambos incluídos no programa de instalação do Office 2013.

Em versões anteriores do Lync e do Office Communicator, era possível usar propriedades do Windows Installer para personalizar e controlar a instalação do Office. Como o Lync 2013 é integrado à instalação do Office, você pode usar os seguintes métodos para personalizar a instalação do Lync 2013:

  - Usar a OCT (Ferramenta de Personalização do Office)

  - Usar o Config.xml para executar tarefas de instalação

  - Usar as opções de linha de comando de instalação

> [!NOTE]  
> O programa de instalação do Lync 2013 não desinstala versões anteriores do Lync ou do Office Communicator. O cliente do Lync 2013 é instalado paralelamente a outros clientes do Lync ou do Office Communicator

Para obter detalhes, consulte [Implantando clientes Lync no Lync Server 2013](lync-server-2013-deploying-lync-clients.md).

## Implantação da Política de Grupo

Como o Lync 2013 agora vem incluído na instalação do Office, o método para implantar configurações de Política de Grupo do Lync mudou. Nas versões anteriores do Lync e do Office Communicator, era possível usar o Communicator.adm para definir configurações de Política de Grupo. Já no Lync 2013, agora você pode usar os modelos administrativos ADMX e ADML do Lync que são fornecidos junto com os modelos administrativos de Política de Grupo do Office.

Para obter detalhes, consulte [Configurações da política de grupo para o Lync 2013](lync-server-2013-group-policy-settings-for-lync-2013.md).

## Atualizações do suplemento de agendamento do Outlook

O Suplemento de Reunião Online para Lync 2013 inclui personalização de convites de reunião e novas opções de reunião.

  - Os administradores podem personalizar os convites de reunião da organização adicionando um logotipo personalizado, uma URL de suporte, uma URL do aviso de isenção legal ou um texto de rodapé personalizado. Para obter detalhes, consulte [Personalizando o suplemento Online Meeting no Lync Server 2013](lync-server-2013-customizing-the-online-meeting-add-in.md).

  - Os novos controles de ativação de opção Mudo para participantes permitem que os organizadores de reuniões agendem conferências ativando por padrão o opção Mudo para o áudio e o vídeo dos participantes.

## Plug-in de Virtual Desktop Infrastructure

O cliente do Lync 2013 agora oferece suporte a áudio e vídeo em um ambiente VDI (Virtual Desktop Infrastructure). Um usuário pode conectar um dispositivo de áudio ou vídeo (por exemplo, um fone de ouvido ou uma câmera) ao computador local (por exemplo, um computador cliente fino ou realocado). O usuário pode conectar-se à máquina virtual, entrar no cliente do Lync 2013 em execução nessa máquina e participar da comunicação por áudio e vídeo em tempo real como se o cliente estivesse em execução localmente. Os recursos a seguir têm suporte em um ambiente de área de trabalho virtual:

  - Integração de dispositivos de áudio e vídeo, incluindo:
    
      - Controles de chamada do dispositivo
    
      - Integração de presença no dispositivo
    
      - Suporte á vários HIDs (dispositivos de interface humana)

  - Suporte a serviços de local e emergência.

  - Suporte a todas as modalidades do Lync, incluindo IM (mensagens instantâneas), áudio, vídeo, compartilhamento de aplicativos, compartilhamento de área de trabalho, compartilhamento do PowerPoint, quadro de comunicações e transferência de arquivos.

  - Suporte a áudio e vídeo em chamadas entre duas pessoas e chamadas em conferência.

Para obter informações sobre a implantação do plug-in de VDI, consulte [Implantando o plug-in Lync VDI no Lync Server 2013](lync-server-2013-deploying-the-lync-vdi-plug-in.md).

## Melhorias de vídeo

Vários novos recursos melhoram consideravelmente a experiência de vídeo dos participantes de conferências.

  - O vídeo foi aprimorado com detecção facial e enquadramento inteligente para que o vídeo do participante se desloque para mantê-lo centralizado no quadro.

  - Agora há suporte a vídeo de alta definição em chamadas entre duas pessoas e conferências com vários participantes. Os usuários podem visualizar resoluções de até 1080P HD.

  - Os participantes podem selecionar entre vários layouts de reunião: o Modo de Exibição de Galeria mostra as fotos e os vídeos de todos os participantes; o Modo de Exibição do Orador mostra o conteúdo da reunião e apenas a foto e o vídeo do orador atual; o Modo de Exibição de Apresentação mostra somente o conteúdo da reunião; e o Modo de Exibição Compacto mostra somente os controles da reunião.

  - Com o novo recurso de Galeria, os participantes podem ver várias transmissões de vídeo ao mesmo tempo. Se houver mais de cinco participantes na conferência, as transmissões de vídeo somente dos participantes mais ativos aparecerão na linha superior e as fotos dos outros participantes serão exibidas.

  - Os participantes podem usar o recurso de fixar vídeo para selecionar uma ou mais das transmissões de vídeo disponíveis para que fiquem sempre visíveis.

  - Os apresentadores podem usar o recurso Destaque de Vídeo para selecionar o vídeo de uma pessoa para que todos os participantes da reunião vejam somente esse participante.

## Integração da sala de chat

O Lync 2013 agora integra os recursos anteriormente disponíveis no Chat de Grupo do Lync 2010. Não há mais necessidade de um cliente de chat em grupo separado.

  - A partir do Lync 2013, os usuários podem pesquisar salas de chat, adicionar salas a seus contatos, monitorar a atividade de salas e ler e postar mensagens.

  - Os usuários podem criar feeds de tópicos para serem notificados se algum participante de uma de suas salas de chat adicionar uma postagem que contenha palavras-chave específicas.

  - Com a nova página de opções **Chat Persistente**, os usuários podem definir sons e alertas de notificação que são acionados quando alguém posta mensagens em suas salas de chat.

## Atualizações do Lync Web App

O Lync Web App é o cliente de conferências baseado na Web para reuniões do Lync Server 2013. Nesta versão, a inclusão do áudio e do vídeo do computador ao Lync Web App proporciona uma experiência de reunião completa para aqueles que não possuem um cliente do Lync instalado localmente. Os participantes da reunião têm acesso a todos os recursos de colaboração e compartilhamento e controles de reunião de apresentador.

Quando um usuário tenta ingressar em uma reunião, mas não tem um cliente instalado localmente, o Lync Web App é aberto. Para permitir opções adicionais de ingresso na reunião, você pode configurar a página Ingresso na Reunião. Consulte [Configurando a página de ingresso na reunião no Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md) na documentação de implantação.

Por conta das melhorias realizadas no Lync Web App, não há uma versão atualizada do Participante disponível para o Lync Server 2013. O Lync Web App é o cliente destinado a participantes de fora da sua organização. Não é necessária a instalação local de um cliente, mas recursos de áudio, vídeo e compartilhamento exigem que um plug-in seja instalado na primeira utilização.

## Lync 2013 para Atualizações de clientes móveis

Além das funcionalidades da presença avançada, contatos e IM, agora, os clientes móveis do Lync 2013 fornecem chamadas com voz e com vídeo pela Internet e conexões de dados para celular. Com um único toque no link da reunião em um item do calendário, os usuários móveis podem ingressar em reuniões com voz e vídeo. Para obter mais informações sobre os clientes móveis do Lync 2013, consulte [Planejamento para clientes móveis no Lync Server 2013](lync-server-2013-planning-for-mobile-clients.md).

## Atualizações da interface do usuário do Lync 2013

## Atualizações de acessibilidade

O Lync 2013 incorpora vários novos recursos de acessibilidade.

  - O Lync 2013 oferece suporte a alta resolução de DPI, permitindo que os usuários ampliem o texto e os gráficos para os valores de pontos por polegada de 125% e 150%.

  - O Lync oferece suporte a alto contraste para que a interface do usuário continue totalmente funcional quando usada com temas de alto contraste no Windows.

  - O Lync oferece mais de 100 atalhos de teclado para que os usuários possam acessar funções importantes sem o uso do mouse. Por exemplo, eles podem pressionar Alt+C para aceitar uma chamada ou Alt+I para ignorá-la sem precisar alternar ou definir o foco. A combinação de teclas Alt+Q encerra uma chamada, Ctrl+N inicia o OneNote e Alt+T abre o menu Ferramentas.

  - O amplo suporte a leitor de tela no Lync 2013 garante que todas as notificações, solicitações de entrada e mensagens instantâneas sejam lidas em voz alta quando há um leitor de tela habilitado.

## Presença durante o compartilhamento

Quando o Lync detecta que um usuário está compartilhando conteúdo, o Lync automaticamente atribui ao usuário o status de presença Apresentando. Esse status bloqueia todas as comunicações de entrada, a menos que a relação de privacidade Grupo de Trabalho tenha sido atribuída ao remetente. Se o usuário estiver usando o recurso de compartilhamento apenas em um monitor secundário, o Lync não atribuirá o status de presença Apresentando.

## Atualizações da janela Conversa

A janela Conversa reformulada oferece acesso mais rápido a recursos importantes.

  - Com o novo recurso de conversas com guias, os usuários agora podem manter todas as suas IMs e salas de chat em uma única janela Conversa. As guias na lateral esquerda da janela Conversa permite que os usuários naveguem facilmente entre todas as conversas ativas.

  - Os usuários podem destacar uma conversa individual em uma janela separada e redimensioná-la. Além disso, também podem reinserir a janela na janela Conversa principal.

  - O Lync 2013 reabre as conversas de um usuário quando ele sai e entra novamente no Lync.

  - Os usuários podem rapidamente adicionar a qualquer conversa ferramentas de IM, vídeo, compartilhamento de programas, compartilhamento de área de trabalho ou webconferência (quadro de comunicações, notas de reunião, blocos de anotações compartilhados e anexos).

  - Em uma reunião em que vídeo ou conteúdo está sendo compartilhado, os usuários podem destacar o vídeo da reunião ou o conteúdo compartilhado em uma janela separada e redimensioná-la.

## Atualizações da janela principal do Lync

A nova aparência simplificada mantém recursos conhecidos, como o campo de notas **O que está acontecendo hoje?**, o seletor de status e o seletor **Defina o local**.

  - Quando as salas de chat estão habilitadas, os usuários veem um novo ícone **Salas de Chat** na página principal do Lync. Com o ícone **Salas de Chat**, eles podem rapidamente acessar suas salas de chat e filtros.

  - Os usuários podem clicar nos ícones de modo de exibição para alternar entre os modos **Contatos**, **Salas de Chat**, **Conversas** ou **Telefone**.

  - Se os usuários tiverem migrado para o Exchange 2013, poderão carregar uma foto de alta resolução.

## Atualizações do modo de exibição Contatos e do Cartão de Visita

O Lync 2013 oferece aos usuários várias maneiras de exibir contatos e grupos no modo de exibição **Contatos**.

  - Com o novo repositório unificado de contatos, depois que os contatos do Lync dos usuários forem migrados para o Exchange 2013, os usuários poderão acessar e gerenciá-los a partir do Lync 2013, do Outlook ou do Outlook Web App e seus Favoritos permanecerão sincronizados. Por exemplo, se um usuário adicionar um contato aos Favoritos no Outlook, esse contato também aparecerá no grupo Favoritos do Lync 2013.

  - Se você tiver adicionado e configurado o proxy XMPP e o gateway XMPP, os usuários poderão adicionar contatos de parceiros XMPP para mensagens instantâneas e presença.

  - O novo recurso **Adicionar um contato que não é da minha organização** oferece aos usuários uma maneira fácil de adicionar pessoas de fora da organização.

  - O novo grupo **Favoritos** permite que os usuários criem uma lista de pessoas que contatam com mais frequência para agilizar o acesso.

  - Os usuários podem usar a nova página de opções **Lista de Contatos** para escolher como desejam classificar e exibir os contatos. Eles podem selecionar um modo de exibição expandido de duas linhas, que mostra as fotos dos contatos, ou um modo de exibição compacto de uma única linha. Os usuários também podem classificar os contatos por ordem alfabética ou por disponibilidade.

## Atualizações de conferências

O Lync 2013 traz várias melhorias para os recursos de conferência.

  - Dependendo do tipo de reunião, os usuários agora podem ativar o opção Mudo para os participantes e permitir ou bloquear o compartilhamento de vídeo ao agendarem a reunião. Essas opções estão disponíveis na página **Opções de Reunião** e são recomendadas para reuniões grandes com mais de 20 participantes.

  - Controles de áudio fáceis de usar na sala de reunião permitem que o usuário controle as opções de áudio, como ativar mudo, desativar mudo, alterar dispositivo etc.

  - Ao compartilhar programas, os usuários podem selecionar vários programas para compartilhamento se precisarem trabalhar com mais de um ao mesmo tempo.

  - Os usuários agora podem carregar apresentações que contêm clipes de vídeo carregando o arquivo do PowerPoint e apontando o mouse sobre o slide para exibir os controles de vídeo, como reproduzir e pausar, bem como os controles de áudio.

  - Durante uma reunião, os usuários podem incorporar outra conversa aberta à reunião usando o comando **Mesclar esta Conversa em** no menu **Mais Opções** ( **…** ).

  - Para ver os nomes dos participantes, os usuários podem passar o mouse sobre o botão **Exibir Participantes** ou clicar em **Mostrar Lista de Participantes** para encaixar o painel na reunião.

  - Dependendo do tipo de reunião, os usuários podem selecionar entre vários modos de exibição de participantes e conteúdo.

  - As gravações de reuniões são automaticamente salvas em um formato que pode ser reproduzido no Windows Media Player (MP4). Os usuários podem facilmente compartilhar o arquivo com qualquer pessoa ou usar o recurso **Publicar** do gerenciador de gravações para postar a gravação em um local compartilhado.

  - O OneNote permite novas maneiras de colaborar em uma reunião. Durante uma reunião, os usuários podem fazer anotações com o OneNote para uso pessoal após a reunião ou usar os blocos de anotações compartilhados e realizar edições em conjunto com os participantes da reunião em tempo real. Todos os membros da equipe podem acessar as anotações compartilhadas para contribuir com informações, desenvolver ideias ou usar as páginas do bloco de anotações como um quadro de comunicações virtual. As pessoas e o conteúdo compartilhado na reunião são automaticamente adicionados às anotações.

  - Os usuários podem alternar entre os tipos de conteúdo usando a opção **Compartilhar conteúdo e liderar atividades da reunião** na parte inferior da sala de reunião. Eles também podem usar o menu **Gerenciar Conteúdo Apresentável** para escolher qual conteúdo desejam compartilhar.

## Consulte Também

#### Outros Recursos

[Planejamento para clientes no Lync Server 2013](lync-server-2013-planning-for-clients.md)

