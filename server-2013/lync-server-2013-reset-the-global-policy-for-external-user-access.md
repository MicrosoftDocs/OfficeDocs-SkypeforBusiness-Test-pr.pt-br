---
title: 'Lync Server 2013: Redefinir a política global para acesso de usuário externo'
TOCTitle: Redefinir a política global para acesso de usuário externo
ms:assetid: 8207e1b1-de9e-461f-975f-fcc5c526849a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182545(v=OCS.15)
ms:contentKeyID: 49307293
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Redefinir a política global para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

Não é possível excluir completamente uma política global. Usar a opção **Excluir** na política global simplesmente a redefine para as configurações padrão, o que não inclui suporte a opções de acesso de usuário externo.

## Para redefinir a política global para as configurações padrão

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso do Usuário Externo** , em **Política de Acesso Externa** .

4.  Na guia **Política de Acesso Externa** , clique em política global, clique em **Editar** e em **Excluir** .

5.  Quando lhe for solicitado confirmar a exclusão, clique em **OK** . Uma mensagem aparece na parte superior da página informando que a política global foi redefinida.

## Redefinindo a política global de acesso externo utilizando os cmdlets Windows PowerShell

A política global de acesso externo pode ser redefinida utilizando os cmdlets Windows PowerShell e Remove-CsExternalAccessPolicy. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para redefinir a política global de acesso externo

  - Esse comendo redefine a política de acesso externo global:
    
        Remove-CsExternalAccessPolicy -Identity "global"

Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet [Remove-CsExternalAccessPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsExternalAccessPolicy).

