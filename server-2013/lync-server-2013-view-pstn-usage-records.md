---
title: 'Lync Server 2013: Exibir registros de uso PSTN'
TOCTitle: Exibir registros de uso PSTN
ms:assetid: 65025c78-c263-472c-9ff9-e170588f10b5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398458(v=OCS.15)
ms:contentKeyID: 49306928
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir registros de uso PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

Um registro de uso de PSTN (rede telefônica pública comutada) especifica uma classe de chamada (por exemplo, interna, local ou interurbana) que pode ser feita por vários usuários ou grupos de usuários em uma organização. Para obter detalhes, consulte [Registros de uso de PSTN no Lync Server 2013](lync-server-2013-pstn-usage-records.md) na documentação de planejamento.

## Para exibir um registro de uso do PSTN ao usar Painel de Controle do Lync Server

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Roteamento de voz** e em **Uso do PSTN** .

4.  Na página **Uso do PSTN** , destaque o registro de uso PSTN que você deseja exibir, clique em **Editar** e em **Mostrar detalhes** .
    
    > [!NOTE]  
    > Uma página somente leitura do registro de uso PSTN selecionado mostra as rotas associadas e as políticas de voz associadas.

## Exibindo as informações de uso do PSTN usando cmdlets do Windows PowerShell

Você também pode exibir as informações de uso de PSTN usando o Windows PowerShell e o cmdlet **Get-CsPstnUsage**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para exibir as informações de uso do PSTN usando cmdlets do Windows PowerShell

  - Para exibir informações sobre todos os usos de PSTN, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsPstnUsage
    
    Este comando retorna informações semelhantes para o seguinte:
    
        Identity : Global
        Usage    : {Internal, Local, Long Distance}

Para obter detalhes, consulte [Get-CsPstnUsage](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPstnUsage).

## Consulte Também

#### Tarefas

[Criar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-create-a-voice-policy-and-configure-pstn-usage-records.md)  
[Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)

