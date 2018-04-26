---
title: 'Lync Server 2013: Requisitos de sistema para Servidor SQL'
TOCTitle: Requisitos de sistema para Servidor SQL
ms:assetid: 9c235085-cbfa-4e9e-9cec-3f5749039a6b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205112(v=OCS.15)
ms:contentKeyID: 49307590
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de sistema para Servidor SQL no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-25_

Antes de implantar o servidor Enterprise Edition, instale o Microsoft SQL Server 2008 R2 ou Microsoft SQL Server 2012 em um computador dedicado que atenda aos requisitos de hardware. Para obter detalhes sobre os requisitos de hardware, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de Suporte. Para obter detalhes sobre os requisitos de software, consulte [Suporte a software de banco de dados no Lync Server 2013](lync-server-2013-database-software-support.md) na documentação de Suporte. Para obter informações sobre as permissões necessárias para a implantação, consulte [Permissões de implantação para Servidor SQL no Lync Server 2013](lync-server-2013-deployment-permissions-for-sql-server.md).

Antes de criar o pool de front end, é necessário também configurar o Windows Firewall para permitir acesso do Lync Server 2013 ao SQL Server através de portas específicas, definindo portas para o servidor usando o SQL Server Configuration Manager e abrindo portas no Windows Firewall com Segurança Avançada.

