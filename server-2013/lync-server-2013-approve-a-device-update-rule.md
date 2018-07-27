---
title: Aprovar uma regra de atualização de dispositivo
TOCTitle: Aprovar uma regra de atualização de dispositivo
ms:assetid: 9dbb1c9a-be0f-4e13-9234-05501ab43ac5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994053(v=OCS.15)
ms:contentKeyID: 52057690
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Aprovar uma regra de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-23_

Após você importar uma regra de atualização, ela é instalada em seus dispositivos de teste. Se os seus testes forem bem-sucedidos e você quiser distribuir a atualização por sua organização, aprove-o utilizando Painel de Controle do Lync Server ou Windows PowerShell

## Para aprovar uma regra de atualização de dispositivo utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na página **Atualização do Dispositivo**, realize uma das ações a seguir:
    
      - Para aprovar uma regra, selecione-a.
    
      - Para aprovar todas as regras, clique em **Editar** e então clique em **Selecionar Tudo**.

4.  Clique em **Ação** e depois em **Aprovar**.

## Aprovar uma regra de atualização de dispositivo utilizando Windows PowerShell Cmdlets

Regras de atualização de dispositivo também podem ser aprovadas pelo uso de Windows PowerShell e do cmdlet **Approve-CsDeviceUpdateRule**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota de Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

## Para aprovar uma única regra de atualização de dispositivo

  - O comando a seguir aprova a regra de atualização de dispositivo d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 encontrada no servidor Web atl-cs-001.litwareinc.com:
    
        Approve-CsDeviceUpdateRule -Identity service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9

## Para aprovar diversas regras de atualização de dispositivo

  - Este comando aprova todas as regras de atualização de dispositivo para dispositivos com a marca Microsoft:
    
        Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "Microsoft"} | Approve-CsDeviceUpdateRule

Para detalhes, veja o tópico Ajuda para o cmdlet [Approve-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Approve-CsDeviceUpdateRule).

## Consulte Também

#### Tarefas

[Importar regras de atualização de dispositivo](lync-server-2013-import-device-update-rules.md)  
[Restaurar uma regra de atualização de dispositivo](lync-server-2013-restore-a-device-update-rule.md)

