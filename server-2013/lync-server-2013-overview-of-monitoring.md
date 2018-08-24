---
title: 'Lync Server 2013: Visão geral de monitoramento'
TOCTitle: Visão geral de monitoramento
ms:assetid: 5d5eb658-7fe0-42e6-acaf-700051d0a823
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204937(v=OCS.15)
ms:contentKeyID: 49886238
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-05_

No Microsoft Lync Server 2013, o monitoramento é usado para coletar informações de uso e dados sobre QoE (qualidade da experiência) relacionados às sessões de comunicação das quais seus usuários participam. Sessão é um termo genérico que abrange uma conexão do usuário com:

  - Conferência

  - Uma modalidade de conferência (como áudio/vídeo ou compartilhamento de aplicativos)

  - Outro usuário em uma conversa ponto a ponto, como mensagens instantâneas ou uma chamada de áudio

> [!NOTE]  
> O Lync Server 2013 registra informações sobre cada sessão: quem chamou quem, quais pontos de extremidade foram usados na sessão, quanto tempo a sessão durou, a qualidade geral da sessão etc. No entanto, o Lync Server não registra e armazena a chamada propriamente dita. Isso também inclui sessões de mensagens instantâneas: embora o Lync Server registre informações sobre as sessões de mensagens instantâneas, ele não mantém um registro de cada mensagem instantânea que foi enviada durante a sessão.

Os detalhes sobre as chamadas coletados pelo Lync Server podem ser empregados para várias finalidades, incluindo:

  - **ROI (retorno do investimento)**. Os administradores podem comparar os dados de uso coletados pelo Servidor de Monitoramento com dados semelhantes coletados de seu sistema de telefonia anterior para comprovar a economia de custos e justificar a implantação do Lync Server.

  - **Gerenciamento de inventário de dispositivos**. As informações de gerenciamento de ativos ajudam os administradores a identificar dispositivos antigos ainda em uso que precisam ser substituídos, bem como dispositivos caros que podem simplesmente não estar sendo usados.

  - Suporte técnico. Dados sobre solução de problemas permitem que os engenheiros de suporte determinem o motivo da falha de uma chamada do usuário sem a necessidade de coletar logs do cliente ou do servidor. Essas informações podem ser prontamente acessadas e compreendidas por funcionários de suporte que não têm um conhecimento técnico profundo do Microsoft Lync 2013 e Lync Server 2013.

  - **Solução de problemas de sistemas**. Permite que os administradores detectem problemas graves que podem impedir que os usuários executem tarefas básicas, como ingressar em uma conferência, estabelecer uma chamada ou enviar uma mensagem instantânea.

Além dessas informações básicas sobre chamadas, o Servidor de Monitoramento também oferece um mecanismo que permite aos pontos de extremidade SIP (como o Lync 2013) fornecer informações sobre solução de problemas às quais, em outras circunstâncias, o servidor não teria acesso:

  - **Métricas de mídia que influenciam a qualidade**. Essas métricas lidam com a transmissão da chamada propriamente dita, ou seja, elas fornecem um log de trajeto à medida que a chamada passa pela rede. Essas métricas, que incluem itens como perda de pacotes, tremulação e tempo entre saída e chegada, fornecem informações sobre o que aconteceu com a chamada do momento em que ela saiu do seu ponto de extremidade até o momento em que chegou ao ponto de extremidade do outro usuário.

  - **Problemas comunicados ao usuário final**. Essas métricas incluem notificações de baixa qualidade que o Lync 2013 apresenta aos usuários finais quando eles estão muito distantes do microfone, estão falando muito baixo, quando a conexão de rede está ruim ou a qualidade está comprometida porque outro programa do computador está consumindo os recursos disponíveis.

  - **Informações sobre o ambiente**. Essas métricas detalham fatores de qualidade das chamadas, como tipo de microfone e alto-falantes usados e se o usuário está conectado através de uma VPN ou de uma rede sem fio.

No final de cada chamada, os pontos de extremidade compatíveis com SIP transmitem essas informações automaticamente para o servidor front-end que intermediou a chamada. Não é necessária nenhuma ação manual para que os pontos de extremidade transmitam essas informações, pois essa função já é incorporada ao protocolo SIP. No entanto, se você desejar coletar e armazenar essas informações, precisará instalar e habilitar o monitoramento. Se fizer isso, as informações sobre as chamadas serão coletadas pelos agentes em execução no servidor front-end e transmitidas para um par de bancos de dados do SQL Server.

Lembre-se de que o processo de instalação e configuração do monitoramento foi simplificado no Lync Server 2013. Em versões anteriores do software, o monitoramento exigia uma função de Servidor de Monitoramento separada, ou seja, era necessário reservar um computador separado para ser usado como o Servidor de Monitoramento. No Lync Server 2013, por sua vez, a função de Servidor de Monitoramento foi eliminada. Em vez disso, o serviço de monitoramento (no formato de "agentes de coleta de dados unificados") foi incorporado a todos os servidores front-end. Isso traz pelo menos dois benefícios importantes. A incorporação do serviço de monitoramento:

  - Diminui o número de funções de servidor necessárias para a implementação do Lync Server 2013. A redução de função de Servidor de Monitoramento também ajuda a reduzir os custos, pois elimina a necessidade de manter servidores dedicados para monitoramento.

  - Simplifica a instalação e a administração do Lync Server 2013. Ao integrar os serviços de monitoramento a cada servidor front-end, não é mais necessário instalar, configurar e gerenciar a função do Servidor de Monitoramento.

Para obter mais informações, consulte o tópico [Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md) no guia de implantação do Lync Server 2013.

