---
title: 'Lync Server 2013: Componentes e topologia para monitoramento'
TOCTitle: Componentes e topologia para monitoramento
ms:assetid: c1bb36b0-1fb8-4d8e-9cc9-9bef740fe3c6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412952(v=OCS.15)
ms:contentKeyID: 49886393
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologia para monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-05_

Como os agentes do conjunto de dados unificados são instalados e ativados automaticamente em cada servidor de Front-end, não é necessário configurar um servidor para agir como o servidor de Monitoramento; cada servidor de Front-end já funciona como um servidor de Monitoramento. No entanto, você precisará instalar e configurar um banco de dados para agir como o repositório de dados de backend para seus dados de monitoramento. O Microsoft Lync Server 2013 pode usar qualquer um dos seguintes bancos de dados como o repositório de backend para o monitoramento:

  - Microsoft SQL Server 2008 R2 Enterprise Edition

  - Microsoft SQL Server 2008 R2 Standard Edition

  - Microsoft SQL Server 2012 Enterprise Edition

  - Microsoft SQL Server 2012 Standard Edition

Observe que você deve usar as edições de 64 bits destes bancos de dados; as versões de 32 bits do SQL Server não podem ser usadas como repositório de backend para monitoramento. Da mesma forma, o Lync Server 2013 não suporta o Express Editions do SQL Server 2008 ou SQL Server 2012. Para obter mais informações sobre os requisitos do banco de dados para o Lync Server 2013, consulte o tópico [Suporte a software de banco de dados no Lync Server 2013](lync-server-2013-database-software-support.md) no guia de Suportabilidade do Lync Server 2013.

Tenha em mente que o SQL Server deve ser instalado e configurado antes de implantar e configurar o monitoramento. No entanto, você não precisa implantar o SQL Server sozinho; não precisa configurar os bancos de dados de monitoramento antecipadamente. Ao invés disso, os bancos de dados serão criados automaticamente para você ao publicar sua topologia do Lync Server.

Os dados de monitoramento pode compartilhar uma instância do SQL Server com outros tipos de dados. Geralmente, o banco de dados de registro de detalhes da chamada (LcsCdr) e o banco de dados de Qualidade da Experiência (QoEMetrics) compartilham a mesma instância SQL; também é comum para os dois bancos de dados de monitoramento estarem na mesma instância SQL como o banco de dados de arquivamento (LcsLog). Sobre o único requisito real com instâncias do SQL Server é que uma instância do SQL Server é limitada ao seguinte:

  - Uma instância do banco de dados de backend do Lync Server 2013. (Como regra geral, não é recomendado que seu banco de dados de monitoramento seja posicionado na mesma instância do SQL ou mesmo no mesmo computador, como o banco de dados de backend. Embora tecnicamente possível, você tem o risco de monitorar o banco de dados usando o espaço de disco necessários pelo banco de dados de backend.)

  - Uma instância do banco de dados de registro de detalhes da chamada.

  - Uma instância do banco de dados da Qualidade da Experiência.

  - Uma instância do banco de dados de arquivamento.

Em outras palavras, não é possível ter duas instâncias do banco de dados LcsCdr na mesma instância do SQL Server. Se você precisar de várias instâncias do banco de dados LcsCdr, será necessário configurar várias instâncias do SQL Server.

## Consulte Também

#### Outros Recursos

[Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md)

