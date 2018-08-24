---
title: 'Lync Server 2013: Ferramentas administrativas do Lync Server'
TOCTitle: Ferramentas administrativas do Lync Server
ms:assetid: 9b006f93-4f3d-461d-89b8-e80a34fdb3c5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg195756(v=OCS.15)
ms:contentKeyID: 49307577
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Ferramentas administrativas do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico descreve as ferramentas administrativas do Lync Server 2013.

As ferramentas administrativas são instaladas por padrão em cada servidor do Lync Server. Além disso, você pode instalar as ferramentas administrativas em outros computadores, como consoles administrativos dedicados. Para os procedimentos para instalar as ferramentas administrativas, consulte [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md). Para os procedimentos para abrir as ferramentas para executar tarefas administrativas, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

Certifique-se de analisar os requisitos de infraestrutura, sistema operacional, software e direitos de administrador antes de instalar ou usar as ferramentas administrativas do Lync Server. Para detalhes sobre os requisitos de infraestrutura, consulte [Requisitos de infraestrutura das ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-infrastructure-requirements.md). Para detalhes sobre requisitos de sistema operacional e software para instalar as ferramentas administrativas do Lync Server, consulte [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md), [Requisitos adicionais de software para Lync Server 2013](lync-server-2013-additional-software-requirements.md) e [Suporte adicional e requisitos de servidor no Lync Server 2013](lync-server-2013-additional-server-support-and-requirements.md). Os direitos de usuário e permissões requeridas para instalar e usar as ferramentas são descritos em [Direitos e permissões de administrador necessários para configuração e administração do Lync Server 2013](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md).

As ferramentas administrativas consistem de:

  - **Assistente de Implantação do Lync Server**   Use para implantar o Lync Server e para instalar todas as ferramentas administrativas.

  - **Lync ServerConstrutor de Topologias**   Use para definir componentes em sua implantação.

  - **Painel de Controle do Lync Server**   Use para o gerenciamento contínuo da sua implantação usando uma interface baseada em web.

  - **Shell de Gerenciamento do Lync Server**   Use para o gerenciamento contínuo da sua implantação usando a linha de comando.

  - **Lync Server Ferramenta de log**   Use para solucionar problemas em sua implantação.

  - **Serviço de Log Centralizado**   Coletar logs e arquivos de rastreamento de um computador, pool, site ou global. Selecionar e definir os cenários que contêm provedores, sinalizadores e níveis de rastreamento. Os registros em log são coletados, agregados e exibidos com ferramentas, como qualquer ferramenta com base em texto ou Snooper.exe.

Você pode gerenciar sua implantação usando principalmente o Construtor de Topologias e o Painel de Controle do Lync Server.

## Assistente de Implantação

Você deve usar o Assistente de Implantação do Lync Server incluído na mídia de instalação para instalar todas as ferramentas administrativas em um computador em que o Lync Server ainda não esteja instalado. Durante o processo de instalação das ferramentas administrativas, o Assistente de Implantação do Lync Server é instalado localmente junto com as demais ferramentas, para que você possa usá-lo posteriormente para instalar arquivos para componentes adicionais ou remover arquivos indesejáveis do computador.

Para detalhes sobre como executar o Assistente de Implantação do Lync Server pela primeira vez a partir da mídia de instalação do Lync Server, consulte [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md).

## Construtor de Topologias

Para detalhes sobre as tarefas de implantação que podem ser executadas usando o Construtor de Topologias, consulte a documentação de Implantação para cada função de servidor.

## Painel de Controle do Lync Server

Você pode usar o Painel de Controle do Lync Server 2013 para executar a maioria das tarefas administrativas exigidas para gerenciar e manter o Lync Server 2013. O Painel de Controle do Lync Server fornece a você uma interface de usuário gráfica (GUI) para gerenciar a configuração dos servidores executando o Lync Server, além dos usuários, clientes e dispositivos em sua organização. O Shell de Gerenciamento do Lync Server usa Painel de Controle do Lync Server como mecanismo subjacente para executar a configuração do Lync Server.

