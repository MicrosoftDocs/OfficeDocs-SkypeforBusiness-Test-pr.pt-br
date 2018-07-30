---
title: 'Lync Server 2013: Posicionamento do servidor em uma implantação do pool de front-ends do Enterprise Edition'
TOCTitle: Posicionamento do servidor em uma implantação do pool de front-ends do Enterprise Edition
ms:assetid: 0516b18d-14c0-4237-9279-0f92e341b1bd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398102(v=OCS.15)
ms:contentKeyID: 49305727
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Posicionamento do servidor em uma implantação do pool de front-ends do Enterprise Edition para o Lync Server 2013

 

_**Tópico modificado em:** 2013-11-11_

Esta seção descreve as funções do servidor, os bancos de dados e compartilhamentos de arquivo que você colocar em uma implantação de pool de Front-Ends do Lync Server 2013.

## Funções do Servidor

No Lync Server 2013, o serviço de Conferência A/V, o serviço de Mediação, Monitoramento e Arquivamento são colocados no Servidor Front-End, mas é necessário executar configurações adicionais para habilitá-los. Se você não os posicionar no Servidor de Mediação com o Servidor Front-End, poderá implantá-lo como um Servidor de Mediação autônomo em um computador separado.

É possível colocar um servidor de aplicativo confiável com o Servidor Front-End.

As funções do servidor mostradas a seguir devem ser implantadas cada uma em um computador separado:

  - Diretor

  - Servidor de Borda

  - Servidor de Mediação (se não colocado junto ao Servidor Front-End)

  - Servidor Office Web Apps

Não é possível colocar a função de servidor de Chat Persistente com o servidor front-end.

## Banco de dados

Você pode colocar cada um dos bancos de dados a seguir no mesmo servidor de banco de dados:

  - Banco de dados de back-end

  - Banco de dados de monitoramento

  - Banco de dados de arquivamento

  - Banco de dados do Chat Persistente

  - Banco de dados de conformidade do Chat Persistente

É possível colocar qualquer um ou todos esses bancos de dados em uma única instância SQL Server ou usar instâncias SQL Server separadas para cada um, com as seguintes limitações:

  - Cada instância SQL Server pode conter um único banco de dados de back-end, de Monitoramento ou de Arquivamento, um único banco de dados Chat Persistente e um único banco de dados de conformidade Chat Persistente.

  - O servidor de banco de dados não pode dar suporte para mais de um pool de Front-Ends, um Servidor de Arquivamento e um Monitoring Server, mas pode dar suporte para um de cada, independentemente de os bancos de dados usarem a mesma instância SQL Server ou instâncias SQL Server separadas.

   É possível colocar um compartilhamento de arquivo com um banco de dados, conforme será descrito ainda nesta seção.

> [!NOTE]  
> No Lync Server 2013, você tem a opção de integrar o armazenamento de Arquivamento com o armazenamento do Exchange 2013 para alguns ou todos os usuários em sua implantação. Não é possível implantar servidores que estão executando Lync Server ou componentes nos mesmos servidores que o armazenamento de Exchange.

> [!IMPORTANT]  
> Embora a colocação de bancos de dados seja suportada, o tamanho dos bancos de dados pode aumentar muito rápido. Por exemplo, quando você considera colocar o banco de dados de Arquivamento com outros bancos de dados, se estiver arquivando as mensagens de mais de alguns usuários, o espaço em disco exigido pelo banco de dados de Arquivamento poderá aumentar bastante. Por esse motivo, não recomendamos colocar vários bancos de dados, especialmente o banco de dados de Arquivamento, o banco de dados do Chat Persistente ou o banco de dados de conformidade do Chat Persistente com o banco de dados back-end.

## Compartilhamento de arquivo

O compartilhamento de arquivo pode ser um servidor separado ou pode ser colocado no mesmo servidor como qualquer um ou todos a seguir:

  - Servidor de banco de dados, incluindo o Servidor Back-End de um pool de Front-Ends Enterprise Edition

  - Banco de dados de arquivamento

  - Banco de dados de monitoramento

  - Banco de dados do Chat Persistente

  - Banco de dados de conformidade do Chat Persistente

Um compartilhamento de arquivo único pode ser usado para múltiplos pools de Front-Ends, servidores Standard Edition (todos no mesmo site).

> [!NOTE]  
> No Lync Server 2013, o Monitoramento e o Arquivamento usam o compartilhamento de arquivo do Lync Server como o Servidor Front-End.

## Outros componentes

Não é possível colocar um servidor proxy reverso, que não é um componente Lync Server 2013, mas é necessário em sua implantação se você quiser dar suporte ao compartilhamento do conteúdo Web para usuários federados com qualquer função de servidor do Lync Server 2013. É possível, contudo, implementar o suporte ao proxy reverso para uma implantação do Lync Server 2013 configurando o suporte em um servidor proxy reverso existente em sua organização, que é usado para outros aplicativos.

Não é possível colocar nenhum componente do Unificação de Mensagens (UM) do Exchange ou componente do SharePoint com qualquer função do SharePoint Server.

