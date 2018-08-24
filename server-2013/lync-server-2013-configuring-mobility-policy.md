---
title: 'Lync Server 2013: Configurando a política de mobilidade'
TOCTitle: Configurando a política de mobilidade
ms:assetid: 595536e0-9bb3-49a3-8d13-1a77351ebc62
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690018(v=OCS.15)
ms:contentKeyID: 49306796
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a política de mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-13_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

O Lync Server 2013 traz políticas de mobilidade que determinam quem pode usar os recursos de mobilidade, Chamada via Trabalho, voz por IP (VoIP) ou vídeo, determinando também se WiFi será necessário ou não para uso de VoIP ou vídeo. O recurso de Chamada via Trabalho permite que um usuário móvel faça e receba chamadas de um telefone celular usando um número de telefone comercial em vez do número de telefone celular. Esse recurso impede que a parte recebendo a chamada veja o número de telefone celular de quem a realiza e permite que um usuário evite as tarifas de chamada de saída. Configurar VoIP e vídeo faz com que seja possível para os usuários realizar e receber chamadas VoIP e de vídeo. As configurações para uso de WiFi definem se o dispositivo de um usuário precisará utilizar uma rede WiFi em vez da rede de dados do celular.

Por padrão, os recursos de mobilidade, Chamada via Trabalho, VoIP e vídeo estão habilitados. As configurações que determinam exigência de WiFi para VoIP e vídeo estão desabilitadas. Os administradores podem determinar quem tem acesso a esses recursos executando um cmdlet. Você pode desabilitar as opções globalmente, por site ou por usuário.

Para poder usar os recursos de mobilidade e Telefonar via Trabalho, os usuários devem atender aos seguintes pré-requisitos:

  - Os usuários devem ser habilitados para o Lync Server 2013.

  - Os usuários devem ser habilitados para o Enterprise Voice.

  - Os usuários deve ser atribuídos a uma política de mobilidade que tem a opção **EnableMobility** definida como True.

Para que os usuários possam usar o Telefonar via Trabalho, eles devem atender aos dois seguintes pré-requisitos adicionais:

  - Os usuários devem ser atribuídos a uma política de voz tem a opção **Habilitar toques de telefones simultâneos** selecionada.

  - Os usuários devem ser atribuídos a uma política de mobilidade que tem a opção **EnableOutsideVoice** definida como True.

> [!NOTE]  
> Os usuários que não estão habilitados para o Enterprise Voice podem usar seus dispositivos móveis para realizar chamadas de Lync para Lync por VoIP, ou ingressar em conferências usando o link Clique para Ingressar em seus dispositivos móveis, quando você atribuir aos usuários as opções apropriadas para política de voz. Para detalhes, consulte <a href="lync-server-2013-defining-your-mobility-requirements.md">Definindo seus requisitos de mobilidade para Lync Server 2013</a>.

Para detalhes sobre como habilitar usuários para o Lync Server 2013, consulte [Habilitar ou reabilitar uma conta de usuário para o Lync Server](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md). Para detalhes sobre como habilitar usuários para o Enterprise Voice, consulte [Habilitar usuários para Enterprise Voice no Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md). Para detalhes sobre como definir opções de política de voz, consulte [Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md).

## Para modificar a política global de mobilidade

1.  Faça logon em qualquer computador onde o Shell de Gerenciamento do Lync Server e o Ocscore estão instalados como membro da função CsAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Desabilite o acesso à mobilidade e Telefonar via Trabalho globalmente. Na linha de comando, digite:
    
        Set-CsMobilityPolicy -EnableMobility $False -EnableOutsideVoice $False
    
    > [!NOTE]  
    > Você pode desabilitar o Telefonar via Trabalho sem desativar o acesso à mobilidade. No entanto, você não pode desabilitar a mobilidade sem também desabilitar o Telefonar via Trabalho.

## Para modificar a política de mobilidade por site

1.  Faça logon em qualquer computador onde o Shell de Gerenciamento do Lync Server e o Ocscore estão instalados como membro da função CsAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Crie uma política de nível de site e desabilite VoIP e vídeo, então habilite Exigir WiFi para áudio por IP e para vídeo por IP pelo site. Na linha de comando, digite:
    
        New-CsMobilityPolicy -Identity site:<site identifier> -EnableIPAudioVideo $False -RequireWiFiForIPAudio $True -RequireWiFiForIPVideo $True

## Para modificar a política de mobilidade por usuário

1.  Faça logon em qualquer computador onde o Shell de Gerenciamento do Lync Server e o Ocscore estão instalados como membro da função CsAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Crie políticas de nível de mobilidade do usuário e desabilite a mobilidade e o Telefonar via Trabalho por usuário. Na linha de comando, digite:
    
        New-CsMobilityPolicy -Identity <policy name> -EnableMobility $False -EnableOutsideVoice $False
        Grant-CsMobilityPolicy -Identity <user identifier> -PolicyName <policy name>
    
    Você pode desabilitar o Telefonar via Trabalho sem desativar o acesso à mobilidade. No entanto, você não pode desabilitar a mobilidade sem também desabilitar o Telefonar via Trabalho.
    
    Por exemplo:
    
        New-CsMobilityPolicy "tag:disableOutsideVoice" -EnableOutsideVoice $False
        Grant-CsMobilityPolicy -Identity -MobileUser1@contoso.com -PolicyName Tag:disableOutsideVoice

## Consulte Também

#### Tarefas

[Habilitar ou reabilitar uma conta de usuário para o Lync Server](lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md)  
[Habilitar usuários para Enterprise Voice no Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md)  
[Modificar uma política de voz e configurar registros de uso PSTN no Lync Server 2013](lync-server-2013-modify-a-voice-policy-and-configure-pstn-usage-records.md)  

#### Conceitos

[Definindo seus requisitos de mobilidade para Lync Server 2013](lync-server-2013-defining-your-mobility-requirements.md)  

#### Outros Recursos

[New-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy)  
[Set-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMobilityPolicy)  
[Get-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsMobilityPolicy)  
[Grant-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Grant-CsMobilityPolicy)  
[Remove-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsMobilityPolicy)

