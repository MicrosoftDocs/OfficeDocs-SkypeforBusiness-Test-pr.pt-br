---
title: Como o arquivamento funciona no Lync Server 2013
TOCTitle: Como o arquivamento funciona no Lync Server 2013
ms:assetid: 536a52a9-cfb7-4392-9620-ffc5b319b31b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204900(v=OCS.15)
ms:contentKeyID: 49306722
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Como o arquivamento funciona no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-04_

O arquivamento do Lync Server 2013 fornece opções para ajudar você a atender às suas necessidades de conformidade. Para implementar e mantê-lo de uma maneira que atenda de forma mais eficaz aos requisitos da sua organização, você deve compreender:

  - Quais tipos de informações podem ser arquivadas.

  - Como habilitar e desabilitar o arquivamento na sua implantação.

  - As opções de arquivamento que você pode configurar para controlar como o arquivamento será implementado.

## Quais tipos de informações podem ser arquivadas?

Os seguintes tipos de conteúdo podem ser arquivados:

  - Mensagens instantâneas de ponto a ponto

  - Conferências (reuniões), que são mensagens instantâneas com vários participantes

  - Conteúdo de conferências, incluindo conteúdo carregado (por exemplo, folhetos) e conteúdo relacionado ao evento (por exemplo, entradas, saídas, compartilhamento de cargas e alterações de visibilidade)

  - Os quadros de comunicações e votações compartilhados durante uma conferência

Os seguintes tipos de conteúdo não são arquivados:

  - Transferências de arquivo de ponto a ponto

  - Áudio/vídeo para mensagens instantâneas e conferências de ponto a ponto

  - O compartilhamento de área de trabalho e aplicativos para mensagens instantâneas e conferências de ponto a ponto

O Lync Server também não arquiva as conversas do Chat Persistente. Para arquivar as conversas do Chat Persistente, você deve habilitar e configurar o servidor de conformidade, que é um componente que pode ser implantado com o Microsoft Lync Server 2013, Servidor de Chat Persistente. Para obter detalhes, consulte [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md) na Documentação de planejamento.

## Como eu começo a utilizar o arquivamento?

O arquivamento é instalado automaticamente em cada Servidor Front-End quando você implanta o servidor, mas o arquivamento não é habilitado até você configurá-lo. Como você deve configurá-lo é determinado pelo modo como você implanta o arquivamento:

  - **Arquivamento utilizando a integração do Microsoft Exchange.** Se você tiver usuários que estiverem hospedados no Exchange 2013 e tiverem suas caixas de correio colocadas em bloqueio In-loco, é possível selecionar a opção para integrar o armazenamento do Lync Server 2013 ao armazenamento do Exchange. Se você escolher a opção de integração do Microsoft Exchange, utilize as políticas e configurações do Exchange 2013 para controlar o arquivamento de dados do Lync Server 2013 para esses usuários.

  - **Arquivamento utilizando os bancos de dados de arquivamento do Lync Server.** Se você tiver usuários que não estiverem hospedados no Exchange 2013, que não tiverem suas caixas de correio colocadas em bloqueio In-loco ou se você não quiser utilizar a integração do Microsoft Exchange para quaisquer ou todos os usuários na sua implantação, é possível implantar os bancos de dados de arquivamento do Lync Server utilizando o SQL Server para armazenar dados de arquivamento para esses usuários. Neste caso, as políticas e configurações de arquivamento do Lync Server 2013 determinam se o arquivamento está habilitado e com ele foi implantado. Para utilizar o Lync Server 2013, você deve adicionar os bancos de dados do SQL Server apropriados para a sua topologia e publicar a topologia.

## Configuração de arquivamento ao utilizar a integração do Microsoft Exchange

Se seus usuários estiverem hospedados no Exchange 2013 e as caixas de correio deles tiverem sido colocadas em bloqueio In-loco, você pode escolher a opção de **integração do Microsoft Exchange** (como descrita posteriormente neste seção) para arquivar o Lync Server 2013 para esses usuários e, então será possível controlar o arquivamento para esses usuários especificando as políticas e configurações de Bloqueio In-loco do Exchange, assim como as configurações do Lync Server para controlar o seguinte:

  - Se arquivará mensagens instantâneas, conferências ou ambas.

  - Se implementará o modo crítico para a sua implantação do Lync Server.

  - Seleção das opções de integração do Microsoft Exchange para utilizar o Exchange 2013 para armazenar os dados arquivados.

