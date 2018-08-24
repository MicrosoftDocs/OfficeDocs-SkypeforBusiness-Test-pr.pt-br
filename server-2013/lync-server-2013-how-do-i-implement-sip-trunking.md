---
title: 'Lync Server 2013: Como implementar tronco SIP?'
TOCTitle: Como implementar tronco SIP?
ms:assetid: 273a22b1-8a4c-4187-acf8-c57d5c6598ce
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425743(v=OCS.15)
ms:contentKeyID: 49306178
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Como implementar tronco SIP no Lync Server 2013?

 

_**Tópico modificado em:** 2016-12-08_

Para implementar o tronco SIP, você deve rotear a conexão através de um Servidor de Mediação, que age como um proxy para sessões de comunicação entre clientes do Lync Server 2013 e o provedor de serviço e mídia de transcodificação, quando necessário.

Cada Servidor de Mediação tem uma interface de rede interna e externa. A interface interna se conecta ao Servidores Front-End. A interface externa é normalmente chamada de interface gateway, pois tem sido usada tradicionalmente para conectar o Servidor de Mediação a um gateway PSTN ou a um IP-PBX. Para implementar um tronco SIP, conecte a interface externa do Servidor de Mediação ao componente de borda externa do ITSP.

> [!NOTE]  
> O componente de borda externa do ITSP pode ser um SBC (controlador de borda da sessão), um roteador ou um gateway.

Para obter detalhes sobre o Servidor de Mediação, consulte [Componente do Servidor de Mediação no Lync Server 2013](lync-server-2013-mediation-server-component.md).

## Tronco SIP centralizado versus distribuído

*Centralizado* Tronco SIP roteia todo o tráfego Voz por Protocolo Internet (VoIP), incluindo o tráfego site de filial, através do site central. O modelo de implantação centralizado é simples, econômico e é geralmente a abordagem recomendada para implementar troncos SIP com Lync Server 2013.

Tronco SIP *distribuído* é um modelo de implantação no qual você implementa um tronco SIP local em um ou mais sites de filiais. O tráfego VoIP é encaminhado do site de filial diretamente para um provedor de serviço sem passar pelo site central.

O tronco SIP distribuído é exigido somente nos seguintes casos:

  - O site de filial exige a conectividade telefônica persistente (por exemplo, se a WAN ficar inativa). Esse requisito deve ser analisado para cada site de filial; algumas de suas filiais podem exigir redundância e failover, enquanto outras não.

  - A resiliência é necessária entre dois site central. É preciso se certificar de um tronco SIP termina em cada site central. Por exemplo, se você tiver os site central de Dublin e Tukwila e ambos usarem o tronco SIP de apenas um local, se o tronco ficar inativo, os usuários do outro local não poderão fazer chamadas PSTN.

  - O site de filial e o site central estão em países/regiões diferentes. Por motivos legais e de compatibilidade, você precisa de pelo menos um tronco SIP por país/região. Por exemplo, na União Europeia, as comunicações não podem deixar um país/região sem serem terminarem localmente em um ponto centralizado.

Dependendo do local geográficos dos sites e da quantidade de tráfego antecipado dentro de sua empresa, talvez não seja uma boa ideia rotear todos os seus usuários pelo tronco SIP central, ou você pode optar por rotear alguns usuários por um tronco SIP em seu site de filial. Para analisar suas necessidades, responda às seguintes perguntas:

  - Qual o tamanho de cada site (ou seja, quantos usuários estão habilitados para Enterprise Voice)?

  - Quais números DID (discagem direta interna) em cada site recebem a maioria das chamadas?

A decisão sobre implantar um tronco SIP centralizado ou distribuído exige uma análise com bom custo benefício. Em alguns casos, pode ser vantajoso optar pelo modelo de implantação distribuído mesmo se não for necessário. Em uma implantação completamente centralizada, todo o tráfego site de filial é roteado sobre links WAN. Em vez de pagar pela largura de banda exigida pelo link de WAN, convém usar o tronco SIP distribuído. Por exemplo, convém implantar um Servidor Standard Edition em um site de filial com federação para o site central o convém implantar um Aparelho de Filial Persistente ou Servidor de Filial Persistente com um pequeno gateway.

