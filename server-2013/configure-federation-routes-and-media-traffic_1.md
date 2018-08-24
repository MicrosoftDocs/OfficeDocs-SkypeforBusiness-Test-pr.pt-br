---
title: Configurar rotas de federação e tráfego de mídia
TOCTitle: Configurar rotas de federação e tráfego de mídia
ms:assetid: ed6cb922-7863-453a-adce-2ce0ba761d74
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721925(v=OCS.15)
ms:contentKeyID: 49886467
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar rotas de federação e tráfego de mídia

 

_**Tópico modificado em:** 2016-12-08_

A federação é um relacionamento de confiança entre dois ou mais domínios SIP que permite que usuários em organizações separadas se comuniquem por limites de rede. Depois de migrar seu pool piloto Lync Server 2013, é necessário realizar a transição da rota de federação dos seus Servidores de Borda Microsoft Office Communications Server 2007 R2 para a rota de federação do seus Servidores de Borda Lync Server 2013.

Utilize os procedimentos a seguir para realizar a transição da rota de federação e de tráfego de mídia do seu Diretor e Servidor de Borda Office Communications Server 2007 R2 para o seu Servidor de Borda Lync Server 2013, para implantação em um único site.

> [!IMPORTANT]  
> A alteração da rota de federação e de tráfego de mídia exige o agendamento de tempo e inatividade de manutenção dos Servidores de Borda Lync Server 2013 e Office Communications Server 2007 R2. Todo este processo de transição também significa que o acesso federado estará indisponível durante a interrupção. Você deve agendar o tempo de inatividade para um período em que você espera mínima atividade do usuário. Você também deve fornecer notificações suficientes para os seus usuários finais. Planeje conforme o especificado para esta interrupção e defina as expectativas apropriadas na sua organização.

> [!IMPORTANT]  
> Se o seu Servidor de Borda Office Communications Server 2007 R2 herdado está configurado para usar o mesmo FQDN para os serviços de Borda de Acesso, Borda de Webconferência e Borda A/V, os procedimentos desta seção para realizar a transição das configurações de federação para um Servidor de Borda Lync Server 2013 não são suportadas. Se os serviços de borda herdados estão configurados para usar o mesmo FQDN, você deve primeiro migrar todos os seus usuários do Office Communications Server 2007 R2 para o Lync Server 2013, e depois desativar o Servidor de Borda Office Communications Server 2007 R2 antes de ativar a federação no Servidor de Borda Lync Server 2013. Para obter mais informações, consulte os seguintes tópicos:<ul>
> 
> <li><p><a href="move-remaining-users-to-lync-server-2013_1.md">Mover os usuários restantes para o Lync Server 2013</a></p></li>
> 
> 
> <li><p>&quot;Remover Servidores e Funções de Servidores&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268790">http://go.microsoft.com/fwlink/p/?LinkId=268790</a></p></li></ul>


> [!IMPORTANT]  
> Se sua federação XMPP é roteada através de um Servidor de Borda Lync Server 2013, os usuários do Office Communications Server 2007 R2 herdado não poderão se comunicar com o parceiro XMPP federado até que todos os usuários tenham sido movidos para o Lync Server 2013, até que as políticas XMPP e certificados tenham sido configurados, até que o parceiro XMPP federado tenha sido configurado no Lync Server 2013 e, finalmente, até que as entradas de DNS tenham sido atualizadas.

Para publicar, habilitar ou desabilitar com êxito uma topologia ao adicionar ou remover uma função de servidor, você deve estar conectado como um usuário membro dos grupos RTCUniversalServerAdmins e Administradores de Domínio. Também é possível delegar os direitos e permissões apropriados de usuário para adição de funções de servidor. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md) na documentação Implantação do servidor Standard Edition ou do servidor Enterprise Edition. Para fazer outras alterações na configuração, apenas a associação ao grupo RTCUniversalServerAdmins é necessária.

## Para remover a associação de federação herdada de sites do Lync Server 2013

