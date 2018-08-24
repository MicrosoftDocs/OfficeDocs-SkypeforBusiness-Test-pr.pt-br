---
title: 'Lync Server 2013: Implantando Servidor de Chat Persistente'
TOCTitle: Implantando Servidor de Chat Persistente
ms:assetid: e3b930fb-6855-47f0-b6b3-7dfae386540d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205357(v=OCS.15)
ms:contentKeyID: 49308392
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2014-03-31_

O Lync Server 2013, Servidor de Chat Persistente faz parte da infraestrutura do Lync Server 2013.

Implantar o Servidor de Chat Persistente exige que você:

  - Use o Construtor de Topologias para definir ou importar e subsequentemente publicar sua topologia e componentes que deseja implantar.

  - Preparar seu ambiente para implantar os componentes do Servidor de Chat Persistente.

  - Instalar e configurar os componentes do Servidor de Chat Persistente para sua implantação.

O Servidor de Chat Persistente está disponível com o Lync Server 2013Enterprise Edition como um pool separado (não posicionado com o Enterprise EditionServidores Front-End). O Servidor de Chat Persistente exige um SQL ServerServidor Back-End em seu pool do Enterprise Edition para armazenar o conteúdo da sala de chat e outros metadados relevantes. Recomendamos instalar o **PersistentChatStore** em uma instância dedicada do SQL ServerServidor Back-End, embora posicionar o Lync Server 2013Servidor Back-End e **PersistentChatStore** na mesma instância do SQL Server é suportado.

O Servidor de Chat Persistente também pode ser implantado com o Lync Server 2013Standard Edition. Neste caso, o **PersistentChatService**Servidor Front-End é posicionado no computador do Standard Edition e o **PersistentChatStore**Servidor Back-End pode ser implantado na instância do SQL Server Express local.

Para obter detalhes sobre configurações de colocação suportadas, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md).

> [!IMPORTANT]  
> Não suportamos alta disponibilidade para Servidor de Chat PersistenteStandard Edition. O desempenho e a escala serão limitados. Além disso, suportamos apenas o novo Servidor de Chat PersistenteServidor Standard Edition. Não suportamos a atualização do Lync Server 2010, Servidor de Chat de Grupo para um Lync Server 2013Servidor de Chat PersistenteStandard Edition.

Se sua organização exige suporte de conformidade, é possível instalar o serviço de Conformidade do Servidor de Chat Persistente no Servidor de Chat PersistenteServidor Front-End. Um banco de dados separado é necessário para conformidade.

Como mínimo, cada topologia exige um servidor com o Lync Server 2013 instalado e um servidor com o software do banco de dados do SQL Server instalado.

Use o Construtor de Topologias para adicionar o Servidor de Chat Persistente às suas implantações do Lync Server 2013. É possível escolher adicionar um ou mais Pools de Servidor de Chat Persistente usando o Construtor de Topologias. Siga as mesmas instruções de implantação para implantar vários Pools de Servidor de Chat Persistente como você faria com qualquer pool. Para obter detalhes, consulte [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md) na documentação de Implantação.

Para obter detalhes sobre as topologias disponíveis e os requisitos técnicos e de software para instalar o Servidor de Chat Persistente, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na documentação de Planejamento, [Como o servidor de chat persistente funciona no Lync Server 2013](lync-server-2013-how-persistent-chat-server-works.md) na documentação de Planejamento, Implantação ou Operações e [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) na documentação de Suportabilidade.

Para obter detalhes sobre a aquisição de certificados, criação do banco de dados do SQL Server e criação dos repositórios de arquivos, consulte [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md)na documentação de Implantação.

Um único Servidor de Chat PersistenteServidor Front-End pode suportar 20.000 usuários ativos. É possível ter um Pool de Servidor de Chat Persistente com até 4 Servidores Front-End ativos suportando um total de 80.000 usuários simultâneos.

Servidor de Chat Persistente também é suportado em um servidor virtual. O servidor virtual pode suportar até 20.000 usuários simultâneos se corresponder as especificações do servidor físico.

> [!IMPORTANT]  
> O Servidor de Chat Persistente deve estar instalado em um sistema de arquivo NTFS para ajudar a forçar a segurança do sistema de arquivos. O FAT32 não é um sistema de arquivos suportado para o Servidor de Chat Persistente.

## Nesta seção

  - [Como o servidor de chat persistente funciona no Lync Server 2013](lync-server-2013-how-persistent-chat-server-works.md)

  - [Lista de verificação de implantação para o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-deployment-checklist-for-persistent-chat-server.md)

  - [Requisitos técnicos do Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-technical-requirements-for-persistent-chat-server.md)

  - [Configurar sistemas e infraestrutura para o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-setting-up-systems-and-infrastructure-for-persistent-chat-server.md)

  - [Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013](lync-server-2013-adding-persistent-chat-server-to-your-deployment.md)

  - [Instalando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-installing-persistent-chat-server.md)

  - [Adicionando um administrador de Chat Persistente no Lync Server 2013](lync-server-2013-adding-a-persistent-chat-administrator.md)

  - [Configurando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md)

  - [Configurando Servidor de Chat Persistente usando cmdlets do Windows PowerShell](configuring-persistent-chat-server-by-using-windows-powershell-cmdlets.md)

  - [Configuração de solução de problemas do Servidor de Chat Persistente usando cmdlets do Windows PowerShell no Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md)

  - [Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md)

  - [Failouver e failback do Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-failing-over-and-failing-back-persistent-chat-server.md)

