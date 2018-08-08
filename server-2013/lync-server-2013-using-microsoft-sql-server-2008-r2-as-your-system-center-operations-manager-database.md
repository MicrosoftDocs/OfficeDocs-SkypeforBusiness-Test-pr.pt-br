---
title: "Usando M. SQL Server 2008 R2 como seu b. de dados de System Center Operations Manager"
TOCTitle: "Usando M. SQL Server 2008 R2 como seu b. de dados de System Center Operations Manager"
ms:assetid: 0efe76da-8854-499e-bdc7-3623244a8e85
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687969(v=OCS.15)
ms:contentKeyID: 49886101
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando Microsoft SQL Server 2008 R2 como seu banco de dados de System Center Operations Manager

 

_**Tópico modificado em:** 2013-07-29_

Para usar o SQL Server 2008 R2 como banco de dados back-end, conclua as etapas detalhadas neste tópico.

## Como configurar o SQL Server 2008 R2 e o SQL Server Reporting Services

Antes de começar a instalar o System Center Operations Manager, duas alterações devem ser feitas na configuração do SQL Server 2008 R2 e do SQL Server Reporting Services (essas alterações são necessárias somente se você estiver usando o SQL Server 2008 R2 como banco de dados do Operations Manager). Primeiro, execute o procedimento a seguir no computador que hospedará seu banco de dados do Operations Manager:

1.  Clique em **Iniciar** e, em seguida, em **Executar**.

2.  Na caixa de diálogo **Executar**, digite **C:\\Program Files\\Microsoft SQL Server\\ MSRS10\_50.ARCHINST\\Reporting Services\\ReportServer** e pressione ENTER.

3.  Na pasta **ReportServer**, abra o arquivo **rsreportserver.config** no Bloco de Notas ou em qualquer outro editor de texto.

4.  Próximo ao início do arquivo, você verá uma série de nós "Add Key". Encontre a entrada que começa com **\<Add Key="SecureConnectionLevel"** e defina o valor como **0**:
    
        <Add Key="SecureConnectionLevel" Value="0"/>

5.  Salve o arquivo **rsreportserver.config** e feche o editor de texto.

Depois de atualizar o arquivo de configuração do Report Server, você deve atribuir o certificado correto ao SQL Server Reporting Services. Para isso:

1.  Clique em **Iniciar**, em **Todos os Programas**, em **Microsoft SQL Server 2008 R2**, em **Ferramentas de Configuração** e em **Gerenciador de Configuração do Reporting Services**.

2.  Na caixa de diálogo **Conexão de Configuração do Reporting Services**, certifique-se de que o nome do seu servidor aparece na caixa **Nome do Servidor**. Selecione a instância do SQL Server que hospedará seu banco de dados do Operations Manager (por exemplo, **ARCHINST**) na lista suspensa **Instância do Servidor de Relatórios** e clique em **Conectar**.

3.  No Gerenciador de Configuração do Reporting Services, clique em **URL do Serviço Web**.

4.  Na página **URL do Serviço Web**, selecione o certificado a ser usado para o seu Reporting Services na lista suspensa **Certificado SSL** e clique em **Aplicar**. Depois de alguns segundos, você verá duas URLs listadas sob **URLs do Serviço Web do Servidor de Relatórios**.

5.  Clique em ambas para verificar se pode acessar o SQL Server Reporting Services.

6.  Feche o Gerenciador de Configuração do Reporting Services.

## Como criar um banco de dados do System Center Operations Manager para uso com o SQL Server 2008 R2

Se você deseja configurar o System Center Operations Manager para usar um banco de dados do SQL Server 2008 R2, será necessário criar o banco de dados do Operations Manager "manualmente" no computador que estiver executando o SQL Server 2008 R2 (novamente, estas etapas não são necessárias se você estiver usando o SQL Server 2005 ou o SQL Server 2008 como banco de dados back-end).

