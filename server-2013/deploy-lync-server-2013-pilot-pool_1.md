---
title: Implantar o pool piloto de Lync Server 2013
TOCTitle: Implantar o pool piloto de Lync Server 2013
ms:assetid: 19c27053-8b21-401f-ad91-75c2dd355e91
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204718(v=OCS.15)
ms:contentKeyID: 49306033
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar o pool piloto de Lync Server 2013

 

_**Tópico modificado em:** 2013-11-22_

Uma das primeiras etapas necessárias para a migração para Lync Server 2013 é implantar um pool piloto. O pool piloto é o local onde você testa a coexistência do Lync Server 2013 com sua implantação do Office Communications Server 2007 R2. A coexistência é um estado temporário que permanece até você mover todos os usuários e pools para o Lync Server 2013.

Ao implantar um pool piloto, você usa o Assistente Definir novo pool de front-ends. Você deve implantar os mesmos recursos e cargas de trabalho em seu pool piloto do Lync Server 2013 que você possui em seu pool do Office Communications Server 2007 R2. Caso tenha implantado Servidor de Arquivamento, Monitoring Server ou System Center Operations Manager para arquivamento ou monitoramento de seu ambiente do Office Communications Server 2007 R2, e você deseja continuar o arquivamento ou monitoramento durante toda a migração, você também precisará implantar estes recursos em seu ambiente piloto. A versão que você implantou para arquivar ou monitorar seu ambiente do Office Communications Server 2007 R2 não irá capturar dados em seu ambiente do Lync Server 2013.

> [!NOTE]  
> O procedimento a seguir discute os recursos e configurações que você deve considerar como parte do processo de implantação do pool piloto. Esta seção destaca somente os principais pontos que você deve considerar como parte da implantação do pool piloto. Para obter detalhes sobre as etapas, consulte o guia de implantação <a href="lync-server-2013-deploying-lync-server.md">Implantando o Lync Server 2013</a>.

**Para implantar um pool piloto do Lync Server 2013**

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Abra o Construtor de Topologia e selecione criar uma nova topologia.

3.  Insira o domínio SIP primário.
    
    ![Criar Nova Topologia, página Definir domínio primário](images/JJ204718.68775d87-f32c-494a-8386-6d4c81e81284(OCS.15).jpg "Criar Nova Topologia, página Definir domínio primário")

4.  Continue completando o assistente até que chegue no assistente **Assistente Definir o novo pool de Front-Ends**. Clique em Próximo.

5.  Insira FQDN do pool. Ao definir seu pool piloto, é possível escolher para implantar um Pool de Front-Ends Enterprise Edition ou um Servidor Standard Edition. O Lync Server 2013 não exige que as características do seu pool piloto correspondam àquilo que foi implantado em seu pool herdado.
    

    > [!WARNING]
    > O pool ou o FQDN definido para seu pool piloto deve ser exclusivo. Ele não pode corresponder ao nome de atualmente implantado no pool do Office Communications Server 2007 R2 ou qualquer outro servidor atualmente implantado.

    
    ![Página Definir o FQDN do pool de Front-End](images/JJ204718.5ff4336c-13fa-47cc-899b-066f267eb3f0(OCS.15).jpg "Página Definir o FQDN do pool de Front-End")

6.  Defina o computador que será adicionado ao pool.
    
    ![Caixa de diálogo Definir Novo Pool de Front-End](images/JJ204718.374f0ed4-988b-465f-9861-8d1db401e76f(OCS.15).jpg "Caixa de diálogo Definir Novo Pool de Front-End")

7.  Na página **Selecionar recursos**, marque as caixas de seleção para os recursos que você deseja neste pool de front end. Por exemplo, se estiver implantando apenas mensagens instantâneas e recursos de presença, você deve selecionar a caixa de seleção Conferência para permitir as mensagens instantâneas com vários participantes, mas não marca as caixas de seleção Conferência discada (PSTN), Enterprise Voice ou Controle de Admissão de Chamadas, porque estas representam voz, vídeo e recursos de conferência colaborativos. Para obter informações adicionais sobre seleção de recursos, consulte [Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md) na documentação Implantação.
    
    ![Página Selecionar Recursos do Pool de Front-End](images/JJ205144.5c3f3ff9-6e17-4d66-9b13-3bd55b38246b(OCS.15).jpg "Página Selecionar Recursos do Pool de Front-End")

