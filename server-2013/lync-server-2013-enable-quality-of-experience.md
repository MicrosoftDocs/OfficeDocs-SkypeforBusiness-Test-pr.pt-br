---
title: Habilitar a qualidade da experiência
TOCTitle: Habilitar a qualidade da experiência
ms:assetid: c8bb3c67-b324-4d94-8158-00c792c7ac42
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182583(v=OCS.15)
ms:contentKeyID: 49308070
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar a qualidade da experiência

 

_**Tópico modificado em:** 2013-02-23_

A QoE (Qualidade da Experiência) registra dados numéricos que indicam a qualidade da mídia e informações sobre participantes, nomes de dispositivo, drivers, endereços IP e tipos de ponto de extremidade envolvidos em chamadas e sessões. Para obter detalhes, consulte [Planejamento de monitoramento no Lync Server 2013](lync-server-2013-planning-for-monitoring.md), na documentação de Planejamento.

Use o procedimento a seguir para habilitar QoE para toda sua organização ou para cada site em sua organização.

> [!NOTE]  
> Para habilitar o QoE, é necessário primeiro configurar o monitoramento e um back-end de monitoramento. Para obter detalhes, consulte <a href="lync-server-2013-deploying-monitoring.md">Implantando o monitoramento no Lync Server 2013</a>.

## Para habilitar o QoE usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Monitoramento e Arquivamento** e em **Dados da Qualidade da Experiência**.

4.  Na página **Dados da Qualidade da Experiência**, clique no conjunto adequado na tabela, clique em **Ação** e em **habilitar QoE**.

## Para habilitar o QoE pelo uso dos cmdlets Windows PowerShell

É possível habilitar QoE usando o Windows PowerShell e o cmdlet **Set-CsQoEConfiguration**. É possível executar este cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para habilitar o QoE para um único local

  - Para habilitar o QoE, defina o parâmetro EnableQoE para True ($True).
    
        Set-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $True

## Para desabilitar o QoE para um único local

  - Para desabilitar o QoE, defina o parâmetro EnableQoE para False ($False). Isto não desinstala o monitoramento. Pausa o conjunto e armazena os dados do QoE.
    
        Set-CsQoEConfiguration -Identity "site:Redmond" -EnableQoE $False

## Para usar um único comando para habilitar o QoE em vários locais

  - Este comando habilita o QoE para todas as definições de configuração do QoE atualmente em uso na sua organização.
    
        Get-CsQoEConfiguration | Set-CsQoEConfiguration "site:Redmond" -EnableQoE $True

Para obter detalhes, consulte [Set-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsQoEConfiguration).

## Consulte Também

#### Outros Recursos

[Planejamento de monitoramento no Lync Server 2013](lync-server-2013-planning-for-monitoring.md)  
[Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md)

