---
title: Excluindo uma configuração de arquivamento
TOCTitle: Excluindo uma configuração de arquivamento
ms:assetid: a8744d39-5cf2-474c-9a99-a0f3a37f846f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205167(v=OCS.15)
ms:contentKeyID: 49307727
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluindo uma configuração de arquivamento

 

_**Tópico modificado em:** 2013-02-23_

Você pode excluir uma configuração de site ou configuração de pool. A configuração global não pode ser removida. Se você excluir a configuração global, ela será automaticamente redefinida para os valores padrão. Para obter detalhes sobre como as configurações de Arquivamento são implementadas, incluindo quais opções você pode especificar e a hierarquia das configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, documentação de Implantação ou documentação de Operações.

## Para excluir uma configuração de site ou pool para arquivamento

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Na lista de configuração de arquivamento, clique na configuração de site ou pool que deseja excluir, clique em **Editar** e em **Excluir**.

5.  Clique em **Confirmar**.

## Remoção de configurações de arquivamento usando os cmdlets Shell de Gerenciamento do Lync Server

As configurações de arquivamento podem ser também excluídas usando o Windows PowerShell e o cmdlet Remove-CsArchivingConfiguration. Esse cmdlet pode ser executado doShell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

## Remoção das definições de uma coleção específica de configurações de arquivamento

  - O comando a seguir remove as definições de configuração de arquivamento aplicadas ao site de Redmond:
    
        Remove-CsArchivingConfiguration -Identity "site:Redmond"

## Remoção de todas as definições de configuração de arquivamento aplicadas ao escopo do site

  - Esse comando remove todas as definições de configuração de arquivamento aplicadas ao escopo do site:
    
        Get-CsArchivingConfiguration -Filter "site:*" | Remove-CsArchivingConfiguration

## Remoção das definições de configuração de arquivamento baseado em um valor de propriedade específico

  - Esse comando remove todas as definições de configuração de arquivamento onde o arquivamento do Exchange foi desativado:
    
        Get-CsArchivingConfiguration | Where-Object {$_.EnableExchangeArchiving -eq $False} | Remove-CsArchivingConfiguration

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Remove-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsArchivingConfiguration).

## Consulte Também

#### Conceitos

[Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md)  

#### Outros Recursos

[Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

