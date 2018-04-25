---
title: Evitar sessões de serviços no Lync Server 2013
TOCTitle: Evitar sessões de serviços no Lync Server 2013
ms:assetid: 977dcc5c-2aac-48ef-86a1-a8d47b4d9e74
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182553(v=OCS.15)
ms:contentKeyID: 49307540
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Evitar sessões de serviços no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Você pode usar o Painel de Controle do Lync Server para impedir novas sessões de todos os serviços do Lync Server 2013 em execução em um computador específico ou para impedir novas sessões de um serviço específico do Lync Server 2013.

## Para impedir novas sessões para todos os serviços do Lync Server em um computador

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Topologia** e em **Status**.

4.  Na página **Status**, classifique ou pesquise na lista conforme o necessário para encontrar o computador que está executando os serviços para os quais você deseja impedir novas sessões e clique nele.

5.  Clique em **Ação**.

6.  Clique em **Impedir novas sessões para todos os serviços**.

## Para impedir novas sessões para um serviço específico

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Topologia** e em **Status**.

4.  Na página **Status**, classifique ou pesquise na lista conforme o necessário para encontrar o computador que está executando o serviço que você deseja iniciar ou interromper e clique nele.

5.  Clique em **Propriedades**.

6.  Classifique a lista de serviços, se necessário e clique no serviço para o qual você deseja impedir novas sessões.

7.  Clique em **Ação**.

8.  Clique em **Impedir novas sessões para o serviço**.

9.  Clique em **Fechar**.

## Consulte Também

#### Outros Recursos

[Gerenciando a topologia do Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)

