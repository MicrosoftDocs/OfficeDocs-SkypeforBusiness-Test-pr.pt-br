---
title: 'Lync Server 2013: Opções de implantação do gateway PSTN'
TOCTitle: Opções de implantação do gateway PSTN
ms:assetid: d1ab4f74-18aa-40c7-a8cf-ec806cf6e28a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398899(v=OCS.15)
ms:contentKeyID: 49308182
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Opções de implantação do gateway PSTN no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

## Gateways PSTN

Gateways PSTN são componentes de hardware de terceiros que convertem a sinalização e a mídia entre a infraestrutura do Enterprise Voice e o PSTN, diretamente ou por meio de uma conexão com troncos SIP. Em qualquer uma das topologias, o gateway encerra o PSTN. Ele fica isolado em sua própria subrede e é conectado à rede empresarial através do Servidor de Mediação.

Normalmente, uma empresa com vários sites implantaria um ou mais gateways em cada site. Sites de filiais podem se conectar ao PSTN através do gateway ou do Aparelho de Filial Persistente, o que combina gateway e servidores em uma única caixa. Se o site de filial usar um gateway, um registrador e o Servidor de Mediação serão necessários no site, amenos que o link de WAN seja resiliente. Um ou mais Servidor de Mediação, que são colocados no Servidores Front-End, podem rotear chamadas para os gateways de cada site. Recomendamos que o registrador, o Servidor de Mediação e o exigidos no site sejam implantados como um Aparelho de Filial Persistente.

Determinar o número, o tamanho e o local dos gateways PSTN é talvez a decisão mais importante e cara que você precisa tomar ao planejar sua infraestrutura Enterprise Voice.

Há várias perguntas a considerar. Tenha em mente que as respostas destas perguntas são interdependentes

  - Quantos gateways PSTN são necessários? A resposta depende do número de usuários, do número antecipado de chamadas simultâneas (carga de tráfego) e do número de sites (cada site precisa de um).

  - Qual deve ser o tamanho dos gateways? A resposta depende do número de usuários no site e da carga de tráfego.

  - Onde os gateways devem ser localizados? A resposta depende em parte da topologia e em parte da distribuição geográfica de sua organização.

Você também deve considerar suas opções de topologia de gateway (para obter detalhes, consulte Topologias de Gateway posteriormente neste tópico).

## Suporte de Tronco M:N

O Servidor de Mediação pode rotear chamadas através de vários gateways, Controladores de Borda da Sessão (SBCs) oferecidos por provedores de serviço de telefonia pela Internet ou uma combinação dos dois. Além disso, vários Servidor de Mediação no pool podem interagir com vários gateways. A rota lógica definida entre um Servidor de Mediação e o gateway é chamada *tronco* . Quando o usuário interno faz uma chamada PSTN, o roteamento de saída lógico no Pool de Front-Ends escolhe qual tronco rotear em todas as combinações possíveis que podem estar disponíveis para roteamento nesta chamada. Com balanceamento de carga DNS, se uma chamada falhar ao atingir um gateway devido a um problema com um determinado Servidor de Mediação no pool, a chamada pode ser tentada novamente para um Servidor de Mediação alternativo no pool.

Para obter detalhes sobre como planejar para múltiplos gateways, consulte [Tronco M:N no Lync Server 2013](lync-server-2013-m-n-trunk.md).

Para obter detalhes sobre outros aprimoramentos de roteamento de saída, consulte [Rotas de voz no Lync Server 2013](lync-server-2013-voice-routes.md).

## Topologias de gateway

Ao considerar as perguntas fundamentais da implantação de gateway, siga estas etapas:

1.  Conte os sites nos quais você deseja fornecer a conectividade PSTN usando Enterprise Voice.

2.  Estime o tráfego em cada site (número de usuários e número médio de chamadas por hora, por usuário).

3.  Implante um ou mais gateways em cada site a fim de manipular o tráfego antecipado.

A topologia de gateway distribuído resultante é exibida na figura a seguir.

**Topologia de gateway distribuída**

![Diagrama da topologia do gateway distribuído](images/Gg398899.f0f65a0b-a462-491a-878b-4d4bf0a96f6d(OCS.15).jpg "Diagrama da topologia do gateway distribuído")

Com essa topologia, as chamadas entre os trabalhadores em cada site e entre sites são todas roteadas através de sua intranet. As chamadas para o PSTN são roteadas sobre a rede IP da empresa até os gateways mais próximos do local dos números de destino. Mas e se sua organização suportar dezenas ou centenas ou até mesmo milhares de sites espalhados em um ou mais continentes, assim como fazem muitas instituições financeiras e outras grandes empresas? Nesses casos, a implantação de um gateway separado em cada site não é prática.

Para resolver esse problema, muitas empresas grandes preferem implantar um ou alguns grandes site central de telefonia, como mostra a figura a seguir.

**Topologia de site central de telefonia**

![Topologia do gateway do centro de dados](images/Gg398899.927f4808-bf74-405a-be20-2cd9cd87af6d(OCS.15).jpg "Topologia do gateway do centro de dados")

Nessa topologia, diversos gateways de grande porte suficientes para acomodar a carga de usuário antecipada são implantados em cada site central. Todas as chamadas aos usuários na empresa são encaminhadas pelo provedor de serviço de telefonia da empresa a um site central. A lógica de roteamento no site central determina se a chamada deve ser roteada pela intranet ou para o PSTN.

## Local do gateway

O local do gateway também pode determinar os tipos de gateways que você escolhe e como eles são configurados. Há dezenas de protocolos PSTN, nenhum em um padrão mundial. Se todos os seus gateways estiverem localizados em um único país/região, isso não será um problema, mas se você localizar os gateways em diversos países/regiões, cada um precisa estar configurado de acordo com os padrões de PSTN nesse país/região. Além disso, os gateways certificados para operação no, por exemplo, Canadá, talvez não sejam certificados na Índia, Brasil ou União Europeia.

## Tamanho e número de gateways

Os gateways PSTN que a maioria das organizações considerará implantar variam com relação ao tamanho de 2 a 960 portas. (Há gateways ainda maiores, mas eles são usados principalmente pelos provedores de serviço de telefonia.) Ao estimar o número de portas exigido por sua organização, use as seguintes diretrizes:

  - Organizações com uso leve de telefonia (uma chamada PSTN por usuário, por hora) deve alocar uma porta para cada 15 usuários. Por exemplo, se você tiver 20 usuários, precisará de um gateway com duas portas.

  - Organizações com um uso moderado de telefonia (duas chamadas PSTN por usuário, por hora) deve alocar uma porta para cada 10 usuários. Por exemplo, se você tiver 100 usuários, precisará de um total de 10 portas alocadas entre um ou mais gateways.

  - Organizações com uso pesado de telefonia (três ou mais chamadas PSTN por usuário, por hora) devem alocar uma porta para cada cinco usuários. Por exemplo, se você tiver 47.000 usuários, precisará de um total de 9.400 portas alocadas entre pelo menos 10 grandes gateways.

  - É possível adquirir portas adicionais à medida que o número de usuários ou quantidade de tráfego em sua organização aumenta.

Para qualquer quantidade de usuários que você deve suportar, você tem a opção de implantar uma quantidade menor de gateways maiores ou menores. Como regra, recomenda-se um mínimo de dois gateways para uma organização a fim de manter a disponibilidade, caso um gateway falhe.

Cada gateway PSTN implantado precisa ter pelo menos um Servidor de Mediação correspondente.

