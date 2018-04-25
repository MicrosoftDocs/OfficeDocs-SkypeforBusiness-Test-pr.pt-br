---
title: Iniciar ou parar serviços do Lync Server 2013
TOCTitle: Iniciar ou parar serviços do Lync Server 2013
ms:assetid: 1c70b4ec-9de5-4f7a-a3c9-c0eb76710505
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520958(v=OCS.15)
ms:contentKeyID: 49306063
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Iniciar ou parar serviços do Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Você pode usar o Painel de Controle do Lync Server para iniciar ou parar todos os serviços do Lync Server 2013 executados em um computador específicos ou iniciar e parar um serviço específico.

## Para iniciar ou parar todos os serviços do Lync Server em um computador

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação, clique em **Topologia** e clique em **Status**.

4.  Na página **Status**, classifique ou procure pela lista para encontrar o computador executando os serviços que você deseja iniciar ou parar e clique neles.

5.  Clique em **Ação**.

6.  Clique em **Iniciar todos os serviços** ou **Parar todos os serviços**.

## Para iniciar ou parar um serviço específico

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação, clique em **Topologia** e clique em **Status**.

4.  Na página **Status**, classifique ou procure pela lista para encontrar o computador executando os serviços que você deseja iniciar ou parar e clique neles.

5.  Clique em **Propriedades**.

6.  Classifique a lista de serviços, se necessário e clique no serviço que você deseja iniciar ou parar.

7.  Clique em **Ação**.

8.  Clique em **Iniciar serviço** ou **Parar serviço**.

9.  Clique em **Fechar**.

## Consulte Também

#### Tarefas

[Evitar sessões de serviços no Lync Server 2013](lync-server-2013-prevent-sessions-for-services.md)  

#### Outros Recursos

[Gerenciando a topologia do Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)

