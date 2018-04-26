---
title: 'Lync Server 2013: Recursos obrigatórios para Servidor de Chat Persistente'
TOCTitle: Recursos obrigatórios
ms:assetid: bce50b95-f3c8-407e-963a-d8896ee77fbc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205211(v=OCS.15)
ms:contentKeyID: 49307936
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recursos obrigatórios para Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2016-02-05_

A alta disponibilidade e a recuperação de desastres do Servidor de Chat Persistente requer recursos adicionais além dos normalmente necessários para a operação completa. Antes de configurar o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastres, verifique se você tem os seguintes recursos além do que é necessário para a operação padrão do Servidor de Chat Persistente. Para obter informações de configuração adicionais, consulte [Configurando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md).

  - Uma instância de banco de dados dedicada localizada no data Center físico no qual o front-end residencial do serviço do Servidor de Chat Persistente está localizado. Esse banco de dados servirá como espelho do SQL Server para o banco de dados principal do Chat Persistente. Como opção, atribua um SQL Server adicional para servir como testemunha de espelhamento se você deseja um failover automatizado para o banco de dados espelho.

  - Uma instância de banco de dados dedicada localizada no outro data Center físico. Este banco de dados servirá como o banco de dados secundário de Envio de logs do SQL Server para o banco de dados no data Center principal.

  - Uma instância dedicada do banco de dados para servir como o espelho do SQL Server para o banco de dados secundário. Como opção, atribua um SQL Server adicional ao servidor como testemunha de espelhamento. Ambos devem estar localizado no mesmo data Center físico que o banco de dados secundário.

  - Se o conformidade do Servidor de Chat Persistente estiver ativada, são necessários três bancos de dados dedicados adicionais. Sua distribuição é igual a descrita anteriormente para o banco de dados do Chat Persistente. Embora seja possível que o banco de dados de conformidade compartilhe a mesma instância do SQL Server que o banco de dados do Chat Persistente, nós recomendamos instância independentes para alta disponibilidade e recuperação de desastres.

  - É necessário criar e designar um compartilhamento de arquivos para os logs de transação de Envio de logs do SQL Server. Todos os Servidores SQL em ambos os centros que executam o banco de dados do Chat Persistente devem ter acesso para gravação/leitura nesse compartilhamento de arquivos. Este compartilhamento não está definido como parte de uma função FileStore.

  - Um compartilhamento de arquivos no servidor do bancos de dados secundário para servir como a pasta de destino dos logs de transação do SQL Server copiados do compartilhamento de arquivos do servidor principal.

As seguintes imagens fornecem exemplos sobre como o Pool de Servidor de Chat Persistente inteiro pode ser configurado em duas topologias de pool ampliadas diferentes:

  - Pool de Servidor de Chat Persistente ampliado quando os data centers estão geo-localizados com alta largura de banda/baixa latência.

  - Pool de Servidor de Chat Persistente alongado quando os data centers estão geo-localizados com baixa largura de banda/alta latência.

A seguinte imagem mostra uma topologia ampliada do Pool de Servidor de Chat Persistente, no qual os data centers estão geo-localizados com alta largura de banda/baixa latência.

**Pool de servidor de chat persistente ampliado quando os data centers estão geo-localizados com alta largura de banda/baixa latência.**

![Exame de configuração HBW do pool de servidores do chat persistente](images/JJ205211.55d10910-c824-41e6-bed2-08d13a2abd65(OCS.15).jpg "Exame de configuração HBW do pool de servidores do chat persistente")

A seguinte imagem mostra uma topologia ampliada do Pool de Servidor de Chat Persistente, no qual os data centers estão geo-localizados com baixa largura de banda/alta latência.

**Pool de servidor de chat persistente ampliado quando os data centers estão geo-localizados com baixa largura de banda/alta latência.**

![Exame de configuração LBW do pool de servidores do chat persistente](images/JJ205211.586b0a3a-3767-4991-944f-ee54389512aa(OCS.15).jpg "Exame de configuração LBW do pool de servidores do chat persistente")

