---
title: Configurando o Microsoft Lync Server 2013 para usar arquivamento do Microsoft Exchange Server 2013
TOCTitle: Configurando o Microsoft Lync Server 2013 para usar arquivamento do Microsoft Exchange Server 2013
ms:assetid: 260346d1-edc8-4a0c-8ad2-6c2401c3c377
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ679896(v=OCS.15)
ms:contentKeyID: 49886140
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Microsoft Lync Server 2013 para usar arquivamento do Microsoft Exchange Server 2013

 

_**Tópico modificado em:** 2014-06-24_

O Microsoft Lync Server 2013 oferece aos administradores a opção de ter transcrições de mensagem instantânea e conferência da Web arquivadas na caixa de correio do Microsoft Exchange Server 2013 do usuário ao invés de um banco de dados do SQL Server. Se você habilitar esta opção, as transcrições são gravadas na pasta Lixeira da caixa de correio do usuário. A pasta Lixeira é uma pasta oculta encontrada na pasta Itens Recuperáveis. Embora esta página não esteja visível para os usuários finais, a pasta é indexada pelo mecanismo de pesquisa do Exchange e pode ser descoberta usando a pesquisa da caixa de correio do Exchange e/ou Microsoft SharePoint Server 2013. Como a informação é armazenada na mesma pasta usada pelo recurso Retenção Local do Exchange (responsável pelo arquivamento de email e outras comunicações do Exchange), os administradores podem usar uma única ferramenta para pesquisar todas as comunicações eletrônicas arquivadas para um usuário.

> [!IMPORTANT]  
> Para desabilitar completamente o arquivamento de conversas do Lync, você também deverá desabilitar o histórico de conversas do Lync. Para obter mais informações, consulte os seguintes tópicos: <a href="lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md">Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013</a>, <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy">New-CsClientPolicy</a>, e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy">Set-CsClientPolicy</a>.

Para poder arquivar transcrições no Exchange 2013, você deve começar a configurar a autenticação servidor para servidor entre dois servidores. Após a autenticação servidor para servidor ser definida, é possível executar as seguintes tarefas no Microsoft Lync Server 2013 (observe que, dependendo da sua configuração, você não poderá precisar concluir todas estas tarefas):

1.  Habilitar o arquivamento do Exchange modificando suas definições de configuração de arquivamento do Lync Server. Esta etapa é obrigatória para todas as implantações.

2.  Habilitar o arquivamento para comunicações internas e/ou externas dos usuários. Esta etapa é obrigatória para todas as implantações.

3.  Configurar a propriedade ExchangeArchivingPolicy para cada usuário. Esta etapa é obrigatória apenas no Lync Server e Exchange localizados em diferentes florestas.

## Etapa 1: Habilitar o Arquivamento do Exchange

O arquivamento no Lync Server é gerenciado principalmente usando as definições de configuração de arquivamento. Ao instalar o Lync Server 2013, você é fornecido com um único conjunto global destas configurações. (Os administradores podem opcionalmente criar novos conjuntos de configurações de arquivamento no escopo local). Por padrão, o arquivamento não é habilitado nas configurações globais, nem o arquivamento do Exchange habilitado nestas configurações. Para poder usar o arquivamento do Exchange, os administradores devem configurar as propriedades EnableArchiving e EnableExchangeArchiving nestas definições de configuração. A propriedade EnableArchiving pode ser definida para um dos seguintes três valores:

  - **Nenhum** . o Arquivamento é desabilitado. Este é o valor padrão. Se o EnableArchiving é definido para Nenhum, nada será arquivado em seu banco de dados de arquivamento do Lync Server ou Exchange 2013.

  - **ImOnly** . Apenas transcrições de mensagem instantânea são arquivadas. Se o arquivamento do Exchange está habilitado, estas transcrições serão arquivadas no Exchange 2013. Se o arquivamento do Exchange está desabilitado, estas transcrições serão arquivadas no Lync Server.

  - **ImAndWebConf** . As transcrições de mensagem instantânea e de conferência da Web são arquivadas. Se o arquivamento do Exchange está habilitado, estas transcrições serão arquivadas no Exchange 2013. Se o arquivamento do Exchange está desabilitado, estas transcrições serão arquivadas no Lync Server.

A propriedade EnableExchangeArchiving é um valor booleano: definir EnableExchangeArchiving para True ($True) para habilitar o arquivamento do Exchange ou definir EnableExchangeArchiving para False ($False) para desabilitar o arquivamento do Exchange. Por exemplo, este comando habilita o arquivamento de transcrições de mensagens instantâneas e também habilita o arquivamento do Exchange:

    Set-CsArchivingConfiguration -Identity "global" -EnableArchiving ImOnly -EnableExchangeArchiving $True

