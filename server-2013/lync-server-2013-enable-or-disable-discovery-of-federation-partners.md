---
title: 'Lync Server 2013: Habilitar ou desabilitar descoberta de parceiros de federação'
TOCTitle: Habilitar ou desabilitar descoberta de parceiros de federação
ms:assetid: 91fd036b-b1af-47cf-b1cf-0aa0a783c2aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182550(v=OCS.15)
ms:contentKeyID: 49307462
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

Na ocasião em que você implantou seus Servidores de Borda e habilitou a federação para a sua organização, deve ter especificado se haveria suporte para a descoberta automática de domínios parceiros federados. Use o procedimento deste tópico para alterar essa configuração.

> [!NOTE]  
> O procedimento a seguir assume que você já habilitou a federação para sua organização. Para obter detalhes sobre como habilitar a federação, consulte <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a> na documentação Implantação ou na documentação Operações.

## Para habilitar ou desabilitar a descoberta automática de domínios federados para a sua organização

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso de Usuário Externo** e clique em **Configuração de Borda de Acesso**.

4.  Na página **Configuração da Borda de Acesso**, clique em **Global**, **Editar** e em **Exibir detalhes**.

5.  Em **Editar Configuração da Borda de Acesso**, sob **Habilitar comunicações com usuários federados**, selecione ou desmarque a opção **Habilitar descoberta de domínios de parceiros** para habilitar ou desabilitar a descoberta automática de domínios de parceiros.

6.  Clique em **Confirmar**.

Para permitir que os usuários federados colaborem com usuários em sua implantação do Lync Server, também é necessário configurar pelo menos uma política de acesso externa para suportar o acesso de usuário federado. Para obter detalhes, consulte [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) na documentação Implantação ou na documentação Operações. Para obter detalhes sobre como controlar o acesso para domínios federados específicos, consulte [Gerenciar domínios SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md), [Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md) e [Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md) na documentação Operações.

## Habilitando ou desabilitando a descoberta de parceiros da federação utilizando os cmdlets Windows PowerShell

A descoberta de parceiros da federação pode ser gerenciada utilizando os cmdlets Windows PowerShell e Set-CsAccessEdgeConfiguration. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para habilitar a descoberta de parceiros da federação

  - Para habilitar a descoberta de parceiros de federação, defina o valor da propriedade **EnablePartnerDiscovery** como Verdadeiro ($True). Observe que é necessário habilitar o roteamento DNS SRV para alterar o valor dessa propriedade.
    
        Set-CsAccessEdgeConfiguration -UseDnsSrvRouting -EnablePartnerDiscovery $True

## Para desabilitar a descoberta de parceiros da federação

  - Para desabilitar a descoberta de parceiros de federação, defina o valor da propriedade **EnablePartnerDiscovery** como Falso ($False).
    
        Set-CsAccessEdgeConfiguration -UseDnsSrvRouting -EnablePartnerDiscovery $False

