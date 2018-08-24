---
title: 'Lync Server 2013: Suporte a tronco SIP'
TOCTitle: Suporte a tronco SIP
ms:assetid: e3042831-e8d8-4ea2-baa2-1a697401ffa0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399005(v=OCS.15)
ms:contentKeyID: 49308388
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Se você planeja usar o Enterprise Voice com troncos SIP, deverá implantar um Servidor de Mediação e garantir que as outras infraestruturas e componentes atendam aos requisitos de suporte apropriados ao seu modelo de implantação. Para obter detalhes sobre como determinar se deve ou não implantar troncos SIP, consulte [Visão geral do tronco SIP no Lync Server 2013](lync-server-2013-overview-of-sip-trunking.md) na documentação de Planejamento.

É possível usar o Microsoft Unified Communications Open Interoperability Program para infraestrutura de telefonia empresarial para encontrar gateways PSTN qualificados, IP-PBXs e serviços de tronco SIP, incluindo provedores de serviço de telefonia IP qualificados. Para obter detalhes, consulte o site do Microsoft Unified Communications Open Interoperability Program em [http://go.microsoft.com/fwlink/p/?LinkId=203309](http://go.microsoft.com/fwlink/p/?linkid=203309).

## Suporte ao Servidor de Mediação

Para implementar o tronco SIP, você deve rotear a conexão através de um Servidor de Mediação, que age como um proxy para as sessões de comunicação entre clientes do Lync Server 2013 e o provedor de serviço. O Servidor de Mediação decodifica o tráfego de mídia de clientes e servidores e o codifica novamente antes de enviá-lo ao provedor de serviço. Essa nova codificação é necessária, pois os troncos SIP não suportam alguns codecs usados como RTA (Real Time Audio) ou negociação de protocolo ICE (Interactive Connectivity Establishment) para passagem de firewall.

Cada Servidor de Mediação pode ter dois adaptadores de rede, que fornecem uma interface de rede interna e externa. A interface externa é normalmente chamada de interface de gateway, pois tem sido usada tradicionalmente para se conectar a um gateway PSTN ou a um IP-PBX. Para implementar um tronco SIP, conecte a interface externa a um SBC (Controlador de Borda da Sessão) em um provedor de serviço.

## Tronco SIP centralizado versus distribuído

O tronco SIP *centralizado* roteia todo tráfego VoIP, incluindo tráfego de site filial, por meio de seu centro de dados. O modelo de implantação centralizada é simples, econômico e é geralmente a abordagem preferida para implementação de troncos SIP com o Lync Server 2013.

Dependendo dos padrões de uso em sua empresa, não convém rotear todos os usuários pelo tronco SIP centralizado. Para analisar suas necessidades, responda às seguintes perguntas:

  - Qual o tamanho de cada site? Quantos usuários?

  - Quais números DID (Discagem direta interna) em cada site recebem a maior quantidade de chamadas telefônicas?

Tronco SIP *distribuído* é um modelo de implantação no qual você implementa um tronco SIP local em um ou mais sites de filiais. O tráfego VoIP é roteado a partir do site da filial diretamente para o provedor de serviço, sem passar por seu data center.

O tronco SIP distribuído é exigido somente nos seguintes casos:

  - O site da filial exige conectividade de telefone persistente (por exemplo, se a WAN ficar inativa). Se a filial não precisar de redundância e failover, o provedor de serviço cobrará mais e a configuração demorará mais. Isso deve ser analisado para cada site de filial. Algumas de suas filiais pode exigir redundância e failover, enquanto outras não.

  - O site da filial e o data center estão em países/regiões diferentes. Por motivos legais e de compatibilidade, você precisa de pelo menos um tronco SIP por país/região.

A decisão sobre implantar um tronco SIP centralizado ou distribuído exige uma análise econômica. Em alguns casos, pode ser vantajoso optar pelo modelo de implantação distribuído mesmo se não for necessário. Em uma implantação totalmente centralizada, todo tráfego do site da filial é roteado por links de WAN. Em vez de pagar pela largura de banda exigida pelo link de WAN, você pode usar o tronco SIP distribuído.

> [!NOTE]  
> Para obter detalhes sobre por que e como você pode usar o tronco SIP distribuído, consulte <a href="lync-server-2013-branch-site-sip-trunking.md">Tronco SIP do site da filial no Lync Server 2013</a> na documentação Planejamento.

## Tipos de conexão de tronco SIP suportadas

O Lync Server 2013 suporta os seguintes tipos de conexão para tronco SIP:

  - MPLS (Multiprotocol Label Switching) é uma rede privada que direciona e transporta dados de um nó de rede para o próximo. A largura de banda em uma rede MPLS é compartilhada com outros assinantes e cada pacote de dados recebe um rótulo para diferenciar os dados de um assinante dos dados de outro assinante. Esse tipo de conexão não exige VPN. Uma possível desvantagem é que o tráfego IP excessivo pode interferir com a operação VoIP, a menos que o tráfego VoIP receba prioridade.

  - Uma conexão privada sem outro tráfego é normalmente o tipo de conexão mais confiável e segura (por exemplo, uma conexão de fibra óptica dedicada ou linha T1). Este tipo de conexão oferece a maior capacidade de realização de chamadas, mas é geralmente o mais caro. VPN não é necessário. Conexões privadas são adequadas para organizações com alto volume de chamadas ou com requisitos de segurança e disponibilidade rígidos.

  - A Internet pública é o tipo de conexão mais barato, mas também o menos confiável e com menor capacidade de realização de chamadas. Seu ITSP (Internet Telephony Service Provider) pode ajudar a proteger este tipo de conexão de tronco SIP se suportar TLS e SRTP (Secure Real-Time Transport Protocol) para criptografar o tráfego de sinalização e de mídia. Se não for possível configurar uma conexão de tronco SIP por meio da Internet a fim de usar o TLS e o SRTP, recomendamos que você use um túnel VPN para fornecer uma conexão mais segura. Entre em contato com seu ITSP para determinar se ele oferece suporte a TLS com o SRTP.

## Selecionando um tipo de conexão

O tipo de conexão de tronco SIP mais apropriado para sua empresa depende de suas necessidades e de seu orçamento.

  - Para empresas de médio ou grande porte, normalmente uma rede MPLS fornece o maior valor. Pode fornecer a largura de banda necessária por uma taxa mais barata do que uma rede privada especializada.

  - Empresas de grande porte podem exigir uma conexão privada de fibra ótica ou T1.

  - Para uma pequena empresa ou site de filial com baixo volume de chamada, o tronco SIP pela Internet pode ser a melhor opção. No entanto, esse tipo de conexão não é recomendado para sites de médio ou grande porte.

## Suporte ao codec

O proxy do provedor de serviço deve suportar os seguintes codecs:

  - G.711 a-law (usado principalmente fora da América do Norte)

  - G.711 µ-law (usado na América do Norte)

