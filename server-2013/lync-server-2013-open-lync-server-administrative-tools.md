---
title: Abrir ferramentas administrativas do Lync Server
TOCTitle: Abrir ferramentas administrativas do Lync Server
ms:assetid: 8c58de94-9e0a-4368-9e14-9afcaa1142d0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg195741(v=OCS.15)
ms:contentKeyID: 49307389
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Abrir ferramentas administrativas do Lync Server

 

_**Tópico modificado em:** 2012-06-28_

Você pode usar os procedimentos neste tópico para abrir ferramentas administrativas para implantar, configurar ou solucionar problemas em sua topologia do Lync Server 2013.

  - Assistente de Implantação

  - Construtor de Topologias

  - Painel de Controle do Lync Server 2013

  - Shell de Gerenciamento do Lync Server 2013

## Assistente de Implantação

Use o procedimento a seguir para iniciar o Assistente de Implantação localmente, para adicionar ou remover arquivos de componente do Lync Server 2013.

## Para iniciar o assistente de implantação do Lync Server 2013

1.  Faça logon no computador no qual o Assistente de Implantação do Lync Server está instalado como um membro do grupo Admins. do Domínio e do grupo RTCUniversalServerAdmins.

2.  Clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013**, e depois em **Assistente de Implantação do Lync Server**.

## Construtor de Topologias

Use o procedimento a seguir para abrir o Construtor de Topologias para definir os servidores que deseja implantar em sua topologia do Lync Server 2013.

## Abrir o Construtor de Topologias do Lync Server 2013 para desenhar a topologia

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.
    
    > [!NOTE]  
    > Você pode definir uma topologia usando uma conta que seja membro do grupo Usuários local, mas para ler, publicar ou habilitar uma topologia, o que é necessário para instalar um Lync Server 2013 em um servidor, você deve usar uma conta que seja membro do grupo Admins. de Domínio e do grupo RTCUniversalServerAdmins e que tenha permissões de controle total (ou seja, leitura, gravação e alteração) no compartilhamento de arquivos que será utilizado para arquivar repositórios de arquivos, para que o Construtor de Topologias possa configurar as listas de controle de acesso discricionário (DACLs), ou uma conta com direitos de usuário equivalentes.

2.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

## Painel de Controle do Lync Server 2013

Use um dos procedimentos a seguir para abrir o Painel de Controle do Lync Server 2013 para gerenciar a configuração dos servidores, usuários, clientes e dispositivos no seu ambiente.

> [!NOTE]  
> Você pode usar uma conta de usuário que esteja atribuída à função CsAdministrator para executar qualquer tarefa no Painel de Controle do Lync Server 2013. Você pode usar outras funções para fazer logon no Painel de Controle do Lync Server 2013 para executar tarefas administrativas específicas, dependendo da tarefa que precise realizar. Por exemplo, você pode usar a CSArchivingAdministrator para administrar o Arquivamento no Painel de Controle do Lync Server 2013. Para detalhes sobre funções, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de Planejamento. Para detalhes sobre as funções que podem ser usada para executar uma tarefa específica, consulte a documentação da tarefa.

## Para abrir o Painel de Controle do Lync Server 2013 a partir de qualquer computador dentro do firewall da organização

1.  A partir de uma conta de usuário que esteja atribuída à função CsAdministrator ou a outra função que tenha os direitos de usuário e permissões apropriados para a tarefa a ser executada, faça logon em qualquer computador em sua implantação interna com uma resolução de tela mínima de 1024 x 768.
    
    > [!IMPORTANT]  
    > Se uma URL simples do administrador tiver sido configurada, você pode acessar o Painel de Controle do Lync Server 2013 a partir de um navegador de internet que esteja em execução em qualquer computador dentro do firewall da sua organização. Para detalhes sobre como configurar uma URL simples do administrador, consulte <a href="lync-server-2013-planning-for-simple-urls.md">Planejamento de URLs simples no Lync Server 2013</a>, na documentação de Planejamento, e <a href="lync-server-2013-edit-or-configure-simple-urls.md">Editar ou configurar URLs simples no Lync Server 2013</a> na documentação de Implantação.

2.  Abra uma janela do navegador e insira a URL do Administrador configurada para a sua organização.

## Para abrir o Painel de Controle do Lync Server 2013 em um computador executando o Lync Server 2013

1.  A partir de uma conta de usuário que seja membro da função CsAdministrator ou outra função que tenha os direitos de usuário e permissões apropriados para a tarefa a ser executada, faça logon no computador em que o Lync Server 2013 está instalado ou, no mínimo, as ferramentas administrativas do Lync Server 2013. Para definir as configurações, o computador deve ter uma resolução de tela mínima de 1024 x 768.

2.  Inicie o Painel de Controle do Lync Server 2013: clique em **Iniciar**, em **Todos os programas**, aponte para **Ferramentas Administrativas**, aponte para **Microsoft Lync Server 2013**, e depois clique em **Painel de Controle do Lync Server 2013**.

## Shell de Gerenciamento do Lync Server 2013

Use o procedimento a seguir para abrir o Shell de Gerenciamento do Lync Server 2013 para administrar servidores, usuários, cliente e dispositivos em seu ambiente usando a linha de comando.

> [!NOTE]  
> Você pode usar uma conta de usuário que esteja atribuída à função CsAdministrator para executar qualquer tarefa no Shell de Gerenciamento do Lync Server 2013. Você pode fazer logon usando outras funções para executar tarefas administrativas específicas, dependendo da tarefa que precisa realizar. Por exemplo, você pode usar a CSArchivingAdministrator para executar cmdlets relacionados à administração de Arquivamento. Para detalhes sobre funções, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de Planejamento. Para detalhes sobre as funções que podem ser usada para executar um cmdlet específico, consulte a documentação do cmdlet.<br />Você também pode executar certos cmdlets usando uma conta de usuário nos grupos RTCUniversalServerAdmins, RTCUniversalUserAdmins, ou RTCUniversalReadOnlyAdmins, dependendo do cmdlet.

## Para abrir o Shell de Gerenciamento do Lync Server 2013

  - Se você abrir uma janela do Windows PowerShell em vez do Shell de Gerenciamento do Lync Server 2013, por padrão não poderá executar os cmdlets do Lync Server 2013 . Para executar cmdlets do Lync Server 2013 de dentro do Windows PowerShell, digite as instruções abaixo no prompt de comando do Windows PowerShell:
    
    `Import-Module Lync`

  - Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

## Consulte Também

#### Tarefas

[Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md)  

#### Conceitos

[Ferramentas administrativas do Lync Server 2013](lync-server-2013-lync-server-administrative-tools.md)

