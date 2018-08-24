---
title: Exibir Definições de Configuração de Reunião
TOCTitle: Exibir Definições de Configuração de Reunião
ms:assetid: d03a4684-9d8b-4728-917d-5b5c91511e2c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721894(v=OCS.15)
ms:contentKeyID: 49886424
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Definições de Configuração de Reunião

 

_**Tópico modificado em:** 2013-02-23_

No Painel de Controle do Lync Server 2013, você usa uma definição de configuração de reunião para controlar como as reuniões são implementadas em sua implantação. Isto inclui a seguintes configurações de reunião:

  - Uma configuração global criada por padrão ao implantar o Lync Server 2013.

  - Configurações a nível do usuário ou do site opcionais que você cria e usa para especificar como as reuniões são implementadas para sites ou usuários específicos.

## Para exibir configurações de reunião

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Conferência** e em **Configuração da reunião**.

4.  Na página **Configuração de Reunião**, clique na configuração de reunião que você deseja exibir.

5.  Em **Editar Filtro de Arquivo**, marque a caixa de seleção **Mostrar detalhes...**.
    
    **Editar configuração da reunião - \<política\>** abre exibindo as configurações da política selecionada. Para obter detalhes sobre a definição da configuração, consulte [Criar ou Modificar um Conjunto de Configurações de Reunião no Lync Server 2013](lync-server-2013-create-or-modify-a-collection-of-meeting-configuration-settings.md).

## Exibindo informações de configuração da reunião utilizando os cmdlets do Lync Server PowerShell

As configurações da reunião também podem ser exibidas utilizando o Lync Server PowerShell e o cmdlet Get-CsMeetingConfiguration. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Exibir informações de configuração da reunião

  - Para exibir informações sobre todas as configurações de reunião, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsMeetingConfiguration
    
    Isto retorna informações semelhantes à seguinte:
    
        Identity                        : Global
        PstnCallersBypassLobby          : True
        EnableAssignedConferenceType    : True
        DesignateAsPresenter            : Company
        AssignedConferenceTypeByDefault : True
        AdmitAnonymousUsersByDefault    : True
        RequireRoomSystemsAuthorization : False
        LogoURL                         :
        LegalURL                        :
        HelpURL                         :
        CustomFooterText                :
        AllowConferenceRecording        : True

Para obter mais informações, consulte o tópico de ajuda para o cmdlet do [Get-CsMeetingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMeetingConfiguration).

