---
title: Redefinir uma regra de atualização de dispositivo
TOCTitle: Redefinir uma regra de atualização de dispositivo
ms:assetid: d1f597e7-dffd-4756-af07-10613a5d8729
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994069(v=OCS.15)
ms:contentKeyID: 52057728
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Redefinir uma regra de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-23_

Se você não gosta do modo como uma atualização funciona em seus dispositivos de teste, você pode resetar a regra de atualização do dispositivo, que remove o status da regra como pendente e desinstala a atualização dos dispositivos de teste.

Você pode remover uma regra de atualização de dispositivo utilizando o Painel de Controle do Lync Server ou então o Windows PowerShell.

> [!NOTE]  
> Para desinstalar uma regra que você já tenha aprovado (ou seja, implantadas), restaure-a. Para detalhes, consulte <a href="lync-server-2013-restore-a-device-update-rule.md">Restaurar uma regra de atualização de dispositivo</a>.

## Para resetar uma regra de atualização de dispositivo utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Atualização de Dispositivo**.

4.  Na página de **Atualização de Dispositivo**, realize uma das ações a seguir:
    
      - Para resetar uma regra, selecione a regra que você deseja resetar.
    
      - Para resetar todas as regras, no menu **Editar**, clique em **Selecionar Tudo**.
    
      - Para selecionar todas as regras para uma marca, use o menu da coluna **Marca**.

5.  Clique em **Ação** e depois em **Cancelar atualizações pendentes**.
    

    > [!TIP]
    > Se tem certeza de que você nunca desejará implementar a(s) regra(s) de atualização de dispositivo que você cancelou, pode ser melhor excluí-las. Para detalhes, consulte <A href="lync-server-2013-remove-a-device-update-rule.md">Remover uma regra de atualização de dispositivo</A>.



## Para resetar uma regra de atualização de dispositivo utilizando cmdlets Windows PowerShell

As regras de atualização de dispositivo também podem ser resetadas utilizando o Windows PowerShell e o cmdlet **Reset-CsDeviceUpdateRule**. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

## Para resetar uma regra de atualização de dispositivo específica em um servidor

  - O comando a seguir reseta a regra de atualização de dispositivo d5ce3c10-2588-420a-82ac-dc2d9b1222ff9 no servidor Web atl-cs-001.litwareinc.com:
    
        Reset-CsDeviceUpdateRule -Identity "service:WebServer:atl-cs-001.litwareinc.com/d5ce3c10-2588-420a-82ac-dc2d9b1222ff9"

## Para resetar todas as regras de atualização de dispositivo em um servidor

  - Esse comando reseta todas as regras de atualização de dispositivo no servidor Web atl-cs-001.litwareinc.com:
    
        Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*"  | Reset-CsDeviceUpdateRule

## Para resetar todas as regras de atualização de dispositivo contendo uma marca específica

  - Nesse exemplo, todas as regras de atualização de dispositivo pela organização contendo Marca igual a Microsoft são resetadas:
    
        Get-CsDeviceUpdateRule | Where-Object {$_.Brand -eq "Microsoft"} | Reset-CsDeviceUpdateRule

Para detalhes, consulte o tópico Ajuda para o cmdlet [Reset-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Reset-CsDeviceUpdateRule).

## Consulte Também

#### Tarefas

[Aprovar uma regra de atualização de dispositivo](lync-server-2013-approve-a-device-update-rule.md)

