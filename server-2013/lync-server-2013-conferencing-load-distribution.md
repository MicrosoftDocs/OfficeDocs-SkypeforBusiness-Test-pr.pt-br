---
title: Distribuição de carga de conferência
TOCTitle: Distribuição de carga de conferência
ms:assetid: 5901a076-1b6f-4720-8837-95fc7f3c37f3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204922(v=OCS.15)
ms:contentKeyID: 49306799
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Distribuição de carga de conferência

 

_**Tópico modificado em:** 2012-10-22_

Ao contrário de algumas outras soluções de conferência dedicadas, a arquitetura do Lync Server é um modelo de hardware compartilhado. Isto significa que o mesmo hardware é compartilhado por muitos componentes de software, cada um dos quais suporta diferentes comunicações em tempo real. Cada tipo de comunicações em tempo real coloca cargas específicas sobre os servidores. Por exemplo, o Servidor Front-End pode executar os componentes de roteamento do SIP (Protocolo de Iniciação de Sessão) , aplicativos Web (como a pesquisa do Catálogo de Endereços), Serviço de Webconferência, Serviço de Conferência A/V, Enterprise Voice aplicativos (por exemplo, Aplicativo Atendedor de Conferência and Aplicativo Grupo de Resposta) e Servidor de Mediação. Um conjunto de bancos de dados no Servidor Front-End também fornece armazenamento e processamento para o usuário, contato, presença, conferência e dados de roteamento de voz. Com esse compartilhamento de hardware, os componentes, os serviços e os processos competem com os recursos de CPU e memória, dessa forma, as cargas de trabalho que não sejam de conferência não têm um impacto direto sobre a escala do servidor..

Comparada a outras soluções de conferência baseadas na porta de hardware, a arquitetura de conferência do Lync Server é um modelo sem reserva. Quando um usuário agenda uma reunião, o Lync Server cria um registro no banco de dados de conferências, que armazena dados de conferência, mas não reserva quaisquer recursos de hardware para a reunião agendada com antecedência. Em vez disso, o Lync Server incorpora a lógica de balanceamento de carga para alocar dinamicamente os recursos de conferência no Servidores Front-End de uma forma que distribui as cargas igualmente em todo o Servidores Front-End no pool. Isso provisiona e utiliza de forma eficaz os recursos de hardware, mas dificulta o fornecimento de suporte para as reuniões muito grandes (especialmente sem um planejamento adequado). Por exemplo, quando um pool do Lync Server 2013 está sendo executado próximo da sua capacidade máxima, cada Servidor Front-End pode hospedar aproximadamente 125 reuniões de tamanho médio. Adicionar outra reunião pequena não seria um problema, mas a adição de uma reunião para 1000 usuários seria um problema, pois o Servidores Front-End provavelmente não seria capaz de suportar tal reunião grande ao mesmo tempo que as outras 125 reuniões.