Essas opções de configuração de arquivamento do Lync Server 2013 serão descritas posteriormente nesta seção. Para obter informações sobre como configurar as políticas e configurações de Bloqueio In-loco do Exchange para suportar o arquivamento, consulte a documentação do produto do Exchange 2013.

## Configuração de arquivamento ao utilizar o armazenamento do banco de dados do Lync Server

Se você quiser utilizar os bancos de dados de arquivamento do Lync Server (utilizando os bancos de dados do SQL Server) para arquivar dados para quaisquer usuários na sua implantação, é possível configurar as políticas de arquivamento do Lync Server para controlar se o arquivamento está habilitado para esses usuários. Em cada política de arquivamento, você pode habilitar e desabilitar o arquivamento para uma ou ambas as opções a seguir:

  - Comunicações internas

  - Comunicações externas

Por padrão, o arquivamento não é habilitado para comunicações internas ou externas em qualquer política de arquivamento do Lync Server. Você pode habilitar e desabilitar as comunicações utilizando o Painel de Controle do Lync Server 2013 ou os cmdlets no Shell de Gerenciamento do Lync Server 2013.

As políticas de arquivamento do Lync Server 2013 incluem o seguinte:

  - **Política de arquivamento global**. Essa é uma política de arquivamento padrão e se aplica a toda a sua implantação. Ela é criada quando você implanta o Lync Server 2013 e, por padrão, desabilita o arquivamento para as comunicações internas e externas. Não é possível excluir essa política. Se você escolher a opção excluir, a política global será redefinida para as configurações padrão.

  - **Política de arquivamento do site**. Opcionalmente, você pode habilitar ou desabilitar o arquivamento para um ou mais sites específicos criando e configurando uma política de arquivamento em nível de site para o site. Quando você criar uma política de arquivamento em nível de site, por padrão, o arquivamento não está ativado. Você pode excluir qualquer política de arquivamento em nível de site que tenha criado. Uma política de arquivamento em nível de site substitui a política global, mas somente para o site especificado na política. Por exemplo, se você habilitar o arquivamento de comunicações internas e externas em sua política global e criar uma política de site na qual você desabilita o arquivamento de comunicações externas, somente as comunicações internas serão arquivadas para esse site.

  - **Política de arquivamento do usuário**. Opcionalmente, você pode habilitar ou desabilitar o arquivamento para um ou mais usuários e grupos de usuários específicos criando, configurando e aplicando uma política de arquivamento em nível de usuário para os usuários e grupos de usuários especificados. Quando você cria uma política de arquivamento em nível de usuário, por padrão, o arquivamento não está habilitado. É possível excluir qualquer política de arquivamento em nível de usuário que você criou e também é possível alterar a quais usuários e grupos de usuários a política de arquivamento se aplica. Uma política de arquivamento em nível de usuário substitui a política global e as políticas do site, mas somente para os usuários e grupos de usuários aos quais a política foi aplicada. Por exemplo, se você desabilitar o arquivamento de comunicações internas e externas em sua política global, crie uma política em nível de site e habilite nela o arquivamento de comunicações internas e externas e, em seguida, crie uma política em nível de usuário e desabilite nela o arquivamento de comunicações externas, as comunicações serão arquivadas para as comunicações internas e externas para todos os usuários do site, exceto para os usuários aos quais você aplicar a política em nível de usuário, somente as comunicações internas seriam arquivadas.

Para obter detalhes sobre como configurar inicialmente as políticas de arquivamento ao implantar o arquivamento, consulte [Configurando e atribuindo políticas de arquivamento](lync-server-2013-configuring-and-assigning-archiving-policies.md) na Documentação de implantação. Para obter detalhes sobre o uso das políticas de arquivamento para habilitar e desabilitar as comunicações após a implantação, consulte [Gerenciando o arquivamento de comunicações internas e externas no Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md) na Documentação de operações.

> [!NOTE]  
> Se você implementar os bancos de dados do Lync Server 2013 e habilitar a integração do Microsoft Exchange, as políticas do Exchange 2013 substituirão as políticas de arquivamento do Lync Server, mas somente para os usuários que estiverem hospedados no Exchange 2013 e tiverem suas caixas de correio colocadas em bloqueio In-loco. O arquivamento do Lync Archiving depende somente da política de Bloqueio In-loco do Microsoft Exchange.

## Quais opções eu tenho para configurar um arquivamento?

