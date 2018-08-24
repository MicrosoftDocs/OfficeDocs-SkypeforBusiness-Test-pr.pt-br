---
title: Requisitos de infraestrutura de rede para Lync Server 2013
TOCTitle: Requisitos de infraestrutura de rede para Lync Server 2013
ms:assetid: 35c7bb3f-8e0f-48b7-8a2c-857d4b42a4c4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425841(v=OCS.15)
ms:contentKeyID: 49306362
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de infraestrutura de rede para Lync Server 2013

 

_**Tópico modificado em:** 2014-08-28_

A placa do adaptador de rede de cada servidor na topologia do Lync Server 2013  deve oferecer suporte a pelo menos 1 Gbps (gigabit por segundo). Em geral, você deve conectar todas as funções de servidor da topologia do Lync Server usando uma LAN (rede local) de baixa latência e largura de banda alta. O tamanho da LAN depende do tamanho da topologia:

  - Nas topologias do Standard Edition, os servidores devem ficar em uma rede que ofereça suporte a Ethernet de 1 Gbps ou equivalente.

  - Nas topologias do Pool de Front-Ends, a maioria dos servidores deve ficar em uma rede que ofereça suporte a mais de 1 Gbps, especialmente no caso de suporte a conferências de A/V (áudio/vídeo) e compartilhamento de aplicativos.

Para a integração com PSTN, você pode usar linhas T1/E1 ou troncos SIP.

## Requisitos de rede para áudio/vídeo

Os requisitos de rede para o áudio/vídeo (A/V) em uma implementação do Lync Server incluem o seguinte:

  - Se estiver implantando um Servidor de Borda ou um Pool de borda único usando balanceamento de carga DNS, será possível configurar o firewall externo como NAT. Para obter detalhes sobre esses requisitos, consulte [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md) na documentação de planejamento.
    
    > [!IMPORTANT]  
    > Se tiver um Pool de borda e estiver usando um balanceador de carga de hardware, será preciso usar endereços IP públicos em cada um dos Servidores de Borda e não será possível usar NAT para os servidores ou o pool em seu dispositivo NAT (por exemplo, o firewall ou outro dispositivo da infraestrutura que faria o tráfego NAT de entrada ou saída). Para obter detalhes, consulte <a href="lync-server-2013-port-summary-scaled-consolidated-edge-with-hardware-load-balancers.md">Resumo de porta - borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013</a> na documentação de planejamento de acesso de usuários externos.

  - Caso sua organização use uma infraestrutura de QoS (Qualidade de Serviço), o subsistema de mídia estará projetado para operar dentro dessa infraestrutura existente.

  - Caso você utilize o protocolo IPsec, é recomendável desabilitá-lo nos intervalos de portas usados para o tráfego de A/V. Para obter detalhes, consulte [Exceções Ipsec no Lync Server 2013](lync-server-2013-ipsec-exceptions.md) na documentação de planejamento.

Para garantir a melhor qualidade da mídia, siga este procedimento:

  - Provisione os vínculos da rede para dar suporte a uma taxa de transferência de 65 Kbps (quilobits por segundo) por fluxo de áudio e 500 Kbps por fluxo de vídeo, se estiver habilitado, durante os períodos de uso máximo. Uma sessão de áudio ou vídeo bidirecional consiste em dois fluxos.

  - Para lidar com picos inesperados de tráfego acima desse nível e o aumento do uso ao longo do tempo, os pontos de extremidade de mídia do Lync Server podem se adaptar a variações nas condições da rede e oferecer suporte a cargas iguais ao triplo da taxa de transferência (consulte o parágrafo anterior) para áudio e vídeo, sem deixar de manter uma qualidade aceitável. No entanto, não presuma que essa adaptabilidade suportará uma rede subprovisionada. Nesse caso, a capacidade dos pontos de extremidade de mídia do Lync Server de lidar dinamicamente com variações nas condições da rede, como, por exemplo, perdas elevadas temporárias de pacotes.

  - Para vínculos de rede em que o provisionamento envolve altíssimo custo e dificuldade, considere a opção de provisionar para um volume menor de tráfego. Neste cenário, deixe a elasticidade dos pontos de extremidade de mídia do Lync Server absorver a diferença o esse volume de tráfego e o nível de tráfego de pico ao custo de certa redução na qualidade da voz. Além disso, há uma diminuição na reserva dinâmica que, de outra forma, estaria disponível para absorver picos súbitos de tráfego.

  - Para os vínculos que não podem ser provisionados corretamente a curto prazo (por exemplo, um local com vínculos de WAN de péssima qualidade), considere a possibilidade de desabilitar o vídeo para determinados usuários.

  - Provisione sua rede para assegurar um atraso máximo de ponta a ponta (latência) de 150 ms (milissegundos) sob carga máxima. A latência é o único dano na rede que os componentes de mídia do Lync Server não conseguem reduzir, e é importante localizar e eliminar os pontos fracos.

  - Para servidores executando software antivírus, inclua todos os servidores que executam o Lync Server na lista de exceções para fornecer os níveis ideais de desempenho e qualidade de áudio.

## Requisitos da Rede de Conferência

A largura de banda que é usada para baixar o conteúdo da conferência do servidor do IIS (Serviços de Informações da Internet) depende do tamanho do conteúdo carregado.

