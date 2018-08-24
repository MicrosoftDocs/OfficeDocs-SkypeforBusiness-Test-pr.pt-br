---
title: 'Lync Server 2013: Configurar bypass de mídia'
TOCTitle: Configurar bypass de mídia
ms:assetid: f50a7a13-c6a0-48f1-bee1-e45fa2b2f9b8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413028(v=OCS.15)
ms:contentKeyID: 49308616
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar bypass de mídia no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Esta seção assume que você já publicou e configurou pelo menos um ou mais Servidores de Mediação (conforme descrito em [Definir um Servidor de Mediação no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-a-mediation-server-in-topology-builder.md) e [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md) ou em [Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md) e [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md), respectivamente, todos na documentação de Implantação).

Esta seção também assume que você definiu pelo menos um par de gateway para oferecer conectividade de PSTN, conforme descrito no [Definir um gateway no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-a-gateway-in-topology-builder.md). Se o par ao qual você está se conectando for o SBC de um provedor de tronco SIP, certifique-se de que o provedor qualificado e que suporta bypass de mídia. Por exemplo, vários provedores de tronco SIP permitirão que seu SBC receba tráfego do Servidor de Mediação. Caso sim, o bypass não deve ser habilitado para o tronco em questão. Além disso, não é possível habilitar o bypass de mídia a não ser que sua organização releve seus endereços IP de rede internos para o provedor de tronco SIP.

> [!NOTE]  
> O bypass de mídia não irá interoperar com cada gateway PSTN, IP-PBX e SBC. A Microsoft testou um conjunto de gateways PSTN e SBCs com parceiros certificados e fez alguns testes com IP-PBXs da Cisco. O bypass de mídia é suportado apenas com produtos e versões listados no Programa de Interoperabilidade Aberta do Unified Communications – Lync Server em <a href="http://go.microsoft.com/fwlink/p/?linkid=214406">http://go.microsoft.com/fwlink/p/?linkId=214406</a>.

Esta seção descreve como habilitar o bypass de mídia para reduzir o processamento necessário do Servidor de Mediação. Antes de habilitar o bypass de mídia, certifique-se de que seu ambiente cumpre as condições exigidas para suportar o bypass de mídia, conforme descrito em [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md) na documentação de Planejamento. Também certifique-se de usar a informação em [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md) para decidir se deseja habilitar as configurações globais do bypass de mídia para sempre do bypass no Servidor de Mediação ou para usar as informações de site e região ao determinar o bypass do Servidor de Mediação.

Se você já configurou opcionalmente o controle de admissão de chamada (CAC), outro recurso do Enterprise Voice avançado, observe que a reserva de largura de banda realizada pelo controle de admissão de chamada não é aplicada a qualquer chamada na qual o bypass de mídia é implantado. A verificação se a implantação do bypass de mídia é realizado primeiro e se o bypass de mídia é implantado, o controle de admissão de chamada não é usado para a chamada; apenas se a verificação do bypass de mídia falhar, a verificação é realizada para o controle de admissão de chamada. Os dois recursos são mutuamente exclusivos para qualquer chamada roteada para o PSTN. Esta é a lógica porque o bypass de mídia assume que as restrições de largura de banda não existam entre os pontos de extremidade de mídia em uma chamada; o bypass de mídia não pode ser realizado em links com largura de banda restrita. Como resultado, um dos seguintes serão aplicados em uma chamada PSTN: a) a mídia ignora o Servidor de Mediação e o controle de admissão de chamada não reserva largura de banda para a chamada; ou b) o controle de admissão de chamada aplica a reserva de banda larga para a chamada e a mídia é processada pelo Servidor de Mediação envolvido na chamada.

## Próximas etapas: Habilitar o bypass de mídia na conexão de tronco

Após definir as configurações iniciais para a conectividade PSTN (planos de discagem, políticas de voz, registros de uso PSTN, roteamento de chamada de saída e regras de conversão), inicie o processo habilitando o bypass de mídia usando as etapas em [Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md).

## Consulte Também

#### Tarefas

[Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Configurar o bypass de mídia para sempre ignorar o Servidor de Mediação](lync-server-2013-configure-media-bypass-to-always-bypass-the-mediation-server.md)  
[Definir as configurações globais de bypass de mídia para usar informações locais e da região](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md)  

#### Conceitos

[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)  

#### Outros Recursos

[Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