Além de utilizar as políticas e habilitar e desabilitar o arquivamento, você tem outras opções de arquivamento que podem ser configuradas para toda a sua implantação e, opcionalmente, para sites e pools específicos. Você controla a maioria das opções de arquivamento utilizando uma ou mais configurações de arquivamento, que estão disponíveis no Painel de Controle do Lync Server 2013, mas também tem outra opção que está disponível para configuração utilizando o Shell de Gerenciamento do Lync Server 2013.

## Opções de configuração de arquivamento disponíveis no Painel de Controle do Lync Server 2013

Cada configuração de arquivamento fornece as seguintes opções:

A configuração em nível global é criada automaticamente quando você implanta o arquivamento e pode ser configurada, mas não excluída. Se você selecionar a opção para excluir a configuração global, as configurações são redefinidas para os valores padrão. Você pode criar várias configurações de site e de pool que, em conjunto com a configuração global, controlam as configurações de arquivamento. Para a configuração global e cada configuração de site e de pool, você tem as seguintes opções:

  - Desabilite o arquivamento, habilite o arquivamento somente para mensagens instantâneas (IM) ou habilite o arquivamento das mensagens instantâneas e das conferências.

  - Configure o modo crítico para bloquear as mensagens instantâneas e as sessões de conferência no evento de uma falha do Lync Server. As falhas incluem o seguinte:
    
      - **Mensagens instantâneas**. Um problema com o serviço de armazenamento do Lync Server. Neste caso, as mensagens instantâneas são bloqueadas para os usuários que estiverem habilitados para arquivamento.
    
      - **Conferências**. Uma falha poderia ser um compartilhamento de arquivos indisponível ou um problema com o serviço de armazenamento. Neste caso, todas as conferências ativas hospedadas no pool no momento da falha serão alternadas para o modo restrito e novas conferências não poderão ser ativadas.
    
    As mensagens instantâneas e conferências são recuperadas automaticamente após as falhas serem corrigidas.

  - Especifique o uso da integração do Microsoft Exchange Server 2013 para utilizar o Exchange 2013 para armazenar os dados arquivados, em vez de configurar os bancos de dados do SQL Server separados para armazenar os dados de arquivamento do Lync Server 2013.

  - Configure as opções de limpeza para os dados arquivados. Isso inclui especificar quando limpar os dados arquivados, que pode ser uma das opções a seguir:
    
      - Após um número de dias especifico que você especificou
    
      - Após os dados de arquivamento terem sido exportados (o que inclui os dados que foram carregados para o Exchange, se você habilitar a integração do Microsoft Exchange).
    
    > [!NOTE]  
    > Se você habilitar a integração do Microsoft Exchange, a limpeza para os usuários hospedados no Exchange 2013 e que tiverem suas caixas de correio colocadas em bloqueio In-loco será controlada pelo Exchange. A única qualificação é para os arquivos de conferência, que estão armazenados no compartilhamento de arquivos do Lync Server. Esses arquivos são limpos a partir do compartilhamento de arquivos somente após os arquivos terem sido exportados (carregador para o Exchange), se você selecionar a opção para limpar os dados após os dados de arquivamento terem sido exportados ou após um número máximo de dias especificado, caso tenha especificado um número máximo de dias para retenção.

Por padrão, nenhuma opção de arquivamento está habilitada. Você pode gerenciar as configurações de arquivamento utilizando o Painel de Controle do Lync Server 2013.

