---
title: Configurando o Servidor de Gerenciamento Primário
TOCTitle: Configurando o Servidor de Gerenciamento Primário
ms:assetid: 44e2e9a8-c130-4c66-9871-80b1ff11b27c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204844(v=OCS.15)
ms:contentKeyID: 49306573
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o Servidor de Gerenciamento Primário

 

_**Tópico modificado em:** 2016-12-08_

Para obter total vantagem das novas capacidades de monitoramento de integridade incluídas no Microsoft Lync Server 2013, os administradores devem primeiro designar um computador para agir como o servidor de gerenciamento primário. Em tal computador, você deve, então, instalar System Center Operations Manager 2007 R2 ou System Center Operations Manager 2012. Além disso, você deve instalar uma versão suportada do SQL Server para funcionar como seu banco de dados de back-end Operations Manager. Se você estiver utilizando o System Center Operations Manager 2012, você pode usar uma das seguintes versões do SQL Server como banco de dados de back-end:

  - SQL Server 2008 R2 Service Pack 1

  - SQL Server 2008 R2 Service Pack 2

Se você estiver usando o System Center Operations Manager 2007 R2, é recomendado que você instale o SQL Server 2005 Service Pack 4 ou SQL Server 2008 Service Pack 3. Você também pode utilizar o SQL Server 2008 R2 como banco de dados de backend para System Center Operations Manager 2007 R2. Consulte o Apêndice 1 desta documentação para mais informações sobre a configuração do SQL Server 2008 R2 para funcionar com System Center Operations Manager 2007 R2.

Ao instalar o System Center Operations Manager 2012 ou System Center Operations Manager 2007 R2, você precisa instalar todos os componentes de tal produto, incluindo:

  - Banco de dados operacional

  - Servidor

  - Console

  - Cmdlets Windows PowerShell

  - Console da Web

  - Relatório

  - Data warehouse

Esses componentes e respectivas instalações não serão debatidas em detalhes neste documento. Para detalhes sobre System Center Operations Manager 2007 R2, consulte a documentação do Operations Manager 2007 R2 em [http://go.microsoft.com/fwlink/?linkid=257526\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=257526%26clcid=0x416) e a documentação do System Center Operations Manager 2012 em [http://go.microsoft.com/fwlink/?linkid=257527\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=257527%26clcid=0x416). Você deve seguir tais instruções se for utilizar o SQL Server 2005 ou SQL Server 2008 Service Pack 1 como banco de dados de back-end.

Se estiver utilizando o System Center Operations Manager 2012, então você pode usar o SQL Server 2012 como banco de dados de back-end. Para detalhes sobre SQL Server 2012, consulte os Manuais Online para SQL Server 2012 em [http://go.microsoft.com/fwlink/?linkid=257528\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=257528%26clcid=0x416).

Tenha em mente que você pode possuir apenas um Servidor de Gerenciamento Primário por implantação Lync Server. Além disso, enquanto você utiliza o System Center Operations Manager 2012 ou System Center Operations Manager 2007 R2, você não pode executar dois aplicativos simultaneamente — você deve escolher um deles. Por exemplo,s e você está executando o System Center Operations Manager 2012, então todos os agentes do System Center devem também executar o System Center Operations Manager 2012. Você não pode possuir alguns agentes executando o System Center Operations Manager 2012 e outros executando o System Center Operations Manager 2007 R2.