1.  Abra a topologia do pool piloto usando o Construtor de Topologia

2.  No painel esquerdo, navegue até o nó do site.

3.  Clique com o botão direito no site e clique em **Editar propriedades**.

4.  Selecione **Rota de federação** no painel esquerdo.

5.  Em Atribuição de rota de federação de local, desmarque a caixa de seleção ao lado de **Habilitar federação SIP** para desabilitar a rota de federação pelo **BackCompatSite**.
    
    ![Caixa de diálogo Editar Propriedades, rota de Federação](images/JJ721925.2a80c103-c0cc-43ed-ba00-420f9add006a(OCS.15).jpg "Caixa de diálogo Editar Propriedades, rota de Federação")

6.  Clique em **OK** para fechar a página Editar Propriedades.

7.  A partir do **Construtor de Topologias**, selecione o nó superior **Lync Server**.

8.  No menu **Ações**, clique em **Publicar topologia** e complete o assistente.

## Para configurar o Servidor de Borda herdado como um Servidor de Borda não federado

1.  No **Construtor de Topologia**, no painel **Ações**, clique em **Mesclar topologia do Office Communications Server 2007 R2**.

2.  Clique em **Avançar** para continuar.

3.  Em **Especificar Configuração de Borda**, selecione o **FQDN Interno do Servidor de Borda** configurado atualmente para federação e clique em **Alterar**.
    
    ![Mesclar Topologia OCS 2007 R2, Especificar Configuração de Borda](images/JJ721925.42c15aaf-c1ac-4fb1-a086-665835c57b23(OCS.15).jpg "Mesclar Topologia OCS 2007 R2, Especificar Configuração de Borda")

4.  Clique em **Avançar** e aceite as configurações padrão até chegar à página **Especificar Borda Externa**:
    
    ![Página Especificar borda externa do Construtor de Topologia](images/JJ205243.32e97ce5-92f0-477e-8125-5d2ece237b13(OCS.15).jpg "Página Especificar borda externa do Construtor de Topologia")

5.  Em **Especificar Borda Externa**, desmarque a caixa de seleção **Este pool de Borda é usado para conectividade de IM pública e de federação**. Essa ação removerá a associação de federação com o BackCompatSite.
    
    > [!IMPORTANT]  
    > Esta etapa é importante. É necessário desmarcar essa opção para remover a associação de federação herdada.

6.  Clique em **Avançar** e aceite as configurações padrão das páginas restantes do assistente.

7.  Em **Resumo**, clique em **Avançar** para começar a mesclar as topologias.

8.  Na coluna **Status**, verifique se o valor é **Êxito** e clique em **Concluir** para fechar o assistente.

9.  No menu **Ação**, selecione **Publicar Topologia** e depois clique em **Avançar**.

10. Quando o **Assistente de publicação** é concluído, clique em **Finalizar** para fechar o assistente.
    
    ![Construtor de Topologias com site exibido após a mesclagem](images/JJ721925.92b679ad-332f-49aa-b4e2-19f939b711ca(OCS.15).jpg "Construtor de Topologias com site exibido após a mesclagem")
    
    Conforme exibido na figura anterior, a **Federação SIP** localizada na **Atribuição de rota de federação de local** está definida como **Desabilitada**

## Para configurar certificados no Servidor de Borda do Lync Server 2013

1.  Exporte o certificado externo do Proxy de Acesso, com a chave privada, do Servidor de Borda herdado do Office Communications Server 2007 R2.

2.  No Servidor de Borda do Lync Server 2013, importe o certificado externo do Proxy de Acesso da etapa anterior.

3.  Atribua o certificado externo do Proxy de Acesso para a interface externa do Lync Server 2013 do Servidor de Borda.

4.  O certificado de interface interna do Servidor de Borda do Lync Server 2013 não deve ser alterado.

## Para alterar a rota de federação do Office Communications Server 2007 R2 para usar o Servidor de Borda do Lync Server 2013

