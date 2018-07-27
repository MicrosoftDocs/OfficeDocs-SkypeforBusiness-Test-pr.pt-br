---
title: 'Lync Server 2013: Habilitar ou desabilitar acesso de usuário anônimo'
TOCTitle: Habilitar ou desabilitar acesso de usuário anônimo
ms:assetid: f10c19e6-b6f9-4d26-9923-0165f36e4af8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ619192(v=OCS.15)
ms:contentKeyID: 49308549
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar acesso de usuário anônimo no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

Os usuários anônimos são aqueles que não possuem conta de usuário no Serviços de Domínio Active Directory da organização ou em um domínio federado com suporte, e podem ser convidados a participar remotamente de uma conferência local. Ao permitir a participação anônima em reuniões, você habilita os usuários anônimos (isto é, usuários cuja identidade é verificada apenas por meio da chave de reunião ou conferência) a participarem de reuniões. Para permitir a participação anônima em sua organização, é necessário que você habilite esse recurso.

Se mais tarde você quiser prevenir o acesso de usuários anônimos temporariamente ou permanentemente, é possível desabilitar esse acesso à sua organização. Use o procedimento desta seção para habilitar ou desabilitar o acesso de usuários anônimos à sua organização.

> [!NOTE]  
> Habilitar o acesso de usuários anônimos à sua organização apenas especifica que seus servidores que estão executando o serviço de Borda de Acesso dão suporte ao acesso de usuários anônimos. Os usuários anônimos não podem participar de nenhuma reunião da sua organização até que seja configurada ao menos uma política de conferência e que esta seja aplicada a um ou mais usuários ou grupos de usuários. Os únicos usuários que podem convidar usuários anônimos para reuniões são aqueles com uma política de conferência designada configurada para dar suporte aos usuários anônimos. Para obter detalhes de como configurar as políticas de conferência para dar suporte a usuários anônimos, consulte <a href="lync-server-2013-conferencing-policies.md">Políticas de conferência no Lync Server 2013</a>.

## Para habilitar ou desabilitar o acesso de usuários anônimos à sua organização

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Acesso de Usuário Externo** e clique em **Configuração da Borda de Acesso**.

4.  Na página **Configuração da Borda de Acesso**, clique em **Global**, **Editar** e em **Exibir detalhes**.

5.  Em **Editar Configuração da Borda de Acesso**, execute um dos procedimentos a seguir:
    
      - Para habilitar o acesso de usuários anônimos à sua organização, marque a caixa de seleção **Habilitar comunicações com usuários anônimos**.
    
      - Para desabilitar o acesso de usuários anônimos à sua organização, desmarque a caixa de seleção **Habilitar comunicações com usuários anônimos**.

6.  Clique em **Confirmar**.

## Habilitar ou desabilitar o acesso de usuário anônimo usando os cmdlets do Windows PowerShell

Você pode gerenciar o acesso de usuário anônimo usando o cmdlet Windows PowerShell e o **Set-CsAccessEdgeConfiguration**. É possível executar este cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para habilitar o acesso do usuário anônimo

  - Para habilitar o acesso de usuário anônimo, defina o valor da propriedade **AllowAnonymousUsers** para Verdadeiro ($True):
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $True

## Para desabilitar o acesso do usuário anônimo

  - Para desabilitar o acesso de usuário anônimo, defina o valor da propriedade **AllowAnonymousUsers** para Falso ($False):
    
        Set-CsAccessEdgeConfiguration -AllowAnonymousUsers $False

## Consulte Também

#### Conceitos

[Referência das configurações da política de conferência para Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md)

