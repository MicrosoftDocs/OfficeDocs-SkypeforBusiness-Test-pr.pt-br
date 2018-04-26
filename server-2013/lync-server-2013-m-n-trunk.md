---
title: 'Lync Server 2013: Tronco M:N'
TOCTitle: Tronco M:N
ms:assetid: dc4c5d66-297c-48a5-91b9-b9b8ce44a6e0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398971(v=OCS.15)
ms:contentKeyID: 49308315
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tronco M:N no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

O Lync Server 2013 suporta maior flexibilidade na definição de um tronco para fins de roteamento de chamada de versões anteriores. Um tronco é uma associação lógica entre um Servidor de Mediação e um número de porta do ouvinte com um gateway e um número de porta do ouvinte. Isto quer dizer várias coisas: Um Servidor de Mediação pode ter vários troncos no mesmo gateway; um Servidor de Mediação pode ter vários troncos com diferentes gateways; ao contrário, um gateway pode ter vários troncos para Servidor de Mediação diferentes.

Um tronco raiz ainda precisa ser criado quando um gateway é adicionado à topologia do Lync usando o Construtor de Topologias. O número de gateways que um determinado Servidor de Mediação pode lidar depende da capacidade de processamento do servidor durante as horas de pico. Se você implantar um Servidor de Mediação no hardware que excede os requisitos mínimos de hardware para o Lync Server 2013, conforme descrito no [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) na documentação de Suportabilidade, a estimativa de quantas chamadas não bypass ativas um Servidor de Mediação autônomo pode tratar é de aproximadamente 1000 chamadas. Ao implantar no hardware estas especificações, o Servidor de Mediação deve realizar a transcodificação, mas ainda roteará chamadas para vários gateways, mesmo se os gateways não suportam o bypass de mídia.

Ao definir uma rota de chamada, você especifica os troncos associados à essa rota, mas não especifica quais Servidor de Mediação estão associados a essa rota. Em vez disso, você usa o Construtor de Topologias para associar gateways ao Servidor de Mediação. Em outras palavras, o roteamento determina qual tronco usar para uma chamada e o Servidor de Mediação associado a esse tronco lida com a chamada.

O Servidor de Mediação pode ser implantado como um pool; esse pool pode ser colocado com um Pool de Front-Ends ou pode ser implantado como um pool autônomo. Quando um Servidor de Mediação é colocado com um Pool de Front-Ends, o tamanho do pool pode ser no máximo 10 (o limite do tamanho do pool do registrador). Reunidos, esses novos recursos aumentam a confiabilidade e a flexibilidade de implantação para o Servidor de Mediação, mas exigem recursos associados nas seguintes entidades pares:

  - **Gateway PSTN.** Um gateway qualificado do Lync Server 2013 precisa implementar o balanceamento de carga DNS, que permite a um gateway PSTN qualificado agir como um balanceador de carga para um pool de Servidor de Mediação e, dessa forma, balancear a carga de chamadas no pool.

  - **Controlador de Borda da Sessão.** Para um tronco SIP, a entrada de ponto é um Controlador de Borda da Sessão (SBC) no provedor de serviço de telefonia pela Internet. Na direção do Pool do servidor de mediação para o SBC, o SBC pode receber conexões de qualquer Servidor de Mediação no pool. Na direção do SBC para o pool, o tráfego pode ser enviado para qualquer Servidor de Mediação no pool. Um método de obter isso é através do balanceamento de carga DNS, se suportado pelo provedor de serviço e SBC. Uma alternativa é oferecer ao provedor de serviço os endereços IP de todos os Servidor de Mediação no pool, e o provedor de serviço provisionará eles em seu SBC como um tronco SIP separado para cada Servidor de Mediação. O provedor de serviço irá tratar o balanceamento de carga em seus próprios servidores. Nem todos os provedores de serviço ou SBCs podem suportar estas capacidades. Além disso, o provedor de serviço pode cobrar mais por esta capacidade. Geralmente, cada tronco SIP para o SBC é tarifado mensalmente.

  - **IP-PBX.** Na direção do Pool do servidor de mediação para a terminação SIP IP-PBX, o IP-PBX pode receber conexões de qualquer Servidor de Mediação no pool. Na direção do IP-PBX para o pool, o tráfego pode ser enviado para qualquer Servidor de Mediação no pool. Como a maioria dos IP-PBXs não suportam balanceamento de carga DNS, recomendamos que conexões SIP diretas individuais sejam definidas do IP-PBX para cada Servidor de Mediação no pool. O IP-PBX tratará seu próprio balanceamento de carga distribuindo o tráfego pelo grupo de troncos. Assumimos que o grupo de tronco possui um conjunto de regras de roteamento consistente no IP-PBX se um determinado IP-PBX suporta este conceito de grupo de tronco e como ele insere com a própria redundância do IP-PBX e arquitetura de agrupamento precisa ser determinado antes de poder decidir se um grupo do Servidor de Mediação pode interagir corretamente com um IP-PBX.

Um Pool do servidor de mediação precisa ter uma visualização uniforme do gateway par com o qual ele interage. Isso significa que todos os membros do pool acessam a mesma definição do gateway par a partir do repositório de configurações e têm a mesma probabilidade de interagir com ele para chamadas de saída. Dessa forma, não é possível segmentar o pool de modo que alguns Servidor de Mediação se comuniquem com apenas alguns gateway pares para chamadas de saída. Se essa segmentação for necessária, um pool separado de Servidor de Mediação deverá ser usado. Isso seria o caso, por exemplo, se os recursos associados nos gateways PSTN, troncos SIP ou IP-PBXs para interação com um pool, conforme detalhado anteriormente neste tópico, não estivessem presentes.

Um determinado gateway PSTN, IP-PBX ou ponto de tronco SIP pode rotear para vários Servidor de Mediação ou troncos. O número de gateways que este determinado pool de Servidor de Mediação pode controlar depende do número de chamadas que usam bypass de mídia. Se um grande número de chamadas usam bypass de mídia, um Servidor de Mediação no pool pode tratar muitas chamadas, porque apenas o processamento de camada de sinalização é necessário.

