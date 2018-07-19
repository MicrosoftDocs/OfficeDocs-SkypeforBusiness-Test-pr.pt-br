---
title: Remover uma regra de atualização de dispositivo
TOCTitle: Remover uma regra de atualização de dispositivo
ms:assetid: ad6e0c6a-cda4-4147-92d5-48bc393ac456
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994066(v=OCS.15)
ms:contentKeyID: 52057712
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover uma regra de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-23_

Remover uma regra de atualização de dispositivo retira-a permanentemente da fila de atualização do dispositivo.

Remover uma regra é diferente de desinstalar uma atualização dos dispositivos na sua implantação ou dos seus dispositivos de teste. Para desinstalar uma atualização aprovada da sua implantação, você *restaura* a regra de atualização de dispositivo. Para detalhes, consulte [Restaurar uma regra de atualização de dispositivo](lync-server-2013-restore-a-device-update-rule.md). Para desinstalar de seus dispositivos de teste uma atualização que você não tenha aprovado, você a *reseta*. Para detalhes, consulte [Redefinir uma regra de atualização de dispositivo](lync-server-2013-reset-a-device-update-rule.md).

Você pode remover uma regra de atualização de dispositivo utilizando o Painel de Controle do Lync Server ou então o Windows PowerShell.

## Para remover regras de atualização de dispositivo utilizando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Atualização de Dispositivo**.

4.  Na página de **Atualização de Dispositivo**, realize uma das ações a seguir:
    
      - Para remover uma regra, selecione a regra que você deseja excluir.
    
      - Para remover todas as regras, clique no menu **Editar** e então em **Selecionar Tudo**.

5.  Clique em **Editar** e então em **Excluir**.

## Remoção das regras de atualização de dispositivo por uso de Cmdlets Windows PowerShell

Regras de atualização de dispositivo também podem ser removidas utilizando o Windows PowerShell e o cmdlet **Remove-CsDeviceUpdateRule**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou então de uma sessão de assistência remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover uma única regra de atualização de dispositivo de um servidor

  - O comando a seguir remove a regra de atualização de dispositivo d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 do servidor Web em atl-cs-001.litwareinc.com.
    
        Remove-CsDeviceUpdateRule -Identity "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"

## Para remover todas as regras de atualização de dispositivo de um servidor

  - Esse comando remove todas as regras de atualização de dispositivo do servidor Web em atl-cs-001.litwareinc.com.
    
        Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*" | Remove-CsDeviceUpdateRule

Para detalhes, veja o tópico Ajuda para o cmdlet [Remove-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsDeviceUpdateRule).

## Consulte Também

#### Tarefas

[Aprovar uma regra de atualização de dispositivo](lync-server-2013-approve-a-device-update-rule.md)

