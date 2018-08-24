---
title: 'Lync Server 2013: Novos recursos do Servidor de Chat Persistente'
TOCTitle: Novos recursos do Servidor de Chat Persistente
ms:assetid: c3ec6f33-6261-4bf5-aa31-baa8ab2a87d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412965(v=OCS.15)
ms:contentKeyID: 49308026
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novos recursos do Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013, Servidor de Chat Persistente permite você participar de uma conversa baseada em tópico entre várias partes que persiste com o tempo. O Servidor de Chat Persistente pode ajudar sua organização a fazer o seguinte:

  - Aprimorar a comunicação entre equipes geograficamente espalhadas e equipes multifuncionais

  - Ampliar a consciência sobre as informações e a participação

  - Aprimorar a comunicação com sua organização estendida

  - Reduzir a sobrecarga de informações

  - Aprimorar a consciência sobre as informações

  - Aumentar a dispersão de conhecimento e informações importantes

O Lync Server 2013, Servidor de Chat Persistente não está disponível no Microsoft Office 365. Neste momento, está disponível apenas para clientes do Lync 2013 locais.

No Lync 2013, a funcionalidade Chat Persistente está integrada no cliente do Lync 2013. Como resultado, os usuários têm acesso à Mensagem Instantânea/Presença, Áudio/Vídeo, Conferência e Chat Persistente todos no cliente do Lync 2013. Para obter mais informações sobre o cliente Lync 2013, consulte <http://go.microsoft.com/fwlink/p/?linkid=270877>.

Este tópico descreve as mudanças do recurso entre a nova versão do Lync Server 2013, Servidor de Chat Persistente e a versão anterior do ( Microsoft Lync Server 2010, Chat de Grupo), incluindo:

  - Oferece uma experiência administrativa no Painel de Controle do Lync Server e elimina o Ferramenta de Administração do Chat de Grupo

  - Integrar definições de configuração para o Servidor de Chat Persistente no Construtor de Topologia eliminando o Ferramenta de Configuração do Chat de Grupo

  - Migração fácil e atualização de versões anteriores do Servidor de Chat Persistente

  - Oferece soluções de alta disponibilidade e recuperação de desastres

