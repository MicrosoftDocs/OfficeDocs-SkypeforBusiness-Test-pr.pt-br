---
title: Configurando Lync Server 2013 para trabalhar com o servidor de Office Web Apps
TOCTitle: Configurando Lync Server 2013 para trabalhar com o servidor de Office Web Apps
ms:assetid: 6231e519-9010-4ff9-b5a6-b5859c2b3e11
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204944(v=OCS.15)
ms:contentKeyID: 49306897
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Lync Server 2013 para trabalhar com o servidor de Office Web Apps

 

_**Tópico modificado em:** 2013-04-22_

Para que você possa configurar o Lync Server 2013 para usar o Servidor do Office Web Apps, é necessário implantar e configurar o Servidor do Office Web Apps. Consulte o documento **Guia para implantar o Servidor do Office Web Apps e o Office Web Apps** para obter informações detalhadas sobre como instalar e configurar um único Servidor do Office Web Apps ou um farm de Servidores do Office Web Apps para alta disponibilidade.

Depois que o Servidor do Office Web Apps for instalado com êxito e seu web farm estiver configurado corretamente, você precisará configurar o Lync Server para comunicar-se com o novo servidor. Para isso, é necessário adicionar a URL de descoberta do Servidor do Office Web Apps à sua topologia do Lync Server. Para adicionar o Servidor do Office Web Apps à sua topologia, execute as seguintes etapas:

1.  Clique em **Iniciar** , em **Todos os Programas** , em **Microsoft Lync Server 2013** e depois em **Construtor de Topologias do Lync Server**.

2.  Na caixa de diálogo **Construtor de Topologias**, selecione **Baixar Topologia da implantação existente** e clique em **OK**.

3.  Na caixa de diálogo **Salvar Topologia como**, digite um nome para o documento de topologia (por exemplo, **PreWebAppsServerTopology**) na caixa **Nome do arquivo** e clique em **Salvar**. Posteriormente, essa topologia poderá ser recuperada e publicada novamente se houver problemas com a nova topologia.

4.  No Construtor de Topologias, expanda **Lync Server 2013**, expanda o nome do seu site, expanda **Pools de Front-Ends Enterprise Edition**, clique com o botão direito do mouse no nome de um dos seus pools e depois em **Editar Propriedades**.

5.  Na caixa de diálogo **Editar Propriedades**, na guia **Geral**, encontre o cabeçalho **Associar Servidor do Office Web Apps** e clique em **Novo** (ou selecione um Servidor do Office Web Apps existente na lista suspensa).

6.  Na caixa de diálogo **Definir Novo Servidor do Office Web Apps**, digite o FQDN (nome de domínio totalmente qualificado) do computador do Servidor do Office Web Apps na caixa **FQDN do Servidor do Office Web Apps**. Quando você fizer isso, a URL de descoberta de seu Servidor do Office Web Apps deverá ser inserida automaticamente na caixa **Office Web URL de descoberta de Servidor do Office Web Apps**.
    
    Se o Servidor do Office Web Apps estiver instalado localmente e na mesma zona de rede que o Lync Server 2013, a opção **O Servidor do Office Web Apps é implantado em uma rede externa (ou seja, de perímetro/Internet)** não deverá ser selecionada.
    
    Se o Servidor do Office Web Apps for implantado fora do seu firewall interno, seleciona a opção **O Servidor do Office Web Apps é implantado em uma rede externa (ou seja, de perímetro/Internet)**.

7.  Na caixa de diálogo **Definir Novo Servidor do Office Web Apps**, clique em **OK** e depois em **OK** na caixa de diálogo **Editar Propriedades**. Em seguida, a URL de descoberta do Office Web Apps será listada como uma das associações do pool.

Você precisará repetir esse processo para cada pool que precisar ser associado ao seu Servidor do Office Web Apps.

Depois que você adicionar a URL de descoberta à topologia, terá que publicar a topologia atualizada. Para isso, no Construtor de Topologias:

1.  Clique em **Ação** e depois em **Publicar Topologia**.

2.  No assistente Publicar Topologia, na página **Publicar a topologia**, clique em **Avançar**.

3.  Na página **Assistente de publicação concluído**, clique em **Concluir**.

4.  Feche o Construtor de Topologias.

