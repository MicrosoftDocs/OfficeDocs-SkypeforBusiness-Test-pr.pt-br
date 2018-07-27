---
title: 'Lync Server 2013: Configurações de rede para recursos avançados do Enterprise Voice'
TOCTitle: Configurações de rede para recursos avançados do Enterprise Voice
ms:assetid: 7f6de9e4-c8a4-44e4-8d14-21fe8c45283a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398637(v=OCS.15)
ms:contentKeyID: 49307256
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações de rede para recursos avançados do Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-10_

O Lync Server tem três recursos avançados do Enterprise Voice: serviço de controle de admissão de chamadas (CAC), serviços de emergência (E9-1-1) e desvio de mídia. Esses recursos compartilham determinados requisitos de configuração para regiões de rede, sites de rede e associação de cada sub-rede na topologia do Lync Server com um site de rede. Para obter detalhes sobre o planejamento da implantação desses recursos, consulte:

  - [Planejamento para controle de admissão de chamada no Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md)

  - [Planejamento para serviços de emergência (E9-1-1) no Lync Server 2013](lync-server-2013-planning-for-emergency-services-e9-1-1.md)

  - [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

Para obter mais detalhes sobre a implantação de cada um desses recursos, consulte "[Implantando recursos avançados de Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)" na documentação de implantação.

Este tópico fornece uma visão geral dos requisitos de configuração que são comuns aos três recursos avançados da Enterprise Voice.

## Regiões de Rede

Uma região de rede é um hub de rede ou backbone de rede usada somente na configuração do serviço de controle de admissão de chamadas (CAC), E9-1-1 e bypass de mídia.

> [!NOTE]  
> As regiões de rede não são as mesmas que as regiões de conferência de discagem do Lync Server, que são necessárias para associar os números de de conferência de discagem com um ou mais planos de discagem do Lync Server. Para obter detalhes sobre as regiões de conferência de discagem, consulte &quot;<a href="lync-server-2013-dial-in-conferencing-requirements.md">Exigências da conferência discada no Lync Server 2013</a>&quot; na documentação de Planejamento.

O CAC requer que cada região de rede tenha um tipo de site central do Lync Server associado, que gerencia o tráfego de mídia dentro da região (ou seja, toma decisões com base em políticas que você configurou sobre se uma sessão de vídeo ou áudio em tempo real pode ou não ser estabelecida). Os sites centrais do Lync Server não representam localizações geográficas, mas grupos lógicos de servidores configurados como um pool ou um conjunto de pools. Para obter detalhes sobre os sites centrais, consulte "[Topologias de referência no Lync Server 2013](lync-server-2013-reference-topologies.md)" na documentação de Planejamento. Consulte também "[Topologias suportadas no Lync Server 2013](lync-server-2013-supported-topologies.md)" na documentação de Suporte.

Para configurar uma região de rede, você pode usar a guia **Regiões** na seção **Configuração de Rede** do Painel de Controle do Lync Server, ou executar os cmdlets **New-CsNetworkRegion** ou **Set-CsNetworkRegion**Shell de Gerenciamento do Lync Server. Para obter instruções, consulte "[Criar ou modificar uma região de rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-region.md)" na documentação de Implantação, ou consulte a documentação do Shell de Gerenciamento do Lync Server.

As mesmas definições de região de rede são compartilhadas por todos os três recursos avançados do Enterprise Voice. Se você já criou áreas de rede para um recurso, não será necessário criar novas regiões de rede para outros recursos. No entanto, pode ser necessário modificar uma definição de região de rede existente para aplicar as configurações específicas do recurso. Por exemplo, se você criou áreas de rede para E9-1-1 (que não requer um site central associado) e posteriormente implantou o serviço de controle de admissão de chamadas, é necessário modificar cada uma das definições de região de rede para especificar um site central.

Para associar um site central do Lync Server com uma região de rede, especifique o nome do site central usando a seção **Configuração de Rede** dos cmdlets Painel de Controle do Lync Server, ou executando os cmdlets **New-CsNetworkRegion** ou **Set-CsNetworkRegion**Shell de Gerenciamento do Lync Server. Para obter instruções, consulte "[Criar ou modificar uma região de rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-region.md)" na documentação de Implantação, ou consulte a documentação do Shell de Gerenciamento do Lync Server.

## Sites de rede

Um site de rede representa uma localização geográfica, como um escritório principal, filiais ou regionais. Cada site de rede deve ser associado a uma região específica de rede.

> [!NOTE]  
> Os sites de rede são usados somente pelos recursos avançados da Enterprise Voice. Eles não são os mesmos sites de filial que você pode configurar na topologia do Lync Server. Para obter detalhes sobre os sites de filial, consulte &quot;<a href="lync-server-2013-reference-topologies.md">Topologias de referência no Lync Server 2013</a>&quot; na documentação de Planejamento. Consulte também <a href="lync-server-2013-supported-topologies.md">Topologias suportadas no Lync Server 2013</a> na documentação de Suporte.

Para configurar um site de rede e associá-lo a uma região de rede, você poderá usar a seção **Configuração de Rede** do Painel de Controle do Lync Server, ou executar os cmdlets Shell de Gerenciamento do Lync Server**New-CsNetworkSite** ou **Set-CsNetworkSite**. Para obter detalhes, consulte [Criar ou modificar um site da rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-site.md) na documentação de Implantação, ou consulte a documentação do Shell de Gerenciamento do Lync Server.

## Identifique as subredes IP

Para cada site de rede, você precisará trabalhar com seu administrador de rede para determinar quais subredes IP são atribuídas a cada site de rede. Se seu administrador de rede já organizou as subredes IP em regiões de rede e sites de rede, seu trabalho fica muito mais simples.

No exemplo, o site de Nova York na região da América do Norte pode ser atribuído às seguintes sub-redes IP: 172.29.80.0/23, 157.57.216.0/25, 172.29.91.0/23, 172.29.81.0/24. Suponha que Bob, que geralmente trabalha em Detroit, viaja para o escritório de Nova York para treinamento. Quando ele liga o computador e se conecta à rede, seu computador terá um endereço IP em um dos quatro intervalos alocados para Nova York, por exemplo 172.29.80.103.


> [!WARNING]
> As subredes IP especificadas durante a configuração de rede no servidor devem corresponder ao formato oferecido por computadores clientes para poder ser usado adequadamente pelo bypass de mídia. Um cliente do Lync leva seu endereço IP local e mascara o endereço IP com a máscara de subrede associada. Ao determinar o ID de bypass associado com cada cliente, o Registrador irá comprar a lista de subredes IP associadas com cada local de rede na subrede oferecida pelo cliente para uma correspondência exata. Por este motivo, é importante que as subredes inseridas durante a configuração de rede no servidor sejam subredes reais ao invés de subredes virtuais. (Se você implantar o controle de admissão de chamada, mas não o bypass de mídia, o controle de admissão de chamada funcionará mesmo se você configurar as subredes virtuais.)<BR>Por exemplo, se um cliente Lync faz logon em um computador com um endereço IP de 172.29.81.57, uma máscara de subrede IP de 255.255.255.0, ele irá solicitar o ID de bypass associado com a subrede 172.29.81.0. Se a subrede é definida como 172.29.0.0/16, embora o cliente pertença à subrede virtual, o Registrador não irá considerar uma correspondência porque ele está procurando especificamente pela subrede 172.29.81.0. Portanto, é importante que o administrador insira subredes exatamente conforme fornecidos pelos Lync clientes (que são provisionados com subredes durante a configuração de rede estática ou por DCE.)



## Associando Subredes aos Locais de Rede

Cada subrede na rede corporativa deve ser associado um site de rede (ou seja, cada sub-rede deve ser associado a uma localização geográfica). Essa associação de sub-redes permite que os recursos avançados Enterprise Voice da Enterprise Voice localizem de forma efetiva os pontos de extremidade geograficamente. Por exemplo, localizar os pontos de extremidade permite que CAC regule o fluxo de áudio e dados de vídeo em tempo real indo e voltando do local de rede.

Para associar subredes aos sites de rede, você pode usar a seção **Configuração de Rede** do Painel de Controle do Lync Server ou pode executar o Shell de Gerenciamento do Lync Server. Para obter instruções, consulte [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md) na documentação de Implantação, ou consulte a documentação Shell de Gerenciamento do Lync Server.

## Consulte Também

#### Outros Recursos

[Planejamento para controle de admissão de chamada no Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md)  
[Planejamento para serviços de emergência (E9-1-1) no Lync Server 2013](lync-server-2013-planning-for-emergency-services-e9-1-1.md)  
[Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

