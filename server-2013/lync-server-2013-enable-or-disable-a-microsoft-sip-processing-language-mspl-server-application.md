---
title: "Hab./Desab. um app do servidor de idiomas de proc. SIP da Microsoft (MSPL)"
TOCTitle: "Hab./Desab. um app do servidor de idiomas de proc. SIP da Microsoft (MSPL)"
ms:assetid: b20af38d-224a-4459-991d-0b7eabb3ca7c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182573(v=OCS.15)
ms:contentKeyID: 49307852
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar um aplicativo do servidor de idiomas de processamento SIP da Microsoft (MSPL)

 

_**Tópico modificado em:** 2012-09-21_

Você pode usar o Painel de Controle do Lync Server para habilitar ou desabilitar aplicativos de servidor do Microsoft SIP Processing Language (MSPL) que funcionam em seu ambiente do Lync Server 2013. Esses aplicativos são aplicativos somente com scripts que usam uma linguagem de scripts em vez do API do Microsoft Lync 2013 Preview.

Nem todos os scripts podem ser habilitados ou desabilitados. Por exemplo, o script DefaultRouting está habilitado e essa opção não pode ser alterada para DefaultRouting.

## Para habilitar ou desabilitar um aplicativo de servidor do MSPL

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Topologia** e em **Aplicativo de Servidor**.

4.  Na página **Aplicativo de Servidor**, clique no título de uma coluna para classificar os aplicativos, se for necessário, e clique no aplicativo de servidor que você deseja modificar.

5.  Clique em **Ação**.

6.  Clique em **Habilitar aplicativo** ou **Desabilitar aplicativo** (ou seja, se o script suportar essa opção).

## Consulte Também

#### Tarefas

[Marcar um aplicativo de idioma de processamento SIP da Microsoft (MSPL) como crítico ou não crítico](lync-server-2013-mark-a-microsoft-sip-processing-language-mspl-application-as-critical-or-not-critical.md)  

#### Conceitos

[Exibir aplicativos de servidor do Idioma de Processamento SIP da Microsoft (MSPL) no Lync Server 2013](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  

#### Outros Recursos

[Gerenciando a topologia do Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)