Você pode especificar as seguintes configurações de arquivamento:

  - **Configuração de arquivamento global**. Essa é a configuração de arquivamento padrão e se aplica a toda a sua implantação. Ela é criada quando você implanta o Lync Server 2013 e, por padrão, não habilita a função de arquivamento. É possível modificar a configuração global, mas não é possível excluí-la. Se você escolher excluir a opção para a configuração, a configuração global será redefinida para as configurações padrão.

  - **Configuração de arquivamento do site**. Opcionalmente, você pode configurar o arquivamento para um ou mais sites específicos criando e definindo uma configuração em nível de site para um site individual. Uma configuração de arquivamento em nível de site existe somente se você criá-la. É possível modificar e excluir qualquer configuração de arquivamento em nível de site. Uma configuração de arquivamento em nível de site substitui uma configuração global, mas somente para o site especificado na configuração em nível de site. Por exemplo, se você habilitar o arquivamento somente para as mensagens instantâneas na sua configuração global e criar uma configuração de site na qual você habilite o arquivamento para as mensagens instantâneas e conferências, as conferências serão somente arquivadas para o restante da sua organização.

  - **Configuração de arquivamento do pool**. Opcionalmente, você pode especificar as configurações de arquivamento para um ou mais pools específicos criando e definindo uma configuração em nível de pool para um pool individual. Uma configuração de arquivamento em nível de pool existe somente se você criá-la. É possível modificar e excluir qualquer configuração de arquivamento em nível de pool. Uma configuração de arquivamento em nível de pool substitui uma configuração global e qualquer configuração de arquivamento de site que tiver sido criada. Por exemplo, se você habilitar o arquivamento somente para as mensagens instantâneas na sua configuração global, crie uma configuração em nível de site na qual você habilite o arquivamento para as mensagens instantâneas e conferências para o site e, então crie uma configuração em nível de pool na qual você habilite o arquivamento somente para as mensagens instantâneas, as comunicações devem ser arquivadas para mensagens instantâneas e conferências para todos os usuários do site, exceto para os usuários hospedados no pool especificado na configuração em nível de pool. Para todos os outros usuários na sua organização, o arquivamento deveria ser habilitado somente para mensagens instantâneas.

Para obter detalhes sobre como definir as configurações iniciais de arquivamento ao implantar o arquivamento, consulte [Configurando opções de arquivamento](lync-server-2013-configuring-archiving-options.md) na Documentação de implantação. Para obter detalhes sobre como utilizar as políticas de arquivamento para habilitar e desabilitar as comunicações após a implantação, consulte [Gerenciando opções de configuração do arquivamento no Lync Server 2013 para sua empresa, sites e pools](lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md) na Documentação de operações.

## Opções de arquivamento disponíveis somente no Windows PowerShell

Utilizando o Shell de Gerenciamento do Lync Server 2013, você pode usar cmdlets para implementar as opções que não estão disponíveis no Painel de Controle do Lync Server 2013. Essas opções incluem o seguinte:

  - **Arquivar mensagens duplicadas**. Para obter detalhes, consulte [New-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsArchivingConfiguration) e [Set-CsArchivingConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsArchivingConfiguration) na Documentação de operações.

  - **Exportar dados arquivados**. Para obter detalhes, consulte [Export-CsArchivingData](https://docs.microsoft.com/en-us/powershell/module/skype/Export-CsArchivingData)

## Como eu acesso os dados arquivados?

O acesso aos dados arquivados depende de onde os dados estão armazenados:

  - **Armazenamento do Microsoft Exchange**. Se você escolher a opção de integração do Exchange, o Lync Server depositará o conteúdo de arquivamento no armazenamento do Exchange 2013 para todos os usuários hospedados no Exchange 2013 e que tiveram suas caixas de correio colocadas em Retenção Local. Os dados arquivados são armazenados na pasta Itens recuperáveis das caixas de correio dos usuários, que geralmente é invisível pra os usuários e só pode ser pesquisada pelos usuários que tiverem uma função de Exchange**Gerenciamento de Descoberta**. O Exchange permite a pesquisa federada e a descoberta, junto com o SharePoint, se implantado. Para obter mais detalhes sobre armazenamento, retenção e descoberta de dados armazenados no Exchange, consulte a documentação do Exchange 2013 e do SharePoint.

  - **Arquivamento do Lync Server**. Se você configurar os bancos de dados de arquivamento do Lync Server 2013 para armazenamento dos dados do Lync Server, o conteúdo de arquivamento dos depósitos do Lync Server nos bancos de dados de arquivamento do Lync Server (bancos de dados do SQL Server) para quaisquer usuários que não estiverem hospedados no Exchange 2013 e que suas caixas de correio não tenham sido colocadas em bloqueio In-loco. Esses dados não podem ser pesquisados, mas eles podem ser exportados para formatos que podem ser pesquisados utilizando outras ferramentas. Para obter detalhes sobre a exportação de dados armazenados nos bancos de dados de arquivamento, consulte [Exportando dados arquivados do Lync Server 2013](lync-server-2013-exporting-archived-data.md) na Documentação de operações.

Para obter mais detalhes sobre como o Lync Server 2013 e o Exchange 2013 funcionam juntos, consulte [Suporte a Servidor Exchange e à integração com SharePoint no Lync Server 2013](lync-server-2013-exchange-and-sharepoint-integration-support.md) na Documentação de suporte.

