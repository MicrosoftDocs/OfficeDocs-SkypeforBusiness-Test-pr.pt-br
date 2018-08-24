---
title: 'Lync Server 2013: Habilitar Estacionamento de Chamadas para usuários'
TOCTitle: Habilitar Estacionamento de Chamadas para usuários
ms:assetid: 9430763f-3394-467c-9c6d-426bf761604e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398753(v=OCS.15)
ms:contentKeyID: 49307494
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar Estacionamento de Chamadas para usuários no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-11_

Os usuários não podem estacionar chamadas ou recuperar chamadas estacionadas até estarem habilitados para o Estacionamento de Chamada na política de voz.

> [!NOTE]  
> Por padrão, o Estacionamento de Chamada está desativado para todos os usuários.

Você pode habilitar o Estacionamento de Chamada no escopo global, ou escopo do site ou do usuário. O escopo do usuário tem precedência sobre o escopo do site e o escopo do site tem precedência sobre o escopo global. Se você tem várias políticas de voz, reveja todas as políticas para habilitar o Estacionamento de Chamada, não somente a política global.

## Para usar o Painel de Controle do Lync Server para habilitar o Estacionamento de Chamada para os usuários

1.  Faça logon no computador como membro do grupo **RTCUniversalServerAdmins** ou como membro da função administrativa **CsVoiceAdministrator** , **CsServerAdministrator** , ou **CsAdministrator** .

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerdo, clique em **Roteamento de voz** .

4.  Clique na guia **Política de Voz** .

5.  Dê um duplo clique sobre uma política de voz existente para abrir a caixa de diálogo **Editar Política de Voz** .

6.  Sob **Recursos de Chamadas** , selecione **Habilitar o estacionamento de chamadas** .

7.  Clique em **OK** para salvar a política de voz

## Para usar cmdlets para habilitar o Estacionamento de Chamada para os usuários

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função administrativa CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Set-CsVoicePolicy -Identity <VoicePolicy> -EnableCallPark $true
    
    Por exemplo, para habilitar o Estacionamento de Chamada para a política de voz global:
    
        Set-CsVoicePolicy -EnableCallPark $true

## Consulte Também

#### Tarefas

[Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)

