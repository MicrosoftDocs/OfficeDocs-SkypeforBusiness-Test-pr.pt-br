---
title: Associando um Repositório de Monitoramento ao Pool de Front End
TOCTitle: Associando um Repositório de Monitoramento ao Pool de Front End
ms:assetid: d3a20d5e-3f24-4cff-bc9b-4f84fea30e6b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205271(v=OCS.15)
ms:contentKeyID: 49308200
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Associando um Repositório de Monitoramento ao Pool de Front End

 

_**Tópico modificado em:** 2013-04-22_

No Microsoft Lync Server 2013, os dados de monitoramento podem apenas ser coletados em pools de front-end que foram associados com um repositório de armazenamento, uma tarefa geralmente realizada para definir um pool de front-end no Construtor de Topologia. Para associar um repositório de monitoramento com um novo pool de Front-end, certifique-se de selecionar a opção **Monitoramento (registro de detalhes da chamada e registro das métricas de qualidade de experiência)** na página **Selecionar recursos** do assistente Definir novo pool de front-end. Observe que, se você selecionar esta opção, também deve especificar um repositório SQL de forma a concluir o assistente. No entanto, este repositório precisa existir no momento da execução do assistente. Isto significa que você pode primeiro associar um pool com um repositório de monitoramento e posteriormente instalar e configurar esse repositório.

Em alternativa, é possível associar um pool de front-end existente com um repositório de monitoramento novo ou diferente ao concluir o seguinte procedimento:

1.  Clique em **Iniciar** , clique em **Todos os Programas** , clique em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na caixa de diálogo **Construtor de Topologias**, selecione **Baixar topologia da implantação existente** e clique em **OK**.

3.  Na caixa de diálogo **Salvar como**, insira um nome de arquivo da sua topologia atual e clique em **Salvar**. A topologia salva pode ser recuperada posteriormente e republicada em caso que hajam problemas com a nova topologia.

4.  No Construtor de Topologias, expanda **Lync Server 2013**, expanda o nome do site contendo o pool de front-end e expanda **Pools de front-end do Enterprise Edition**.

5.  Clique com o botão direito no nome do pool a ser associado com o repositório de monitoramento e clique em **Editar Propriedades**.

6.  Na caixa de diálogo **Editar propriedades**, na guia **Geral**, selecione a opção **Monitoramento (CDR e métricas QoE)** e selecione um banco de dados existente do SQL Server da lista suspensa **Monitoramento do repositório do SQL Server**. (Em alternativa, clique em **Novo** para associar o pool com um novo repositório do banco de dados.) Se você escolher usar um novo repositório do banco de dados, na caixa de diálogo **Definir novo repositório SQL**, insira o FQDN do computador do SQL Server na caixa **FQDN do Sql Server**. Se você deseja usar a instância padrão do SQL Server para este repositório, selecione **Instância padrão**; caso contrário, selecione **Instância nomeada** e insira o nome da instância na caixa **Instância nomeada**.
    
    A caixa de diálogo **Editar propriedades** também oferece a opção de criar um espelho SQL para seu banco de dados de monitoramento (um espelho SQL permite manter duas cópias do seu banco de dados de monitoramento, uma cópia armazenada no computador do repositório de monitoramento e outro no computador do SQL espelho). Para habilitar o espelhamento, selecione **Esta instância SQL está na relação de espelho** e insira o número da porta para o servidor espelho na caixa **Número da porta de espelho**.

7.  Na caixa de diálogo **Editar propriedades**, clique em **OK**.

Após associar o repositório de monitoramento com um pool de front-end, você deve publicar a nova topologia antes das alterações entrarem em vigor. Para publicar sua nova topologia, conclua as seguintes etapas no Construtor de Topologia:

1.  Clique em **Ação**, aponte para **Topologia** e clique em **Publicar**.

2.  No assistente Publicar topologia, na página **Publicar a topologia**, clique em **Avançar**.

3.  Na página **Publicar assistente concluído**, clique em **Concluir**.

Após a topologia ser publicada, é possível instalar o banco de dados de monitoramento no computador que irá hospedar o repositório de monitoramento. O banco de dados de monitoramento pode ser instalado utilizando o Shell de Gerenciamento do Lync Server e o Windows PowerShell. Para instalar o banco de dados localmente (isto é, para instalar o banco de dados no mesmo computador onde você está executando o Shell de Gerenciamento do Lync Server), inicie o Shell de Gerenciamento no computador adequado, digite o seguinte comando e pressione ENTER:

    Install-CsDatabase -LocalDatabases

Ao executar o comando anterior, Install-CsDatabase lerá a topologia atual do Lync Server, determine quais bancos de dados precisam ser instalados no computador local e, automaticamente, instale e configure cada banco de dados.

Para instalar o banco de dados em um computador remoto (isto é, um computador diferente daquele onde o Shell de Gerenciamento está executando), você deve incluir pelo menos dois parâmetros: o parâmetro ConfiguredDatabases e o parâmetro SqlServerFqdn. Estes parâmetros dizem ao cmdlet Install-CsDatabase para recuperar a topologia do Lync Server e instalar e configurar os bancos de dados necessários no computador especificado pelo parâmetro SqlServerFqdn. O parâmetro SqlServerFqdn deve usar um valor de parâmetro representando o FQDN do computador onde os bancos de dados devem ser instalados.

Por exemplo, este comando instala o banco de dados de monitoramento no computador atl-sql-001.litwareinc.com:

    Install-CsDatabase -ConfiguredDatabases -SqlServerFqdn atl-sql-001.litwareinc.com

Em alternativa, é possível instalar o banco de dados de monitoramento executando o Assistente de implantação do Lync Server no computador que irá hospedar o repositório de monitoramento. Para fazer isso, faça o login no computador adequado e conclua o seguinte procedimento:

1.  Clique em **Iniciar**, **Todos os Programas**, **Microsoft Lync Server 2013** e em **Assistente de Implantação do Lync Server**.

2.  No Assistente de Implantação, clique em **Instalar ou Atualizar o Sistema do Lync Server**.

3.  Na página **Implantar**, em **Etapa 2: Instalar ou remover componentes do Lync Server**, clique em **Executar novamente**.

4.  No assistente de Instalação dos componentes do Lync Server, na página **Instalar componentes do Lync Server**, clique em **Avançar**.

5.  Na página **Especificar caminho para MSIs**, digite o caminho para o arquivo Ocscore.msi (um arquivo incluído com sua mídia de instalação do Lync Server) e clique em **Avançar**.

6.  Na página **Executando Comandos**, clique em **Concluir**.

Para garantir que todos os serviços necessários do Lync Server foram iniciados, clique em **Executar** no cabeçalho **Etapa 4: Iniciar serviços** da página **Implantar**

