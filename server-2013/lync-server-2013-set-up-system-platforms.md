---
title: 'Lync Server 2013: Configurar plataformas de sistema'
TOCTitle: Configurar plataformas de sistema
ms:assetid: 2e72e49d-2737-4b5b-8c0a-60f6ecb15bf1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204783(v=OCS.15)
ms:contentKeyID: 49306261
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar plataformas de sistema no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Antes de iniciar a implantação do Servidor de Chat Persistente, você deve instalar o sistema operacional exigido no hardware que atende os requisitos do sistema nos servidores:

Para obter detalhes sobre o hardware suportado para servidores executando o Lync Server 2013, servidores do banco de dados e servidores de arquivos, consulte [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) na documentação de Suportabilidade. Para obter detalhes sobre os sistemas operacionais suportados e software de banco de dados, consulte [Suporte a software e à infraestrutura de servidor no Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md) na documentação de Suportabilidade. Para obter detalhes sobre os requisitos de atualização do Windows, consulte [Suporte adicional e requisitos de servidor no Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md) na documentação de Suportabilidade.

O Servidor de Chat PersistenteServidor Front-End, **PersistentChatService**, pode ser implantado em um ou mais computadores autônomos em um pool do Lync Server 2013Enterprise Edition. Eles não podem ser posicionados no Lync ServerEnterprise EditionServidores Front-End. O Servidor de Chat Persistente pode ser implantado pelo Bootstrapper, da mesma forma que outras funções do Lync Server. Os Serviços da Web do **Chat Persistente para Upload/Download de arquivos** e Serviços da Web do **Chat Persistente para Gerenciamento da Sala de Bate-papo** são componentes da Web implantados no Lync Server 2013Servidores Front-End.

Um único Servidor de Chat PersistenteServidor Front-End pode suportar 20.000 usuários ativos. É possível ter um Pool de Servidor de Chat Persistente com até 4 front-ends ativos suportando um total de 80.000 usuários simultâneos. O Chat PersistenteServidor Back-End, **PersistentChatStore**, armazena salas de bate-papo e categorias. Recomendamos que você instale o **PersistentChatStore** em um SQL ServerServidor Back-End exclusivo no seu pool do Enterprise Edition; embora podemos suportar o posicionamento do Lync Server 2013Servidor Back-End e **PersistentChatStore** na mesma instância do SQL Server.

Se a organização exige o suporte de conformidade, é possível instalá-lo usando o Construtor de Topologias. O serviço de Conformidade do Servidor de Chat Persistente está instalado no mesmo computador que o Servidor de Chat PersistenteServidor Front-End. Um banco de dados separado é exigido para conformidade. Para obter detalhes sobre os requisitos de conformidade para Servidor de Chat Persistente, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na documentação de Planejamento.

Como mínimo, cada topologia exige um servidor com o Lync Server 2013 instalado e um servidor com o software do banco de dados do SQL Server instalado. O Construtor de Topologias suporta vários Pools de Servidor de Chat Persistente. Siga as mesmas instruções de implantação para implantar vários Pools de Servidor de Chat Persistente como você faria para qualquer pool do [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md) na documentação de Implantação.

Também é possível implantar o Servidor de Chat Persistente com o Lync Server 2013Standard Edition. Neste caso, o **PersistentChatService**Servidor Front-End é posicionado no Servidor Standard Edition e você pode implantar o **PersistentChatStore**Servidor Back-End na instância do SQL Server Express local.

> [!IMPORTANT]  
> Nós não suportamos o Servidor de Chat PersistenteStandard Edition para alta disponibilidade. Desempenho e escala será limitado. Além disso, suportamos apenas novas implantações do Servidor de Chat Persistente  Servidor Standard Edition. Não suportamos uma atualização do Lync Server 2010, Servidor de Chat de Grupo para um Lync Server 2013Servidor de Chat PersistenteStandard Edition.

## Consulte Também

#### Conceitos

[Suporte adicional e requisitos de servidor no Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md)  

#### Outros Recursos

[Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md)  
[Suporte a software e à infraestrutura de servidor no Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md)  
[Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md)  
[Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md)

