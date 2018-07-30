---
title: 'Lync Server 2013: Esquema do banco de dados de Chat Persistente'
TOCTitle: Esquema do banco de dados de Chat Persistente
ms:assetid: 58d7d94f-42f5-4c3e-8fe5-901fbe92152e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558653(v=OCS.15)
ms:contentKeyID: 49306787
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Esquema do banco de dados de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-18_

Documenta o esquema do banco de dados do Chat Persistente no Lync Server 2013  software de comunicação.

O banco de dados do Chat Persistente refere-se ao banco de dados correspondente às funções do Servidor Back-end do Lync Server 2013**PersistentChatStore** (correspondente ao banco de dados mgc) e **PersistentChatComplianceStore** (correspondente ao banco de dados mgccomp). O objetivo da publicação desse esquema é permitir que você crie consultas e obtenha algumas ideias sobre a criação de relatórios úteis sobre uso de chat, salas ativas, pôsteres principais e etc.

> [!IMPORTANT]  
> Reservamo-nos o direito de desenvolver este esquema. A Microsoft não garante manter compatibilidade com versões anteriores completa para esse esquema publicado.

Sigas estas práticas recomendadas:

  - Nenhum SELECT\* // é suportado, pois a lista de colunas pode aumentar.

  - Nenhuma modificação de esquema gerado pelo usuário é suportada.

  - Nenhuma operações de gravação é suportada.

  - Teste quaisquer consultas que você crie em bancos de dados de tamanho representativo para certificar-se de que as consultas podem ser executadas em um nível que atenda às suas necessidades.

## Nesta seção

  - [Tabelas de lista de Servidores de Chat Persistente no Lync Server 2013](lync-server-2013-list-of-persistent-chat-server-tables.md)

  - [Lista de tabelas de conformidade do Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-list-of-persistent-chat-server-compliance-tables.md)

  - [Detalhes da tabela do Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-persistent-chat-server-table-details.md)

  - [Amostragem de consultas de banco de dados de Chat Persistente para Lync Server 2013](lync-server-2013-sample-persistent-chat-database-queries.md)

