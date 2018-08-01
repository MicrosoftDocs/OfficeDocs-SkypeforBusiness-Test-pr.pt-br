---
title: 'Lync Server 2013: Configuração de hardware'
TOCTitle: Configuração de hardware
ms:assetid: 37a9f295-cde3-4beb-9a6a-2580082798ab
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425852(v=OCS.15)
ms:contentKeyID: 49306400
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração de hardware para Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

A configuração do hardware e de outros componentes, necessários na infraestrutura na qual você precisa implementar a sua topologia, exigem o seguinte antes da publicação da topologia no Construtor de Topologias:

  - Instale o hardware para cada componente no design da topologia criado e salvo utilizando o Construtor de Topologias, incluindo todos os computadores necessários (servidores que executam o Lync Server 2013, servidores de banco de dados, servidores que executam IIS (Serviços de Informações da Internet) e servidores de proxy reverso, conforme apropriado), adaptadores de rede, balanceadores de carga de hardware e dispositivos de armazenamento (como servidores de arquivos). Confirme se as recomendações de número e velocidade dos adaptadores de rede foram seguidas. Se você for utilizar balanceadores de carga de hardware, certifique-se de que você tem as informações adequadas do fornecedor para configurá-los para uso com o Lync Server 2013. Se você for usar um servidor de arquivos ou outro servidor para alojar o compartilhamento de arquivos necessário pelo Lync Server, certifique-se de que o servidor está disponível e pronto para a configuração do compartilhamento de arquivos. Para obter detalhes sobre como definir uma topologia que especifica os componentes necessários para a implantação, consulte [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md). Para obter detalhes sobre os requisitos de hardware para servidores, consulte [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) na documentação de Capacidade de Suporte.

  - Certifique-se de que a infraestrutura de rede atende aos requisitos. Para obter detalhes, consulte [Requisitos de infraestrutura de rede para Lync Server 2013](lync-server-2013-network-infrastructure-requirements.md) na documentação de Planejamento.

  - Configure o Serviços de Domínio Active Directory. A configuração do AD DS inclui prepará-lo e definir todos os componentes que você deseja implementar nele. Para obter os detalhes de como preparar o AD DS, consulte [Preparando Serviços de Domínio do Active Directory para o Lync Server 2013](lync-server-2013-preparing-active-directory-domain-services.md) na documentação da Implementação.

  - Configure as permissões exigidas para criar o compartilhamento de arquivos. Permissões para uso de compartilhamentos de arquivos pelo Lync Server 2013 são configuradas automaticamente pelo Construtor de Topologias quando você publica sua topologia. No entanto, a conta do usuário utilizada para publicar a topologia deve ter controle total (leitura/gravação/modificação) no compartilhamento de arquivos para que o Construtor de Topologias configure as permissões exigidas. Para certificar-se de que o compartilhamento de arquivos possa ser gerenciado adequadamente durante o processo de publicação do Construtor de Topologia, o usuário ou grupo do domínio do qual o usuário é membro deve se tornar membro do grupo de Administradores locais na máquina em que o compartilhamento de arquivos está localizado. Em um cenário com diversos domínios, o usuário ou grupo do Domínio A deve se tornar membro do grupo de Administradores locais na máquina no Domínio B em que o compartilhamento de arquivos será localizado.
    
    Para obter detalhes sobre a atualização usando compartilhamento de arquivos em um DFS (sistema de arquivos distribuído), consulte [Configurar armazenamento de arquivo para Lync Server 2013](lync-server-2013-configure-dfs-file-storage.md).
    

    > [!WARNING]  
    > O compartilhamento de arquivo do Lync Server 2013, Enterprise Edition não pode ser localizado no Servidor Front-End.



  - Instale e configure o balanceador de carga de hardware para o Serviços Web. Com o balanceamento de carga do Sistema de Nome de Domínio (DNS) implantado, você ainda precisa usar balanceadores de carga de hardware para esses pools, mas somente para o tráfego de HTTP/HTTPS. O balanceador de carga de hardware é usado para o tráfego de HTTPS dos clientes pelas portas 443 e 80. Embora você ainda precise de balanceadores de carga de hardware para esses pools, sua configuração e administração será principalmente para o tráfego HTTP/HTTPS, aos quais os administradores dos balanceadores de carga de hardware estão acostumados.

Depois de concluir todas as tarefas de preparação descritas neste tópico, mas antes de publicar a topologia, também é necessário:

  - [Instalar sistemas operacionais e software de pré-requisito nos servidores para Lync Server 2013](lync-server-2013-install-operating-systems-and-prerequisite-software-on-servers.md)

  - [Configurar o IIS para Lync Server 2013](lync-server-2013-configure-iis.md)

  - [Configurar o SQL Server para Lync Server 2013](lync-server-2013-configure-sql-server-for-lync-server.md)

  - [Configurar registros DNS no Lync Server 2013 para um pool de Front-Ends ou servidor Standard Edition](lync-server-2013-configure-dns-records-for-a-front-end-pool-or-standard-edition-server.md)

