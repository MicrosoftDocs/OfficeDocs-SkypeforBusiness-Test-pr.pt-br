---
title: Funções de Usuário no Servidor de Chat Persistente
TOCTitle: Funções de Usuário no Servidor de Chat Persistente
ms:assetid: 343a0563-9ca5-4ad0-b4f3-a72f1d7f1a81
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ676774(v=OCS.15)
ms:contentKeyID: 49886172
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Funções de Usuário no Servidor de Chat Persistente

 

_**Tópico modificado em:** 2015-03-19_

O Servidor de Chat Persistente fornece o conceito de membros permitidos/negados que se aplica a categorias de Chat Persistente e controla quem pode acessar as salas de uma categoria particular.

> [!IMPORTANT]  
> Membros permitidos/negados em uma categoria não é o mesmo que uma função de <strong>Membro</strong>, que se aplica a uma sala de Chat Persistente.<br />As pesquisas exibem todas as salas de chat abertas e fechadas das quais o usuário que fez a pesquisa está na lista de membros permitidos/negados. Salas secretas não são exibidas a menos que o usuário que fez a pesquisa seja membro de uma delas. O usuário pode pesquisar apenas as salas das quais ele já é membro ou às quais ele pode solicitar associação.

A lógica principal do conceito de membros permitidos/negados sem baseia em paredes éticas. Por exemplo, é comum que instituições bancárias e financeiras tenham limites éticos que impeçam que comerciantes e analistas compartilhem comunicações enquanto implementam políticas e convenções. Para tratar desse requisito, um administrador pode criar categorias de modo que uma categoria permita que salas sejam criadas e usadas por comerciantes e a outra categoria, por analistas. Com isso, uma restrição é projetada no sistema proibindo a adição de um usuário como membro de uma sala se a categoria pai impedir isso.

A seguir, são exibidas os quatro Servidor de Chat Persistente de funções de usuário:

  - **Criador:** usuários que têm permissão para criar salas de chat. Esses usuários estão na lista Criadores de certas categorias: eles podem criar salas de chat nessa categoria e podem também atribuir associações de acordo com a categoria e atribuir gerentes para que administrem a sala de chat. O usuário que cria uma sala de chat é automaticamente adicionado como gerente da sala.
    
    > [!NOTE]  
    > A função de criador simplesmente concede direitos de criação de salas de chat. É a promoção automática a gerente que permite que o criador refine melhor as associações, os gerentes e assim por diante nos serviços de chat criados.    
    Esta função existe para lhe dar a opção de controlar quem cria salas de chat em sua organização, particularmente se quiser gerenciar centralmente a criação de salas de chat para impor políticas e convenções e, subsequentemente, delegar o gerenciamento das salas de chat a outros usuários na organização.

  - **Gerente:** usuários que gerenciam as propriedades de uma sala de chat. Os gerentes de sala de chat podem modificar a lista de membros (adicionar ou remover membros) e modificar a lista de gerentes da sala de chat (adicionar ou remover gerentes). Os gerentes de sala de chat podem adicionar a si próprios à lista de membros ou de apresentadores (para salas de auditório) para que possam participar da sala de chat. Os gerentes de sala de chat também podem desabilitar as salas de chat (os administradores podem consultar as salas de chat desabilitadas e exclui-las permanentemente). Os gerentes podem alterar todas as propriedades de uma sala de chat, à exceção da respectiva categoria. Apenas o administrador do Chat Persistente pode alterar a categoria depois de a sala de chat ter sido criada.
    
    > [!IMPORTANT]  
    > Se o gerente for também o criador em outra categoria, ele poderá alterar a categoria para uma em que ele esteja autorizado a criar salas.

  - **Membro:** usuários que são membros de uma sala de chat. Esses usuários podem ver as salas de chat no diretório (mesmo que a sala seja secreta), bem como inscrever-se na sala de chat (inclusive opções de metadados, como mensagens não lidas, filtros ego e filtros por palavra-chave) e participar da sala de chat (podem postar, a menos que seja uma sala de auditório, na qual apenas os apresentadores podem postar, e podem também obter conteúdo e pesquisar). Os usuários que não são membros da sala de chat poderão pesquisar a sala se estiverem na lista de membros permitidos da categoria, mas precisarão solicitar acesso para participar da sala de chat e acessar o conteúdo (não há como solicitar acesso ou aprovações no sistema; isso é feito externamente por email, telefone ou outras formas de contato).

  - **Apresentador:** usuários que podem postar em uma sala de auditório.

As seguintes funções são de administrador do Servidor de Chat Persistente:

  - Administrador do **Chat Persistente (CsPersistentChatAdministrator):** esta é uma nova função de RBAC (controle de acesso baseado em função) para administração e gerenciamento do Servidor de Chat Persistente. Usuários ou grupos de segurança designados como CsPersistentChatAdministrator podem administrar o Servidor de Chat Persistente usando os cmdlets Windows PowerShell remotamente (isto é, de um computador diferente do Servidor de Chat Persistente). O Servidor de Chat Persistente verifica se o administrador do Chat Persistente é membro do grupo local RTC Local Administrators no Servidor de Chat PersistenteServidor Front-End.
    
    A função CsPersistentChatAdministrator permite gerenciar salas de chat (modificar todas as propriedades, inclusive associações, gerentes, categorias, marcar salas como desabilitadas), bem como criar e gerenciar categorias de sala de chat que definem quem pode criar e acessar as salas de chat. Os administradores também podem marcar salas de chat como desabilitadas e limpar salas de chat que não estão mais ativas. Os administradores não estão sujeitos às restrições dos criadores ou membros permitidos. Eles podem criar qualquer tipo de sala de chat e adicionar a si próprios como membros de qualquer sala. Eles também podem modificar e gerenciar a implantação do Chat PersistenteServidor de Chat de Grupo para Lync Server 2013Servidor de Chat Persistente.

  - **Administrador do Lync:** administrador empresarial global do Lync Server 2013, responsável pela implantação.

  - **Gerente de operações:** usuário responsável por gerenciar as operações diárias.

  - **Desenvolvedores e parceiros terceirizados:** os desenvolvedores terceirizados ampliam o sistema, fornecendo especialmente uma solução de parede ética para conversas em grupo, suporte e ferramentas de conformidade, clientes móveis/da Web e uma estrutura de desenvolvimento de bot.

