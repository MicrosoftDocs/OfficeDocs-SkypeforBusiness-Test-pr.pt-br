---
title: 'Lync Server 2013: Visão geral de Estacionamento de Chamada'
TOCTitle: Visão geral de Estacionamento de Chamada
ms:assetid: 985dc326-0aef-4308-b98b-c1d0069311e7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205124(v=OCS.15)
ms:contentKeyID: 49307549
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de Estacionamento de Chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

O Lync Server 2013Aplicativo de Estacionamento de Chamada permite aos usuários do Enterprise Voice:

  - Colocar uma chamada em espera e recuperá-la no mesmo telefone ou em outro.

  - Colocar uma chamada em espera para transferi-la para um departamento ou área geral, por exemplo, um departamento de vendas ou um depósito onde há um telefone de área comum.

  - Colocar uma chamada em espera e manter o telefone original livre para outras chamadas.

Quando um usuário estaciona uma chamada, o Lync Server transfere a chamada para um número temporário, chamado uma *órbita* , onde a chamada é mantida até que seja recuperada ou que expire. O Lync Server envia a órbita ao usuário que estacionou a chamada. Para recuperar a chamada estacionada, o usuário pode discar o número de órbita ou clicar no link de órbita ou na janela de Conversação.

O usuário que estacionou uma chamada pode notificar alguém para recuperar a chamada usando um mecanismo externo, como mensagens instantâneas ou um sistema de paginação, para comunicar o número de órbita para outra pessoa. O usuário que estacionou a chamada pode deixar a janela de Conversação aberta para receber notificações quando a chamada for recuperada.

Como os âmbitos de órbita são globalmente exclusivas, é possível recuperar chamadas de qualquer site do Lync Server ou telefone PBX, se o roteamento estiver configurado apropriadamente. Se ninguém recuperar a chamada dentro do tempo configurável, a chamada tocará novamente para a pessoa que a estacionou. Se essa pessoa não atender, a chamada será transferida para um destino de fallback, como um operador, se estiver configurado assim. Você pode configurar o número de vezes que a chamada toca antes de ser transferida, entre uma a dez vezes. Se ninguém atender a chamada transferida, ela será desconectada. A órbita é liberada quando a chamada é recebida ou desconectada.

Quando você implanta o Estacionamento de Chamada, precisa reservar intervalos de números de extensão para estacionar as chamadas. Essas extensões precisam ser extensões virtuais: extensões que não têm nenhum usuário ou telefone atribuído. Você configura a tabela de órbitas do estacionamento de chamada com os intervalos de números de extensões e especifica qual serviço de Aplicativo hospeda o aplicativo de Estacionamento de Chamada que trata cada intervalo. Cada pool de Front-End tem uma tabela de Estacionamento de Chamada no Servidor Back-End correspondente, que é usada para gerenciar as chamadas estacionadas no pool. A lista de intervalos de órbita é armazenada no Repositório de Gerenciamento Central e é usada para rotear a órbitas para o pool de destino. Cada pool do Lync Server onde o aplicativo Estacionamento de Chamada é implantado e configurado pode ter um ou mais intervalos de órbitas. Os intervalos de órbitas devem ser exclusivos na implantação do Lync Server.

Você também define outras configurações de Estacionamento de Chamada, como para onde as chamadas são redirecionadas quando atingem o tempo limite e se a pessoa ao telefone ouve música enquanto aguarda. Você também pode especificar o arquivo de música a ser reproduzido enquanto a chamada está em espera.

> [!NOTE]  
> Arquivos de música de espera personalizados do Estacionamento de Chamada não são gravados com o backup como parte do processo de recuperação de desastres do Lync Server 2013 e serão perdidos, caso os arquivos que foram enviados ao pool forem danificados, corrompidos ou apagados. Sempre mantenha uma cópia de backup separada dos arquivos de música de espera personalizados que você tenha enviado ao Estacionamento de Chamada.

O aplicativo Estacionamento de Chamada é um componente do Enterprise Voice. Ao implantar o Enterprise Voice, o aplicativo Estacionamento de Chamada é instalado e ativado automaticamente. Antes de usar o Estacionamento de Chamada, o administrador do Enterprise Voice deve configurá-lo e ativá-lo para os usuários por meio da política de voz.

