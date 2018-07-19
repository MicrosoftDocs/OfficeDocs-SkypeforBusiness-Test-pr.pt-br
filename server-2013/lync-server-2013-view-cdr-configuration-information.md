---
title: Visualizar Informações de Configuração do CDR
TOCTitle: Visualizar Informações de Configuração do CDR
ms:assetid: 77bd553f-da89-4c84-a5d0-2f7e91d04383
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688096(v=OCS.15)
ms:contentKeyID: 49886268
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizar Informações de Configuração do CDR

 

_**Tópico modificado em:** 2013-02-23_

O CDR (registro de detalhes de chamadas) permite rastrear o uso de aspectos como as sessões de mensagens instantâneas ponto a ponto, chamadas de telefone VoIP e chamadas de conferência. Esses dados de uso incluem informações os usuários envolvidos na chamadas, o horário e o período da chamada.

Quando você instala o Microsoft Lync Server 2013, um conjunto global e exclusivo de configurações de CDR é criado para você. Os administradores também têm a opção de criar conjuntos de configurações personalizadas que podem ser aplicadas a sites individuais. Você pode visualizar as configurações de CDR usadas pela organização usando o Painel de Controle do Lync Server ou o cmdlet [Get-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCdrConfiguration).

## Para visualizar informações de configuração de CDR usando o Painel de Controle do Lync Server

1.  No Painel de Controle do Lync Server, clique em **Monitoramento e arquivamento**.

2.  Uma lista com todas as configurações de CDR será exibida na guia **Registro de Detalhes de Chamada**. Para cada conjunto de configurações, você verá o **Nome** do conjunto; se o CDR foi habilitado ou não (a propriedade **CDR**); e se a limpeza foi habilitada ou não (a propriedade **Limpeza de CDR**). Para ver informações detalhadas sobre um conjunto, clique duas vezes no conjunto ou selecione o conjunto correto, clique em **Editar** e em **Mostrar Detalhes**. Observe que só é possível visualizar informações detalhadas de um conjunto de configurações de CDR por vez.

## Para visualizar informações de configuração de CDR usando os cmdlets do Shell de Gerenciamento do Lync Server

Você também pode visualizar configurações de CDR usando o Shell de Gerenciamento do Lync Server e o cmdlet Get-CsCdrConfiguration cmdlet. Você pode executar esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para visualizar informações de configuração do CDR

  - Para visualizar informações sobre todas as configurações de CDR, digite o comando a seguir no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsCdrConfiguration
    
    Esse comando retornará informações semelhantes a estas:
    
        Identity               : Global
        EnableCDR              : True
        EnablePurging          : True
        KeepCallDetailForDays  : 90
        KeepErrorReportForDays : 60
        PurgeHourOfDay         : 2

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCdrConfiguration).

