---
title: 'Lync Server 2013: Configurar o SQL Server para Lync Server 2013'
TOCTitle: Configurar o SQL Server para Lync Server 2013
ms:assetid: 375e5cc4-e436-46dc-9b02-5063f35cdcc1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425848(v=OCS.15)
ms:contentKeyID: 49306377
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o SQL Server para Lync Server 2013

 

_**Tópico modificado em:** 2013-08-12_

Os tópicos desta seção analisam como implantar e configurar o SQL Server para uso em uma implantação corporativa do Lync Server. O Servidores Standard Edition usa uma versão colocada do SQL Server Express de SQL Server, que tem o tamanho ideal para cargas de trabalho do Servidor Standard Edition.

O Lync Server 2013  Repositório de Gerenciamento Central armazena dados de usuário de todos os servidores do Enterprise Edition em um pool e foi projetado para se localizar no servidor back-end baseado no SQL Server. Como repositório centralizado, o Repositório de Gerenciamento Central não pode ser instalado no mesmo computador como qualquer outra função do Lync Server 2013. O Repositório de Gerenciamento Central não pode residir em um servidor do Enterprise Edition do pool. O Repositório de Gerenciamento Central é criado automaticamente quando a topologia é publicada pela primeira vez e o banco de dados é criado. O computador designado como servidor back-end já deve estar executando o software de banco de dados do SQL Server para que a instalação seja bem-sucedida.

## Nesta seção

  - [Posicionamento de dados do Servidor SQL e do arquivo de log para Lync Server 2013](lync-server-2013-sql-server-data-and-log-file-placement.md)

  - [Configurar SQL Server no Lync Server 2013](lync-server-2013-configure-sql-server.md)

  - [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md)

  - [Instalação de banco de dados usando o Shell de Gerenciamento do Lync Server no Lync Server 2013](lync-server-2013-database-installation-using-lync-server-management-shell.md)

  - [Compreendendo os requisitos de firewall para Servidor SQL com Lync Server 2013](lync-server-2013-understanding-firewall-requirements-for-sql-server.md)

  - [Configurar Agrupamento do SQL Server para Lync Server 2013](lync-server-2013-configure-sql-server-clustering.md)

