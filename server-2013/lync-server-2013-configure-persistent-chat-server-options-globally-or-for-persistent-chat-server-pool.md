---
title: 'Lync Server 2013: Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente'
TOCTitle: Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente
ms:assetid: 1e8d5245-cd58-4aad-9a1c-35b24189bc40
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204731(v=OCS.15)
ms:contentKeyID: 49306095
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar opções do Servidor de Chat Persistente globalmente ou para pool do Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-06_

No Painel de Controle do Lync Server 2013, é possível usar a seção **Chat PersistenteConfiguração** da página **Chat Persistente** para definir as configurações do Chat Persistente globalmente onde se aplica a todos os Pools de Servidor de Chat Persistente ou para um Pool de Servidor de Chat Persistente específico.

> [!NOTE]  
> Para configurar e usar o Servidor de Chat Persistente, é necessário primeiro usar o Construtor de Topologias para adicionar suporte de Servidor de Chat Persistenteà topologia, e depois publicar a topologia. Para obter detalhes, consulte <a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação Implantação.

## Para configurar as opções do Chat Persistente globalmente

1.  A partir de uma conta de usuário com a função CsPersistentChatAdministrator ou CsAdministrator atribuída, faça o logon em qualquer computador na sua implementação interna.

2.  No menu **Iniciar**, selecione o Painel de Controle do Lync Server ou abra uma janela de navegador e depois insira o URL de Admin. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]  
    > Você também pode usar o cmdlets Windows PowerShell. Para obter detalhes, consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de Implantação.

3.  Na barra de navegação à esquerda, clique no **Chat Persistente**, depois na Configuração do **Chat Persistente**.

4.  Na página Configuração do **Chat Persistente**, clique em **Novo**, depois em **Configuração do site**.
    
    > [!IMPORTANT]  
    > Escolha esta opção se você deseja que a configuração seja aplicada a todos os Pools de Servidor de Chat Persistente implantados no site. Clique em <strong>Configuração do Pool</strong> se você deseja que a configuração seja aplicada a um Pool de Servidor de Chat Persistente específico.

5.  Em **Selecionar um Site**, selecione o site a ser configurado para a configuração de site do Servidor de Chat Persistente.

6.  Na **Nova Configuração do Chat Persistente**, faça o seguinte:
    
      - Em **Nome** , especifique um nome para a nova definição de configuração. Por padrão, o nome do site já existe.
    
      - Em **Histórico de chat padrão**, defina o número de mensagens de chat que serão processadas para cada sala após a primeira solicitação. Por padrão, o número é 30. Este é o padrão global e os administradores podem desativar o histórico de chat por categoria.
        
        > [!IMPORTANT]  
        > O Servidor de Chat Persistente irá armazenar estas mensagens na memória. Portanto, se você aumentar este número, mais mensagens serão armazenadas. Sempre é possível acessar o conteúdo histórico pela pesquisa. O número padrão simplesmente determina o número máximo de mensagens que você vê inicialmente ao se conectar a uma sala de bate-papo.    
      - Em **Tamanho máximo do arquivo (KB)**, selecione o tamanho máximo do arquivo de cada histórico de chat. Por padrão, o número é 20 MB (20.000 KB). Este é o tamanho máximo para um arquivo que pode ser carregado em qualquer sala de bate-papo no sistema (para o qual cada carregamento de arquivo está habilitado por sua configuração de **Categoria** correspondente).
        
        > [!IMPORTANT]  
        > Esta configuração é forçada no servidor porque os aplicativos personalizados ou os clientes do Chat de Grupo anteriores usando o Office Communications Server 2007 R2Servidor de Chat de Grupo ou o Lync Server 2010, Chat de Grupo podem publicar arquivos em uma sala. O cliente do Lync 2013 não possui uma capacidade de upload/download de arquivos. Portanto, se você possui uma única implantação do Lync 2013 ou um cliente do Lync 2013, não é possível publicar arquivos em uma sala de bate-papo do Servidor de Chat Persistente.    
      - Em **Limite de atualização do participante**, selecione o limite para as atualizações de participantes. O Servidor de Chat Persistente envia informações (quem está conectado a uma sala de bate-papo) para todos os participantes até que o número de usuários conectados atinja este número. Por padrão, o número é 75. Este limite indica o número máximo de participantes em uma determinada sala além do qual o Servidor de Chat Persistente para de enviar atualizações para os clientes conectados sobre quem está presente na sala.
    
      - (Opcional.) Na **URL de gerenciamento da sala** , selecione a URL de gerenciamento da sala. Esta é a URL para o gerenciamento da sala personalizada baseada na Web. Se você não precisa personalizar o gerenciamento da sala e apenas usa a configuração padrão, deixe esta opção em branco. Após a URL ser definida, é aplicada como a URL de gerenciamento da sala interna e externa.
        
        Se você deseja personalizar sua experiência de criação de sala e incluir seu fluxo de trabalho de negócios específicos, é possível construir uma solução de gerenciamento de sala personalizada usando o Kit de Desenvolvimento de Software (SDK) do Servidor de Chat Persistente, hospedá-lo em algum local e inserir a URL. Esta URL é enviada para o cliente para que quando um usuário tentar exibir ou criar uma sala, ele ou ela seja direcionado para sua solução de gerenciamento de sala personalizada.