> [!NOTE]  
> Para obter detalhes sobre o tronco SIP distribuído, consulte <a href="lync-server-2013-branch-site-sip-trunking.md">Tronco SIP do site da filial no Lync Server 2013</a>.

## Tipos de conexão de tronco SIP suportadas

O Lync Server suporta os seguintes tipos de conexão para tronco SIP:

  - MPLS (Multiprotocol Label Switching) é uma rede privada que direciona e transporta dados de um nó de rede para o próximo. A largura de banda em uma rede MPLS é compartilhada com outros assinantes e cada pacote de dados recebe um rótulo para diferenciar os dados de um assinante dos dados de outro assinante. Esse tipo de conexão não exige VPN. Uma possível desvantagem é que o tráfego IP excessivo pode interferir com a operação VoIP, a menos que o tráfego VoIP tenha prioridade.

  - Uma conexão privada sem outro tráfego?por exemplo, uma conexão de fibra ótica arrendada ou linha T1?é normalmente o tipo de conexão mais confiável e segura (por exemplo, uma conexão de fibra óptica. Este tipo de conexão oferece a maior capacidade de realização de chamadas, mas é geralmente o mais caro. VPN não é necessário. Conexões privadas são adequadas para organizações com alto volume de chamadas ou com requisitos de segurança e disponibilidade rígidos.

  - A Internet é o tipo de conexão menos caro, mas também o menos confiável. A conexão com a Internet é o único tipo de conexão de tronco SIP do Lync Server que exige VPN.

## Selecionando um tipo de conexão

O tipo de conexão de tronco SIP mais apropriado para sua empresa depende de suas necessidades e de seu orçamento.

  - Para uma empresa de médio ou grande porte, uma rede MPLS normalmente fornece o maior valor. Ela pode fornecer a largura de banda necessária por uma taxa mais barata do que uma rede privada especializada.

  - Empresas de grande porte podem exigir uma conexão de fibra ótica T1, T3 ou superior (E1, E3 ou superior na União Europeia).

  - Para um site de filial de empresa pequena ou do site de filial com baixo volume de chamada, o tronco SIP pela Internet pode ser a melhor opção. Esse tipo de conexão não é recomendado para sites de médio ou grande porte.

## Requisitos de largura de banda

A quantidade de largura de banda exigida pela sua implementação depende da capacidade da chamada (o número de chamadas simultâneas que você precisa suportar). A disponibilidade de largura de banda precisa ser levada em consideração para que você possa aproveitar ao máximo a capacidade de pico pela qual pagou. Use a fórmula a seguir para calcular o requisito de largura de banda de pico do tronco SIP:

Largura de banda de pico do tronco SIP = máximo de chamadas simultâneas x (64 kbps + tamanho do cabeçalho)

> [!NOTE]  
> O tamanho do cabeçalho é de 20 bytes no máximo.

## Suporte ao codec

O Lync Server 2013 suporta apenas os seguintes codecs:

  - G.711 a-law (usado principalmente fora da América do Norte)

  - G.711 µ-law (usado na América do Norte)

## Provedor de Serviço de Telefonia pela Internet

Como você implementa o lado do provedor de serviço de uma conexão de tronco SIP varia de um ITSP para outro. Para obter informações de implantação, entre em contato com seu provedor de serviço. Para obter uma lista de provedores de serviço de tronco SIP certificados, consulte [o site do Programa de Interoperabilidade Aberta do Microsoft Unified Communications](http://go.microsoft.com/fwlink/?linkid=287029).

Para obter detalhes sobre os provedores de tronco SIP certificado pela Microsoft, entre em contato com seu representante da Microsoft.

> [!IMPORTANT]  
> Você deve usar um provedor de serviço certificado pela Microsoft para garantir que seu ITSP suporte todas as funcionalidades que atravessam o tronco SIP (por exemplo, configurar e gerenciar sessões e suportar todos os serviços de VoIP estendido). O suporte técnico da Microsoft não estender as configurações que usam provedores não certificados. Se você atualmente usa um provedor de serviço Internet não certificado para tronco SIP, é possível optar por continuar usando este provedor como seu ISP e usar um provedor certificado pela Microsoft para tronco SIP.
