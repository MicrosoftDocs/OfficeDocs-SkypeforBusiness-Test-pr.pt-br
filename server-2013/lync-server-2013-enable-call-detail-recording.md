---
title: Habilitar gravação de detalhes da chamada
TOCTitle: Habilitar gravação de detalhes da chamada
ms:assetid: 3b28e432-596f-45a5-a070-577d6fa748d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520980(v=OCS.15)
ms:contentKeyID: 49306430
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar gravação de detalhes da chamada

 

_**Tópico modificado em:** 2013-02-23_

O CDR (registro de detalhes das chamadas) registra informações de utilização e diagnóstico sobre atividades ponto a ponto, incluindo serviço de mensagens instantâneas, chamadas do protocolo VoIP, compartilhamento de aplicativos, transferência de arquivos e reuniões. Os dados de uso podem ser utilizados para calcular o ROI (retorno sobre o investimento), enquanto os dados de diagnóstico podem ser usados para solucionar problemas de atividades ponto a ponto e reuniões.

Use o procedimento a seguir para ativar o CDR para a organização inteira ou para cada local da organização.

> [!NOTE]  
> Para habilitar o CDR, é preciso configurar o monitoramento e o banco de dados de monitoramento. Para obter detalhes, consulte <a href="lync-server-2013-deploying-monitoring.md">Implantando o monitoramento no Lync Server 2013</a>.

## Para habilitar o CDR usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Monitoração e Arquivamento** e em **Registro de Detalhes das Chamadas**.

4.  Na página **Registro de Detalhes das Chamadas** clique no local apropriado na tabela, em **Ação** e em **Ativar CDR**.
    
    > [!NOTE]  
    > O CDR é ativado por padrão.

## Para habilitar o CDR usando os cmdlets Shell de Gerenciamento do Lync Server

Também é possível habilitar o CDR usando o Windows PowerShell e o cmdlet **Set-CsCdrConfiguration**. Este cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para habilitar o CDR para um único local

  - Para desabilitar o CDR, defina o parâmetro EnableCDR como Verdadeiro ($Verdadeiro).
    
        Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $True

## Para desabilitar o CDR para um único local

  - Para desabilitar o CDR, defina o parâmetro EnableCDR como Falso ($Falso). Isso não desinstala o monitoramento, apenas pausa a coleta e o armazenamento de dados de CDR.
    
        Set-CsCdrConfiguration -Identity "site:Redmond" -EnableCDR $False

## Para usar um único comando para habilitar o CDR em vários locais

  - Este comando habilita o CDR para todas as definições de configuração de CDR em uso em sua organização.
    
        Get-CsCdrConfiguration | Set-CsCdrConfiguration "site:Redmond" -EnableCDR $True

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Set-CsCdrConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCdrConfiguration).

## Consulte Também

#### Outros Recursos

[Planejamento de monitoramento no Lync Server 2013](lync-server-2013-planning-for-monitoring.md)  
[Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md)

