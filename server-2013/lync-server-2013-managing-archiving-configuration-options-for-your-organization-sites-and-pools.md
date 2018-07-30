---
title: Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools
TOCTitle: Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools
ms:assetid: 377a6f80-5f2b-4bc1-b507-e930a461fb1d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204802(v=OCS.15)
ms:contentKeyID: 49306384
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools

 

_**Tópico modificado em:** 2012-11-01_

No Painel de Controle do Lync Server 2013, use as configuração de arquivamento para especificar como o arquivamento será implantado. Isso inclui as seguintes configurações de arquivamento:

  - Uma configuração global criada por padrão quando o Lync Server 2013 é implantado.

  - Configurações opcionais no nível do site e no nível do pool que podem ser criadas e usadas para especificar como o arquivamento será implantado em sites ou pool específicos.

As configurações de arquivamento são definidas inicialmente quando o arquivamento é implantado, mas é possível alterar, adicionar e excluir configurações depois da implantação. No Painel de Controle do Lync Server 2013, é possível usar a página **Configuração de Arquivamento** do grupo **Arquivamento e Monitoramento** para gerenciar as configuração no nível global, no nível do site e no nível do pool. Para obter detalhes sobre como as configurações de arquivamento são implantadas, inclusive as opções que podem ser especificadas, e sobre a hierarquia das configurações de arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) nas documentações de planejamento, implantação e operações.

> [!NOTE]  
> Para usar o arquivamento, é preciso configurar as políticas de arquivamento que especificarão se o arquivamento será habilitado para comunicações internas, externas ou ambas para todos os usuários hospedados no Lync Server 2013. Por padrão, o arquivamento não é habilitado para comunicações internas ou externas. Se usar a integração com o Microsoft Exchange, habilite e configure o Exchange 2013 para que dê suporte a todos os usuários hospedados no Exchange 2013, cujas caixas de correio foram postas em Bloqueio In-loco.<br />Antes de habilitar o arquivamento, é preciso especificar as configurações de arquivamento apropriadas para sua implantação e, como opção, para sites e pool específicos, como descrito nesta seção. Para obter detalhes sobre a habilitação do arquivamento, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a> na documentação de implantação.

**Para exibir as informações de configuração de arquivamento usando os cmdlets do Shell de Gerenciamento do Lync Server**

  - É possível também exibir as informações de configuração de arquivamento usando o Lync ServerWindows PowerShell e o cmdlet **Get-CsArchivingConfiguration**. Este cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    No Shell de Gerenciamento do Lync Server, use o seguinte comando para exibir informações sobre todas as suas definições de configuração de arquivamento:
    
        Get-CsArchivingConfiguration

## Nesta seção

  - [Criando uma configuração de arquivamento para gerenciar o arquivamento de sites ou pools específicos](lync-server-2013-creating-an-archiving-configuration-to-manage-archiving-for-specific-sites-or-pools.md)

  - [Habilitar ou Desabilitar o Arquivamento de Sessões de Conferência ou IM](lync-server-2013-enabling-or-disabling-archiving-of-im-or-conferencing-sessions.md)

  - [Habilitar ou Desabilitar a Exclusão de Dados Arquivados](lync-server-2013-enabling-or-disabling-the-purging-of-archived-data.md)

  - [Habilitar ou desabilitar o modo crítico para bloquear ou permitir mensagens instantâneas e sessões de conferência da Web se o arquivamento falhar](lync-server-2013-enabling-or-disabling-critical-mode-to-block-or-allow-im-and-web-conferencing-sessions-if-archiving-fails.md)

  - [Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados no Lync Server 2013](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md)

  - [Habilitando uo Desabilitando Integração com Exchange Storage](lync-server-2013-enabling-or-disabling-integration-with-exchange-storage.md)

  - [Excluindo uma configuração de arquivamento](lync-server-2013-deleting-an-archiving-configuration.md)

## Consulte Também

#### Outros Recursos

[Gerenciando Arquivamento do Lync Server 2013](lync-server-2013-managing-archiving.md)

