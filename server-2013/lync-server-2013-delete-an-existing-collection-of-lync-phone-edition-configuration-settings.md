---
title: Excluir um conjunto existente das configurações do Lync Phone Edition
TOCTitle: Excluir um conjunto existente das configurações do Lync Phone Edition
ms:assetid: 1bfc427d-4dcd-4199-b25f-8d5cfec2164f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687984(v=OCS.15)
ms:contentKeyID: 49886122
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um conjunto existente das configurações do Lync Phone Edition

 

_**Tópico modificado em:** 2013-02-23_

Se você não deseja mais usar um conjunto de configurações para dispositivos executando o Lync Phone Edition, exclua-o. Se você excluir um conjunto de um site, as configurações globais serão aplicadas aos telefones neste site. Não é possível excluir o conjunto global.

> [!NOTE]  
> Ao invés de excluir um conjunto, você pode alterar algumas configurações. Para obter detalhes sobre como fazer isso, consulte <a href="lync-server-2013-create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md">Criar ou Modificar um Conjunto de Configurações de Lync Phone Edition</a>.

## Para excluir um conjunto de definições de configurações do Lync Phone Edition

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e no botão de navegação **Configuração do Dispositivo**.

4.  Na página **Configuração do Dispositivo**, clique no conjunto que você deseja excluir, clique no menu **Editar** e em **Excluir**.
    
    > [!NOTE]  
    > Se você excluir o conjunto global, as configurações são revertidas para as configurações padrões. O conjunto não some.

5.  Na caixa de confirmação, clique em **OK**.

## Para remover as definições de configuração Lync Phone Edition usando os cmdlets do Shell de Gerenciamento do Lync Server

É possível excluir as definições de configuração do Lync Phone Edition usando o Windows PowerShell e o cmdlet **Remove-CsUCConfiguration**. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover um conjunto especificado de definições de configuração do Lync Phone Edition

  - Este comando excluir as definições de configuração do telefone UC para o site Redmond:
    
        Remove-CsUCPhoneConfiguration -Identity "site:Redmond"

## Para remover todas as definições de configuração do Lync Phone Edition aplicadas ao escopo local

  - Este comando remove todas as definições de configuração do telefone UC aplicadas ao escopo de serviço:
    
        Get-CsUCPhoneConfiguration -Filter "site:*" | Remove-CsUCPhoneConfiguration

## Para remover todas as definições de configuração do Lync Phone Edition onde o bloqueio de telefone está desabilitado

  - Este comando exclui qualquer conjunto de definições de configuração do telefone UC onde o bloqueio de telefone foi desabilitado:
    
        Get-CsUCPhoneConfiguration | Where-Object {$_.EnforcePhoneLock -eq $False} | Remove-CsUCPhoneConfiguration

Para obter detalhes, consulte [Remove-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsUCPhoneConfiguration).

