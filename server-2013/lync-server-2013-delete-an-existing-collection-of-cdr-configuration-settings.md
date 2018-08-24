---
title: Excluir um conjunto existente das configurações do CDR
TOCTitle: Excluir um conjunto existente das configurações do CDR
ms:assetid: 8ebf5da8-c0fc-498c-8d85-527d3be8479a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688128(v=OCS.15)
ms:contentKeyID: 49886306
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um conjunto existente das configurações do CDR

 

_**Tópico modificado em:** 2013-02-23_

O registro de detalhes das chamadas (CDR) permite rastrear o uso de aspectos como as sessões de mensagens instantâneas ponto a ponto, chamadas de telefone VoIP e chamadas de conferência. Esses dados de uso incluem informações os usuários envolvidos na chamadas, o horário e o período da chamada.

Ao instalar o Microsoft Lync Server 2013, uma coleção única e global de definições de configuração de CDR é criada para você. Os administradores têm a opção de criar coleções de definições personalizadas que podem ser aplicadas a sites individuais. Através do design, as definições configuradas no escopo do site têm precedência sobre aquelas no escopo global. Se você excluir as definições no escopo do site, então o CDR será gerenciado nesse site usando as definições globais.

Observe que também é possível "excluir" as definições globais. No entanto, as definições globais não serão realmente removidas. Em vez disso, todas as propriedades nessa coleção serão redefinidas para os valores padrão. Por exemplo, como padrão, a limpeza está ativada em uma coleção de definições de configuração de CDR. Suponha que você modifique a coleção global de forma que a limpeza seja desativada. Se você excluir as definições globais mais tarde, todas as propriedades serão redefinidas para seus valores padrão. Neste caso, isso significa que a limpeza será novamente ativada.

Você pode remover as definições de configuração de CDR usando o Painel de Controle do Lync Server, ou o cmdlet [Remove-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCdrConfiguration).

## Para remover as definições de configuração de CDR usando o Painel de Controle do Lync Server

1.  Em Painel de Controle do Lync Server, clique em **Monitoramento e arquivamento**.

2.  Na guia **Registro de Detalhes de Chamada**, selecione a coleção (ou coleções) de definições de CDR a serem removidas. Para selecionar várias coleções, clique na primeira coleção, mantenha pressionada a tecla CTRL e clique em mais coleções.

3.  Clique em **Editar** e depois em **Excluir**.

4.  Na caixa de diálogo Painel de Controle do Lync Server, clique em **OK**.

## Para remover as definições de configuração de CDR usando os cmdlets do Shell de Gerenciamento do Lync Server

Você pode excluir as definições de configuração de gravação de detalhes de chamada usando o Windows PowerShell e cmdlet**Remove-CsCdrConfiguration**. Esse cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover uma coleção especificada das definições de configuração de CDR

  - Este comando remove as definições de configuração de CDR aplicadas ao site da Redmond:
    
        Remove-CsCdrConfiguration -Identity "site:Redmond"

## Para remover todas as definições de configuração de CDR aplicadas ao escopo do site

  - Este comando remove todas as definições de configuração de CDR aplicadas ao escopo do site:
    
        Get-CsCdrConfiguration -Filter "site:*" | Remove-CsCdrConfiguration

## Para remover todas as definições de configuração de CDR que desativam a gravação de detalhes de chamada

  - Este comando remove todas as definições de configuração de CDR onde a gravação de detalhes de chamada foi desativada:
    
        Get-CsCdrConfiguration | Where-Object {$_.EnableCDR -eq $False} | Remove-CsCdrConfiguration

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Remove-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCdrConfiguration).