O Painel de Controle do Lync Server é instalado automaticamente em cada Servidor Front-end ou Servidor Standard Edition do Lync Server. Nesta versão, os Servidores de Borda são administrados remotamente. Também é possível instalar o Painel de Controle do Lync Server em outro computador, como um console de gerenciamento a partir do qual se quer gerenciar o Lync Server de maneira central. Para obter detalhes, consulte [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md).

> [!IMPORTANT]  
> <ul>
> 
> <li><p>Para configurar as definições usando o Painel de Controle do Lync Server, é preciso estar conectado usando uma conta designada com a função de CsAdministrator. Para obter detalhes sobre as funções administrativas predefinidas disponíveis no Lync Server 2013, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a>.</p></li>
> 
> 
> <li><p>Para configurar as definições usando o Painel de Controle do Lync Server, é preciso também usar um computador com uma resolução de tela mínima de 1024 x 768.</p></li></ul>


## Shell de Gerenciamento do Lync Server

No Lync Server, o Shell de Gerenciamento do Lync Server fornece um novo método para administração e gerenciamento. O Shell de Gerenciamento do Lync Server é uma poderosa interface de gerenciamento, construída no Interface da linha de comando do Windows PowerShell, que inclui um conjunto abrangente de cmdlets específicos para o Lync Server. Com o Shell de Gerenciamento do Lync Server, você tem um conjunto rico de configurações de controles de automação. O Construtor de Topologias e o Painel de Controle do Lync Server ambos implementam sub-conjuntos desses cmdlets para oferecer suporte ao gerenciamento do Lync Server. O Shell de Gerenciamento do Lync Server inclui cmdlets para todas as tarefas administrativas do Lync Server, que podem ser usados individualmente para gerenciar sua implantação. Para detalhes, consulte a documentação [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md) ou a ajuda da linha de comando para cada cmdlet.

## Ferramenta de Log

A Ferramenta de Log do Lync Server facilita a solução de problemas ao capturar informações de log e rastreamento do produto enquanto o produto está em execução. Você pode usar a ferramenta para executar sessões de depuração em qualquer função do servidor do Lync Server. Para obter detalhes sobre a Ferramenta de Log, consulte a documentação da Ferramenta de Log do Lync Server 2010 na Biblioteca do TechNet em [http://go.microsoft.com/fwlink/p/?linkId=199265](http://go.microsoft.com/fwlink/p/?linkid=199265).

> [!IMPORTANT]  
> O Serviço de Log Centralizado é recomendado para todo o conjunto de registros de log por meio da Ferramenta de Registro em Log do Lync Server em toda as circunstâncias. A Ferramenta de Registro de Log do Lync Server ainda funcionará, mas ela irá interferir ou ser renderizada de forma muito ineficaz se o Serviço de Log Centralizado já estiver sendo executado. Você somente deve usar o Serviço de Log Centralizado ou a Ferramenta de Registro de Log do Lync Server, mas nunca ambos ao mesmo tempo. Para obter mais informações sobre o Serviço de Log Centralizado e o motivo pelo qual você deve usá-lo exclusivamente, consulte <a href="lync-server-2013-using-the-centralized-logging-service.md">Usando o Serviço de Registro em Log no Lync Server 2013</a>.

## Nesta seção

  - [Requisitos de infraestrutura das ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-infrastructure-requirements.md)

  - [Suporte a sistemas operacionais de servidor e de ferramentas no Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md)

  - [Requisitos de software de ferramentas administrativas no Lync Server 2013](lync-server-2013-administrative-tools-software-requirements.md)

  - [Direitos e permissões de administrador necessários para configuração e administração do Lync Server 2013](lync-server-2013-administrator-rights-and-permissions-required-for-setup-and-administration.md)

  - [Requisitos para publicar uma topologia no Lync Server 2013](lync-server-2013-requirements-to-publish-a-topology.md)

  - [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md)

  - [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md)

  - [Resolver problemas do painel de controle do Lync Server 2013](lync-server-2013-troubleshooting-lync-server-2013-control-panel.md)

  - [Usando o Serviço de Registro em Log no Lync Server 2013](lync-server-2013-using-the-centralized-logging-service.md)

## Consulte Também

#### Outros Recursos

[Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md)

