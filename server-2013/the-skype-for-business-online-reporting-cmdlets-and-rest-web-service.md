---
title: 'Lync Online: Relatório de cmdlets e serviço Web REST do Lync Online'
TOCTitle: Relatório de cmdlets e serviço Web REST do Lync Online
ms:assetid: cadd73a7-c08a-4102-b73a-ccb3ad4987bf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362845(v=OCS.15)
ms:contentKeyID: 56270471
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatório de cmdlets e serviço Web REST do Lync Online

 

_**Tópico modificado em:** 2016-12-08_

Juntamente com o relatório de recursos, o Skype for Business Online fornece acesso a cinco cmdlets Windows PowerShell que ajudam a gerar esses relatórios e também podem ser usados por administradores para retornar relatórios de dados personalizados. O Skype for Business Online também inclui o REST (Representational State Transfer), que pode ser usado por desenvolvedores para recuperar informações de relatório personalizado.

Os relatórios cmdlets disponíveis para administradores incluem:

  - Get-CsActiveUserReport, fornece informações sobre o número de usuários ativos (ou seja, usuários logados em Skype for Business Online e participando de, ao menos, uma conferência ou sessão de comunicação ponto a ponto).

  - Get-CsAVConferenceTimeReport, fornece informações sobre a quantidade de tempo (em minutos) que os usuários despendem em conferências de áudio/vídeo.

  - Get-CsConferenceReport, fornece informações sobre o número e o tipo de conferência das quais os usuários participam.

  - Get-CsP2PAVTimeReport, fornece informações sobre a quantidade de tempo (em minutos) despendida pelos usuários em sessões ponto a ponto que incluem áudio e/ou vídeo.

  - Get-CsP2PSessionReport, fornece informações sobre o número e o tipo de sessão ponto a ponto das quais os usuários participam.

A maioria dos administradores usará os relatórios disponíveis na Central de Admin do Office 365: esses relatórios não só são gerados automaticamente como também fornecem uma representação gráfica de dados que são mais facilmente interpretados que o simples número de valores retornados pelo relatório do cmdlet. Contudo, administradores familiarizados com o Windows PowerShell podem usar os cmdlets dos relatórios para retornar dados não prontamente disponíveis dos relatórios do Lync Online. Por exemplo, os cmdlets dos relatórios retornam informações sobre a duração da sessão (período de tempo, em minutos, de duração de cada sessão). O período de duração da sessão não está disponível nos relatórios do Lync Online. Igualmente, a visualização diária dos relatórios do Lync Online exibe informações somente de 14 dias precedentes. Se desejar visualizar o total diário de um dia diferente (por exemplo, uma data de quatro semanas atrás) é possível usar os cmdlets do relatório.

Os administradores também podem estar interessados no artigo [Using Excel to Retrieve Office 365 Reporting Data](http://msdn.microsoft.com/en-us/library/dn781442.aspx), que explica como usar o recurso de consulta dos dados do OData no Microsoft Excel para criar o relatório do office 365 personalizado. Relatórios personalizados te dão a capacidade de escolher quais dados (e quantos dados) serão retornados do serviço de relatório do Office 365. Os relatórios personalizados também permitem que você além de fazer todas as coisas especifique como os dados deverão ser classificados e agrupados, também fornecem acesso a informações que não são exibidas na central de Administração do Office 365.

Administradores com background de desenvolvedor podem usar o serviço da web REST para obter informações não exibidas no centro administrador Skype for Business Online. O serviço da web REST é similar ao SOAP, em que cada tecnologia fornece um meio de transferência de dados XML entre um cliente e um servidor. No entanto, o serviço REST tem ao menos duas vantagens sobre o SOAP. Primeiro, o REST desempenha a transferência de dados XML usando um formato padrão conhecido como formato de distribuição ATOM. Por contraste, o SOAP não utiliza um formato de transferência de dados padrão. Segundo, o REST é capaz de transferir dados através de redes que bloqueiam verbos HTTP além de GET e POST.

## Consulte Também

#### Outros Recursos

[Relatórios do Lync Online](https://technet.microsoft.com/pt-br/library/dn362827\(v=ocs.15\))  
[Serviço de Relatório na Web do Office 365](http://msdn.microsoft.com/en-us/library/office/jj984325.aspx)  
[Conhecendo o Serviço de Relatório na Web do 365](http://msdn.microsoft.com/en-us/library/office/jj984321.aspx)  
[Relatório On-line de Cmdlets do Exchange](http://technet.microsoft.com/en-us/library/jj200780\(v=exchg.150\).aspx)  
[Usando o Excel para Recuperar Dados de Relatório do Office 365](http://msdn.microsoft.com/en-us/library/dn781442.aspx)

