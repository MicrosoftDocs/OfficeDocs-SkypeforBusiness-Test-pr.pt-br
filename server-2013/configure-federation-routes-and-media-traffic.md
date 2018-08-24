---
title: Configurar rotas de federação e tráfego de mídia
TOCTitle: Configurar rotas de federação e tráfego de mídia
ms:assetid: 8b2f5f81-a955-4ad1-ad74-397322ff9521
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688121(v=OCS.15)
ms:contentKeyID: 49886296
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar rotas de federação e tráfego de mídia

 

_**Tópico modificado em:** 2012-10-15_

A federação é um relacionamento de confiança entre dois ou mais domínios SIP que permite que usuários em organizações separadas se comuniquem por limites de rede. Depois de migrar seu pool piloto Lync Server 2013, é necessário realizar a transição da rota de federação dos seus Servidores de Borda Lync Server 2010 para a rota de federação do seus Servidores de Borda Lync Server 2013.

Use os procedimentos a seguir para fazer a transição da rota de federação e da rota do tráfego de mídia do seu Servidor de Borda e Diretor do Lync Server 2013 para seu Servidor de Borda do Lync Server 2010, para uma implantação de site único.

> [!IMPORTANT]  
> A alteração da rota de federação e de tráfego de mídia exige o agendamento de tempo e inatividade de manutenção dos Servidores de Borda Lync Server 2013 e Lync Server 2010. Todo este processo de transição também significa que o acesso federado estará indisponível durante a interrupção. Você deve agendar o tempo de inatividade para um período em que você espera mínima atividade do usuário. Você também deve fornecer notificações suficientes para os seus usuários finais. Planeje conforme o especificado para esta interrupção e defina as expectativas apropriadas na sua organização.

> [!IMPORTANT]  
> Se seu Servidor de Borda herdado do Lync Server 2010 estiver configurado para usar o mesmo FQDN para o Serviço de Borda de Acesso, para o Serviço de Webconferência e para o Serviço de Borda A/V, os procedimentos nesta seção não são suportados. Se os serviços de Borda herdados estiverem configurados para usar o mesmo FQDN, migre primeiramente todos os seus usuários do Lync Server 2010 para Lync Server 2013, em seguida, encerre o Servidor de Borda do Lync Server 2010 antes de habilitar a federação no Servidor de Borda do Lync Server 2013.

> [!IMPORTANT]  
> Se sua federação XMPP é roteada através de um Servidor de Borda Lync Server 2013, os usuários do Lync Server 2010 herdado não poderão se comunicar com o parceiro XMPP federado até que todos os usuários tenham sido movidos para o Lync Server 2013, até que as políticas XMPP e certificados tenham sido configurados, até que o parceiro XMPP federado tenha sido configurado no Lync Server 2013 e, finalmente, até que as entradas de DNS tenham sido atualizadas.

## Para remover a associação de federação herdada dos sites do Lync Server 2013

1.  Abra o servidor de front end do Lync Server 2013, abra a topologia existente no Construtor de Topologia.

2.  No painel esquerdo, navegue até o nó do site, que está localizado diretamente abaixo do **Lync Server**.

3.  Clique com o botão direito no site e depois clique em **Editar propriedades**.

4.  No painel esquerdo, selecione **Rota de federação**.

5.  Em **Atribuição da rota de federação do site**, desmarque a caixa de seleção **Habilitar federação SIP** para desativar a rota de federação através do ambiente herdado do Lync Server 2010.
    
    ![Caixa de diálogo Editar Propriedades, página Rota de federação](images/JJ688121.8d755ae0-fc7d-4253-b0db-0cf31b863c55(OCS.15).jpg "Caixa de diálogo Editar Propriedades, página Rota de federação")

6.  Clique em **OK** para fechar a página Editar Propriedades.

7.  A partir do **Construtor de Topologias**, selecione o nó superior **Lync Server**.

8.  No menu **Ação**, clique em **Publicar topologia**.

9.  Clique em **Avançar** para concluir o processo de publicação e depois clique em **Concluir** quando o processo de publicação estiver completo.

## Para configurar o Servidor de Borda herdado como um Servidor de Borda não federado

1.  No painel esquerdo, navegue para o nó **Lync Server 2010** e depois para o nó **Pools de borda**.

2.  Clique com o botão direito no servidor de borda, e depois em **Editar Propriedades**.

3.  Selecionar **Geral** no painel esquerdo.

