---
title: Mudar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para sua Empresa, Sites ou Usuários
TOCTitle: Mudar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para sua Empresa, Sites ou Usuários
ms:assetid: b85dc3fb-8ebd-4e3c-ac90-fc79270ac867
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182576(v=OCS.15)
ms:contentKeyID: 49307905
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mudar uma Política de Arquivamento para Habilitar ou Desabilitar o Arquivamento de Comunicações Internos ou Externos para sua Empresa, Sites ou Usuários

 

_**Tópico modificado em:** 2013-02-23_

No Lync Server 2013, você usa políticas para ativar e desativar o arquivamento de comunicações internas para usuários hospedados no Lync Server 2013. Isso inclui as seguintes políticas de Arquivamento:

  - Uma política global criada por padrão ao implantar Lync Server 2013.

  - Políticas opcionais de nível do site e usuário que você pode criar e usar para especificar como o arquivamento é implementado para sites ou usuários específicos.

Inicialmente você configura as políticas de Arquivamento ao implantar o Arquivamento, mas é possível alterar, adicionar e excluir políticas depois da implantação. No Painel de Controle do Lync Server 2013, você pode usar o página de **Arquivamento de política** do grupo **Arquivando e monitorando** para gerenciar políticas a nível global, de site e do usuário. Se você integrar seu armazenamento do Lync Server ao do Exchange 2013, as políticas do usuário do Exchange têm prioridade sobre as políticas de arquivamento do Lync Server 2013.

Para obter detalhes sobre como as políticas são implementadas, incluindo a hierarquias de políticas, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implementação ou Operações.

> [!NOTE]  
> Se você ativou a integração do Microsoft Exchange para a sua implantação, as políticas do Exchange controlam se o arquivamento está habilitado para usuários hospedados no Exchange 2013 e com caixas de correio em Bloqueio in-loco. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-policies-for-archiving-when-using-exchange-server-integration.md">Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server</a> na documentação de Implantação.<br />Você deve especificar todas as opções apropriadas nas configurações de Arquivamento antes de ativar o Arquivamento. Para obter detalhes, consulte <a href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools</a> na documentação de Operações.

## Para alterar uma política de arquivamento

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Política de Arquivamento**.

4.  Na lista de políticas, siga um destes procedimentos:
    
      - Para alterar a política da implantação inteira, clique em **Global** na lista de políticas, clique em **Editar**, em **Mostrar detalhes**.
    
      - Para alterar a política de um único site, clique no nome do site na lista de políticas, clique em **Editar** e em **Mostrar detalhes**.
    
      - Para alterar a política de um único usuário ou grupo de usuários, clique no nome do usuário ou do grupo de usuários na lista de políticas, clique em **Editar** e em **Mostrar detalhes**.

5.  Na página **Editar política de arquivamento**, faça o seguinte:
    
      - Para habilitar ou desabilitar o arquivamento interno da política, marque ou desmarque a caixa de seleção **Arquivar comunicações internas**.
    
      - Para habilitar ou desabilitar o arquivamento externo da política, marque ou desmarque a caixa de seleção **Arquivar comunicações externas**.

6.  Clique em **Confirmar**.
    
    > [!IMPORTANT]  
    > As configurações de uma política do usuário se aplicam somente a usuários específicos e grupos de usuários aos quais você aplica a política. Para obter detalhes, consulte <a href="lync-server-2013-applying-an-archiving-policy-to-users.md">Aplicar uma política de arquivamento aos usuários</a>

## Habilitando e desabilitando o arquivamento usando os cmdlets do Lync Server PowerShell

O arquivamento também pode ser habilitado e desabilitado (para sessões de comunicações internas e externas) usando o cmdlet **Set-CsArchivingPolicy**. Este cmdlet pode ser executado no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Habilitando o arquivamento de sessões de comunicações internas

  - Para habilitar o arquivamento de sessões de comunicações internas, defina o valor da propriedade **ArchiveInternal** como Verdadeiro ($True). Por exemplo:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True

## Habilitando o arquivamento de sessões de comunicações externas

  - Para habilitar o arquivamento de sessões de comunicações externas, defina o valor da propriedade **Archiveexternal** como Verdadeiro ($True). Por exemplo:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveExternal $True

## Habilitando o arquivamento de sessões de comunicações internas e externas

  - Para habilitar o arquivamento de sessões de comunicações internas e externas, defina as propriedades **ArchiveInternal** e **ArchiveExternal** como Verdadeiro:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True

## Desabilitando o arquivamento

  - Para desabilitar o arquivamento, defina as propriedades **ArchiveInternal** e **ArchiveExternal** como Falso ($False). Por exemplo:
    
        Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $False -ArchiveExternal $False

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Set-CsArchivingPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingPolicy).

## Consulte Também

#### Outros Recursos

[Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md)

