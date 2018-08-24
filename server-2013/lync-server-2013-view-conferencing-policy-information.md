---
title: Exibir informações da política de conferência
TOCTitle: Exibir informações da política de conferência
ms:assetid: e99fdc4d-926a-4e36-ac99-ab5035568847
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721918(v=OCS.15)
ms:contentKeyID: 49886456
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações da política de conferência

 

_**Tópico modificado em:** 2013-02-23_

No Painel de Controle do Lync Server 2013, você deve usar políticas de conferência para controlar como conferências são implementadas em sua implantação. Isso inclui as políticas de conferência a seguir:

  - Uma política global que é criada por padrão quando você implanta o Lync Server 2013.

  - Políticas de nível de usuário e site opcionais que você pode criar e usar para especificar como conferências são implementadas para sites ou usuários específicos.

## Para visualizar configurações de política de conferência

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e então clique em **Política de Conferência**.

4.  Na página de **Política de Conferência**, dê um clique duplo na política de conferência que você deseja visualizar.

5.  Em **Editar Filtro de Arquivo**, marque a caixa de seleção **Mostrar Detalhes…**.
    
    **Editar Política de Conferência - \<policy\>** abre exibindo as configurações para a política selecionada. Para obter detalhes sobre como configurar as definições, consulte [Criar ou Modificar uma Política de Conferência no Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md).

## Visualizando Políticas de Conferência Usando os Cmdlets do PowerShell do Lync Server

Políticas de conferência também podem ser visualizadas usando o PowerShell do Lync Server e o cmdlet Get-CsConferencingPolicy cmdlet. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Visualizando Políticas de Conferência

  - Para visualizar informações sobre todas as suas políticas de conferências, digite o seguinte comando no Shell de Gerenciamento do Lync Server e então pressione ENTER:
    
        Get-CsConferencingPolicy
    
    Isto irá retornar informações similares a isso:
    
        Identity                                  : Global
        AllowIPAudio                              : True
        AllowIPVideo                              : True
        AllowMultiView                            : True
        Description                               :
        AllowParticipantControl                   : True
        AllowAnnotations                          : True
        DisablePowerPointAnnotations              : False
        AllowUserToScheduleMeetingsWithAppSharing : True
        AllowNonEnterpriseVoiceUsersToDialOut     : False
        AllowAnonymousUsersToDialOut              : False
        AllowAnonymousParticipantsInMeetings      : True
        AllowExternalUsersToSaveContent           : True
        AllowExternalUserControl                  : False
        AllowExternalUsersToRecordMeeting         : False
        AllowPolls                                : True
        AllowSharedNotes                          : True
        EnableDialInConferencing                  : True
        EnableAppDesktopSharing                   : Desktop
        AllowConferenceRecording                  : False
        EnableP2PRecording                        : False
        EnableFileTransfer                        : True
        EnableP2PFileTransfer                     : True
        EnableP2PVideo                            : True
        AllowLargeMeetings                        : False
        EnableDataCollaboration                   : True
        MaxVideoConferenceResolution              : VGA
        MaxMeetingSize                            : 250
        AudioBitRateKb                            : 200
        VideoBitRateKb                            : 50000
        AppSharingBitRateKb                       : 50000
        FileTransferBitRateKb                     : 50000
        TotalReceiveVideoBitRateKb                : 6000
        EnableMultiViewJoin                       : True

Para maiores informações, consulte o tópico de ajuda para o cmdlet [Get-CsConferencingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsConferencingPolicy).

