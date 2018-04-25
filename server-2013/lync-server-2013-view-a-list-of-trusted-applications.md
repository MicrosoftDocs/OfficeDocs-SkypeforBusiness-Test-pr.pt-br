---
title: Exibir uma lista de aplicativos confiáveis
TOCTitle: Exibir uma lista de aplicativos confiáveis
ms:assetid: f09300b3-67cf-4e70-a51a-23d62479b913
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182604(v=OCS.15)
ms:contentKeyID: 49308544
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir uma lista de aplicativos confiáveis

 

_**Tópico modificado em:** 2012-09-21_

É possível usar o Painel de Controle do Lync Server 2013 para exibir uma lista de aplicativos confiáveis implantados no seu ambiente do Lync Server 2013. Um aplicativo confiável é um aplicativo baseado no API do Microsoft Unified Communications Managed (UCMA) 3.0 Core SDK confiável pelo Lync Server 2013. Este relacionamento de confiança é resumido na seguinte lista:

  - Os aplicativos confiáveis não são desafiados para autenticação pelo Lync Server.

  - Aplicativos confiáveis não são acelerados pelo Lync Server para transações SIP, conexões ou chamadas VoIP de saída.

  - Os aplicativos confiáveis podem representar qualquer usuário e participar de conferências sem aparecer em escalações.

  - Os aplicativos confiáveis são altamente disponíveis e flexíveis.

No Painel de Controle do Lync Server, é possível ver o nome dos aplicativos, o pool onde são executados e a porta que usam.

## Para exibir uma lista de aplicativos confiáveis

1.  Usando uma conta de usuário atribuída à função do CsServerAdministrator, CsAdministrator, CsHelpDesk, ou CsViewOnlyAdministrator, faça logon em qualquer computador de sua implantação interna. Para obter detalhes sobre as funções administrativas predefinidas disponíveis no Lync Server 2013, consulte [Planejamento de controle de acesso baseado em função no Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Topologia** e em **Aplicativos confiáveis**.

4.  Na página **Aplicativos confiáveis**, clique no cabeçalho da coluna para classificar os aplicativos, se necessário.

## Consulte Também

#### Outros Recursos

[Gerenciando a topologia do Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)

