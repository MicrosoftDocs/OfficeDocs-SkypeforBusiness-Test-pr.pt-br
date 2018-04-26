---
title: 'Lync Server 2013: Preparando a infraestrutura e os sistemas'
TOCTitle: Preparando a infraestrutura e os sistemas
ms:assetid: 1254ee38-0679-4714-b293-1050f107c158
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398205(v=OCS.15)
ms:contentKeyID: 49305937
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando a infraestrutura e os sistemas para o Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

A implantação do Lync Server 2013 requer o uso do Construtor de Topologias para definir e publicar o design da topologia. Para identificar os componentes necessários para a topologia, use o Construtor de Topologias para criar e salvar o design da topologia. Antes de publicar a topologia no Construtor de Topologias, faça o seguinte:

  - Adquira e instale o hardware para cada componente no design da topologia criada e salva usando o Construtor de Topologias, incluindo todos os computadores obrigatórios (servidores executando o Lync Server 2013, servidores de banco de dados, servidores executando o IIS e servidores de proxy reverso, conforme o apropriado), adaptadores de rede, balanceadores de carga de hardware e dispositivos de armazenamento (como servidores de arquivo). Para detalhes sobre como definir uma topologia que especifica os componentes necessários para sua implantação, consulte [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md). Para detalhes sobre requisitos de hardware para servidores, consulte [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) na documentação de Suporte.

  - Certifique-se de que a infraestrutura de rede atende aos requisitos. Para obter detalhes, consulte [Requisitos de infraestrutura de rede para Lync Server 2013](lync-server-2013-network-infrastructure-requirements.md) na documentação de Planejamento.

  - Configure o Serviços de Domínio Active Directory. Para publicar e habilitar a topologia, é necessário que os servidores internos sejam representados por contas de computador no AD DS. Para isso, é preciso unir os computadores ao AD DS. Para detalhes sobre como preparar o AD DS, consulte [Preparando Serviços de Domínio do Active Directory para o Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md).

  - Crie um compartilhamento de arquivos. Servidores Standard Edition podem hospedar o compartilhamento de arquivos para o arquivo necessário, enquanto em uma implantação do Enterprise o compartilhamento de arquivos não pode ser hospedado no servidor de front end. As permissões e associações de grupo necessárias para implantar e configurar a lista de controle de acesso (ACL) na pasta e o compartilhamento devem ser definidos corretamente para que o Construtor de Topologias seja concluído com sucesso. Certifique-se de que a pessoa que executa o Construtor de Topologias tem as permissões e associações de grupos a seguir:
    
      - Membro de Administradores Locais
    
      - Membro de Usuários do Domínio
    
      - Controle total sobre o compartilhamento e a pasta do repositório de arquivos

  - Para o Enterprise Edition, instale e configure o SQL Server. Para que a instalação do SQL Server seja concluída com sucesso, o servidor com base no SQL Server deve estar online e a pessoa que estiver publicando a topologia deve ser administradora local no SQL Server e membro do grupo sysadmin na instância do SQL Server.

Depois de concluir todas as tarefas de preparação conforme descrito neste tópico, mas antes de publicar a topologia, também é necessário executar outras tarefas de preparação, incluindo a instalação dos sistemas operacionais Windows e os demais softwares de pré-requisito, configurar o IIS e o DNS. Para detalhes sobre estas tarefas, consulte [Requisitos de sistema para servidores executando Lync Server 2013](lync-server-2013-system-requirements-for-servers-running-lync-server-2013.md), [Configurar o IIS para Lync Server 2013](lync-server-2013-configure-iis.md) e [Preparando a infraestrutura e os sistemas para o Lync Server 2013](lync-server-2013-preparing-the-infrastructure-and-systems.md). Além disso, você deve estar familiarizado com os clientes e seus requisitos. Para detalhes, consulte [Implantando clientes e dispositivos no Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md).

## Nesta seção

  - [Configuração de hardware para Lync Server 2013](lync-server-2013-hardware-setup.md)

  - [Configuração de software no Lync Server 2013](lync-server-2013-software-setup.md)

  - [Preparando Serviços de Domínio do Active Directory para o Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md)

  - [Configurar o SQL Server para Lync Server 2013](lync-server-2013-configure-sql-server-for-lync-server.md)

  - [Configurar registros DNS no Lync Server 2013 para um pool de Front-Ends ou servidor Standard Edition](lync-server-2013-configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)

  - [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md)