7.  Clique em **Confirmar** .

## Para configurar opções do Chat Persistente para um Pool de Servidor de Chat Persistente específico

1.  A partir de uma conta de usuário com a função CsPersistentChatAdministrator ou CsAdministrator atribuída, faça o logon em qualquer computador na sua implementação interna.

2.  No menu **Iniciar** , selecione Painel de Controle do Lync Server ou abra uma janela do navegador e insira a URL de Administração. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).
    
    > [!IMPORTANT]  
    > Você também pode usar o cmdlets Windows PowerShell. Para obter detalhes, consulte <a href="configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md">Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell</a> na documentação de Implantação.

3.  Na barra de navegação à esquerda, clique no **Chat Persistente**, depois clique em Configuração do **Chat Persistente**.

4.  Na página Configuração do **Chat Persistente**, clique em **Novo**, depois em **Configuração do pool**.

5.  Em **Selecione um Serviço** , selecione o serviço associado com o Pool de Servidor de Chat Persistente a ser configurado.

6.  Na **Nova Configuração do Chat Persistente**, faça o seguinte:
    
      - Em **Nome** , especifique um nome para as novas definições de configuração. Por padrão, o nome do pool do site já existe.
    
      - Em **Histórico de chat padrão**, defina o número de mensagens de chat que serão processadas para cada sala após a primeira solicitação. Por padrão, o número é 30. Este é o padrão global e os administradores podem desativar o histórico de chat por categoria.
        
        > [!IMPORTANT]  
        > O Servidor de Chat Persistente irá armazenar estas mensagens na memória. Portanto, se você aumentar este número, mais mensagens serão armazenadas. Sempre é possível acessar o conteúdo histórico pela pesquisa. O número padrão simplesmente determina o número máximo de mensagens que você vê inicialmente ao se conectar a uma sala de bate-papo.    
      - Em **Tamanho máximo do arquivo (KB)** , selecione o tamanho máximo do arquivo de cada histórico de chat. Por padrão, o número é 20 MB (20.000 KB). Este é o tamanho máximo para um arquivo que pode ser carregado em qualquer sala de bate-papo no sistema (para o qual cada carregamento de arquivo está habilitado por sua configuração de **Categoria** correspondente).
        
        > [!IMPORTANT]  
        > Esta configuração é forçada no servidor porque os aplicativos personalizados ou antigos clientes do Chat de Grupo ( Office Communications Server 2007 R2Servidor de Chat de Grupo ou Lync Server 2010, Chat de Grupo) pode publicar arquivos em uma sala. O cliente do Lync 2013 não possui a capacidade de fazer upload/download de arquivos. Portanto, se você possui uma implantação simples do Lync 2013 ou cliente Lync 2013, não é possível publicar arquivos em uma sala de bate-papo do Servidor de Chat Persistente.    
      - Em **Limite de atualização do participante**, selecione o limite para as atualizações de participantes. O Servidor de Chat Persistente envia informações (quem está conectado a uma sala de bate-papo) para todos os participantes até que o número de usuários conectados atinja este número. Por padrão, o número é 75. Este limite indica o número máximo de participantes em uma determinada sala além do qual o Servidor de Chat Persistente para de enviar atualizações para os clientes conectados sobre quem está presente na sala.
    
      - Em **URL de gerenciamento da sala**, selecione a URL de gerenciamento da sala. Esta é a URL para uma implantação de gerenciamento de sala baseado na Web. Se você não precisa personalizar um gerenciamento de sala e apenas usa a configuração padrão, deixe esta opção em branco.
        
        Se você deseja personalizar sua experiência de criação da sala e incluir seu fluxo de trabalho dos negócios específico, é possível construir uma solução de gerenciamento de sala personalizada utilizando o Kit de Desenvolvimento de Software do Servidor de Chat Persistente, hospedá-lo em algum lugar e inserir a URL. Esta URL é enviada para o cliente para que quando um usuário tentar exibir/criar uma sala, ele ou ela seja direcionado para sua solução de gerenciamento de sala personalizada.

7.  Clique em **Confirmar**.