4.  Desmarque a caixa de seleção **Habilitar federação para este pool de Borda (Porta 5061)** e selecione **OK** para fechar a página.
    
    ![Editar Propriedades, Geral, limpar Habilitar federação](images/JJ688121.3be2c8c0-9ed9-4544-bafd-b7694271fafc(OCS.15).jpg "Editar Propriedades, Geral, limpar Habilitar federação")

5.  No menu **Ação**, selecione **Publicar Topologia** e depois clique em **Avançar**.

6.  Quando o **Assistente de publicação** é concluído, clique em **Finalizar** para fechar o assistente.

7.  Verifique se a federação do servidor de borda herdado está desativada.
    
    ![Construtor de Topologias, Pool de Borda, federação desabilitada](images/JJ688121.a2948438-d51a-4aeb-9eaa-d899ca950758(OCS.15).jpg "Construtor de Topologias, Pool de Borda, federação desabilitada")

## Para configurar certificados no Servidor de Borda do Lync Server 2010

1.  Exporte o certificado externo do Proxy de Acesso, com a chave privada, do Servidor de Borda herdado do Lync Server 2010.

2.  No Servidor de Borda do Lync Server 2013, importe o certificado externo do Proxy de Acesso da etapa anterior.

3.  Atribua o certificado externo do Proxy de Acesso para a interface externa do Lync Server 2013 do Servidor de Borda.

4.  O certificado de interface interna do servidor de borda do Lync Server 2013 deve ser solicitado de um AC confiável e atribuído.

## Para alterar a rota de federação do Lync Server 2010 para usar o Servidor de Borda do Lync Server 2013

1.  No Construtor de Topologias, no painel esquerdo, navegue para o nó **Lync Server 2013** e depois para o nó **Pools de borda**.

2.  Clique com o botão direito no servidor de borda, e depois em **Editar Propriedades**.

3.  Selecionar **Geral** no painel esquerdo.

4.  Marque a caixa de seleção **Habilitar federação para este pool de Borda (Porta 5061)** e selecione **OK** para fechar a página.
    
    ![Caixa de diálogo Editar Propriedades, página Geral](images/JJ688121.cc79a88c-cce4-4cab-80ad-4f70325dc7c4(OCS.15).jpg "Caixa de diálogo Editar Propriedades, página Geral")

5.  No menu **Ação**, selecione **Publicar Topologia** e depois clique em **Avançar**.

6.  Quando o **Assistente de publicação** é concluído, clique em **Finalizar** para fechar o assistente.

7.  Verifique se **Federação (porta 5061)** está definida como **Habilitada**.
    
    ![Construtor de Topologias, Pool de Borda, Federação habilitada](images/JJ688121.e8ccdada-23f4-47e5-a99d-5bf795fefc48(OCS.15).jpg "Construtor de Topologias, Pool de Borda, Federação habilitada")

## Para atualizar o próximo salto da federação do Servidor de Borda do Lync Server 2013

1.  No Construtor de Topologias, no painel esquerdo, navegue para o nó **Lync Server 2013** e depois para o nó **Pools de borda**.

2.  Expanda o nó, clique com o botão direito no Servidor de Borda listado e clique em **Editar Propriedades**.

3.  Na página **Geral**, em **Seleção do próximo salto**, selecione na lista suspensa o pool do Lync Server 2013.
    
    ![Caixa de diálogo Editar Propriedades, página Próximo Salto](images/JJ688121.5741b9a8-e729-4457-9f62-38f08a2c5b02(OCS.15).jpg "Caixa de diálogo Editar Propriedades, página Próximo Salto")

4.  Clique em **OK** para fechar a página Editar Propriedades.

5.  A partir do **Construtor de Topologias**, selecione o nó superior **Lync Server**.

6.  No menu **Ações**, clique em **Publicar topologia** e complete o assistente.

## Para configurar o caminho de mídia de saída do Servidor de Borda do Lync Server 2013

1.  No Construtor de Topologia, no painel esquerdo, navegue até o nó **Lync Server 2013** e depois até o pool abaixo de **Servidor Front-End Standard Edition** ou **Pools de Front-Ends Enterprise Edition**.

2.  Clique com o botão direito no pool e clique em **Editar propriedades**.

3.  Na seção **Associações**, marque a caixa de seleção **Associar pool de Borda (para componentes de mídia)**.
    
    ![Editar Propriedades, Geral, Associar pool de borda](images/JJ688121.fd9b18ca-fda2-4764-9bf0-726bf39f6a12(OCS.15).jpg "Editar Propriedades, Geral, Associar pool de borda")

