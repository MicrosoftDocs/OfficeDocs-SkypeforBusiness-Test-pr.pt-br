---
title: Habilitar ou desabilitar o modo crítico para bloquear ou permitir mensagens instantâneas e sessões de conferência da Web se o arquivamento falhar
TOCTitle: Habilitar ou desabilitar o modo crítico para bloquear ou permitir mensagens instantâneas e sessões de conferência da Web se o arquivamento falhar
ms:assetid: fafdcd2e-b778-4ed5-a25f-09208aa3b699
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182609(v=OCS.15)
ms:contentKeyID: 49308683
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar o modo crítico para bloquear ou permitir mensagens instantâneas e sessões de conferência da Web se o arquivamento falhar

 

_**Tópico modificado em:** 2013-02-23_

No Painel de Controle do Lync Server 2013, use as configurações de Arquivamento para habilitar ou desabilitar o modo crítico. Isso inclui as seguintes configurações de Arquivamento:

  - Um configuração global criada por padrão ao implantar o Lync Server 2013.

  - Configurações opcionais de site e pool que você pode criar e usar para especificar como o arquivamente é implementado para sites ou pools específicos.

Inicialmente, você deve definir as configurações de Arquivamento ao implantar o Arquivamento, mas você pode mudar, adicionar ou excluir configurações após a implantação. Para detalhes sobre como as configurações de Arquivamento são implementadas, incluindo quais opções você pode especificar e a hierarquia das configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, documentação de Implantação ou documentação de Operações.

> [!NOTE]  
> Para usar o arquivamento, você deve configurar as políticas de Arquivamento para especificar se deseja habilitar o arquivamento para comunicações internas, comunicações externas ou ambas hospedadas em Lync Server 2013. Por padrão, o arquivamento não está habilitado para comunicações internas ou externas. Antes de habilitar o Arquivamento em qualquer política, você deve especificar as configurações apropriadas de Arquivamento para sua Implantação e, opcionalmente, para sites e pools específicos, conforme descrito nesta seção. Para detalhes sobre como habilitar o Arquivamento, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a> na documentação de Implantação.<br />Se decidir depois de implantar o Arquivamento que você quer usar a integração do Exchange Server para armazenar dados e arquivos de arquivamento nos servidores Exchange 2013 e todos os seus usuários estão hospedados nos servidores Exchange 2013, você deve remover a configuração de banco de dados do SQL Server de sua topologia. Use Construtor de Topologias para isso. Para detalhes, consulte <a href="lync-server-2013-changing-archiving-database-options.md">Modificando opções do banco de dados de arquivamento no Lync Server 2013</a> na documentação de Operações.

## Para ativar ou desativar o bloqueio de sessões de conferência da Web e mensagens instantâneas se o arquivamento falhar

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Clique no nome da configurações de pool, site ou global apropriada na lista de configurações de arquivamente, clique em **Editar**, **Mostrar detalhes** e faça o seguinte:

5.  Para definir como o arquivamento se comporta quando ocorre uma falha, marque ou desmarque a caixa de seleção **Bloquear sessões de conferência da Web e mensagens instantâneas (IM) se o arquivamento falhar**.

6.  Clique em **Confirmar**.

## Habilitar ou Desabilitar o Modo Crítico Usando os cmdlets Lync ServerWindows PowerShell

Você pode habilitar ou desabilitar o modo crítico usando o cmdlet **Set-CsArchivingConfiguration**. Execute esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Habilitar o Modo Crítico

  - Para habilitar o modo crítico, defina o valor da propriedade BlockOnArchiveFailure como True ($True). Exemplo:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $True

## Desabilitar o Modo Crítico

  - Para desabilitar o modo crítico, defina o valor da propriedade BlockOnArchiveFailure como False ($False). Exemplo:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -BlockOnArchiveFailure $False

Para mais informações, veja o tópico de ajuda para o cmdlet[Set-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingConfiguration).

## Consulte Também

#### Tarefas

[Modificando opções do banco de dados de arquivamento no Lync Server 2013](lync-server-2013-changing-archiving-database-options.md)  

#### Conceitos

[Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md)  

#### Outros Recursos

[Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

