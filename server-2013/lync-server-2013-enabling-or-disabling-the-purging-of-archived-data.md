---
title: Habilitar ou Desabilitar a Exclusão de Dados Arquivados
TOCTitle: Habilitar ou Desabilitar a Exclusão de Dados Arquivados
ms:assetid: 28cef09f-0970-4fc3-8315-f26689e3e187
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520968(v=OCS.15)
ms:contentKeyID: 49306213
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou Desabilitar a Exclusão de Dados Arquivados

 

_**Tópico modificado em:** 2013-02-23_

No Painel de Controle do Lync Server 2013, você usa as configurações de Arquivamento para habilitar ou desabilitar a exclusão e configurar como a exclusão é implementada. Isto inclui as seguintes configurações de Arquivamento:

  - Uma configuração global criada por padrão ao implantar o Lync Server 2013.

  - Configurações a nível do pool ou local opcionais que você pode criar e usar para especificar como o arquivamento é implementado para sites ou pools específicos.

Você define inicialmente as configurações de Arquivamento ao implantar o Arquivamento, mas pode alterar, adicionar e excluir configurações após a implantação. Para obter detalhes sobre como as configurações de Arquivamento são implementadas, incluindo quais opções você pode especificar e a hierarquia das configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação e Operação.

> [!NOTE]  
> Para usar o arquivamento de usuários hospedados no Lync Server 2013, você deve configurar as políticas de Arquivamento para especificar se deve habilitar o arquivamento de comunicações internas, comunicações externas ou ambas. Por padrão, o arquivamento não é habilitado para comunicações internas ou externas. Antes de habilitar o Arquivamento em qualquer política, você deve especificar as configurações de Arquivamento adequadas para sua implantação e, opcionalmente, para locais e pools específicos, conforme descrito nesta seção. Para obter detalhes sobre a habilitação do Arquivamento, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a> na documentação de Implantação.<br />Se você decidir após implantar o Arquivamento que deseja usar a integração do Microsoft Exchange para armazenar dados de arquivamento e arquivos nos servidores do Exchange 2013 e todos seus usuários são hospedados em seus servidores do Exchange 2013, você deve remover a configuração do banco de dados do SQL Server da sua topologia. Você deve usar o Construtor de Topologias para fazer isso. Para obter detalhes, consulte <a href="lync-server-2013-changing-archiving-database-options.md">Modificando opções do banco de dados de arquivamento no Lync Server 2013</a> na documentação de Operações.

## Para habilitar ou desabilitar a limpeza do arquivamento

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Clique no nome da configuração global, local ou do pool adequado na lista de configurações de arquivamento, clique em **Editar**, em **Exibir detalhes** e faça o seguinte:
    
      - Para habilitar a limpeza, marque a caixa de seleção **Habilitar limpeza de dados de arquivamento** e execute uma das seguintes ações:
        
          - Para limpar todos os registros, clique em **Limpar dados de arquivamento exportados e armazenados após um período máximo de (dias)** e especifique o número de dias.
        
          - Para limpar somente os dados exportados, clique em **Limpar somente dados de arquivamento exportados**.
    
      - Para desabilitar a limpeza, desmarque a caixa de seleção **Habilitar limpeza de dados de arquivamento**.

5.  Clique em **Confirmar**.

## Habilitar e desabilitar a exclusão dos dados de arquivamento usando cmdlets do Shell de Gerenciamento do Lync Server

Habilitar ou desabilitar a exclusão automática de dados de arquivamento também pode ser gerenciado usando o Windows PowerShell e o cmdlet **Set-CsArchivingConfiguration**. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Habilitar a exclusão de todos os dados de arquivamento

  - Para habilitar a exclusão de todos os dados de arquivamento, defina a propriedade **EnablePurging** para verdadeiro ($True). Por exemplo:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True
    
    Após este comando ser executado, todo dia o Lync Server excluirá todos os registros de arquivamento mais antigos do que o valor especificado para a propriedade **KeepArchivingDataForDays**.

## Habilitar apenas a exclusão de dados de arquivamento exportados

  - Para limitar a exclusão para registros de arquivamento que foram exportados para um arquivo de dados (usando o cmdlet [Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData)), você também deve definir a propriedade PurgeExportedArchivesOnly para Verdadeiro ($True). Por exemplo:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $True -PurgeExportedArchivesOnly $True
    
    Após este comando ser executado, o Lync Server excluirá apenas os registros de arquivamento que cumprem dois critérios: 1) são mais antigos do que o valor especificado para a propriedade **KeepArchivingDataForDays**; e, 2) foram exportados usando o cmdlet **Export-CsArchivingData**.

## Desabilitando a exclusão de todos os dados de arquivamento

  - Para desabilitar a exclusão automática dos registros de arquivamento, defina a propriedade **EnablePurging** para False ($False). Por exemplo:
    
        Set-CsArchivingConfiguration -Identity "site:Redmond" -EnablePurging $False

Para obter mais informações, incluindo opções adicionais para excluir dados de arquivamento, consulte o tópico de ajuda para o cmdlet [Set-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingConfiguration).

## Consulte Também

#### Conceitos

[Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md)  

#### Outros Recursos

[Configurando e atribuindo políticas de arquivamento](lync-server-2013-configuring-and-assigning-archiving-policies.md)  
[Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