1.  No Office Communications Server 2007 R2, Servidor Standard Edition ou no Servidor Front-End, abra as Ferramentas Administrativas do Office Communications Server 2007 R2.

2.  No painel esquerdo, expanda o nó superior e clique com o botão direito no nó **Floresta**. Selecione **Propriedades** e depois clique em **Propriedades globais**.

3.  Clique na guia **Federação**.

4.  Marque a caixa de seleção para habilitar a federação e a conectividade de IM pública.

5.  Insira o FQDN do Lync Server 2013Servidor de Borda e depois clique em **OK**.
    
    ![Propriedades Globais de OCS, guia Federação](images/JJ721925.da633f72-43c6-4dac-8d37-ccd0dcde79c9(OCS.15).jpg "Propriedades Globais de OCS, guia Federação")

## Para ativar a federação do Servidor de Borda do Lync Server 2013

1.  No Construtor de Topologia, no painel esquerdo, navegue até o nó **Pools de Borda** do Lync Server 2013

2.  Expanda o nó, clique com o botão direito do mouse no Servidor de Borda listado e clique em **Editar Propriedades**.
    
    > [!NOTE]  
    > A federação só pode ser habilitada para um único Pool de borda. Se você tiver múltiplos servidores de Borda, selecione um para usar como o Pool de borda de federação.

3.  Na página **Geral**, marque a caixa de seleção **Habilitar federação para este pool de Borda (Porta 5061)**.
    
    ![Editar Propriedades, Geral, Habilitar Federação de Borda](images/JJ688121.cc79a88c-cce4-4cab-80ad-4f70325dc7c4(OCS.15).jpg "Editar Propriedades, Geral, Habilitar Federação de Borda")

4.  Clique em **OK** para fechar a página Editar Propriedades.

5.  Em seguida, navegue até o nó do site.

6.  Clique com o botão direito no site e clique em **Editar propriedades**.

7.  No painel esquerdo, clique em **Rota de federação**.

8.  Em **Atribuição de rota de federação de local**, selecione **Habilitar federação SIP** e na lista selecione o Lync Server 2013  Servidor de Borda.

9.  Clique em **OK** para fechar a página **Editar Propriedades**.
    
    ![Editar Propriedades, Geral, Associar pool de borda](images/JJ721925.33d43297-10cd-412e-bf4a-a1d9a84b9009(OCS.15).jpg "Editar Propriedades, Geral, Associar pool de borda")
    
    Para implantações entre vários locais, realize este procedimento para cada local.

## Para configurar o caminho de mídia de saída do Servidor de Borda do Lync Server 2013

1.  No **Construtor de Topologia**, navegue até o pool Lync Server 2013 abaixo de **Servidores de Front End Standard Edition** ou **Pools de Front-End Enterprise Edition**.

2.  Clique com o botão direito no pool e clique em **Editar propriedades**.

3.  Na seção **Associações**, marque a caixa de seleção **Associar pool de Borda (para componentes de mídia)**.

4.  Na caixa suspensa, selecione o Servidor de Borda do Lync Server 2013.
    
    ![Caixa de diálogo Editar Propriedades, Associar Pool de Borda](images/JJ721925.0cb76b08-5923-4972-8d7a-a829cb77136b(OCS.15).jpg "Caixa de diálogo Editar Propriedades, Associar Pool de Borda")

5.  Clique em **OK** para fechar a página **Editar Propriedades**.

## Para publicar as alterações de configuração do Servidor de Borda

1.  A partir do **Construtor de Topologias**, selecione o nó superior **Lync Server**.

2.  No menu **Ações**, selecione **Publicar Topologia** e conclua o assistente.

