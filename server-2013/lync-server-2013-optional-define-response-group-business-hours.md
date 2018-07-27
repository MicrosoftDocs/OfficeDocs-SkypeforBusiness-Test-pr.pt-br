---
title: 'Lync Server 2013: (Opcional) Definir horário comercial do Grupo de Resposta'
TOCTitle: (Opcional) Definir horário comercial do Grupo de Resposta
ms:assetid: d62551b2-1847-4e1b-abe8-683b72aa94d5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205291(v=OCS.15)
ms:contentKeyID: 49308244
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Definir horário comercial do Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

## Definir o horário comercial

As configurações de horário comercial definem quando o fluxo de trabalho está disponível para atender a chamadas e especificar as ações a serem executadas para chamadas fora do horário comercial. Os administradores do Grupo de Resposta podem usar o cmdlet **New-CsRgsHoursOfBusiness** para criar programações predefinidas que você pode usar para vários grupos de resposta.


> [!TIP]
> Ao criar ou modificar um fluxo de trabalho, é possível especificar uma programação personalizada aplicada apenas a este fluxo de trabalho. Para obter detalhes, consulte <A href="lync-server-2013-create-or-modify-a-hunt-group-workflow.md">Criar ou modificar um fluxo de trabalho de grupo de busca no Lync Server 2013</A> ou <A href="lync-server-2013-create-or-modify-an-interactive-workflow.md">Criar ou modificar um fluxo de trabalho interativo no Lync Server 2013</A>.



> [!NOTE]  
> Se um fluxo de trabalho é definido como o Fluxo de trabalho gerenciado, qualquer usuário com a função CsResponseGroupManager atribuída pode definir e modificar o horário comercial personalizado para fluxos de trabalho que gerenciam.

> [!IMPORTANT]  
> Use a notação 24 horas para os parâmetros nos seguintes cmdlets (por exemplo, 20:00=20:00 horas).

## Para criar um conjunto de horário comercial predefinido

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para cada intervalo de horas exclusivo que você deseja definir, execute:
    
        $x = New-CsRgsTimeRange [-Name <name of time range>] -OpenTime <time when business hours begin> -CloseTime <time when business hours end>
    
    Para criar o conjunto de horário comercial que usa os intervalos definidos, execute:
    
        New-CsRgsHoursOfBusiness -Parent <service where the workflow is hosted> -Name <unique name for collection> [-MondayHours1 <first set of opening and closing times for Monday>] [-MondayHours2 <second set of opening and closing times for Monday>] [-TuesdayHours1 <first set of opening and closing times for Tuesday>] [-TuesdayHours2 <second set of opening and closing times for Tuesday>] [-WednesdayHours1 <first set of opening and closing times for Wednesday>] [-WednesdayHours2 <second set of opening and closing times for Wednesday>] [-ThursdayHours1 <first set of opening and closing times for Thursday>] [-ThursdayHours2 <second set of opening and closing times for Thursday>] [-FridayHours1 <first set of opening and closing times for Friday>] [-FridayHours2 <second set of opening and closing times for Friday>] [-SaturdayHours1 <first set of opening and closing times for Saturday>] [-SaturdayHours2 <second set of opening and closing times for Saturday>] [-SundayHours1 <first set of opening and closing times for Sunday>] [-SundayHours2 <second set of opening and closing times for Sunday>]
    
    O exemplo a seguir especifica o horário comercial de 9:00: 00 às 17:00 para dias úteis, de 8: 00 a 10:00: 00 e novamente a partir de 14: 00. às 18:00 nos sábados e horário não comercial nos domingos:
    
        $a = NewRgsTimeRange -Name "Weekday Hours" -OpenTime "9:00" -CloseTime "17:00"
        $b = NewRgsTimeRange -Name "Saturday Morning Hours" -OpenTime "8:00" -CloseTime "10:00" 
        $c = NewRgsTimeRange -Name "Saturday Afternoon Hours" -OpenTime "14:00" -CloseTime "18:00" 
        New-CsRgsHoursOfBusiness -Parent "ApplicationServer:Redmond.contoso.com" -Name "Help Desk Business Hours" -MondayHours1 $a -TuesdayHours1 $a -WednesdayHours1 $a -ThursdayHours1 $a -FridayHours1 $a -SaturdayHours1 $b -SaturdayHours2 $c

## Consulte Também

#### Conceitos

[Criar ou modificar um fluxo de trabalho de grupo de busca no Lync Server 2013](lync-server-2013-create-or-modify-a-hunt-group-workflow.md)  
[Criar ou modificar um fluxo de trabalho interativo no Lync Server 2013](lync-server-2013-create-or-modify-an-interactive-workflow.md)  

#### Outros Recursos

[New-CsRgsTimeRange](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsTimeRange)  
[New-CsRgsHoursOfBusiness](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsHoursOfBusiness)