Para criar um banco de dados do Operations Manager manualmente, siga as etapas:

1.  Na mídia de instalação do System Center Operations Manager 2007 R2, na pasta SupportTools\\AMD64, dê um duplo clique em **DBCreateWizard.exe**.

2.  No Assistente para Configuração do Banco de Dados, na página **Benvindo ao Assistente para Configuração do Banco de Dados**, clique em **Avançar**.

3.  Na página **Informações do Banco de Dados**, deixe todas as configurações como estão e clique em **Avançar**

4.  Na página **Configuração do Grupo de Gerenciamento**, digite um nome para o seu Grupo de Gerenciamento (por exemplo, Monitoramento do **Lync Server**) na caixa **Nome do Grupo de Gerenciamento** e clique em **Avançar**.

5.  Na página **Relatórios de Erros do Operations Manager**, clique em **Avançar**.

6.  Na página **Resumo**, clique em **Concluir**.

## Como criar um data warehouse do System Center Operations Manager para uso com o SQL Server 2008 R2

O Microsoft Lync Server 2013 é entregue com três novos relatórios do System Center Operations Manager:

  - **Relatório de Disponibilidade de Cenário de Ponta a Ponta (End to End Scenario Availability Report)**   Este relatório detalha a disponibilidade/duração para os principais serviços do Lync Server, como inscrição ou presença.

  - **Relatório de Capacidade (Capacity Report)**   Usando informações de contador de desempenho, este relatório exibe tendências para componentes do sistema, como disponibilidade de memória e uso do processador.

  - **Relatório de Componentes (Component Report)**   Este relatório lista os principais geradores de alertas agrupados por componente do Lync Server.

Para usar esses relatórios, você deve instalar um data warehouse do System Center Operations Manager (um data warehouse fornece um armazenamento de longo prazo de dados operacionais). Para usar um data warehouse com o SQL Server 2008 R2, você deve executar as etapas a seguir no computador que hospeda seu banco de dados do SQL Server:

1.  Na mídia de instalação do System Center Operations Manager, na pasta Setup\\SupportTools\\AMD64, dê um duplo clique em **DBCreateWizard.exe**.

2.  No Assistente para Configuração do Banco de Dados, na página **Benvindo ao Assistente para Configuração do Banco de Dados**, clique em **Avançar**.

3.  Na página **Informações do Banco de Dados**, selecione **Banco de Dados Data Warehouse do Operations Manager** na lista suspensa **Tipo de Banco de Dados** e clique em **Avançar**.

4.  Na página **Resumo**, clique em **Concluir**.

## Como instalar o console do System Center Operations Manager

O console do Operations Manager é a principal ferramenta usada para gerenciar o System Center Operations Manager. Antes de instalar o console do Operations Manager, certifique-se de ter instalado uma versão compatível do SQL Server juntamente com o Serviço de Relatórios do SQL Server. Também é recomendado executar o Gerenciador de Configuração do SQL Server Reporting Services para verificar se o Serviço de Relatórios foi instalado e configurado corretamente.

Para instalar o console do System Center Operations Manager:

1.  Na mídia de instalação do System Center Operations Manager, dê um duplo clique em **SetupOM.exe**.

2.  Na Instalação do System Center Operations Manager 2007 R2, clique em **Verificar Pré-Requisitos**.

3.  No Visualizador de Pré-Requisitos do System Center Operations Manager, selecione os componentes do System Center a serem instalados: (**Servidor**, **Console** e **PowerShell**) e clique em **Verificar**. Verifique se nenhum problema de bloqueio foi identificado e clique em **Fechar**. Se um problema de bloqueio foi identificado, corrija-o e clique em **Verificar** para executar novamente o teste de pré-requisitos.

4.  Na Instalação do System Center Operations Manager, clique em **Instalar Operations Manager**.

5.  No assistente de Instalação do System Center Operations Manager, na página **Benvindo ao Assistente de Instalação do System Center Operations Manager**, clique em **Avançar**.