3.  Aguarde que a replicação do Active Directory ocorra em todos os pools na implantação.
    
    > [!NOTE]  
    > Poderá ser exibido a seguinte mensagem:<br />    <strong>Aviso: a topologia contém mais de um Servidor de Borda Federado. Isso pode ocorrer durante a migração para uma versão superior do produto. Nesse caso, somente um Servidor de Borda seria ativamente usado para federação. Verifique se o registro SRV DNS externo aponta para o Servidor de Borda correto. Se desejar que vários Servidores de Borda de federação permaneçam ativos simultaneamente (isto é, não em um cenário de migração), verifique se todos os parceiros federados estão usando o Office Comunications Server 2007 R2 ou superior e certifique-se de que o registro SRV DNS externo liste todos os Servidores de Borda ativamente para federação.</strong><br />    Esse aviso é esperado e pode ser ignorado com segurança.

## Para verificar o acesso remoto e de federação para usuários externos

1.  No Servidor de Front End Lync Server 2013, abra o Shell de Gerenciamento do Lync Server.

2.  Para verificar o status do acesso remoto e de federação, digite o seguinte na linha de comando:
    
        Get-CsAccessEdgeConfiguration

3.  Para habilitar o acesso remoto e de federação, digite o seguinte na linha de comando:
    
        Set-CsAccessEdgeConfiguration
    
    Para obter mais informações sobre esses cmdlets, consulte os seguintes tópicos: [Get-CsAccessEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsAccessEdgeConfiguration) e [Set-CsAccessEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsAccessEdgeConfiguration).

4.  Aguarde até a conclusão da replicação para ativar os servidores de Borda do Lync Server 2013 e testar o acesso externo e de federação.

## Para configurar o Servidor de Borda do Lync Server 2013

1.  Ative todos os Servidores de Borda do Lync Server 2013.

2.  Atualize as funções de roteamento do firewall externo ou as configurações do balanceador de carga de hardware para enviar tráfego SIP para acesso externo (geralmente, a porta 443) e federação (geralmente, a porta 5061) para o Lync Server 2013  Servidor de Borda, em vez do Servidor de Borda herdado.
    
    > [!NOTE]  
    > Se você não tem um balanceador de carga de hardware, você precisa atualizar o registro A do DNS para a federação resolver o novo servidor de borda de acesso do Lync Server. Para realizar essa tarefa com o mínimo de interrupção, reduza o valor de TTL do FQDN da Borda de Acesso do Lync Server externo para que quando o DNS for atualizado para apontar para a nova Borda de Acesso do Lync Server, a federação e o acesso remoto sejam atualizado rapidamente.

3.  Em seguida, interrompa a **Borda de Acesso do Servidor do Lync Server** de cada computador do Servidor de Borda.

4.  Em cada computador do Servidor de Borda herdado, abra o applet **Serviços** nas **Ferramentas Administrativas**.

5.  Na lista de serviços, localize **Borda de acesso do Office Communications Server**.

6.  Clique com o botão direito do mouse no nome dos serviços e selecione **Interromper** para interromper o serviço.

7.  Defina o tipo de inicialização para **Desativado**.

8.  Clique em **Ok** para fechar a janela **Propriedades**.

## Para testar a conectividade de usuários externos e o acesso externo

  - Usuários de pelo menos um domínio federado, um usuário interno no Lync Server 2013 e no Office Communications Server 2007 R2. Teste IM, presença, A/V e compartilhamento de desktop.

  - Usuários de cada provedor de serviços de IM públicos, aos quais sua empresa oferece suporte, (e para os quais o provisionamento foi realizado) que se comunicam com um usuário no Lync Server 2013 e no Office Communications Server 2007 R2.

  - Verifique se usuários anônimos podem participar de conferências.

  - Um usuário hospedado no Office Communications Server 2007 R2 usando acesso de usuário remoto (que faz login no Office Communications Server 2007 R2 de fora da intranet, mas sem VPN) com um usuário no Lync Server 2013 e no Office Communications Server 2007 R2. Teste IM, presença, A/V e compartilhamento de desktop.

  - Um usuário hospedado no Lync Server 2013 usando acesso de usuário remoto (que faz login no Lync Server 2013 de fora da intranet, mas sem VPN) com um usuário no Lync Server 2013 e no Office Communications Server 2007 R2. Teste IM, presença, A/V e compartilhamento de desktop.

