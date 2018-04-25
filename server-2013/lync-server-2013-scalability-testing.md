---
title: Teste de Escalabilidade
TOCTitle: Teste de Escalabilidade
ms:assetid: bf41bac6-d4ec-4de6-9a44-a82d01a87279
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205226(v=OCS.15)
ms:contentKeyID: 49307965
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Teste de Escalabilidade

 

_**Tópico modificado em:** 2012-10-01_

O Lync Server 2013 oferece a infraestrutura do servidor para todas as comunicações em tempo real do Lync Server, incluindo mensagem instantânea (IM) e presença, conferência e Enterprise Voice. Isto inclui qualquer recurso que usa os recursos de hardware de um pool do Lync Server 2013 e, portanto, afeta o desempenho e a escala. Todas as organizações não usam os mesmos recursos.

Por exemplo, algumas organizações podem usar vídeo em conferências muito pesadas enquanto outros podem não ter ou quase não ter uso de vídeo. Algumas organizações preferem compartilhamento de slides do PowerPoint ao compartilhamento de aplicativos, enquanto outros preferem o oposto. Estas organizações que implantam o Enterprise Voice podem ou não usar o Aplicativo Grupo de Resposta pesadamente. A maioria das organizações implanta o Servidores de Monitoramento, mas não muitas delas implantam o Servidores de Arquivamento. Além disso, as organizações não têm a mesma infraestrutura, incluindo capacidade de hardware, capacidade de rede e número de pools e tamanho dos pools implantados. A diversidade dos recursos e infraestrutura é um desafio para o teste de escalabilidade – não é possível simular todas as combinações possíveis de recursos e infraestruturas.

Para determinar o suporte de escalabilidade do Lync Server, conduzimos testes usando todos os recursos do Lync Server simultaneamente, com base no modelo de uso médio (modelo do usuário). Para determinar um modelo de usuário adequado das cargas de trabalho do Lync Server, analisamos vários pontos de dados, incluindo pesquisas do cliente, feedback do programa de melhoria da experiência do cliente da Microsoft, dados de uso do Lync Server do departamento de TI interno da Microsoft e dados retirados do Live Meeting Service. Em vários casos, o modelo do usuário tem uma tendência em relação às cargas pesadas para oferecer uma margem confortável de uso dentro de uma organização.

Em nossos testes de escalabilidade, definimos pools do Lync Server 2013 de acordo com as especificações de hardware e software recomendadas, incluindo componentes de infraestrutura, como Serviços de Domínio Active Directory, balanceadores de carga de hardware e firewalls. Definimos ambientes do Lync Server o mais parecidos possível aos ambientes reais comuns. Usamos a Ferramenta de Tensão e Desempenho do Lync Server 2013 para simular as cargas do Lync Server 2013 (com base no nosso modelo de usuário).

Realizamos várias iterações de testes de escalabilidade (incluindo várias execuções de testes de três semanas). Usamos os resultados de todos os testes para ajudar com a sintonização do desempenho e verificar o suporte para os números de escalabilidade em nosso modelo do usuário.