Para desabilitar o arquivamento do Exchange, use um comando semelhante ao seguinte, que habilita o arquivamento de mensagem instantânea, mas desabilita o arquivamento para Exchange (em outras palavras, as transcrições serão arquivadas no Lync Server):

    Set-CsArchivingConfiguration -Identity "global" -EnableArchiving ImOnly -EnableExchangeArchiving $False

> [!NOTE]  
> Se a propriedade EnableArchiving estar definida para Nenhum, então o Lync Server não irão arquivar transcrições de mensagem instantânea e de conferência da Web. Neste caso, o servidor simplesmente ignora o valor configurado para EnableExchangeArchiving.

O arquivamento do Exchange também pode ser habilitado (ou desabilitado) usando o Painel de Controle do Lync Server. Para fazer isso, conclua o seguinte procedimento:

1.  No Painel de Controle, clique em **Monitoramento e Arquivamento** e clique em **Configuração de Arquivamento** .

2.  Na guia **Configuração de Arquivamento** , clique duas vezes no conjunto de configurações de arquivamento a ser modificado (por exemplo, o conjunto **Global** ).

3.  No painel **Editar configuração de arquivamento** , clique na lista suspensa **Configuração de arquivamento** e selecione **Arquivar sessões de IM** (para arquivar apenas sessões de mensagem instantânea) ou **Arquivar sessões de IM e conferência da Web** (para arquivar sessões de mensagem instantânea e conferência da Web).

4.  Após escolher os itens a serem arquivados, marque a caixa de seleção **Integração do Exchange Server** para habilitar o arquivamento do Exchange. Para desabilitar o arquivamento do Exchange, desmarque esta caixa de seleção.

> [!NOTE]  
> A caixa de seleção <strong>Integração do Exchange Server</strong> não estará disponível se a <strong>Configuração de arquivamento</strong> está definido para <strong>Desabilitar arquivamento</strong> . Você deve habilitar o arquivamento primeiro e depois habilitar o arquivamento do Exchange.

Se o Lync Server 2013 e o Exchange 2013 estão localizados na mesma floresta, o arquivamento para usuários individuais (ou pelo menos para usuários com contas de email no Exchange 2013) é gerenciado usando as políticas de Retenção Local do Exchange. Se você possui usuários hospedados em uma versão anterior do Exchange, o arquivamento destes usuários serão gerenciados utilizado as políticas de arquivamento do Lync Server. Observe que apenas usuários com contas no Exchange 2013 podem ter suas transcrições do Lync arquivadas no Exchange.

Se o Lync Server 2013 e o Exchange 2013 estão localizados em florestas diferentes, o arquivamento para usuários individuais é gerenciado configurando a propriedade ExchangeArchivingPolicy para cada conta de usuário individual. Consulte a Etapa 3 para obter mais informações.

## Etapa 2: Habilitar o arquivamento de comunicações internas e/ou externas

Após ter habilitado o arquivamento (e o arquivamento do Exchange), você deve modificar as políticas de arquivamento adequadas para garantir que as sessões do usuário sejam realmente arquivadas. Observe que apenas habilitar o arquivamento (Etapa 1) não faz com que o Lync Server comece a arquivar transcrições de mensagem instantânea e conferência da Web. Ao invés disso, você deve usar políticas de arquivamento para habilitar o arquivamento interno e/ou externo. Ao instalar o Lync Server 2013, você também instala uma única política de arquivamento global que contém duas propriedades:

  - **ArchiveInternal** . Quando definido para True ($True) indica que as sessões de comunicação interna envolvendo apenas usuários com contas do Active Directory em sua organização serão arquivadas.

  - **ArchiveExternal** . Quando definido para True ($True) indica que as sessões de comunicação interna (sessões envolvendo pelo menos um usuário que não possui uma conta do Active Directory em sua organização) serão arquivadas.

Por padrão, ambos os valores de propriedade são definidos para False, significando que as sessões de comunicação interna e externa não são arquivadas. Para modificar a política global, é possível usar o Shell de Gerenciamento do Lync Server e o cmdlet Set-CsArchivingPolicy. Este comando habilita o arquivamento de sessões de comunicação interna e externa:

    Set-CsArchivingPolicy -Identity "global" -ArchiveInternal $True -ArchiveExternal $True

