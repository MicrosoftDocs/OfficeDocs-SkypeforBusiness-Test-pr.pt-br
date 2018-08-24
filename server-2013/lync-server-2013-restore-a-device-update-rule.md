---
title: Restaurar uma regra de atualização de dispositivo
TOCTitle: Restaurar uma regra de atualização de dispositivo
ms:assetid: ac490baf-c7a0-48d9-8fd0-ba5729489341
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994061(v=OCS.15)
ms:contentKeyID: 52057686
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurar uma regra de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-23_

Para desinstalar uma regra de atualização de dispositivo dos dispositivos em sua implantação, restaure-a. Restaurar uma regra de atualização de dispositivo desinstala a atualização e reinstala a versão anterior dessa regra.

Você pode restaurar uma regra de atualização de dispositivo utilizando Painel de Controle do Lync Server ou Windows PowerShell.

## Para restaurar uma regra de atualização de dispositivo utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Atualização de Dispositivo**.

4.  Na página de **Atualização de Dispositivo**, realize uma das ações a seguir:
    
      - Para restaurar uma regra, selecione-a.
    
      - Para restaurar todas as regras, clique em **Editar** e então em **Selecionar Tudo**.

5.  Clique no menu **Ação** e então em **Restaurar**.

## Restaurar as regras de atualização de dispositivo por uso de cmdlets Windows PowerShell

Regras de atualização de dispositivo também podem ser restauradas por uso de Windows PowerShell e do cmdlet **Restore-CsDeviceUpdateRule**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou então por uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

## Para restaurar uma única regra de atualização de dispositivo em um servidor

  - O comando a seguir restaura a regra de atualização de dispositivo d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 no servidor Web atl-cs-001.litwareinc.com:
    
        Restore-CsDeviceUpdateRule -Identity "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"

## Para restaurar todas as regras de atualização de dispositivo em um servidor

  - Esse comando restaura todas as regras de atualização de dispositivo no servidor Web atl-cs-001.litwareinc.com:
    
        Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*" | Restore-CsDeviceUpdateRule

Para detalhes, veja o tópico Ajuda para o cmdlet [Restore-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Restore-CsDeviceUpdateRule).

