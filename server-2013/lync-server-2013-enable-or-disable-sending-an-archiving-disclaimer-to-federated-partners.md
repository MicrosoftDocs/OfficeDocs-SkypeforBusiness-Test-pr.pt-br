---
title: 'Lync Server 2013: Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados'
TOCTitle: Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados
ms:assetid: c8e9a2fa-9dc1-4e4d-919f-56ece8004864
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182584(v=OCS.15)
ms:contentKeyID: 49308074
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

No momento em que você implantou seus Servidores de Borda e habilitou a federação para a sua organização, deve ter especificado se enviaria automaticamente a isenção de arquivamento para parceiros federados. Se você arquiva comunicações externas, deverá habilitar o envio de uma isenção de arquivamento. Use o procedimento deste tópico para alterar essa configuração.

> [!NOTE]  
> O procedimento a seguir assume que você já habilitou a federação para sua organização. Para obter detalhes sobre como habilitar a federação, consulte <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a> na documentação Implantação ou na documentação Operações.

## Para habilitar ou desabilitar o envio de uma isenção de responsabilidade de arquivamento para parceiros federados

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso de Usuário Externo** e clique em **Configuração de Borda de Acesso** .

4.  Na guia **Configuração de Borda de Acesso** , clique em **Global** , em **Editar** e clique em **Mostrar detalhes** .

5.  Em **Editar Configuração de Borda de Acesso** , em **Habilitar comunicações com usuários federados** , marque ou desmarque a caixa de seleção **Enviar aviso de isenção de responsabilidade de arquivamento para parceiros federados** para habilitar ou desabilitar o envio automático do aviso de isenção de responsabilidade de arquivamento.

6.  Clique em **Confirmar** .

Para permitir que os usuários federados colaborem com usuários em sua implantação do Lync Server 2013, também é necessário configurar pelo menos uma política de acesso externa para suportar o acesso de usuário federado. Para obter detalhes, consulte [Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md) na documentação Implantação ou na documentação Operações. Para obter detalhes sobre como controlar o acesso para domínios federados específicos, consulte [Configurar suprote para domínios externos permitidos no Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md) na documentação Implantação ou na documentação Operações.

## Habilitar ou desabilitar a isenção de responsabilidade do arquivamento usando os cmdlets do Windows PowerShell

O uso da isenção de responsabilidade de arquivamento também pode ser gerenciado usando o Windows PowerShell e o cmdlet Set-CsAccessEdgeConfiguration. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para habilitar a isenção de responsabilidade de arquivamento

  - Para habilitar a isenção de responsabilidade de arquivamento, defina o valor da propriedade **EnableArchivingDisclaimer** para True ($True):
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $True

## Para desabilitar a isenção de responsabilidade de arquivamento

  - Para desabilitar a isenção de responsabilidade de arquivamento, defina o valor da propriedade **EnableArchivingDisclaimer** para False ($False):
    
        Set-CsAccessEdgeConfiguration -EnableArchivingDisclaimer $False

