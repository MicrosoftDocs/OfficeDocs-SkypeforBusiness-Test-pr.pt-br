---
title: 'Lync Server 2013: Configurando o envio de logs do SQL Server ao banco de dados primário do servidor de chat persistente'
TOCTitle: Configurando o envio de logs do SQL Server ao banco de dados primário do servidor de chat persistente
ms:assetid: 088ea1c2-d592-4a11-b3b8-f1e2f8beae93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204653(v=OCS.15)
ms:contentKeyID: 49305803
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o envio de logs do SQL Server no Lync Server 2013 ao banco de dados primário do servidor de chat persistente

 

_**Tópico modificado em:** 2012-11-12_

Usando o SQL Server Management Studio, conecte-se à instância de banco de dados do Envio de Log secundária do Servidor de Chat Persistente e certifique-se de que o SQL Server Agent esteja em execução.

Usando o SQL Server Management Studio conectado à instância de banco de dados primária do Chat Persistente, execute as seguintes etapas:

1.  Certifique-se de que o Agente SQL Server esteja em execução.

2.  Clique com o botão direito no banco de dados mgc e, em seguida, clique em **Propriedades**.

3.  Em **Selecionar uma página**, clique em **Envio de Logs de Transações**.

4.  Selecione a caixa de seleção **Habilitar como banco de dados primário em uma configuração de envio de log**.

5.  Em **Backups de log de transações**, clique em **Configurações de Backup**.

6.  Na caixa **Caminho de rede para a pasta Backup**, digite o caminho de rede até o compartilhamento criado para a pasta de backup do log de transação.

7.  Se a pasta de backup estiver localizada no servidor primário, digite o caminho local até a pasta de backup na caixa **Se a pasta de backup estiver localizada no servidor primário, digite um caminho local para a pasta (exemplo: c:\\backup)**. (Se a pasta backup não estiver no servidor primário, deixa essa caixa em branco.)
    
    > [!IMPORTANT]  
    > Se a conta de serviço SQL Server no servidor primário for executada na conta do sistema local, você deverá criar sua pasta de backup no servidor primário e especificar o caminho local desta pasta.

8.  Configure os parâmetros **Excluir arquivos com mais de** e **Alertar se nenhum backup ocorrer em**.

9.  Observe a agenda de backup listada na caixa **Agenda** em **Trabalho de backup**. Para personalizar a agenda de sua instalação, clique em **Agenda** e ajuste a agenda do SQL Server Agent conforme o necessário.

10. Em **Compactação**, selecione **Usar a configuração padrão do servidor** e clique em **OK**.

11. Em **Instâncias e bancos de dados do servidor secundário**, clique em **Adicionar**.

12. Clique em **Conectar** e conecte-se à instância do SQL Server configurada como seu servidor secundário.

13. Na caixa de diálogo **Banco de dados secundário**, selecione o banco de dados **mgc** da lista.

14. Na guia **Inicializar Banco de Dados Secundário**, escolha a opção **Sim, gerar um backup completo do banco de dados primário e restaurá-lo no banco de dados secundário (e criar o banco de dados secundário caso ele não exista)**.

15. Na guia **Copiar Arquivos**, na caixa **Pasta de destino dos arquivos copiados**, digite o caminho da pasta na qual os backups de logs de transação devem ser copiadas. Normalmente, essa pasta está localizada no servidor secundário.

16. Observe agenda de cópia listada na caixa **Agenda** em **Trabalho de cópia**. Para personalizar a agenda de sua instalação, clique em **Agenda** e ajuste a agenda do SQL Server Agent conforme o necessário. Essa agenda deve ser quase a mesma que a agenda de backup.

17. Na guia **Restauração**, em **Estado do banco de dados ao restaurar backups**, escolha a opção **Nenhum modo de recuperação**.

18. Em **Atrasar restauração de backups pelo menos:**, selecione **0 minutos**.

19. Escolha um limite de alerta sob **Alertar se nenhuma restauração ocorrer em**.

20. Observe a agenda de restauração listada na caixa **Agenda** em **Trabalho de restauração**. Para personalizar a agenda de sua instalação, clique em **Agenda**, ajuste a agenda do SQL Server Agent conforme o necessário e clique em **OK**. Essa agenda deve ser quase a mesma que a agenda de backup.

21. Na caixa de diálogo **Propriedades do Banco de Dados**, clique em **OK** para começar o processo de configuração.

