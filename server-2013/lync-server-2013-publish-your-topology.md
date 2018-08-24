---
title: 'Lync Server 2013: Publicar sua topologia'
TOCTitle: Publicar sua topologia
ms:assetid: bfed3829-7a54-4b5c-a7cb-28871acd35e7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412935(v=OCS.15)
ms:contentKeyID: 49307992
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publicar sua topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Sempre que usar o Construtor de Topologias para construir sua topologia, publique a topologia em um banco de dados no Repositório de Gerenciamento Central para que os dados sejam usados para a implantação do Lync Server 2013. Execute o procedimento a seguir para publicar a topologia.

## Para publicar a topologia

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  No Construtor de Topologias, na árvore de console, clique com o botão direito em **Lync 2013** e em **Topologia de publicação** .

3.  Na página **Bem-vindo** do assistente, clique em **Avançar** .

4.  Na página **Construtor de Topologia encontrou um repositório CMS** , clique em **Avançar** .

5.  Na página **Criar outros bancos de dados** , clique em **Avançar** .

6.  Quando o status indicar que a criação do banco de dados foi bem-sucedida, faça o seguinte:
    
      - Para exibir o log, clique em **Exibir log** .
    
      - Para fechar o assistente, clique em **Concluir** .
        
        > [!IMPORTANT]  
        > Se esta for uma nova instalação de uma Servidor de Borda ou de um Pool de borda, você deve exportar a configuração da Servidor de Borda de uma Servidor Front-End, um Pool de Front-Ends ou uma Servidor Standard Edition existente. Para exportar a configuração, consulte <a href="lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md">Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda</a>. Você importará o arquivo de configuração de uma mídia externa ou de um compartilhamento de rede durante a configuração e a fase de implantação da Servidores de Borda pela Assistente de Implantação do Lync Server.<br />        Depois que a Servidores de Borda estiver operacional e o banco de dados de armazenamento de configuração local estiver replicando com a implantação interna, as atualização subsequentes das configuração do Lync Server 2013 serão publicadas e replicada no Servidores de Borda.
