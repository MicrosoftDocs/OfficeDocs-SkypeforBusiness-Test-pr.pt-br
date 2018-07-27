---
title: 'Lync Server 2013: Posicionamento do servidor em uma implantação do servidor Standard Edition'
TOCTitle: Posicionamento do servidor em uma implantação do servidor Standard Edition
ms:assetid: 0763ffab-4fd6-463a-8e62-d97876b376d3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398131(v=OCS.15)
ms:contentKeyID: 49305786
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Posicionamento do servidor em uma implantação do servidor Standard Edition para o Lync Server 2013

 

_**Tópico modificado em:** 2013-01-20_

Esta seção descreve as funções do servidor, os bancos de dados e os compartilhamentos de arquivos que podem ser colocados em uma implantação do servidor Standard Edition do Lync Server 2013.

## Funções do Servidor

No Lync Server 2013, o serviço de Conferência A/V, o serviço de Mediação, Monitoramento e Arquivamento são colocados no Servidor Standard Edition, mas é necessário executar configurações adicionais para habilitá-los. Você pode optar por implantar o serviço de Mediação em servidores separados.

É possível colocar um servidor de aplicativo confiável com o Servidor Standard Edition.

As funções do servidor mostradas a seguir devem ser implantadas cada uma em um computador separado:

  - Diretor

  - Servidor de Borda

  - Servidor de Mediação (se não for colocado com o servidor Standard Edition)

  - Servidor Office Web Apps

## Banco de dados

Por padrão, o banco de dados back-end do SQL Server Express é colocado no servidor Standard Edition. Você não pode movê-lo para um computador separado. Com uma exceção, não é possível colocar outros bancos de dados no servidor Standard Edition. Se você optar por implantar Servidor de Chat Persistente em um servidor Standard Edition, você pode colocar o banco de dados do Chat Persistente e o banco de dados da Conformidade com Chat Persistente no mesmo servidor Standard Edition.

Você pode colocar cada um dos bancos de dados a seguir em um único servidor de banco de dados:

  - Banco de dados de monitoramento

  - Banco de dados de arquivamento

  - Um banco de dados de back-end de um pool de Front-Ends Enterprise Edition

É possível colocar qualquer um ou todos esses bancos de dados em uma única instância SQL ou usar instâncias separadas para cada um, com as seguintes limitações:

  - Cada instância SQL pode conter apenas um banco de dados de back-end (para um pool de Front-Ends Enterprise Edition), um único banco de dados de Monitoramento, um único banco de dados de Arquivamento, um único banco de dados de chat persistente e um único banco de dados de conformidade de chat persistente.

  - O servidor de banco de dados não pode dar suporte para mais do que um pool de Front-Ends Enterprise Edition, um servidor executando o Arquivamento, um servidor executando o Monitoramento, um único banco de dados do Chat Persistente e um único banco de dados de conformidade do Chat Persistente, mas pode dar suporte para um de cada, independentemente de os bancos de dados usarem a mesma instância do SQL Server ou instâncias separadas do SQL Server.

   É possível colocar um compartilhamento de arquivo com um banco de dados, conforme será descrito ainda nesta seção.

> [!NOTE]  
> No Lync Server 2013, você tem a opção de integrar o armazenamento de Monitoramento e de Arquivamento com o armazenamento do Exchange 2013 para alguns ou todos os usuários em sua implantação. Não é possível implantar servidores que estão executando o Lync Server ou componentes nos mesmos servidores que o armazenamento do Exchange.

> [!IMPORTANT]  
> Embora a colocação de bancos de dados seja suportada, o tamanho dos bancos de dados pode aumentar muito rápido. Por exemplo, quando você considera colocar o banco de dados de Arquivamento com outros bancos de dados, se estiver arquivando as mensagens de mais de alguns usuários, o espaço em disco exigido pelo banco de dados de Arquivamento poderá aumentar bastante. Por esse motivo, não recomendamos colocar vários bancos de dados, especialmente o banco de dados de Arquivamento, o banco de dados do Chat Persistente e o banco de dados de conformidade do Chat Persistente com o banco de dados back-end de um pool de Enterprise.

## Compartilhamentos de arquivo

O compartilhamento de arquivo pode ser um servidor separado ou pode ser colocado no mesmo servidor como qualquer um ou todos a seguir:

  - Servidor de banco de dados, incluindo o Servidor Back-End de um pool de Front-Ends Enterprise Edition

  - Banco de dados de arquivamento

  - Banco de dados de monitoramento

  - Banco de dados do Chat Persistente

  - Banco de dados de conformidade do Chat Persistente

Um compartilhamento de arquivo único pode ser usado para múltiplos pools de Front-Ends, servidores Standard Edition (todos no mesmo site).

> [!NOTE]  
> No Lync Server 2013, o Monitoramento e o Arquivamento usam o compartilhamento de arquivo do Lync Server como o Servidor Standard Edition.

## Outros componentes

Não é possível colocar um servidor proxy reverso, que não é um componente Lync Server 2013, mas é necessário em sua implantação se você quiser dar suporte ao compartilhamento do conteúdo Web para usuários federados com qualquer função de servidor do Lync Server 2013. É possível, contudo, implementar o suporte ao proxy reverso para uma implantação do Lync Server 2013 configurando o suporte em um servidor proxy reverso existente em sua organização, que é usado para outros aplicativos.

Não é possível colocar nenhum componente do UM do Exchange ou componente do SharePoint com qualquer função do Lync Server 2013.

