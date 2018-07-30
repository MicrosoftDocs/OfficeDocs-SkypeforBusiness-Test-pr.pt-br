---
title: Implantar pool piloto do Lync Server 2013
TOCTitle: Implantar pool piloto do Lync Server 2013
ms:assetid: a81aba1e-e636-434b-8c56-4150435bb55d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205144(v=OCS.15)
ms:contentKeyID: 49307725
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar pool piloto do Lync Server 2013

 

_**Tópico modificado em:** 2013-11-22_

Uma das primeiras etapas necessárias para a migração para Lync Server 2013 é implantar um pool piloto. O pool piloto é o local onde você testa a coexistência do Lync Server 2013 com sua implantação do Lync Server 2010. A coexistência é um estado temporário que permanece até você mover todos os usuários e pools para o Lync Server 2013.

Ao implantar um pool piloto, você usa o assistente Definir novo pool de front end. Você deve implantar os mesmos recursos e cargas de trabalho no pool piloto que tenham no pool do Lync Server 2013 que você tenha em seu pool do Lync Server 2010. Se você implantou o Servidor de Arquivamento, Servidor de Monitoramento, ou System Center Operations Manager para arquivamento ou monitorar do seu ambiente do Lync Server 2010 deseja continuar o arquivamento ou o monitoramento durante a migração, é necessário também implantar esses recursos em seu ambiente piloto. A versão implantada para arquivamento ou monitor do seu ambiente do Lync Server 2010 não irá capturar dados no seu ambiente do Lync Server 2013.

> [!NOTE]  
> O procedimento a seguir discute os recursos e configurações que você deve considerar como parte do processo de implantação do pool piloto. Esta seção destaca somente os principais pontos que você deve considerar como parte da implantação do pool piloto. Para obter detalhes sobre as etapas, consulte o guia de implantação <a href="lync-server-2013-deploying-lync-server.md">Implantando o Lync Server 2013</a>.

**Para implantar um pool piloto do Lync Server 2013**

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Expanda a árvore até atingir **Lync Server 2013Pools de front end do Enterprise Edition** .

3.  Clique com o botão direito em **Pools de front end do Enterprise Edition** , e selecione **Novo pool de front end** .
    
    ![Submenu de seleção do pool de Servidores do Construtor de Topologias](images/JJ205144.c2feed27-3418-42a6-a254-76e83607db9c(OCS.15).jpg "Submenu de seleção do pool de Servidores do Construtor de Topologias")

4.  Insira FQDN do pool. Ao definir seu pool piloto, é possível escolher para implantar um Pool de Front-Ends Enterprise Edition ou um Servidor Standard Edition. O Lync Server 2013 não exige que as características do seu pool piloto correspondam àquilo que foi implantado em seu pool herdado.
    

    > [!WARNING]
    > O pool ou o FQDN definido para seu pool piloto deve ser exclusivo. Ele não pode corresponder ao nome de atualmente implantado no pool do Lync Server 2010 ou qualquer outro servidor atualmente implantado.

    
    ![Página Definir Novo FQDN do Assistente de Pool Front-End](images/JJ205144.c5fd138c-e75a-413a-827f-b1461c996d40(OCS.15).jpg "Página Definir Novo FQDN do Assistente de Pool Front-End")

5.  Na página **Selecionar recursos** , marque as caixas de seleção para os recursos que você deseja neste pool de front end. Por exemplo, se estiver implantando apenas mensagens instantâneas e recursos de presença, você deve selecionar a caixa de seleção Conferência para permitir as mensagens instantâneas com vários participantes, mas não marca as caixas de seleção Conferência discada (PSTN), Enterprise Voice ou Controle de Admissão de Chamadas, porque estas representam voz, vídeo e recursos de conferência colaborativos. Para obter informações adicionais sobre seleção de recursos, consulte [Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md) na documentação Implantação.
    
    ![Página Selecionar Recursos do Pool de Front-End](images/JJ205144.5c3f3ff9-6e17-4d66-9b13-3bd55b38246b(OCS.15).jpg "Página Selecionar Recursos do Pool de Front-End")

6.  Na página **Selecionar funções do servidor posicionado** , recomendamos colocar o Servidor de Mediação no Lync Server 2013. Ao mesclar uma topologia herdada com o Lync Server 2013, precisamos que você primeiro posicione o Lync Server 2010Servidor de Mediação. Depois de mesclar as topologias e configurar o Lync Server 2013   Servidor de Mediação, é possível decidir manter o Servidor de Mediação posicionado ou alterá-lo para um servidor autônomo ao mover a função do Servidor de Mediação para o Lync Server 2013 posteriormente, durante o processo de implantação.
    
    ![Página Selecionar funções de servidor colocadas do Pool Front-End](images/JJ205144.e00b7eba-010b-44ed-b0a6-6ab3e534fb8c(OCS.15).jpg "Página Selecionar funções de servidor colocadas do Pool Front-End")

7.  Na página **Associar Funções de Servidor com este Pool de Front End** , durante a implantação do pool piloto, não escolha a opção **Habilitar um pool de Borda a ser usado pelo componente de mídia deste pool de front-end**. Esse recurso será ativado e colocado online em uma fase posterior da migração. Mantenha essa configuração desmarcada por enquanto.
    
    ![Página Associar funções de servidor com a página do pool Front-End](images/JJ205144.2d95a798-ad76-4dad-9392-ce41f4d938d1(OCS.15).jpg "Página Associar funções de servidor com a página do pool Front-End")

8.  Na página **Selecione um servidor dos aplicativos web do Office** , clique em **Novo** , e especifique o FQDN do servidor de aplicativos.
    
    ![Definir Novas Propriedades de FQDN do Office Online Server](images/JJ205144.25c6b455-f1b8-4326-a569-6e338153d398(OCS.15).jpg "Definir Novas Propriedades de FQDN do Office Online Server")

9.  Na página **Definir o armazenamento do arquivamento do SQL Server** , ao definir o armazenamento do SQL Server para arquivamento e monitoramento do Lync Server, selecione a instância do SQL Server criada anteriormente para Lync Server 2013.
    
    ![Página Definir repositório SQL Server de arquivamento](images/JJ205144.0f76f1dc-d0d7-42a0-aea3-400b8e1f35cd(OCS.15).jpg "Página Definir repositório SQL Server de arquivamento")

10. Para publicar sua topologia, clique com o botão direito no nó do **Lync Server** e clique em **Publicar topologia** .
    
    ![Construtor de Topologias exibindo uma topologia configurada](images/JJ205144.c3eafa20-159e-4355-a23d-9f72aeb26037(OCS.15).jpg "Construtor de Topologias exibindo uma topologia configurada")

11. Quando o processo de publicação for concluído, clique em **Finalizar** .

Para instalar uma cópia local do armazenamento de configuração e iniciar os serviços necessários, consulte [Configurand Servidores e pools Front-End para Lync Server 2013](lync-server-2013-setting-up-front-end-servers-and-front-end-pools.md) na documentação de Implantação.


