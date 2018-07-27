---
title: 'Lync Server 2013: Requisitos técnicos de Arquivamento'
TOCTitle: Requisitos técnicos de Arquivamento
ms:assetid: 896d60e2-be4b-462d-8357-4cd307ab7304
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205059(v=OCS.15)
ms:contentKeyID: 49307390
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos de Arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Os requisitos técnicos do Lync Server 2013 incluem:

  - Requisitos de infraestrutura.

  - Software que é pré-requisito e que deve estar instalado para o arquivamento.

  - Requisitos de armazenamento de dados para arquivamento.

  - Requisitos de dimensionamento e considerações para a implantação de arquivamento.

  - Requisitos de desempenho e considerações para os bancos de dados de arquivamento.

> [!NOTE]  
> As informações sobre dimensionamento e desempenho não estão disponíveis nesta versão do Lync Server 2013.

## Requisitos de infraestrutura

Os requisitos de infraestrutura de arquivamento do Lync Server 2013 são os mesmos para a implantação do Lync Server 2013. Para obter detalhes, consulte [Determinando seus requisitos de infraestrutura para Lync Server 2013](lync-server-2013-determining-your-infrastructure-requirements.md) na documentação de planejamento.

## Pré-requisitos de arquivamento

O Lync Server 2013 simplifica os pré-requisitos de arquivamento porque:

  - O servidor de arquivamento não é mais uma função do servidor. Em vez disso, o agente de coleta de dados unificada é executado em um pool e em servidores Standard Edition para registrar dados para arquivamento, de forma que não é preciso configurar plataformas de sistemas separados para arquivamento.

  - O arquivamento usa o armazenamento de arquivos do Lync Server 2013 para o armazenamento temporário de conteúdos de reuniões, de forma que não é preciso configurar um repositório de arquivos para o arquivamento.

  - No Lync Server 2013, o enfileiramento de mensagens não é necessário.

## Requisitos de armazenamento de dados para arquivamento

Além disso, você deve configurar a infraestrutura para o armazenamento de arquivamento. Isso inclui uma ou ambas as opções abaixo:

  - Armazenamento do **Microsoft Exchange**. Conteúdo de reuniões, como apresentações em PowerPoint, são arquivados como anexos. Se quiser usar a integração do Microsoft Exchange para que os dados do arquivo do Lync sejam armazenados com dados de conformidade do Exchange, use o Exchange 2013 em sua implantação do Exchange e verifique se o tamanho máximo de armazenamento comporta o armazenamento de arquivos de reunião. Se você implantar o arquivamento por meio da opção de integração do Microsoft Exchange, os dados arquivados do Lync serão armazenados com dados de conformidade do Exchange 2013 somente para os usuários hospedados em seus servidores do Exchange 2013. Você deve implantar o Exchange 2013 antes de implantar e ativar o arquivamento por meio da opção de integração do Microsoft Exchange. Se optar por usar o armazenamento do Exchange 2013, não será necessário implantar bancos de dados separados do SQL Server para arquivamento, a menos que você tenha usuários do Lync que não estejam hospedados em seus servidores do Exchange 2013.

  - Armazenamento do banco de dados do **SQL Server para arquivamento**. Para oferecer suporte a usuários que não estão hospedados em servidores do Exchange 2013, ou se não quiser usar a opção de integração do Microsoft Exchange, implante o armazenamento de arquivamento por meio do banco de dados do SQL Server. O Lync Server 2013 é compatível com as seguintes versões 64 bits do SQL Server:
    
      - Microsoft SQL Server 2008 R2 Enterprise
    
      - Microsoft SQL Server 2008 R2 Standard
    
      - Microsoft SQL Server 2012 Enterprise
    
      - Microsoft SQL Server 2012 Standard
    
    > [!NOTE]  
    > Microsoft SQL Server 2008 R2 Express e Microsoft SQL Server 2012 Express não são compatíveis com versões de arquivamento de 32 bits do SQL Server. Para conhecer outros requisitos e restrições do SQL, consulte <a href="lync-server-2013-database-software-support.md">Suporte a software de banco de dados no Lync Server 2013</a> na documentação de planejamento e suporte.    
    Você deve configurar as plataformas do SQL Server antes de implantar e habilitar o arquivamento. Se a conta utilizada para publicar a topologia tiver os direitos e permissões apropriados, é possível criar o banco de dados de arquivamento (LcsLog) ao publicar a topologia. Também é possível criar o banco de dados posteriormente, incluindo-o como parte do procedimento de instalação. Para obter mais informações sobre o SQL Server, consulte o SQL Server TechCenter em [http://go.microsoft.com/fwlink/?linkid=129045\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=129045%26clcid=0x416).

