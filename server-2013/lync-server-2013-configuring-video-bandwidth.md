---
title: Configuriando largura de banda de vídeo no Lync Server 2013
TOCTitle: Configuriando largura de banda de vídeo no Lync Server 2013
ms:assetid: 446bed91-b26f-4ab2-b2f5-36e6810b405b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204842(v=OCS.15)
ms:contentKeyID: 49306572
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuriando largura de banda de vídeo no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-02_

Lync Server 2013 inclui diversas configurações para gerenciamento de vídeo para conferências com vários grupos e dois grupos. Quando você implanta o Lync Server 2013, deve avaliar se a configuração padrão é adequada para a sua organização e modificá-la, caso necessário.

Os parâmetros descritos nesta seção se aplicam tanto a conferências de dois grupos quanto de vários grupos. Visualize ou modifique tais configurações utilizando um dos cmdlets a seguir:

  - **Get-CsConferencingPolicy**

  - **Set-CsConferencingPolicy**

  - **New-CsConferencingPolicy**

Verifique as configurações a seguir na sua política de conferência:

  - **VideoBitRateKb**   Esta configuração especifica a taxa de bit máximo de vídeo por segundo (kbps) utilizado pelo vídeo enviado pelo usuário. O valor padrão é 50000 kbps. Valores válidos vão de 0 a 50000.
    
    Essa configuração aplica-se separadamente a um vídeo principal e vídeo panorâmico.
    
    Exemplo: se você especificar 2000 kbps, então Lync Server poderá enviar 2000 kbps para o fluxo de vídeo principal e 2000 kbps par ao fluxo de vídeo panorâmico.
    
    > [!NOTE]  
    > A largura de banda de rede de vídeo máxima para um ponto de extremidade Lync 2013 é de 8000 kbps para o vídeo principal e 2500 kbps para o vídeo panorâmico. Esses valores máximos são alcançados apenas se vários vídeos são recebidos ou enviados. Para detalhes, consulte a seção &quot;Utilização de rede de tráfego de mídia&quot; em <a href="lync-server-2013-network-bandwidth-requirements-for-media-traffic.md">Requisitos de largura de banda de rede para tráfego de mídia no Lync Server 2013</a>. Essa seção lista a largura de banda máxima e típica para fluxo de vídeo para todas as resoluções suportadas.

  - **TotalReceiveVideoBitRateKb**   Esta configuração, que é nova no Lync Server 2013, especifica o bitrate máximo permitido (em kilobits por segundo) para todos os fluxos de vídeo recebidos pelo cliente. Isto é, especifica o total combinado para todos os fluxos de vídeo, exceto fluxos de vídeo panorâmico, que o cliente pode receber. Por exemplo, se você especificar 1500 kbps, então um cliente poderá receber até 1500 kbps de vídeo, o que pode consistir de vários fluxos de vídeo ou um único fluxo. Essa configuração aplica-se apenas a clientes Lync Server 2013.
    
    O valor padrão para **TotalReceiveVideoBitRateKb** é 50000 kbps. Se a configuração **EnableMultiviewJoin** para o Modo de exibiçãod e Galeria estiver definido como Verdadeiro, **TotalReceiveVideoBitRateKb** não deverá ser definido em menos de 420 kbps. Se a configuração **EnableMultiviewJoin** para o Modo de exibição de Galeria for definido como Falso, **TotalReceiveVideoBitRateKb** não deverá ser definido para menos de 100 kbps. Se **EnableMultiviewJoin** estiver definido como Verdadeiro e você define o valor para abaixo de 420 kbps, os valores se tornarão padrão para o valor limite. Esse limiar ajuda a evitar uma desconfiguração acidental que pode resultar de uma experiência de usuário pobre.
    
    > [!NOTE]  
    > For details about the <strong>EnableMultiviewJoin</strong> setting, see <a href="lync-server-2013-configuring-gallery-view.md">Configurando o modo de exibição de galeria</a>.

  - **MaxVideoConferencingResolution**   This parameter is no longer used for Lync Server 2013 clients in Lync Server 2013 conferences. Lync Server 2013 conferences use the bit rate controls described earlier in this section. This setting is still used for legacy clients joining a Lync Server 2013 conference. This parameter determines the maximum resolution allowed for legacy clients in conferences organized by users who are homed on Lync Server 2013. That is, legacy clients are treated the same as they were in previous versions of Lync Server or Office Communications Server.

In addition to conferencing policy settings that apply to users, evaluate media configuration settings. View or modify these settings by using one of the following cmdlets:

  - **Get-CsMediaConfiguration**

  - **Set- CsMediaConfiguration**

  - **New- CsMediaConfiguration**

Verify the following setting:

  - **MaxVideoRateAllowed**   This per-pool setting specifies the maximum rate at which video signals will be transferred at the client endpoints. It applies only to previous versions of Lync Server clients.
    
    > [!NOTE]  
    > Lync Server 2013 clients ignore this setting and use the TotalReceiveVideoBitRateKb setting in conferencing policy instead.    
    The default value is HD720P. Valid values are HD720p15M, VGA600K, and CIF250K.
    
    Example: If you specify 1500 kbps, then all the legacy clients in the pool can receive up to 1500 kbps of video in two-party or multiparty conferences.

The following procedures are examples of using Shell de Gerenciamento do Lync Server to modify the settings described in this section.

## To modify conferencing policy for video settings

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  At the command line, run the following cmdlet to edit conferencing policy:
    
        Set-CsConferencingPolicy -Identity Pool01ConferencingPolicy -VideoBitRateKb 2000 -TotalReceiveVideoBitRateKb 2000 

## To modify media configuration for legacy clients

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  At the command line, run the following cmdlet to edit the media configuration:
    
        Set-CsMediaConfiguration -Identity site:Redmond01 -MaxVideoRateAllowed CIF250K

