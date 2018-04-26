---
title: 'Lync Server 2013: Alta disponibilidade de compartilhamento de arquivo'
TOCTitle: Alta disponibilidade de compartilhamento de arquivo
ms:assetid: b8c8d5ec-9397-4128-8d1e-8ec6c30fade7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205203(v=OCS.15)
ms:contentKeyID: 49307911
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alta disponibilidade de compartilhamento de arquivo no Lync Server 2013

 

_**Tópico modificado em:** 2012-03-30_

Para garantir a alta disponibilidade de compartilhamento de arquivos do Lync Server em um único data Center, você pode usar o Sistema de arquivos distribuídos (DAS). O DAS oferece suporte a failover de um servidor de arquivos para outro no mesmo data Center. Para uma implantação em grande escala, nós recomendamos que você use servidores de arquivos dedicados emparelhados usando DAS.

Dependendo do tamanho da rede e da quantidade de resiliência desejada, você pode usar um par de servidores para hospedar todos os compartilhamentos de arquivos em um site ou usar um par por pool de front-end.

O DAS é o melhor mecanismo de replicação de arquivos, sem objetivo de tempo recuperado (RTO) publicado ou compromisso de objetivo de ponto de recuperação (RPO). O failover entre os servidores de DAS deve ser concluído rapidamente, mas o atraso na replicação de dados pode impedir que os usuários continuem trabalhos em andamento quando o failover ocorre.

Se você usa o DAS e o armazenamento de dados no compartilhamento de arquivos for importante, você deve efetuar o backup de compartilhamentos de arquivos frequentemente, como a cada 4 a 8 horas. Quando um compartilhamento de arquivos cai e a replicação não está atualizada, é possível usar o backup para recuperar o conteúdo no servidor com falha para o outro servidor emparelhado com o que está indisponível.

