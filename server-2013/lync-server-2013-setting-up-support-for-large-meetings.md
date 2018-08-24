---
title: Configurar suporte para grandes reuniões
TOCTitle: Configurar suporte para grandes reuniões
ms:assetid: 8e22d34b-b395-408d-9d48-8f2a3abe9513
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205074(v=OCS.15)
ms:contentKeyID: 49307407
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar suporte para grandes reuniões

 

_**Tópico modificado em:** 2014-05-12_

Suportar reuniões grandes de até 1.000 usuários exige criar uma topologia apropriada, atender a pré-requisitos de hardware e software e configurar o ambiente apropriadamente.

## Requisitos de topologia

Uma grande reunião exige pelo menos um Servidor Front-End e um Servidor Back-End. No entanto, para fornecer alta disponibilidade, recomendamos dois pools Servidor Front-End com Servidores Back-End espelhado.

O usuário que hospeda as grandes reuniões deve ter sua conta de usuário hospedada nesse pool. No entanto, não recomendamos que você hospede outras contas de usuário nesse pool. Em vez disso, use-o apenas para reuniões grandes. A prática recomendada é criar uma conta de usuário especial nesse pool para ser usada apenas para hospedar reuniões grandes. Já que a definição de grandes reuniões é otimizada para um melhor desempenho, usá-la como usuário normal poderia gerar problemas como incapacidade de promover uma sessão de P2P em uma reunião quando um ponto de extremidade de PSTN estiver envolvido.

Gerenciar um pool com exatamente dois servidores front-end exige algumas considerações especiais. Para obter mais informações, consulte [Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença no Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).

Além disso, se você desejar oferecer failover e backup de recuperação de desastres para o pool usado em grandes reuniões, poderá emparelhar com um pool dedicado de configuração semelhante em outro datacenter. Para mais detalhes, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

![Configuração do pool de reuniões grandes](images/JJ205074.ee00e1c0-c3b2-464d-aa89-a1e877cd034d(OCS.15).jpg "Configuração do pool de reuniões grandes")

