---
title: 'Lync Server 2013: Fallback do Servidor de Chat Persistente'
TOCTitle: Fallback do Servidor de Chat Persistente
ms:assetid: 67b91de4-6ddc-43e6-9812-5e1aa84a7980
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204970(v=OCS.15)
ms:contentKeyID: 49306964
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Fallback do Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Este procedimento descreve as etapas necessárias para recuperar-se de uma falha do Servidor de Chat Persistente e restabelecer as operações no data center primário.

Durante a falha do Servidor de Chat Persistente, o data center primário sofre uma paralisação completa e os bancos de dados primário e espelho ficam indisponíveis. O data center primário faz failover para o servidor de backup.

O procedimento a seguir restaura a operação normal após o backup do data center primário e a recomposição dos servidores. O procedimento pressupõe que o data center primário tenha sido recuperado da paralisação total e que o banco de dados mgc e o banco de dados mgccomp tenham sido recompostos e reinstalados com o uso do Construtor de Topologias.

O procedimento também pressupõe que nenhum servidor espelho ou de backup novo tenha sido implantado durante o período de failover e que o único servidor implantado seja o de backup e seu servidor espelho, conforme definido em [Failover do Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-failing-over-persistent-chat-server.md).

Estas etapas foram criadas para recuperar a configuração como ela se encontrava antes do desastre que resultou no failover do servidor primário para o servidor de backup.

## Para fazer failback do Servidor de Chat Persistente

1.  Limpe todos os servidores da lista de servidores ativos do Servidor de Chat Persistente usando o cmdlet `Set-CsPersistentChatActiveServer` do Shell de Gerenciamento do Lync Server. Isso impedirá que todos os Servidores de Chat Persistente se conectem ao banco de dados mgc e ao banco de dados mgccomp durante o failback.
    
    > [!IMPORTANT]  
    > O agente do SQL Server no Servidor Back-End do Servidor de Chat Persistente secundário deve estar em execução em uma conta privilegiada. Em termos específicos, a conta deve incluir:    <ul>    
> 
> <li><p>Acesso de leitura ao compartilhamento de rede no qual os backups serão colocados.</p></li>    
> 
> 
> <li><p>Acesso de gravação ao diretório local específico em que os backups serão copiados.</p></li>    </ul>


2.  Desabilite o espelhamento no banco de dados mgc de backup:
    
    1.  Usando o SQL Server Management Studio, conecte-se à instância mgc de backup.
    
    2.  Clique com o botão direito do mouse no banco de dados mgc, aponte para **Tarefas** e clique em **Espelhar** .
    
    3.  Click **Remover Espelhamento** .
    
    4.  Clique em **OK** .
    
    5.  Execute as mesmas etapas com o banco de dados mgccomp.

3.  Faça backup do banco de dados mgc para que ele possa ser restaurado para o novo banco de dados primário:
    
    1.  Usando o SQL Server Management Studio, conecte-se à instância mgc de backup.
    
    2.  Clique com o botão direito do mouse no banco de dados mgc, aponte para **Tarefas** e clique em **Fazer Backup** . A caixa de diálogo **Backup de Banco de Dados** será exibida.
    
    3.  Em **Tipo de backup** , selecione **Completo** .
    
    4.  Para **Componente de backup** , clique em **Banco de dados** .
    
    5.  Aceite o nome de conjunto de backup padrão sugerido em **Nome** ou insira outro nome para o conjunto de backup.
    
    6.  *\<Opcional\>* Em **Descrição** , insira uma descrição para o conjunto de backup.
    
    7.  Remova o local de backup padrão da lista de destinos.
    
    8.  Adicione um arquivo à lista usando o caminho para o local de compartilhamento estabelecido para o envio de logs. Esse caminho está disponível para o banco de dados primário e para o banco de dados de backup.
    
    9.  Clique em **OK** para fechar a caixa de diálogo e iniciar o processo de backup.

4.  Restaure o banco de dados primário usando o banco de dados de backup criado na etapa anterior.
    
    1.  Usando o SQL Server Management Studio, conecte-se à instância mgc primária.
    
    2.  Clique com o botão direito do mouse no banco de dados mgc, aponte para **Tarefas** , aponte para **Restaurar** e clique em **Banco de Dados** . A caixa de diálogo **Restaurar Banco de Dados** será exibida.
    
    3.  Selecione **Do dispositivo** .
    
    4.  Clique no botão "procurar", que abrirá a caixa de diálogo **Especificar Backup** . Em **Mídia de backup** , selecione **Arquivo** . Clique em **Adicionar** , selecione o arquivo de backup criado na etapa 3 e clique em **OK** .
    
    5.  Em **Selecione os conjuntos de backup a serem restaurados** , selecione o backup.
    
    6.  Clique em **Opções** no painel **Selecionar uma página** .
    
    7.  Em **Opções de restauração** , selecione **Substituir o banco de dados existente** .
    
    8.  Em **Estado de recuperação** , selecione **Deixar o banco de dados pronto para uso** .
    
    9.  Clique em **OK** para iniciar o processo de restauração.

5.  Configure o envio de logs do SQL Server para o banco de dados primário. Siga os procedimentos em [Configurando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server-for-high-availability-and-disaster-recovery.md) para estabelecer o envio de logs para o banco de dados mgc primário.

6.  Defina os servidores ativos do Servidor de Chat Persistente. No Shell de Gerenciamento do Lync Server, use o cmdlet **Set-CsPersistentChatActiveServer** para definir a lista de servidores ativos.
    
    > [!IMPORTANT]  
    > Todos os servidores ativos devem estar localizados no mesmo data center que o novo banco de dados primário ou em um data center que tenha uma conexão de baixa latência/alta largura de banda com o banco de dados.

Em seguira, restaure o pool ao seu estado normal executando o seguinte comando Windows PowerShell:

    Set-CsPersistentChatState -Identity "service: lyncpc.dci.discovery.com" -PoolState Normal

Consulte o tópico de ajuda sobre o cmdlet [Set-CsPersistentChatState](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsPersistentChatState) para obter mais informações.