Para obter detalhes adicionais sobre a versão mais atual do Servidor de Chat Persistente, consulte o seguinte:

  - A Ajuda do Chat Persistente em <http://go.microsoft.com/fwlink/p/?linkid=270945> que fornece uma lista detalhada dos recursos do Chat Persistente, como eles funcionam e como usá-los enquanto executa o Servidor de Chat Persistente.

  - O [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na documentação de Planejamento, o [Implantando Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md) na documentação de Implantação, o [Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md) na documentação de Migração e o [Gerenciar Lync Server 2013, Servidor de Chat Persistente](managing-lync-server-2013-persistent-chat-server.md) na documentação de Operações, todos oferecem instruções para configurar o Servidor de Chat Persistente.

  - O arquivo Documentation.msi do Servidor de Chat Persistente (arquivo do Windows Installer) permite acesso dos usuários completo à documentação offline sobre o Servidor de Chat Persistente.

## Principais mudanças de topologia do Servidor de Chat Persistente

As seguintes mudanças de alto nível do Servidor de Chat Persistente incluem:

O Servidor de Chat Persistente é agora uma função do servidor. No Microsoft Lync Server 2010, o Servidor de Chat de Grupo era um aplicativo confiável de terceiros para o Microsoft Lync Server 2010. O Chat Persistente pode ser adicionado à sua topologia do Lync Server 2013 usando o Construtor de Topologias. No Lync Server 2013, a funcionalidade do Servidor de Chat Persistente é implementada usando três novas funções do servidor:

  - **PersistentChatService :** Esta é a função de front-end para o Chat Persistente. Em implantações do Standard Edition, a Função de Serviço do Servidor de Chat Persistente é posicionada no servidor do Standard Edition implantado pelo Bootstrapper, assim como qualquer outra função do Lync Server. Nas implantações do Enterprise Edition, a Função de Serviço do Chat Persistente é implantada em computadores autônomos pelo Bootstrapper, como qualquer outra função do Lync Server.

  - **PersistentChatStore :** Servidor de Back-End que corresponde ao banco de dados de conteúdo do Chat Persistente, onde todo o conteúdo de bate-papo é armazenado.

  - **PersistentChatComplianceStore :** Função do Servidor de Back-End que corresponde ao banco de dados de Conformidade do Chat Persistente, onde todos os eventos de conformidade são armazenados.

Estas funções do Servidor de Chat Persistente são opcionais e são instaladas apenas por clientes que desejam uma funcionalidade do Servidor de Chat Persistente completa. A função do **PersistentChatComplianceStore** é necessária apenas se escolher implantar a Conformidade do Chat Persistente.

A função **PersistentChatService** executa dois serviços:

  - Serviço de Chat Persistente

  - Serviço de Conformidade do Chat Persistente

Ter estes dois serviços executando em cada Servidor de Chat Persistente oferece alta disponibilidade para estes serviços em um Pool de Servidor de Chat Persistente multiservidor.

Além disso, para suportar o upload e download de arquivos nas salas do Chat Persistente, o Servidor de Chat Persistente inclui um serviço da Web. Anteriormente, este serviço foi posicionado no Servidor de Chat Persistente, Servidor Front-End e exigi que o IIS (Serviços de Informações da Internet) seja instalado como um pré-requisito. No Lync Server 2013Servidor de Chat Persistente, o serviço da Web de Upload/Download é posicionado com o Lync Server 2013Servidor Front-End. Como efeito colateral, o IIS (Serviços de Informações da Internet) não é mais um pré-requisito para o Servidor de Chat Persistente. O serviço da Web de Upload/Download de arquivos é identificado como **PersistentChat** no Gerenciador do IIS (Serviços de Informações da Internet).

> [!IMPORTANT]  
> A função <strong>PersistentChatService</strong> pode ser executada no mesmo servidor que o Lync Server 2013Servidor Front-End apenas se este Servidor Front-End é um Standard EditionServidor Front-End. A função <strong>PersistentChatService</strong> não pode ser executada independente de um Lync Server 2013Servidor Front-End. Pode ser instalado apenas no contexto de uma implantação do Lync Server 2013.

No Servidor de Chat Persistente, o serviço de Pesquisa foi eliminado. No Lync Server 2010, Chat de Grupo, o serviço de Pesquisa é executado em cada Servidor de Chat de GrupoServidor Front-End e realizado um roteamento em um dos Servidores do Canal. O Lync Server 2013 confia no roteamento usando objetos de contato, onde cada Pool de Servidor de Chat Persistente é representado por um objeto de contato usado pelo Lync ServerServidores Front-End para identificar e direcionar solicitações para um Pool de Servidor de Chat Persistente adequado e para um dos computadores executando o Servidor de Chat Persistente no pool.

No Lync Server 2013, há modificações do serviço de Conformidade:

  - No Lync Server 2010, o serviço de Conformidade é executado de forma autônoma (não posicionado) e apenas em um único servidor. O serviço de Conformidade agora executa em todos os Servidor de Chat PersistenteServidores Front-End, junto com o serviço do Chat Persistente e portanto oferece alta disponibilidade em um Pool de Servidor de Chat Persistente multiservidor. Um único adaptador de conformidade pode ser configurado para extrair dados do banco de dados de conformidade e em um dos outros sistemas (arquivo XML, arquivos hospedados pelo Exchange e assim por diante). O Servidor de Chat Persistente inclui um adaptador XML.

  - A fila do Enfileiramento de Mensagem (também conhecida como MSMQ) compartilhada pelo serviço do Chat Persistente e o serviço de Conformidade em cada Servidor de Chat PersistenteServidor Front-End é agora uma fila privada compartilhada apenas pelos dois serviços. Todos os serviços de conformidade gravam no mesmo banco de dados de Back-End de Conformidade. Eles também leem do banco de dados, para fins de envio de dados para sua instância do adaptador. O Servidor de Back-End de Conformidade é representado como a nova função do Servidor de Back-End.
    
    > [!IMPORTANT]  
    > Como em versões anteriores, todos os dados de conformidade são processados no mesmo momento. Os dados podem ser processados por qualquer instância do adaptador invocada pelo serviço de conformidade executando em vários computadores do Lync Server 2013, Servidor de Chat Persistente. No Servidor de Chat Persistente, qualquer uma das instâncias do adaptador pode processar os dados.    
    > [!NOTE]  
    > Para obter informações sobre a instalação de Enfileiramento de Mensagem, consulte <a href="lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md">Instalar sistemas operacionais e software de pré-requisito nos servidores para Lync Server 2013</a> na documentação de Implementação.

No Lync Server 2013, há melhorias na alta disponibilidade e recuperação de desastres:

  - Melhorias de alta disponibilidade: O espelhamento do SQL Server é usado para oferecer alta disponibilidade para o banco de dados de conteúdo do Servidor de Chat Persistente e o banco de dados de conformidade do Chat Persistente dentro de um centro de dados (local).

  - Melhorias de recuperação de desastres: O Servidor de Chat Persistente suporta uma arquitetura de pool avançada permite que um único Pool de Servidor de Chat Persistente seja avançado entre dois locais (isto é, um único pool lógico na topologia com servidores no pool fisicamente localizados entre dois locais). Envio de Log do SQL Server é usado para recuperação de desastres entre locais.

Para obter mais informações sobre a alta disponibilidade e recuperação de desastres, consulte [Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md) na documentação de Implantação.

## Administração Principal e Mudanças de Gerenciamento para o Servidor de Chat Persistente

O Lync Server 2013 tornou mais fácil administrar e gerenciar o Servidor de Chat Persistente oferecendo:

  - Gerenciamento e administração unificada. O Lync Server 2013 torna mais fácil gerenciar e administrar o Servidor de Chat Persistente utilizando ferramentas já familiares para administradores do Lync. O Servidor de Chat Persistente inclui uma experiência da interface do usuário administrativa integrada com o Painel de Controle do Lync Server, que resolve problemas de desempenho com versões anteriores da interface do usuário do Servidor de Chat de Grupo. Além disso, o Servidor de Chat Persistente inclui um conjunto de cmdlets do Windows PowerShell para administrar e gerenciar categorias do Servidor de Chat Persistente, salas do Servidor de Chat Persistente (incluindo a exclusão de salas e exclusão de conteúdo obsoleto) e complementos.

  - Modelo de administração simplificado. O Lync Server 2013 alterou e simplificou o modelo do Servidor de Chat Persistente abordando os seguintes requisitos principais do cliente:
    
      - Remover hierarquias aninhadas complexas de escopos e categorias.
    
      - Suporte para definir as listas de negação, assim como as listas de permissão (escopo) para os clientes do MindAlign atuais planejando migrar para o Servidor de Chat Persistente.

## O que está diferente sobre as Funções do Usuário de versões anteriores do Servidor de Chat de Grupo?

O Lync Server 2010, Chat de Grupo tinha uma função do administrador do usuário, uma função do administrador da sala de bate-papo e uma função do administrador do Lync Server que pode gerenciar complementos. O Servidor de Chat Persistente apenas oferece uma função de Administrador do Chat Persistente (que é semelhante a outras funções RBAC do Lync Server). Qualquer pessoa que seja membro desta função RBAC pode gerenciar salas de bate-papo, complementos e categorias (e portanto, obter acesso do usuário para estas categorias) e configuração do Pool de Servidor de Chat Persistente.

## O que está diferente sobre as categorias de sala de bate-papo de versões anteriores do Servidor de Chat de Grupo?

As categorias de sala de bate-papo não podem mais ser aninhadas e a categoria raiz não pode mais ser modificada. AllowedMembers/DeniedMembers compreendem qual escopo usado para estar nas versões herdadas do Servidor de Chat de Grupo (exceto que não suporta a especificação de uma lista Negada). Os escopos não podem mais ser substituídos, porque não há categorias aninhadas. Um Administrador do Chat Persistente no Lync Server 2013 pode criar e gerenciar categorias de sala de bate-papo. Como parte da criação e gerenciamento de categorias de sala de bate-papo, um Administrador do Chat Persistente pode configurar diretores (grupos/recipientes/usuários do Active Directory) que tenham acesso para ser membros/criadores de salas de bate-papo de uma determinada categoria. Uma categoria do Chat Persistente também pode adicionar DeniedMembers a uma categoria e elas se tornam exclusões explícitas para a lista de permissões. O DeniedMembers substituem o que está em AllowedMembers.

## O que está diferente nas propriedades de sala de bate-papo de versões anteriores do Servidor de Chat de Grupo?

Um novo conceito de salas de bate-papo abertas existe no Lync Server 2013, Servidor de Chat Persistente. Todos os membros permitidos podem participar da sala de bate-papo, sem associação exclusiva.

As seguintes propriedades da sala de bate-papo incluídas nas versões anteriores do Servidor de Chat Persistente foram eliminadas:

  - Tópico: Uma sala agora possui apenas uma Descrição.

  - Criar lista de Novo Membro: No Servidor de Chat Persistente, todas as salas de bate-papo começam com uma associação vazia (e pode maximizar para uma associação igual aos Membros Permitidos).

  - Upload de arquivos: Usado para ser uma configuração por sala de bate-papo para controlar se os upload/downloads de arquivos eram permitidos. Isto é agora definido apenas para o nível de categoria e aplica-se a todas as salas nesta categoria.

  - Histórico de bate-papo: Usado para ser uma configuração por sala de bate-papo para controlar se o Histórico de Bate-papo estava habilitado, mas agora é definido apenas no nível da categoria e aplica-se a todas as salas nesta categoria.

  - Convites: Uma sala sempre herda a configuração Convites para a categoria ou pode ser desativada na sala. Uma sala não pode ativar Convites se a categoria foi definida anteriormente para Convites desativado.

## O que está diferente sobre as políticas de versões anteriores do Servidor de Chat de Grupo?

O Servidor de Chat Persistente possui uma nova política do Lync habilitada com o Chat Persistente, configurações por usuário/pool/local/global. No cliente do Lync 2013, o ambiente do Chat Persistente está disponível apenas para usuários com a política habilitada para Chat Persistente (diretamente ou através da configuração de pool/local/global).

Versões anteriores do Servidor de Chat de Grupo não tinham qualquer política integrada às políticas do Lync Server. Como base por sala/categoria e por usuário, utilizando o recurso **É possível carregar arquivos** por usuário, é possível tornar o usuário um administrador de usuários, um administrador de sala de bate-papo ou configurar a capacidade do usuário de carregar arquivos. O recurso do Servidor de Chat Persistente**Carregamento de arquivos** é apenas por categoria.

## Registro em log

Registro em log para o Servidor de Chat Persistente e o Gerenciador de Operações do Centro do Sistema está integrado no registro em log de rastreamento do Lync Server 2013.

## Consulte Também

#### Outros Recursos

[Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md)