Em alternativa, é possível usar New-CsArchivingPolicy para criar uma nova política no escopo local ou no escopo por usuário. Por exemplo, este comando cria uma nova política de arquivamento por usuário chamada RedmondArchivingPolicy:

    New-CsArchivingPolicy -Identity "RedmondArchivingPolicy" -ArchiveInternal $True -ArchiveExternal $True

Se você criar uma política por usuário, precisará atribuir esta política para os usuários adequados. Por exemplo:

    Grant-CsArchivingPolicy -Identity "Ken Myer" -PolicyName  "RedmondArchivingPolicy"

As políticas de arquivamento também podem ser gerenciadas usando o Painel de Controle do Lync Server. Dentro do Painel de Controle, clique em **Monitoramento e Arquivamento** e em **Política de Arquivamento** . Para modificar uma política existente, clique duas vezes na política (por exemplo, Global) e, no painel **Editar política de arquivamento** , marque ou desmarque as caixas de seleção **Arquivar comunicações internas** e **Arquivar comunicações externas** conforme necessário. Para criar uma nova política de arquivamento, clique em **Novo** e selecione **Política local** ou **Política de usuário** . Se você criar uma nova política de usuário, deve acessar as contas de usuário adequadas (na guia **Usuários** ) e atribuir estes usuários com a nova política.

## Etapa 3: Configurar a propriedade ExchangeArchivingPolicy

Se Lync Server 2013 e Exchange 2013 estão localizados em florestas diferentes, não é suficiente apenas habilitar o arquivamento do Exchange nas definições de configuração de arquivamento; isto não resultará nas transcrições de mensagem instantânea e conferência da Web sendo arquivadas no Exchange. Ao invés disso, você também deve configurar a propriedade ExchangeArchivingPolicy em cada conta de usuário relevante do Lync Server. Esta propriedade pode ser definida para uma dos quatro valores possíveis:

1.  Não inicializado. Indica que o arquivamento será baseado nas configurações de Retenção Local definidas para a caixa de correio do Exchange do usuário; se a Retenção Local não foi habilitada na caixa de correio do usuário, o usuário terá suas transcrições de mensagem e conferência da Web arquivadas no Lync Server.

2.  **UseLyncArchivingPolicy** . Indica que as transcrições de mensagem instantânea e conferência da Web do usuário devem ser arquivadas no Lync Server ao invés do Exchange.

3.  **NoArchiving** . Indica que as transcrições de mensagem instantânea e conferência da Web do usuário não devem ser arquivadas. Observe que esta configuração substitui qualquer política de arquivamento do Lync Server atribuída ao usuário.

4.  **ArchivingToExchange** . Indica que as transcrições de mensagem instantânea e conferência da Web do usuário devem ser arquivadas no Exchange independente das configurações de Retenção Local que foram (ou não) atribuídas à caixa de correio do usuário.

Por exemplo, para configurar uma conta de usuário para que as transcrições de mensagem instantânea e conferência da Web sejam sempre arquivadas no Exchange, é possível usar um comando semelhante a este no Shell de Gerenciamento do Lync Server:

    Set-CsUser -Identity "Ken Myer" -ExchangeArchivingPolicy ArchivingToExchange

Se você deseja definir a mesma política de arquivamento para um grupo de usuários (por exemplo, todos os usuários hospedados em um pool do Registrador específico), é possível usar um comando semelhante ao seguinte:

    Get-CsUser -Filter {RegistrarPool -eq "atl-cs-001.litwareinc.com"} | Set-CsUser -ExchangeArchivingPolicy ArchivingToExchange

Observe que você deve usar o Shell de Gerenciamento do Lync Server (e Windows PowerShell) para poder configurar o valor da propriedade ExchangeArchivingPolicy. Esta propriedade não é exposta aos administradores no Painel de Controle do Lync Server.

Se você deseja ver uma lista de todos os usuários atribuídos com uma política de arquivamento específica, é possível usar um comando semelhante ao seguinte, que retorna o nome de exibição do Active Directory de todos os usuários com a propriedade ExchangeArchivingPolicy definida para Não inicializado:

    Get-CsUser | Where-Object {$_.ExchangeArchivingPolicy -eq "Uninitialized"} | Select-Object DisplayName

Da mesma forma, este comando retorna o nome de exibição dos usuários que não tem a propriedade ExchangeArchivingPolicy definida para UseLyncArchivingPolicy:

    Get-CsUser | Where-Object {$_.ExchangeArchivingPolicy -ne "UseLyncArchivingPolicy"} | Select-Object DisplayName

