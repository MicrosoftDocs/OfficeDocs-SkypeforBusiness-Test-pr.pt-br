---
title: 'Lync Server 2013: Monitorando o sistema operacional'
TOCTitle: Monitorando o sistema operacional
ms:assetid: 72406d3e-54c8-4796-8d6d-2144a5b6f030
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn720918(v=OCS.15)
ms:contentKeyID: 62240138
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Monitorando o sistema operacional no Lync Server 2013

 

_**Tópico modificado em:** 2015-01-26_

Você deve monitorar o desempenho de todos os servidores e componentes no Lync Server 2013. Obviamente, um dos componentes mais importantes é o próprio sistema operacional. O Lync Server 2013 oferece suporte às edições x64 de:

  - Windows Server 2008 R2

  - Windows Server 2012 e Windows Server 2012 R2

A maneira mais transparente de monitorar um sistema operacional é usando o Pacote de Gerenciamento do Sistema Operacional do Windows Server. Ele fornece as noções básicas fundamentais de monitoramento, como desempenho, integridade e disponibilidade para computadores que executam o Windows Server 2012, o Windows Server 2012 R2 e o Windows Server 2008 R2.

Por meio de detecção, alerta e resposta automática a eventos importantes e indicadores de desempenho, esses pacotes de gerenciamento reduzem os tempos de resolução dos problemas e aumentam a disponibilidade e o desempenho geral dos sistemas que executam os sistemas operacionais do Windows Server.

Além dos pacotes de gerenciamento relevantes do Windows Server para o System Center Operations Manager, as ferramentas de sistema e os recursos a seguir podem ser usados para monitorar a integridade do sistema operacional (dependendo da versão do sistema operacional).

## Windows Server 2008 R2

O Windows Server 2008 R2 inclui os seguintes recursos e ferramentas adicionais para ajudar os administradores com monitoramento e gerenciamento básicos do sistema operacional:

  - O **Monitor de Recursos do Windows** é uma ferramenta avançada para compreender como os recursos do sistema são usados por processos e serviços. Além de monitorar o uso do recurso em tempo real, um Monitor de Recursos pode ajudar a analisar processos sem resposta, identificar quais aplicativos estão usando arquivos e controlar processos e serviços.

  - O **Componente de Análise de Confiabilidade** é um agente nativo que fornece informações detalhadas de experiência sobre uso e confiabilidade do sistema. Essas informações são expostas por meio de uma interface WMI para serem disponibilizadas para consumo por Sistemas de Leitores Portáteis. A exposição do Componente de Análise de Confiabilidade através de uma interface WMI permite que os desenvolvedores monitorem e analisem aplicativos, aumentando a confiabilidade e o desempenho.

  - O **Windows Server 2008 R2** usa o Componente de Análise de Confiabilidade interno para calcular um índice de confiabilidade, que fornece informações sobre estabilidade e uso geral do sistema ao longo do tempo. O Componente de Análise de Confiabilidade também mantém registro de todas as alterações importantes no sistema que provavelmente exerçam influência sobre a estabilidade, como atualizações do Windows e instalações de aplicativos.

## Windows Server 2008 Monitor de Confiabilidade e Desempenho do Windows

O Monitor de Confiabilidade e Desempenho do Windows é um Snap-in do MMC que combina a funcionalidade das ferramentas autônomas anteriores, incluindo Logs e Alertas de Desempenho, Supervisor de Desempenho de Servidor e Monitor do Sistema. Ele fornece uma interface gráfica para personalizar a coleta de dados de desempenho e as Sessões de Rastreamento de Eventos.

Ele também inclui o Monitor de Confiabilidade, um Snap-in do MMC que acompanha as alterações no sistema, comparando-as com as alterações na estabilidade do sistema, e fornece uma exibição gráfica de sua relação.

## Monitor de Confiabilidade e Desempenho do Windows

Além de combinar funcionalidades de algumas ferramentas autônomas antigas, como Logs e Alertas de Desempenho, Monitor do Sistema e Supervisor de Desempenho de Servidor, o Monitor de Confiabilidade e Desempenho do Windows também fornece uma nova funcionalidade para o Windows Server 2008 e o Windows Server 2008 R2, como esta:

  - Conjuntos de Coletores de Dados

  - Modo de Exibição de Recursos

  - Monitor de Confiabilidade

  - Assistentes e modelos para a criação de logs

O **Conjunto de Coletores de Dados** agrupa os coletores de dados em elementos reutilizáveis para serem usados com cenários de monitoramento de desempenho diferentes. Depois que um grupo de coletores de dados é armazenado como um Conjunto de Coletores de Dados, as operações, como agendamento, podem ser aplicadas a todo o conjunto através de uma única mudança de propriedade. O Monitor de Confiabilidade e Desempenho do Windows inclui modelos padrão de Conjuntos de Coletores de Dados para ajudar os administradores de sistema a iniciar imediatamente a coleta de dados de desempenho específicos de uma função de servidor ou de um cenário de monitoramento.

A home page do Monitor de Confiabilidade e Desempenho do Windows é a nova tela **Modo de Exibição de Recursos**, que apresenta uma visão geral gráfica em tempo real do uso da CPU, do disco, da rede e da memória. Ao expandir cada um desses elementos monitorados, os administradores de sistema conseguem identificar quais processos estão usando quais recursos. Nas versões anteriores do Windows, esses dados em tempo real, específicos de processo, estavam disponíveis apenas de forma limitada no Gerenciador de Tarefas.

O **Monitor de Confiabilidade** calcula um Índice de Estabilidade do Sistema que reflete se problemas inesperados reduziram a confiabilidade do sistema. Um gráfico ao longo do tempo do Índice de Estabilidade identifica rapidamente as datas em que os problemas começaram a ocorrer. O Relatório de Estabilidade do Sistema de acompanhamento fornece detalhes para ajudar a solucionar problemas da causa da confiabilidade reduzida. A exibição lado a lado das alterações no sistema (instalação ou remoção de aplicativos, atualizações no sistema operacional ou adição ou modificação de drivers) junto com as falhas (falhas de aplicativos, panes do sistema operacional ou falhas de hardware) permite o rápido desenvolvimento de uma estratégia para tratar os problemas.

A adição de contadores a arquivos de log e o agendamento de seu início, de sua interrupção ou de sua duração agora podem ser realizados através de uma **interface de Assistente**. Além disso, salvar essa configuração como modelo permite que os administradores de sistema coletem o mesmo log em outros computadores sem repetir os processos de seleção e agencamento do coletor de dados. Os recursos de Logs e Alertas de Desempenho foram incorporados ao Monitor de Confiabilidade e Desempenho do Windows para serem usados com qualquer Conjunto de Coletores de Dados.

