---
title: 'Lync Server 2013: Configuração do Envio de Logs do Servidor SQL entre o espelho primário e o banco de dados secundário de Envio de Logs'
TOCTitle: Configuração do Envio de Logs do Servidor SQL entre o espelho primário e o banco de dados secundário de Envio de Logs
ms:assetid: 4e8e9ce9-4301-47f2-a0c3-669afeb53295
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204887(v=OCS.15)
ms:contentKeyID: 49306671
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração do Envio de Logs do Servidor SQL entre o espelho primário e o banco de dados secundário de Envio de Logs no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Execute as seguintes etapas para que o envio de log continue se o banco de dados Chat Persistente primário tiver feito um failover ao seu banco de dados espelho.

1.  Faça um failover manual no banco de dados Chat Persistente primário ao espelho. Isso pode ser realizado usando o Shell de Gerenciamento do Lync Server e o cmdlet **Invoke-CsDatabaseFailover**. Para obter informações detalhadas, consulte "Usando os Cmdlets Shell de Gerenciamento do Lync Server" em [Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md).

2.  Usando o Management Studio SQL Server, conecte a instância espelho Servidor de Chat Persistente primária.

3.  Certifique-se de que o Agente SQL Server esteja em execução.

4.  Clique com o botão direito no banco de dados mgc e, em seguida, clique em **Propriedades** .

5.  Em **Selecionar uma página** , clique em **Envio de Logs de Transações** .

6.  Selecione a caixa de seleção **Habilitar como banco de dados primário em uma configuração de envio de log** .

7.  Em **Backups de log de transações** , clique em **Configurações de Backup** .

8.  Na caixa de diálogo **Caminho de rede para a pasta Backup** , digite o caminho de rede para compartilhamento que você criou para a pasta backup de log de transação.

9.  Se a pasta de backup estiver no servidor primário, digite o caminho local na pasta de backup na caixa de diálogo **Se a pasta de backup estiver localizada no servidor primário, digite um caminho local para a pasta** . (Se a pasta de backup não estiver o servidor primário, você pode deixa essa caixa de diálogo vazia.)
    
    > [!IMPORTANT]  
    > Se a conta de serviço SQL Server no servidor primário for executada na conta do sistema local, você deverá criar sua pasta de backup no servidor primário e especificar o caminho local desta pasta.

10. Configure os parâmetros **Excluir arquivos com mais de** e **Alertar se nenhum backup ocorrer em** .

11. Observe a agenda de backup listada na caixa de diálogo **Agendar** em **Trabalho de backup** . Para personalizar a agenda para instalação, clique em **Agendar** e ajuste o Agente SQL Server agendado, conforme solicitado.
    
    > [!IMPORTANT]  
    > Use as mesmas configurações que você usou para o banco de dados primário.

12. Em **Compactação** , selecione **Usar a configuração padrão do servidor** e clique em **OK** .

13. Em **Instâncias e bancos de dados do servidor secundário** , clique em **Adicionar** .

14. Clique **Conectar** e conecte-se na instância do SQL Server que você configurou como servidor secundário.

15. Na caixa de diálogo **Banco de dados secundário** , selecione o banco de dados **mgc** da lista.

16. Na guia **Inicializar Banco de Dados Secundário** , selecione a opção **Não, o banco de dados secundário é inicializado** .

17. Na guia **Copiar Arquivos** , em **Pasta de destino dos arquivos copiados** , digite o caminho da pasta à qual a o backup de logs de transação deveriam ser copiados e clique em **OK** . Essa pasta normalmente se encontra no servidor secundário.

18. Abra a lista suspensa **Configuração do Script** e selecione **Configuração de Script na Janela Nova Consulta** .

19. Na nova janela de consulta, em **Propriedades do Banco de Dados** , clique em **OK** para iniciar o processo de configuração.

20. Selecione e execute a primeira metade da consulta (veja etapa 18) até a linha: -- \*\*\*\*\*\* Fim: Script a ser executado no Primário: \*\*\*\*\*\*.
    
    > [!IMPORTANT]  
    > A execução manual desse script é necessária porque o SQL Server Management Studio não suporta banco de dados primário múltiplos em uma SQL Server configuração de Envio de Log.

21. Selecione **Cancelar** para fechar o painel de configuração de envio do Arquivo de Log e para estabelecer uma configuração de trabalho que implemente corretamente o envio do arquivo de log para os bancos de dados primário e espelhado (no case de failover).

22. Faça o failback do banco de dados do Chat Persistente primário ao primário. Isso é feito usando o Shell de Gerenciamento do Lync Server e o cmdlet **Invoke-CsDatabaseFailover**. Para obter informações detalhadas, consulte "Usando os Cmdlets Shell de Gerenciamento do Lync Server" em [Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md).

## Consulte Também

#### Conceitos

[Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)  
[Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md)

