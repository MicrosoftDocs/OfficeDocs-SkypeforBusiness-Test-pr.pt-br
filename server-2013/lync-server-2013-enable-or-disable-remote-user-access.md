---
title: 'Lync Server 2013: Habilitar ou desabilitar acesso de usuário remoto'
TOCTitle: Habilitar ou desabilitar acesso de usuário remoto
ms:assetid: cd9d3ddc-4839-457a-86d9-b15413e74002
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182586(v=OCS.15)
ms:contentKeyID: 49308146
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

Usuários remotos são usuários em suas organizações com uma identidade do Active Directory persistente dentro da organização. Os usuários remotos frequentemente fazem login no Lync Server fora da sua rede utilizando um VON quando não estão conectados à rede da sua organização. Os usuários remotos incluem funcionários trabalhando em casa ou na estrada e outros trabalhadores remotos, como vendedores confiáveis, que foram concedidos com credenciais empresariais. Se você habilitar o acesso de usuário remoto para usuários remotos, os usuários remotos suportados se conectam pela Internet e não precisam se conectar usando um VPN para colaborar com usuários internos utilizando o Lync Server.

Para suportar acesso de usuário remoto, você deve habilitar o acesso de usuário remoto. Ao habilitar o acesso de usuário remoto, você o habilita para toda sua organização. Se posteriormente você quiser impedir temporariamente ou permanentemente o acesso dos domínios federados pelos usuários, poderá desabilitar a federação para sua organização. Use o procedimento nesta seção para habilitar ou desabilitar o acesso do usuário federado para sua organização.

> [!NOTE]  
> Habilitar o acesso de usuário remoto apenas especifica que seus servidores executando as comunicações de suporte do serviço de Borda de Acesso com usuário remotos, mas os usuários remotos não podem participar de mensagem instantânea (IM) ou conferências em sua organização até que você também configure pelo menos uma política para gerenciar o uso do acesso de usuário remoto. As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto. Para obter detalhes sobre as políticas de conferência para o uso do acesso de usuário remoto, consulte <a href="lync-server-2013-configure-policies-to-control-remote-user-access.md">Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013</a>.

## Para habilitar ou desabilitar o acesso do usuário federado na sua organização

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Acesso Externo e Federado** e clique em **Configuração de Borda de Acesso** .

4.  Na página **Configuração da Borda de Acesso** , clique em **Global** , **Editar** e em **Exibir detalhes** .

5.  Em **Editar Configuração da Borda de Acesso** , execute um dos procedimentos a seguir:
    
      - Para habilitar o acesso ao usuário remoto para sua organização, marque a caixa de seleção **Habilitar comunicações com usuários federados** .
    
      - Para desabilitar o acesso ao usuário remoto para sua organização, desmarque a caixa de seleção **Habilitar comunicações com usuários federados** .

6.  Clique em **Confirmar** .

Para habilitar os usuários federados para fazer login em seus servidores executando o Lync Server, também é necessário configurar pelo menos uma política de acesso externa para suportar o acesso de usuário remoto. Para obter detalhes, consulte [Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013](lync-server-2013-configure-policies-to-control-remote-user-access.md) na documentação Implantação ou na documentação Operações.

## Habilitar ou desabilitar o acesso de usuário remoto utilizando cmdlets do Windows PowerShell

O acesso de usuário remoto pode ser gerenciado usando o Windows PowerShell e o cmdlet Set-CsAccessEdgeConfiguration. Este cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para habilitar o acesso de usuário remoto

  - Para habilitar o acesso de usuário remoto, defina o valor da propriedade **AllowOutsideUsers** para True ($True):
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $True

## Para desabilitar o acesso de usuário remoto

  - Para desabilitar o acesso de usuário remoto, defina o valor da propriedade **AllowOutsideUsers** para False ($False):
    
        Set-CsAccessEdgeConfiguration -AllowOutsideUsers $False