6.  Na página **Contrato de Licença do Usuário Final**, selecione **Aceito os termos do contrato de licença** e clique em **Avançar**.

7.  Na página **Registro do Produto**, digite seu nome na caixa **Nome do Usuário** e o nome da sua organização na caixa **Organização**. Digite a chave do seu produto System Center Operations Manager na caixa **Insira a chave do CD de 25 dígitos** e clique em **Avançar**.

8.  Na página **Instalação Personalizada**, selecione as opções do System Center a serem instaladas e clique em **Avançar**. Você deve selecionar **Servidor de Gerenciamento**, **Interfaces de Usuário** e **Console Web**. A opção **Banco de Dados** não deve ser selecionada e não deve ser instalada.

9.  Na página **Instância de Servidor de Banco de Dados SC**, verifique se o nome do computador em que os bancos de dados do Operations Manager estão instalados aparece na caixa **Servidor de Banco de Dados do System Center**. Clique em **Avançar**.

10. Na página **Conta de Ação do Servidor de Gerenciamento**, selecione **Conta de Domínio ou do Computador Local** e insira os valores adequados nas caixas **Conta de Usuário**, **Senha** e **Domínio ou computador local**. Clique em **Avançar**.

11. Na página **SDK e Conta de Serviço de Configuração**, selecione **Conta de Domínio ou do Computador Local** e insira os valores adequados nas caixas **Conta de Usuário**, **Senha** e **Domínio ou computador local**. Clique em **Avançar**.

12. Na página **Relatórios de Erros do Operations Manager**, clique em **Avançar**.

13. Na página **Programa de Aperfeiçoamento da Experiência do Usuário**, clique em **Avançar**.

14. Na página **Pronto para Instalar o Programa**, clique em **Instalar**.

15. Na página **Concluindo a Instalação do System Center Operations Manager**, desmarque as opções **Chave de Criptografia de Backup** e **Iniciar o console** e clique em **Concluir**.

16. Na Instalação do System Center Operations Manager, clique em **Sair**.

## Como instalar o System Center Reporting Services

Depois de instalar e configurar o console do System Center Operations Manager, você deve instalar o System Center Reporting Services. Se estiver usando o SQL Server 2008 R2 como banco de dados back-end do Operations Manager, significa que você deve primeiro fazer uma alteração temporária no grupo de segurança associado ao SQL Server Reporting Services. Se estiver usando o SQL Server 2008 R2, você deve executar as seguintes etapas:

1.  Clique em **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciador de Servidores**.

2.  No Gerenciador de Servidores, expanda **Configuração**, **Usuários e Grupos Locais** e clique em **Grupos**.

3.  Localize o grupo a seguir, onde atl-sc-001 representa o nome do seu computador e ARCHINST representa a instância do SQL Server para o banco de dados do System Center: **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST**.

4.  Clique com o botão direito no grupo e clique em **Renomear**. Renomeie o grupo excluindo **\_50** do nome do grupo. Por exemplo: **SQLServerReportServerUser$atl-sc-001$MSRS10.ARCHINST**.

5.  Feche o Gerenciador de Servidores.

Neste ponto, você está pronto para instalar o System Center Reporting Services. Para isso:

1.  Na mídia de instalação do System Center Operations Manager 2007 R2, dê um duplo clique em **SetupOM.exe**.

2.  Na Instalação do System Center Operations Manager 2007 R2, clique em **Instalar o Operations Manager Reporting**.

3.  No assistente de Instalação do System Center Operations Manager 2007 R2 Reporting, na página **Benvindo à Instalação do Operations Manager Reporting**, clique em **Avançar**.

4.  Na página **Contrato de Licença do Usuário Final**, selecione **Aceito os termos do contrato de licença** e clique em **Avançar**.

