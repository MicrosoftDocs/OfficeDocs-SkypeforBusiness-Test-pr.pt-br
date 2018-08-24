---
title: "Impl. o Lync Server 2013 Standard Edition em um Lync Server 2013 Enterprise existente"
TOCTitle: Implantando o Lync Server 2013 Standard Edition em um Lync Server 2013 Enterprise existente
ms:assetid: 05ea128d-6c94-49b3-b28b-477367196425
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398112(v=OCS.15)
ms:contentKeyID: 49305742
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando o Lync Server 2013 Standard Edition em um Lync Server 2013 Enterprise existente

 

_**Tópico modificado em:** 2012-10-01_

A implantação de um Servidor Standard Edition em uma implantação do Enterprise Edition existente é semelhante à implantação de funções de servidor adicionais. Um Servidor Standard Edition pode ser implantado em outro site, permitindo que os usuários desse site sejam hospedados no Servidor Standard Edition e não no Pool de Front-Ends em uma rede de longa instância (WAN). Os procedimentos de instalação do novo site e dos servidores desse site já foram definidos em outras seções da documentação [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md) e Deploying Lync Server 2010 Standard Edition.

**Para definir um novo site**

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na árvore de console, clique com o botão direito em **Lync Server 2013**, e clique em **Novo Site Central** .

3.  Na página **Identificar o site** , nomeie o site e insira uma descrição (opcional).

4.  Siga os procedimentos para definir o restante da topologia do site. Para obter mais detalhes, consulte [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md).

5.  Publique a topologia atualizada. Para obter detalhes, consulte [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md).

6.  Configure e instale um Servidor Standard Edition. Para obter informações detalhadas, consulte Setting Up Standard Edition Server.
    
    
    > [!CAUTION]
    > Se você implantou um ambiente com apenas um Servidor Standard Edition, você terá iniciado o processo de instalação a partir do Assistente de Implantação do Lync Server usando o link <STRONG>Preparar primeiro servidor Standard Edition</STRONG> para instalar os arquivos de banco de dados iniciais ao novo Servidor Standard Edition. <STRONG>Não</STRONG> siga esse processo ao instalar um Servidor Standard Edition em uma implantação existente do Lync Server 2013.