8.  Na página **Selecionar funções de servidor colocadas**, recomendamos que você coloque o Servidor de Mediação no Lync Server 2013. Ao mesclar uma topologia herdada com o Lync Server 2013, é necessário colocar primeiro o Office Communications Server 2007 R2Servidor de Mediação. Depois de mesclar as topologias e configurar o Lync Server 2013Servidor de Mediação, você pode manter o Servidor de Mediação colocado ou alterá-lo para um servidor autônomo ao mover a função do Servidor de Mediação para o Lync Server 2013 mais adiante no processo de implantação.
    
    ![Página Selecionar funções de servidor colocadas do Pool Front-End](images/JJ205144.e00b7eba-010b-44ed-b0a6-6ab3e534fb8c(OCS.15).jpg "Página Selecionar funções de servidor colocadas do Pool Front-End")

9.  Na página **Associar Funções de Servidor com este Pool de Front End**, durante a implantação do pool piloto, não escolha a opção **Habilitar um pool de Borda a ser usado pelo componente de mídia deste pool de front-end**. Esse recurso será ativado e colocado online em uma fase posterior da migração. Mantenha essa configuração desmarcada por enquanto.
    
    ![Página Associar funções de servidor com a página do pool Front-End](images/JJ205144.2d95a798-ad76-4dad-9392-ce41f4d938d1(OCS.15).jpg "Página Associar funções de servidor com a página do pool Front-End")

10. Na página **Selecione um servidor dos aplicativos web do Office**, clique em **Novo**, e especifique o FQDN do servidor de aplicativos.
    
    ![Definir Novas Propriedades de FQDN do Office Online Server](images/JJ205144.25c6b455-f1b8-4326-a569-6e338153d398(OCS.15).jpg "Definir Novas Propriedades de FQDN do Office Online Server")

11. Na página **Defina o repositório de Arquivamento do SQL Server**, selecione a instância do SQL Server criada anteriormente para o Lync Server 2013.
    
    ![Página Definir repositório SQL Server de arquivamento](images/JJ205144.0f76f1dc-d0d7-42a0-aea3-400b8e1f35cd(OCS.15).jpg "Página Definir repositório SQL Server de arquivamento")

12. Na página **Defina o repositório de Monitoramento do SQL Server**, selecione a instância do SQL Server criada anteriormente para o Lync Server 2013. Clique em **Concluir**.

13. A partir do nó do topo do Construtor de Topologia, clique com o botão direito em **Lync Server** e clique em **Editar Propriedades.** Clique em **URLs simples**.

14. Atualize a **URL de acesso administrativo**.
    
    ![Editar Propriedades, páginas URLs Simples](images/JJ204718.ef596dd2-1983-47e0-b342-4fc7a0e36380(OCS.15).jpg "Editar Propriedades, páginas URLs Simples")
    
    Para informações adicionais sobre URLs simples, consulte o tópico [Editar ou configurar URLs simples no Lync Server 2013](lync-server-2013-edit-or-configure-simple-urls.md) na documentação de Implantação.

15. A partir de **Editar Propriedades**, clique em **Servidor de Gerenciamento Central**.

16. A partir da lista suspensa, selecione o pool do Lync Server 2013.
    
    ![Editar Propriedades, página Servidor de Gerenciamento Central](images/JJ204718.211955fc-85f2-462d-8709-e6ea67092e89(OCS.15).jpg "Editar Propriedades, página Servidor de Gerenciamento Central")

17. Clique em OK para fechar a página **Editar Propriedades**.

18. A partir do menu **Ação**, selecione **Publicar Topologia**.

19. Quando o processo de publicação for concluído, clique em **Finalizar**.

20. Retornando ao Assistente de Implantação do Lync Server 2013, clique em **Instalar ou Atualizar o Sistema do Lync Server**.
    
    ![Assistente de Implantação do Lync Server 2013](images/JJ204718.fb05adef-ad29-4905-9090-d409261b0e48(OCS.15).jpg "Assistente de Implantação do Lync Server 2013")

Para instalar uma cópia local do armazenamento de configuração e iniciar os serviços necessários, consulte [Configurand Servidores e pools Front-End para Lync Server 2013](lync-server-2013-setting-up-front-end-servers-and-front-end-pools.md) na documentação de Implantação.


