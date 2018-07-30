---
title: 'Lync Server 2013: Failover do Servidor de Chat Persistente'
TOCTitle: Failover do Servidor de Chat Persistente
ms:assetid: 2cd79ffd-fee6-44ce-96cf-b98bf25e2690
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204772(v=OCS.15)
ms:contentKeyID: 49306243
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Failover do Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Failover para Servidor de Chat Persistente é projetado para ser principalmente um processo manual.

O procedimento de failover é baseado na previsão de que o centro de dados secundário esteja funcionando, mas os serviços do Servidor de Chat Persistente onde o banco de dados do Chat Persistente primário está localizado estão completamente indisponíveis, incluindo o seguinte:

  - O banco de dados do Servidor de Chat Persistente primário e o banco de dados de espelho do Servidor de Chat Persistente estão desativados.

  - O Lync ServerServidor Front-End está desativado.

O procedimento é baseado em duas etapas básicas:

  - Recuperar o banco de dados do Chat Persistente primário (mgc).

  - Estabelecer o espelhamento para o novo banco de dados primário.

O banco de dados de conformidade do Chat Persistente (mgccomp) não é failed over. O conteúdo deste banco de dados é temporário e é excluído como os processos do adaptador de conformidade dos dados. É sua responsabilidade, como Administrador do Chat Persistente, gerenciar corretamente a saída do adaptador para evitar perda de dados.

## Para realizar um failover do Servidor de Chat Persistente

1.  Remova o envio de log do banco de dados de Envio de Log de Backup do Servidor de Chat Persistente.
    
    1.  Usando o Studio de Gerenciamento do SQL Server, conecte-se à instância do banco de dados onde o banco de dados de gerenciamento de backup do Servidor de Chat Persistente está localizado.
    
    2.  Abra uma janela de consulta para o banco de dados principal.
    
    3.  Use o seguinte comando para derrubar o envio de log:
        
            exec sp_delete_log_shipping_secondary_database mgc

2.  Copie qualquer arquivo de backup não copiado do compartilhamento de backup para a pasta de destino da cópia do servidor de backup.

3.  Aplique qualquer backup do log de transação não aplicado na sequência para o banco de dados secundário. Para obter detalhes, consulte "Tutorial: Aplicar um backup do log de transação Apply (Transact-SQL)" em http://go.microsoft.com/fwlink/?linkid=247428\&clcid=0x416

4.  Coloque o banco de dados de gerenciamento de backup online. Usando a janela de consulta que abra na etapa 1b, faça o seguinte:
    
    1.  Finalize todas as conexões com o banco de dados de gerenciamento, se houver:
        
        1.  **exec sp\_who2** para identificar as conexões com o banco de dados mgc.
        
        2.  **kill \<spid\>** para terminar essas conexões.
    
    2.  Coloque o banco de dados online:
        
        1.  **restaurar banco de dados mgc com recuperação** .

5.  No Shell de Gerenciamento do Lync Server, use o comando **Set-CsPersistentChatState -Identity "service:atl-cs-001.litwareinc.com" –PoolState FailedOver** para executar failover para o banco de dados de backup mgc. Não se esqueça de substituir o nome de domínio totalmente qualificado do seu pool de Chat Persistente por atl-cs-001.litwareinc.com.
    
    O banco de dados de backup de gerenciamento agora serve como o banco de dados primário.

6.  No Shell de Gerenciamento do Lync Server, use o cmdlet **Install-CsMirrorDatabase** para estabelecer um espelho de alta disponibilidade para o banco de dados de backup que agora serve como o banco de dados primário. Use a instância do banco de dados de backup como o banco de dados primário e a instância do banco de dados de espelho de backup como a instância do espelho. Este não é o mesmo espelho do que aquele inicialmente configurado para o banco de dados primário durante a configuração. Para obter detalhes, consulte a seção "Usando cmdlets do Shell de Gerenciamento do Lync Server" no [Implantando espelhamento SQL para alta disponibilidade de Servidor Back-End no Lync Server 2013](lync-server-2013-deploying-sql-mirroring-for-back-end-server-high-availability.md).

7.  Defina os servidores ativos do Servidor de Chat Persistente. No Shell de Comando do Lync Server, use o cmdlet **Set-CsPersistentChatActiveServer** para definir a lista dos servidores ativos.
    
    > [!IMPORTANT]  
    > Todos os servidores ativos devem estar localizados no mesmo data center que o novo banco de dados primário ou em um data center que tenha uma conexão de baixa latência/alta largura de banda com o banco de dados.    
    Neste ponto, o failover do banco de dados do Servidor de Chat Persistente para o banco de dados de backup do Servidor de Chat Persistente é concluído com sucesso.