4.  Na caixa suspensa, selecione o Servidor de Borda do Lync Server 2013.

5.  Clique em **OK** para fechar a página **Editar Propriedades**.

## Para ativar a federação do Servidor de Borda do Lync Server 2013

1.  No Construtor de Topologias, no painel esquerdo, navegue para o nó **Lync Server 2013** e depois para o nó **Pools de borda**.

2.  Expanda o nó, clique com o botão direito do mouse no Servidor de Borda listado e clique em **Editar Propriedades**.
    
    > [!NOTE]  
    > A federação só pode ser habilitada para um único Pool de borda. Se você tiver múltiplos servidores de Borda, selecione um para usar como o Pool de borda de federação.

3.  Na página **Geral**, verifique se a configuração **Habilitar federação para este pool de Borda (Porta 5061)** está marcada.
    
    ![Caixa de diálogo Editar Propriedades, página Geral](images/JJ688121.cc79a88c-cce4-4cab-80ad-4f70325dc7c4(OCS.15).jpg "Caixa de diálogo Editar Propriedades, página Geral")

4.  Clique em **OK** para fechar a página Editar Propriedades.

5.  Em seguida, navegue até o nó do site.

6.  Clique com o botão direito no site e clique em **Editar propriedades**.

7.  No painel esquerdo, clique em **Rota de federação**.

8.  Em **Atribuição de rota de federação de local**, selecione **Habilitar federação SIP** e na lista selecione o Lync Server 2013  Servidor de Borda.
    
    ![Editar Propriedades, página Rota de Federação](images/JJ688121.c50c13b8-0859-4e3e-8793-45c431a5b4b5(OCS.15).jpg "Editar Propriedades, página Rota de Federação")

9.  Clique em **OK** para fechar a página **Editar Propriedades**.
    
    Para implantações entre vários locais, realize este procedimento para cada local.

## Para publicar as alterações de configuração do Servidor de Borda

1.  A partir do **Construtor de Topologias**, selecione o nó superior **Lync Server**.

2.  No menu **Ações**, selecione **Publicar Topologia** e conclua o assistente.

3.  Aguarde que a replicação do Active Directory ocorra em todos os pools na implantação.
    
    > [!NOTE]  
    > Poderá ser exibido a seguinte mensagem:<br />    <strong>Aviso: a topologia contém mais de um Servidor de Borda Federado. Isso pode ocorrer durante a migração para uma versão superior do produto. Nesse caso, somente um Servidor de Borda seria ativamente usado para federação. Verifique se o registro SRV DNS externo aponta para o Servidor de Borda correto. Se desejar que vários Servidores de Borda de federação permaneçam ativos simultaneamente (isto é, não em um cenário de migração), verifique se todos os parceiros federados estão usando o Lync Server. Verifique se o registro SRV DNS externo lista todos os Servidores de Borda habilitados para federação.</strong><br />    Esse aviso é esperado e pode ser ignorado com segurança.

## Para configurar um servidor de borda do Lync Server 2013

1.  Ative todos os Servidores de Borda do Lync Server 2013.

2.  Atualize as funções de roteamento do firewall externo ou as configurações do balanceador de carga de hardware para enviar tráfego SIP para acesso externo (geralmente, a porta 443) e federação (geralmente, a porta 5061) para o Lync Server 2013  Servidor de Borda, em vez do Servidor de Borda herdado.
    
    > [!NOTE]  
    > Se não tiver um balanceador de carga de hardware, será necessário atualizar o registro A de DNS da federação para resolver no novo servidor de borda de acesso do Lync Server. Para obter isso com um mínimo de interrupção, reduza o valor TTL do FQDN de borda de acesso do Lync Server, para que, quando o DNS for atualizado para apontar para a borda de acesso do Lync Server, o acesso de federação e remoto seja atualizado rapidamente.

3.  Em seguida, pare a **Borda de Acesso do Lync Server** de cada computador Servidor de Borda.

4.  Em cada computador do Servidor de Borda herdado, abra o applet **Serviços** nas **Ferramentas Administrativas**.

5.  Na lista de serviços, encontre **Borda de Acesso do Lync Server**.

6.  Clique com o botão direito do mouse no nome dos serviços e selecione **Interromper** para interromper o serviço.

7.  Defina o tipo de inicialização para **Desativado**.

8.  Clique em **Ok** para fechar a janela **Propriedades**.

