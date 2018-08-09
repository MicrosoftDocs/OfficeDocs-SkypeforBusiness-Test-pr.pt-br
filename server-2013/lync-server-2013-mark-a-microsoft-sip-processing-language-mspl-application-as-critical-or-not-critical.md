---
title: "Marcar app de idioma de proc. SIP da Microsoft (MSPL) como crítico/não crítico"
TOCTitle: "Marcar app de idioma de proc. SIP da Microsoft (MSPL) como crítico/não crítico"
ms:assetid: df68fdc6-b7e6-4f07-acdc-0cd4c2c888a1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182598(v=OCS.15)
ms:contentKeyID: 49308356
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Marcar um aplicativo de idioma de processamento SIP da Microsoft (MSPL) como crítico ou não crítico

 

_**Tópico modificado em:** 2012-11-01_

Os aplicativos de servidor da MSPL (Microsoft SIP Processing Language) são aplicativos somente script que usam a linguagem de script MSPL no lugar da API do Microsoft Lync 2010. Alguns aplicativos de servidor MSPL são especificados como críticos. Se um script for crítico, ele deverá ser iniciado durante a inicialização do sistema para que o Lync Server 2013 seja iniciado. Se houver falha no script enquanto o Lync Server estiver em execução, o servidor não será desligado, mas deixará de enviar tráfego para o script e gravará erros no log de eventos.

Você pode usar o Painel de Controle do Lync Server para marcar aplicativos de servidor MSPL (Microsoft SIP Processing Language) como críticos ou desmarcá-los.

Nem todos os scripts suportam essa opção. Por exemplo, o script DefaultRouting é marcado como crítico e essa opção não pode ser alterada para DefaultRouting.

## Para marcar ou desmarcar um aplicativo de servidor MSPL como crítico

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Topologia** e em **Aplicativo de Servidor**.

4.  Na página **Aplicativo de Servidor**, clique no título de uma coluna para classificar os aplicativos, se for necessário, e clique no aplicativo de servidor que você deseja modificar.

5.  Clique em **Ação**.

6.  Clique em **Marcar como crítico** ou **Desmarcar como crítico** (ou seja, se o script suportar essa opção).

## Consulte Também

#### Tarefas

[Habilitar ou desabilitar um aplicativo do servidor de idiomas de processamento SIP da Microsoft (MSPL)](lync-server-2013-enable-or-disable-a-microsoft-sip-processing-language-mspl-server-application.md)  

#### Conceitos

[Exibir aplicativos de servidor do Idioma de Processamento SIP da Microsoft (MSPL) no Lync Server 2013](lync-server-2013-view-microsoft-sip-processing-language-mspl-server-applications.md)  

#### Outros Recursos

[Gerenciando a topologia do Lync Server 2013](lync-server-2013-managing-the-lync-server-topology.md)

