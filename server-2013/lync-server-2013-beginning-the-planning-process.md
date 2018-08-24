---
title: 'Lync Server 2013: Iniciando o processo de planejamento'
TOCTitle: Iniciando o processo de planejamento
ms:assetid: df3722b3-f859-49e1-b3ff-ee6863483731
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398986(v=OCS.15)
ms:contentKeyID: 49308340
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Iniciando o processo de planejamento para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Como o planejamento de uma implantação de comunicação unificada pode ser um pouco intimidador, o  Lync Server oferece duas ferramentas valiosas para ajudar você:

  - **O Ferramenta de Planejamento** é um assistente que apresenta uma série de perguntas sobre sua organização, os recursos do Lync Server que você deseja habilitar e suas necessidades de planejamento de capacidade. Cria uma topologia de implantação recomendada com base nas suas respostas e produz um diagrama do Microsoft Visio desta implantação.

  - **Construtor de Topologias** é um componente de instalação do Lync Server. É possível usar o Construtor de Topologias para criar, ajustar e publicar sua topologia planejada. Ele também valida sua topologia antes de começar as instalações do servidor. Quando você instala o Lync Server em servidores individuais, os servidores leem a topologia publicada como parte do processo de instalação e o programa de instalação implanta o servidor conforme direcionado na topologia.

## Ferramenta de planejamento do Lync Server

O Ferramenta de Planejamento usa suas respostas para as perguntas na ferramenta e gera uma topologia baseada em diretrizes e melhores práticas do Lync Server. Também fornece diversas exibições de uma implantação com base em suas respostas. Ele mostra uma exibição global de todos os seus sites (ou seja, incluindo sites centrais e sites filiais) e as exibições detalhadas mostrando os servidores e outros componentes em cada site.

A execução do Ferramenta de Planejamento não o prende a nenhuma implantação específica ou inicia qualquer processo. Na verdade, a execução do Ferramenta de Planejamento mesmo antes de você ter um plano sólido em mente pode ser uma forma bastante instrutiva de entender os tipos de perguntas nas quais você precisa pensar em seu processo de planejamento.

É possível executar o Ferramenta de Planejamento diversas vezes, respondendo a perguntas de forma diferente, e comparar os resultados. Se você tiver um design com o qual esteja quase satisfeito, mas precisar fazer alterações, poderá retornar ao Ferramenta de Planejamento, carregar o design e fazer as alterações. Demora cerca de 15 minutos para completar o Ferramenta de Planejamento uma vez.

Após estar satisfeito, é possível usar o Ferramenta de Planejamento para criar um diagrama da sua implantação planejada. É possível usar este diagrama enquanto cria a implantação no Construtor de Topologias.

> [!NOTE]  
> A Ferramenta de Planejamento incluída com esta versão do Lync Server 2013 é uma versão de pré-lançamento. Observe que os números do planejamento de capacidade na Ferramenta de Planejamento são preliminares e não são suportados pela versão final.

## Construtor de Topologia do Lync Server

Ao decidir seu plano de implantação, você usa o Construtor de Topologias para começar a implantar. Ao finalizar, você usa o Construtor de Topologias para validar a topologia e, se aprovada, é possível publicá-la. Ao publicar a topologia, o Lync Server a coloca no Repositório de Gerenciamento Central, que é criado neste momento se já não existir. Ao instalar o Lync Server em cada servidor da sua implantação, o servidor lê a topologia do Repositório de Gerenciamento Central e instala sozinho para se encaixar em sua função na implantação.

Como alternativa, se você estiver familiarizado com o Lync Server e precisar de menos orientação prescritiva, ignore o Ferramenta de Planejamento e use os assistentes no Construtor de Topologias para o design inicial de sua implantação e também para as etapas de validação e publicação.

O uso do Construtor de Topologias para planejar e publicar uma topologia é uma etapa necessária. Não é possível ignorar o Construtor de Topologias e instalar o Lync Server individualmente nos servidores em sua implantação. Cada servidor precisa ler a topologia a partir de uma topologia validada e publicada no Repositório de Gerenciamento Central.

## Processo de planejamento de alto nível

Recomendamos o seguinte processo geral para usar a documentação e o Ferramenta de Planejamentopara planejar sua implantação do Lync Server.

1.  Se você está familiarizado com as versões anteriores do Lync Server, leia o [Novos recursos no Lync Server 2013](lync-server-2013-new-features.md) para se familiarizar com os novos recursos e requisitos no Lync Server 2013.

2.  Leia os outros tópicos nesta seção de documentação: [Conhecimentos básicos de topologia para planejamento do Lync Server 2013](lync-server-2013-topology-basics-you-must-know-before-planning.md), [Topologias de referência no Lync Server 2013](lync-server-2013-reference-topologies.md), [Decisões de planejamento inicial para Lync Server 2013](lync-server-2013-initial-planning-decisions.md) e [Clientes para Lync Server 2013](lync-server-2013-clients.md). Observe as decisões de planejamento representadas no [Topologias de referência no Lync Server 2013](lync-server-2013-reference-topologies.md).

3.  Agora que você está mais familiarizado com os recursos do Lync Server e os tipos de perguntas que devem ser respondidas, execute o Ferramenta de Planejamento e veja a topologia resultante e seus detalhes. Certifique-se de que a topologia esteja adequada para os requisitos exclusivos da sua organização.

4.  Se houver cargas de trabalho ou recursos específicos nos quais você esteja interessado ou que precise saber, leia as seções apropriadas do [Planejamento para Lync Server 2013](lync-server-2013-planning.md).

5.  Execute o Ferramenta de Planejamento novamente. É possível iniciar com a implantação criada na etapa 3 e modificar os resultados ou começar desde o início.
    
    Se for necessário, execute o Ferramenta de Planejamento pela terceira vez e repita até que esteja satisfeito com o resultado.

6.  Ao finalizar o plano de topologia, use o Ferramenta de Planejamento para criar e imprimir um diagrama do Visio da sua topologia. É possível usar este diagrama durante o trabalho com o Construtor de Topologias para inserir sua topologia.

7.  Antes de começar a implantar, leia [Determinando seus requisitos de sistema para Lync Server 2013](lync-server-2013-determining-your-system-requirements.md) e [Determinando seus requisitos de infraestrutura para Lync Server 2013](lync-server-2013-determining-your-infrastructure-requirements.md) para se familiarizar com os pré-requisitos e infraestrutura necessária para Lync Server. Além disso, certifique-se de que leu todas as seções do [Planejamento para Lync Server 2013](lync-server-2013-planning.md) que se aplicam às cargas de trabalho e aos recursos que você planeja implantar.

## Migrando de versões anteriores

Se você estiver migrando para o Lync Server a partir de uma versão anterior, consulte a documentação [Migração](migration.md) para obter instruções específicas à sua migração e implantação.

