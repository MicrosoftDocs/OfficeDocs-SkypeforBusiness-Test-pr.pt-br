---
title: 'Lync Server 2013: Excluir um site ou uma política de usuário para acesso de usuário externo'
TOCTitle: Excluir um site ou uma política de usuário para acesso de usuário externo
ms:assetid: 6d907507-825b-4354-9c03-337a459f72de
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521013(v=OCS.15)
ms:contentKeyID: 49307035
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um site ou uma política de usuário para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

Você pode excluir qualquer política de site ou de usuário listada no Painel de Controle do Lync Server na página **Política de Acesso Externo**. Excluir a política global não causa sua exclusão propriamente dita, mas apenas a redefine para suas configurações padrão, que não incluem suporte para nenhuma opção de acesso de usuário externo. Para obter detalhes sobre a redefinição da política global, consulte [Redefinir a política global para acesso de usuário externo no Lync Server 2013](lync-server-2013-reset-the-global-policy-for-external-user-access.md).

## Para excluir uma política de site ou de usuário para o acesso de usuário externo

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Clique em **Acesso de Usuário Externo**, em **Política de Acesso Externo**.

4.  Na guia **Política de Acesso Externo**, clique na política de site ou de usuário que deseja excluir, clique em **Editar** e em **Excluir**.

5.  Quando lhe for solicitado confirmar a exclusão, clique em **OK**.

## Removendo políticas de PIN utilizando cmdlets Windows PowerShell

As políticas de acesso externo podem ser excluídas utilizando os cmdlets Windows PowerShell e Remove-CsExternalAccessPolicy. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover uma política de acesso esterno específica

  - Este comando remove a política de acesso externo aplicada ao site Redmond:
    
        Remove-CsExternalAccessPolicy -Identity "site:Redmond"

## Para remover todas as políticas de acesso externo aplicadas ao escopo por usuário

  - Este comando remove todas as políticas de acesso externo configuradas no escopo por usuário:
    
        Get-CsExternalAccessPolicy -Filter "tag:*" | Remove-CsExternalAccessPolicy

## Para remover todas as políticas de acesso externo em que o acesso de usuário externo está desabilitado

  - Este comando exclui todas as políticas de acesso externo com acesso de usuário externo desabilitado:
    
        Get-CsExternalAccessPolicy | Where-Object {$_.EnableOutsideAccess -eq $False} | Remove-CsExternalAccessPolicy

Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy).

