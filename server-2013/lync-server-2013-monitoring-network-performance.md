---
title: 'Lync Server 2013: Monitorando o desempenho da rede'
TOCTitle: Monitorando o desempenho da rede
ms:assetid: bc3a01da-91eb-4c0c-9598-35e5e46b00f6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn720923(v=OCS.15)
ms:contentKeyID: 62240144
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Monitorando o desempenho da rede no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 é uma tecnologia de comunicação em tempo real bastante dependente da rede para permitir a comunicação entre os usuários, seja através de mensagens instantâneas (IM), chamadas de voz ou comunicação por vídeo. Portanto, é importante monitorar o desempenho da rede continuamente para ajudar a garantir que a modalidade de comunicação escolhida por um usuário forneça a melhor experiência possível.

O desempenho da rede pode ser medido em dois níveis:

  - **Desempenho geral da rede**   Esse nível de medição de desempenho permitirá a uma organização obter uma visão geral da rede e, geralmente, é implementado através de sistemas de monitoramento de rede de terceiros. Esses sistemas receberão dados de desempenho e capacidade de dispositivos de rede remotos, como roteadores e rede comutada em toda a rede para permitir que os administradores determinem a integridade de qualquer componente de rede em qualquer hora do dia.

  - **Desempenho individual do servidor**   Esse nível de medição de desempenho é limitado a um servidor específico e ajudará os administradores a medir o desempenho de um determinado servidor na rede para auxiliar na solução de um problema de desempenho específico ou para medir o desempenho do respectivo servidor em um período específico como parte do processo de planejamento de capacidade.

Você pode monitorar a rede usando as ferramentas descritas nas seções a seguir.

## Ferramentas para monitoramento do desempenho geral da rede

## System Center Operations Manager 2012

O System Center Operations Manager fornece gerenciamento de serviços ponta a ponta, fácil de personalizar e estender para níveis de serviço aprimorados em um ambiente de TI. Isso permite que as equipes de Operações e Gerenciamento de TI identifiquem e resolvam os problemas que afetam a integridade dos serviços de TI distribuídos. O gerenciamento de serviços ponta a ponta não se restringe a ambientes baseados na Microsoft. O suporte para o Web Services for Management (WS-Management), o protocolo SNMP e as soluções de parceiros permitem que sistemas que não executam os sistemas operacionais Microsoft e o hardware sejam incluídos no monitoramento de serviços dentro do System Center Operations Manager 2012.

## System Center Operations Manager 2012 e soluções de gerenciamento de rede de terceiros

**EMC Smarts**   As EMC Solutions for Operations Manager o ajudam a resolver rapidamente os problemas que afetam completamente os níveis de serviço. Ao usar as EMC Solutions for Operations Manager, você poderá gerenciar e monitorar toda a sua cadeia de serviços de TI com uma única solução automatizada integrada. Você identificará facilmente as causas principais dos problemas de desempenho e disponibilidade, resolvendo-os com mais rapidez, o que reduzirá efeitos e custos. Os principais benefícios incluem:

  - Gerenciamento avançado, fácil de usar   Foco na entrega de valor comercial estratégico em vez de classificar e filtrar manualmente alertas confusos.

  - **Resolução mais rápida**   Solucione problemas de TI e atenda às necessidades comerciais com mais rapidez, reduzindo efeito e custo.

  - **Operações simples**   Evite a complexidade da TI, combinando várias ferramentas, aplicativos e terminais de gerenciamento.

Para obter mais informações, consulte:

[Microsoft System Center Operations Manager](http://go.microsoft.com/fwlink/p/?linkid=243651)

[Soluções para o Microsoft System Center Operations Manager](http://www.emc.com/collateral/software/data-sheet/h6135-server-manager-ds.pdf)

## Soluções de terceiros

**HP Network Management Center (anteriormente conhecido como HP OpenView)**   [HP Network Management Center](https://h10078.www1.hp.com/cda/hpms/display/main/hpms_content.jsp?zn=bto%26cp=1-11-15-119_4000_100__) fornece gerenciamento integrado de falhas e desempenho para melhorar o desempenho e a disponibilidade da rede. O Network Management Center faz parte da solução automatizada de gerenciamento de rede HP que unifica gerenciamento de falhas, desempenho, configuração e alterações.

**Produtos Cisco Network Management and Automation**   Para o Enterprise, a Cisco tem vários produtos de gerenciamento disponíveis, incluindo o CiscoWorks LAN Management Solution e o Cisco Network Analysis Module, para ajudar a melhorar a eficiência operacional e reduzir o tempo de inatividade da rede. Para obter dados adicionais sobre esses produtos, consulte o site da Cisco em [http://www.cisco.com/en/US/products/sw/netmgtsw/index.html](http://www.cisco.com/en/us/products/sw/netmgtsw/index.html).

Simple Network Management Protocol (SNMP)   O SNMP é um padrão de gerenciamento de rede que define uma estratégia para o gerenciamento de redes TCP/IP. Ele permite que você capture informações de configuração e status sobre a rede e envie as informações para um computador designado para monitoramento de eventos. Esse protocolo de gerenciamento de rede com base em padrões usa uma arquitetura distribuída que inclui o seguinte:

  - Vários nós gerenciados e, cada um deles com uma entidade SNMP denominada agente que fornece acesso remoto para instrumentação de gerenciamento.

  - Pelo menos uma entidade SNMP, conhecida como gerenciador, que executa aplicativos de gerenciamento para monitorar e controlar elementos gerenciados. Os elementos gerenciados são dispositivos, como hosts, roteadores etc. Eles são monitorados e controlados acessando suas informações de gerenciamento.

  - Um protocolo de gerenciamento, SNMP, é usado para comunicar as informações de gerenciamento entre as estações e os agentes de gerenciamento. As informações de gerenciamento referem-se a um conjunto de objetos gerenciados que residem em um repositório virtual de informações, denominado MIB (base de informações de gerenciamento).

> [!NOTE]  
> Os exemplos de soluções de monitoramento de rede de terceiros são fornecidos acima. Essa lista não é definitiva, e a Microsoft não favorece nenhuma solução de fornecedor específica. Consulte um provedor de serviços de rede e/ou seu respectivo provedor de tecnologia para determinar a melhor solução de monitoramento de rede para a sua organização.

## Ferramentas para monitorar o desempenho individual da rede dos servidores

## System Center Operations Manager 2012

O System Center Operations Manager 2012 permite que os administradores exibam o desempenho de rede dos servidores individuais através do Pacote de Gerenciamento do Windows Server 2012: o pacote de gerenciamento do sistema operacional do Windows Server inclui um pacote de gerenciamento de "Desempenho" que permite aos administradores monitorarem o desempenho e a integridade do Adaptador de Rede.

## Monitor de Rede do Windows

Coleta, exibe, analisa o uso de recursos em um servidor e mede o tráfego de rede. O Monitor de Rede controla exclusivamente a atividade da rede. Por meio da captura e da análise dos dados de rede e utilização desses dados com logs de desempenho, você poderá determinar o uso da rede, identificar problemas de rede e prever as necessidades futuras da rede.

Para obter mais informações sobre o Network Monitor 3.4 e saber como instalar e configurar o Monitor de Rede e capturar e analisar dados, examine esta sessão: Visão geral do Network Monitor 3.3. Consulte também o blog do Monitor de Rede em: <http://blogs.technet.com/b/netmon/>.

