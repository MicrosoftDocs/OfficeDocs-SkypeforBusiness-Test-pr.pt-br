---
title: (Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013
TOCTitle: (Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013
ms:assetid: 56c37b3b-6517-49b9-86b7-ae48cc349119
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688063(v=OCS.15)
ms:contentKeyID: 49886226
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# (Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-07_

As configurações de feriados definem os dias nos quais um grupo de respostas estará fechado para negócios e especificam a ação a ser tomada nesses dias. Um conjunto de feriados é a coleção de feriados que se aplicam a um grupo de respostas.

> [!NOTE]  
> Se um fluxo de trabalho for definido como um fluxo de trabalho gerenciado, então qualquer usuário que estiver atribuído à função CsResponseGroupManager poderá definir e modificar feriados para fluxos de trabalho que eles gerenciam.

## Para criar um conjunto de feriados

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para cada feriado que você deseja definir, execute:
    
        $x = New-CsRgsHoliday [-Name <holiday name>] -StartDate <starting date of holiday> -EndDate <ending date of holiday>
    
    Para criar o conjunto de feriados que contém os feriados que você definiu, execute:
    
        New-CsRgsHolidaySet -Parent <service where the workflow is hosted> -Name <unique name for holiday set> -HolidayList <one or more holidays to be included in the holiday set>
    
    O exemplo a seguir mostra um conjunto de feriados que inclui dois feriados:
    
        $a = New-CsRgsHoliday -Name "New Year's Day" -StartDate "1/1/2013 12:00 AM" -EndDate "1/1/2013 12:00 AM" 
        $b = New-CsRgsHoliday -Name "Independence Day" -StartDate "7/4/2013 12:00 AM" -EndDate "7/5/2013 12:00 AM" 
        New-CsRgsHolidaySet -Parent "ApplicationServer:Redmond.contoso.com -Name "2013 Holidays" -HolidayList ($a, $b)

## Consulte Também

#### Conceitos

[Criar ou modificar um fluxo de trabalho de grupo de busca no Lync Server 2013](lync-server-2013-create-or-modify-a-hunt-group-workflow.md)  
[Criar ou modificar um fluxo de trabalho interativo no Lync Server 2013](lync-server-2013-create-or-modify-an-interactive-workflow.md)  

#### Outros Recursos

[New-CsRgsHoliday](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsHoliday)  
[New-CsRgsHolidaySet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsHolidaySet)