As notas adicionais sobre a topologia incluem:

  - Um compartilhamento de arquivo é necessário para armazenar conteúdo da reunião e, se o Servidor de Arquivamento estiver implantado e ativado, armazenar os arquivos de arquivo. O compartilhamento de arquivo pode ser dedicado ao pool ou pode ser o mesmo compartilhamento de arquivo usado por outro pool no site no qual o pool é implantado. Para obter detalhes sobre a configuração do compartilhamento de arquivo, consulte [Configurar armazenamento de arquivo para Lync Server 2013](lync-server-2013-configure-dfs-file-storage.md)

  - Um Servidor Office Web Apps é necessário para habilitar a função de apresentação do PowerPoint em grandes reuniões. O Servidor Office Web Apps pode ser dedicado ao pool de grande reunião ou pode ser o mesmo Servidor Office Web Apps usado por outros pools no site no qual o pool dedicado está implantado.

  - O balanceamento de carga dos Servidores Front-End exige balanceamento de carga de hardware para o tráfego HTTP (como download de conteúdo de reunião). O balanceamento de carga DNS é recomendado para tráfego SIP. Para obter detalhes, consulte [Requisitos de balanceamento de carga para Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

  - Se desejar usar o Servidor de Monitoramento para o pool dedicado à grande reunião, recomendamos usar o Servidor de Monitoramento e seu banco de dados que são compartilhados por todos os pools de Servidor Front-End em sua implantação do Lync Server.

## Requisitos de hardware e software

Os requisitos de hardware para servidores em um pool dedicado a grandes reuniões são os mesmos dos outros servidores do Lync Server 2013. Para obter detalhes sobre requisitos de hardware, consulte "[Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

Servidores em um pool dedicado a grandes reuniões devem atender aos requisitos de software do Lync Server 2013. Para obter detalhes sobre requisitos de software, consulte a seguinte documentação:

  - [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md)

  - [Suporte a software de banco de dados no Lync Server 2013](lync-server-2013-database-software-support.md)

  - [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md)

Além disso, tanto o Lync Server 2013 quanto todos os clientes Lync Server 2013 devem ter as atualizações mais recentes.

## Requisitos de configuração

Recomendamos criar uma nova política de conferência específica para grandes reuniões, e depois atribuir a política de conferência aos usuários que estão hospedados no pool dedicado a grandes reuniões. Configure a política de conferência usando as seguintes configurações:

  - Defina a opção **MaxMeetingSize** para **1000**. (O padrão é **250**.)

  - Defina a opção **AllowLargeMeetings** para **Verdadeiro**.

  - Defina a opção **EnableAppDesktopSharing** para **Nenhum**.

  - Defina a opção **AllowUserToScheduleMeetingsWithAppSharing** para **Falso**.

  - Defina a opção **AllowSharedNotes** para **Falso**.

  - Defina a opção **AllowAnnotations** para **Falso**.

  - Defina a opção **DisablePowerPointAnnotations** para **Verdadeiro**.

  - Defina a opção **AllowMultiview** para **Falso**.

  - Defina a opção **EnableMultiviewJoin** para **Falso**.

> [!NOTE]  
> O suporte para grandes reuniões de 1.000 usuários no Lync Server 2013 exige a configuração <strong>AllowLargeMeetings</strong> na política de conferência para que o programador de encontro seja definido como verdadeiro. Quando essa configuração é definida como verdadeira, a experiência do Lync será otimizada para reuniões muito grandes quando os usuários ingressarem em tal reunião. Especificamente, em uma grande reunião, o Lync não mostrará a lista de participantes inicial ou atualizará a lista total de participantes da reunião, que é um gargalo de desempenho para o cliente e o Lync Server 2013. Em vez disso, o Lync exibirá apenas as informações sobre o usuário e a lista de apresentadores da reunião. O Lync ainda exibirá corretamente o número total de participantes disponíveis nas grandes reuniões.

Exceto pela configuração **Tamanho máximo das reuniões**, todas as outras configurações de política de conferência especificadas aqui são obrigatórias para desativar as capacidades de conferência que não são necessárias em grandes reuniões.

Além disso, você precisa configurar o pool dedicado a grandes reuniões de forma que cada usuário do Lync Server 2013 que esteja hospedado no pool e seja responsável pelo gerenciamento da programação da reunião tenha as permissões apropriadas. Para tanto, siga estes passos:

  - Defina a opção **Designar como apresentador** para **Nenhum**. Normalmente, um ou apenas alguns usuários de todos os participantes em uma grande reunião são apresentadores, então os participantes não devem ser admitidos automaticamente em grandes reuniões como apresentadores. Em vez disso, os apresentadores devem ser designados explicitamente na hora da programação da reunião, ou serem promovidos explicitamente durante uma grande reunião.

  - Certifique-se de que a caixa de seleção **Tipo de conferência atribuído por padrão** não está selecionada. Essa configuração controla se o Suplemento de Reunião Online para Lync 2013 sempre programa conferências usando a conferência atribuída do organizador, o que significa que as reuniões agendadas têm sempre o mesmo URL de ingresso e informações de áudio. Em cenários de colaboração de pequenos grupos, ter tal tipo de conferência atribuído funciona bem, pois todos tem sua própria conferência atribuída individualmente e o URL de ingresso e informações de áudio constantes ajudam a facilitar um ingresso mais rápido à reunião. No entanto, em uma conferência de grande reunião, a equipe de suporte da grande reunião agenda essas reuniões usando um conjunto simples de credenciais de usuário, e depois fornecem URLs de ingresso de informações de áudio para os solicitantes. Neste caso, usar um URL diferente para ingressar em cada reunião funciona melhor.

  - Certifique-se de que a caixa de seleção **Admitir usuários anônimos por padrão** não esteja selecionada, a menos que seja obrigatória. Essa configuração afeta o tipo padrão de acesso à reunião agendado pelo Suplemento de Reunião Online para Lync 2013, quando uma conferência atribuída não é utilizada. A opção apropriada para essa configuração depende das necessidades da sua organização. Se a maioria das grandes reuniões da sua organização forem internas, não selecione esta opção. Se a maioria das grandes reuniões exigirem que usuários externos possam participar, selecione essa opção.

