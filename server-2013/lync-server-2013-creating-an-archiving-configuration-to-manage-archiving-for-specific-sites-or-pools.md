---
title: Criando uma configuração de arquivamento para gerenciar o arquivamento de sites ou pools específicos
TOCTitle: Criando uma configuração de arquivamento para gerenciar o arquivamento de sites ou pools específicos
ms:assetid: c5c864a6-96c7-4bbb-ab7c-61eb1744246c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205251(v=OCS.15)
ms:contentKeyID: 49308049
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criando uma configuração de arquivamento para gerenciar o arquivamento de sites ou pools específicos

 

_**Tópico modificado em:** 2013-02-23_

No Painel de Controle do Lync Server 2013, você usa as configurações de Arquivamento para controlar como o arquivamento é realizado em sua implantação. Isto inclui as seguintes configurações de Arquivamento:

  - Uma configuração global criada por padrão ao implantar o Lync Server 2013.

  - Configurações do nível local e nível de pool opcional que você pode criar e usar para especificar como o arquivamento é implementado para sites ou pools específicos.

Você inicialmente define as configurações de Arquivamento ao implantar o Arquivamento, mas é possível alterar, adicionar e excluir configurações após a implantação. Para obter detalhes sobre como as configurações de Arquivamento são implementadas, incluindo quais opções é possível especificar e a hierarquia das configurações de Arquivamento, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de Planejamento, Implantação ou Operações.

> [!NOTE]  
> Para usar o arquivamento, você deve configurar as políticas de Arquivamento para especificar se deve habilitar o arquivamento para comunicações internas, comunicações externas ou ambos para usuários hospedados no Lync Server 2013. Por padrão, o arquivamento não é habilitado para comunicações internas e externas. Antes de habilitar o Arquivamento em qualquer política, você deve especificar as configurações de Arquivamento adequadas para sua implantação e, opcionalmente, para sites e pools específicos, conforme descrito nesta seção. Para obter detalhes sobre como habilitar o Arquivamento, consulte <a href="lync-server-2013-configuring-and-assigning-archiving-policies.md">Configurando e atribuindo políticas de arquivamento</a> na documentação de Implantação.<br />Se você decidir após implantar o Arquivamento que deseja usar a integração do Microsoft Exchange para armazenar os dados e arquivos de arquivamento nos servidores do Exchange 2013 e todos seus usuários estão hospedados em seus servidores do Exchange 2013, você deve remover a configuração do banco de dados do SQL Server da sua topologia. Você deve usar o Construtor de Topologias para fazer isso. Para obter detalhes, consulte <a href="lync-server-2013-changing-archiving-database-options.md">Modificando opções do banco de dados de arquivamento no Lync Server 2013</a> na documentação de Operações.

## Para criar uma configuração de arquivamento de um site ou pool

1.  Usando uma conta de usuário atribuída à função CsArchivingAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação da esquerda, clique em **Monitoramento e Arquivamento**, e depois, clique em **Configuração de Arquivamento**.

4.  Na página **Configuração de arquivamento**, clique em **Novo** e siga um destes procedimentos:
    
      - Para criar uma configuração de arquivamento local, clique em **Configuração local** e, em **Selecionar um local**, selecione o local a ser configurado para arquivamento.
    
      - Para criar uma configuração de arquivamento do pool, clique em **Configuração do pool** e, em **Selecionar um pool**, selecione o pool a ser configurado para arquivamento.

5.  Em **Nova configuração de arquivamento**, na caixa de lista suspensa **Configuração de arquivamento**, faça um dos seguintes:
    
      - Para habilitar o arquivamento apenas para sessões de IM, clique em **Arquivar sessões de IM**.
    
      - Para habilitar o arquivamento para sessões de IM e conferências da Web, clique em **Arquivar sessões de IM e conferência da Web**.
    
      - Para desabilitar o arquivamento da política, clique em **Desabilitar arquivamento**.

6.  Também em **Nova configuração de arquivamento**, faça o seguinte:
    
      - Para bloquear a atividade quando o arquivamento não estiver disponível, marque a caixa de seleção **Bloquear sessões de mensagem instantânea ou conferência da Web se o arquivamento falhar**.
    
      - Para usar o Microsoft Exchange Server para armazenar dados de arquivamento, clique na caixa de seleção integração do **Microsoft Exchange**.
    
      - Para habilitar a exclusão de dados, marque a caixa de seleção **Habilitar exclusão dos dados de arquivamento** e faça um dos seguintes:
        
          - Para especificar a exclusão após um número específico de dias, clique em **Excluir dados de arquivamento exportados e dados de arquivamento armazenados após uma duração máxima (dias)** e especifique o número de dias.
        
          - Para limitar a exclusão de dados de arquivamento que foram exportados, clique em **Excluir apenas dados de arquivamento exportados**.

7.  Clique em **Confirmar**.

## Criando definições de configuração de arquivamento usando cmdlets do Lync Server

As definições de configuração de arquivamento também podem ser criadas usando o Windows PowerShell e o cmdlet New-CsArchivingConfiguration do Windows PowerShell. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Criar um novo conjunto de definições de configuração de arquivamento para um local

  - O comando a seguir cria um novo conjunto de definições de configuração de arquivamento para o local Redmond:
    
        New-CsArchivingConfiguration -Identity "site:Redmond"

## Criar um novo conjunto de definições de configuração de arquivamento que permite apenas arquivamento de IM

  - Como nenhum parâmetro (além do parâmetro obrigatório Identity) foi associado no comando anterior, o novo conjunto de definições de configuração usará os valores padrões para todas as suas propriedades. Para criar configurações que usam valores de propriedade diferentes, basta incluir o parâmetro e o valor de parâmetro adequado. Por exemplo, para criar um conjunto de definições de configuração de arquivamento que, por padrão, permite o arquivamento de sessões de mensagem instantânea, use apenas um comando como este:
    
        New-CsArchivingConfiguration -Identity "site:Redmond" -EnableArchiving "ImOnly"

## Especificar vários valores de propriedade ao criar definições de configuração de arquivamento

  - Vários valores de propriedade podem ser modificados incluindo vários parâmetros. Por exemplo, este comando define a nova configuração para arquivar sessões de mensagem instantânea e o bloqueio de mensagem instantânea do serviço de arquivamento não está disponível:
    
        New-CsArchivingConfiguration -Identity "site:Redmond" -EnableArchiving "ImOnly" -BlockOnArchiveFailure $True

Para obter mais informações, consulte o tópico de ajuda para o cmdlet [New-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsArchivingConfiguration).

## Consulte Também

#### Conceitos

[Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md)  

#### Outros Recursos

[Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md)

