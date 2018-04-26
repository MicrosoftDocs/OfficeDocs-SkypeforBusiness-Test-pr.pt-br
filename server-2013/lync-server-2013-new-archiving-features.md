---
title: 'Lync Server 2013: Novos recursos de Arquivamento'
TOCTitle: Novos recursos de Arquivamento
ms:assetid: c002e367-41ad-498d-9d23-8b117ac435b2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205225(v=OCS.15)
ms:contentKeyID: 49307995
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Novos recursos de Arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Arquivamento no Lync Server 2013 pode arquivar os seguintes tipos de conteúdo:

  - Mensagens instantâneas de ponto a ponto

  - As conferências (reuniões) que são mensagens instantâneas de várias partes

  - Conteúdo de conferências, incluindo conteúdo carregado (por exemplo, folhetos) e conteúdo relacionado ao evento (por exemplo, entradas, saídas, compartilhamento de cargas e alterações de visibilidade)

Além disso, o Arquivamento no Lync Server 2013 fornece novos recursos que melhoram a implantação e a eficiência das operações. Esses novos recursos consistem em:

  - **Colocação de arquivamento em servidores front-end.**   O Lync Server 2013 não tem uma função de Servidor de arquivamento separada. O Arquivamento é um recurso opcional disponível em todos os Servidores front-end em uma implantação Enterprise Edition e, nos servidores Standard Edition, que podem ser implementados e configurados para um pool ou site.

  - Integração do **Microsoft Exchange.**   Ao implantar o Arquivamento, você pode integrar o armazenamento de dados para Arquivamento com o armazenamento Exchange 2013 existente para todos os usuários hospedados no Exchange 2013 e para que suas caixas de correio coloquem Bloqueio in-loco, não sendo necessário implantar bancos de dados separados do SQL Server para arquivar dados do Lync. Se você não tem uma implantação do Exchange 2013, ou se preferir não integrar com ela ou ainda se tiver qualquer usuário do Lync 2013 que não está hospedado no Exchange 2013 com caixas de correio com Bloqueio in-loco, é possível implantar bancos de dados de Arquivamento separados usando o SQL Server para armazenar dados arquivados de comunicações do Lync. É possível usar bancos de dados de integração do Microsoft Exchange e de Arquivamento do Lync Server 2013 se você deseja usar a integração do Microsoft Exchange para alguns, mas não todos os usuários em sua implantação. Para obter detalhes sobre o Bloqueio in-loco, consulte “Bloqueio in-loco” em [http://go.microsoft.com/fwlink/p/?LinkId=267500](http://go.microsoft.com/fwlink/p/?linkid=267500).

  - **Espelhamento do repositório SQL.**   Ao implantar o Arquivamento, você pode habilitar o espelhamento de banco de dados do SQL Server em seu banco de dados de Arquivamento.

  - **Arquivamento de quadros de comunicações e polls.**   O conteúdo de conferência arquivado agora inclui quadros de comunicação e pools armazenados durante uma reunião.

Os seguintes tipos de conteúdo não são arquivados:

  - Transferências de arquivo de ponto a ponto

  - Áudio/vídeo para mensagens instantâneas e conferências de ponto a ponto

  - Compartilhamento de aplicativos para mensagens instantâneas ponto a ponto e conferências

## Consulte Também

#### Outros Recursos

[Planejando Arquivamento no Lync Server 2013](lync-server-2013-planning-for-archiving.md)