5.  Na página **Registro do Produto**, certifique-se de que seu nome e o nome da sua organização aparecem nas caixas **Nome do Usuário** e **Organização** e clique em **Avançar**.

6.  Na página **Instalação Personalizada**, clique em **Servidor de Relatórios** e selecione **Este componente e todos os componentes dependentes serão instalados no disco rígido local**. Clique em **Data Warehouse** e selecione **Este componente não estará disponível** e clique em **Avançar**.

7.  Na página **Conectar ao servidor de gerenciamento raiz**, digite o nome do servidor de gerenciamento raiz do seu Operations Manager na caixa **Servidor de Gerenciamento Raiz** e clique em **Avançar**.

8.  Na página **Conectar ao Data Warehouse do Operations Manager**, digite a instância do SQL Server em que seu data warehouse está localizado na caixa **Instância do SQL Server** (se seu data warehouse estiver localizado na instância padrão, digite simplesmente o nome do servidor; por exemplo: atl-sql-001). Verifique se o nome do banco de dados **OperationsManagerDW** aparece na caixa **Nome** e se a porta **1433** aparece na caixa **Porta do SQL Server**. Clique em **Avançar**.

9.  Na página **Instância dos Relatórios do SQL Server**, selecione o servidor de relatórios do SQL Server na lista suspensa **Insira o Servidor do SQL Server Reporting Services** e clique em **Avançar**.

10. Na página **Conta de Gravação do Data Warehouse**, insira o nome e senha do usuário a quem serão inicialmente atribuídas permissões de gravação no data warehouse nas caixas **Conta de Usuário** e **Senha**. Selecione o domínio do usuário na lista suspensa **Domínio** e clique em **Avançar**.

11. Na página **Conta do Leitor de Dados**, insira o nome e senha da conta de usuário a ser usada quando o SQL Reporting Services consultar o data warehouse nas caixas **Conta de Usuário** e **Senha**. Selecione o domínio da conta na lista suspensa **Domínio** e clique em **Avançar**.

12. Na página **Relatórios de Dados Operacionais**, clique em **Avançar**.

13. Na página **Microsoft Update**, clique em **Avançar**.

14. Na página **Pronto para instalar o programa**, clique em **Instalar**.

15. Na página **Concluindo o Assistente de Instalação dos Componentes de Relatórios do Operations Manager**, clique em **Concluir**.

16. Na Instalação do System Center Operations Manager 2007 R2, clique em **Sair**.

Depois de instalar os relatórios do System Center, use o procedimento a seguir para redefinir o nome do grupo de segurança associado aos relatórios do SQL Server. Novamente, este procedimento é necessário somente se você estiver usando o SQL Server:

1.  Clique em **Iniciar**, aponte para **Ferramentas Administrativas** e clique em **Gerenciador de Servidores**.

2.  No Gerenciador de Servidores, expanda **Configuração**, **Usuários e Grupos Locais** e clique em **Grupos**.

3.  Localize o grupo a seguir, onde atl-sc-001 representa o nome do seu computador e ARCHINST representa a instância do SQL Server para os bancos de dados de arquivamento e monitoramento: **SQLServerReportServerUser$atl-sc-001$MSRS10.ARCHINST**.

4.  Clique com o botão direito no grupo e clique em **Renomear**. Renomeie o grupo adicionando **\_50** ao final do nome do grupo, imediatamente antes do nome da instância do SQL Server. Por exemplo: **SQLServerReportServerUser$atl-sc-001$MSRS10\_50.ARCHINST**.

5.  Feche o Gerenciador de Servidores.

Se o Console de Operações do System Center estiver aberto, será necessário fechar o aplicativo e reiniciá-lo; se você não o fizer, a guia **Relatórios** não aparecerá na interface do usuário do Console de Operações. Observe que depois de reiniciar o Console de Operações pela primeira vez, pode demorar vários minutos até que todos os Relatórios de Monitoramento apareçam na guia **Relatórios**.

