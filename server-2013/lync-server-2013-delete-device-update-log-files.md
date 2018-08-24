---
title: Excluir arquivos do log de atualizações do dispositivo
TOCTitle: Excluir arquivos do log de atualizações do dispositivo
ms:assetid: 58d4097f-5bbf-4824-a04d-2a6555cd93c3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994039(v=OCS.15)
ms:contentKeyID: 52057609
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir arquivos do log de atualizações do dispositivo

 

_**Tópico modificado em:** 2013-02-23_

O Serviço Web de Atualização de Dispositivos mantém uma coleção de arquivos de log extensa. Essa coleção inclui logs de auditoria conduzidas pelo próprio serviço e arquivos de log carregados a partir dos dispositivos do cliente. Para impedir que o servidor preencha os logs de serviço do Serviço Web de Atualização de Dispositivos, provavelmente você vai querer limpar os arquivos de log que estiverem armazenados há um determinado tempo. Defina um número de dias com base na atividade de atualização e o número de dispositivos do cliente na sua organização, e usando o Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server.

## Para limpar o log de atualização do dispositivo usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Clientes** e em **Configuração de Log de Dispositivo**.

3.  Na página **Configuração de Log de Dispositivo**, clique duas vezes na configuração que deseja alterar.

4.  Na caixa de diálogo **Editar Configuração de Log**, em **Número de dias para manter arquivos de log (1-365)**, especifique um número de dias.

5.  Clique em **Confirmar**. Todos os arquivos que estiverem no servidor por mais dias do que o número de dias especificado serão excluídos. Essa configuração será aplicada a essa configuração até você alterá-la.

## Limpando o log de atualização do dispositivo usando os cmdlets Windows PowerShell

Você pode limpar os logs de atualização do dispositivo usando o Windows PowerShell e o cmdlet **Clear-CsDeviceUpdateLog**. Esse cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

## Para limpar os logs de atualização do dispositivo em um servidor

  - O seguinte comando limpa o log de atualização do dispositivo no servidor Web atl-cs-001.litwareinc.com. Todas as entradas do log com mais de 10 dias ( o valor especificado pelo parâmetro DaysBack) serão removidas do log.
    
        Clear-CsDeviceUpdateLog -Identity "service:WebServer:atl-cs-001.litwareinc.com" -DaysBack 10

## Para limpar todos os logs de atualização do dispositivo

  - Este comando remove entradas desatualizadas (neste exemplo, entradas com mais de 10 dias) de todos os logs de atualização do dispositivo atualmente em uso na sua organização.
    
        Get-CsService -WebServer | Foreach-Object {Clear-CsDeviceUpdateLog -Identity $_.Identity -DaysBack 10}

Para obter detalhes, consulte o tópico de Ajuda do cmdlet [Clear-CsDeviceUpdateLog](https://docs.microsoft.com/en-us/powershell/module/skype/Clear-CsDeviceUpdateLog). en-us

