---
title: 'Lync Server 2013: Definindo seus requisitos para Enterprise Voice'
TOCTitle: Definindo os requisitos de sua organização para Enterprise Voice
ms:assetid: 3310f78e-c658-4557-95fa-159ce3c22953
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425826(v=OCS.15)
ms:contentKeyID: 49306323
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo seus requisitos para Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2012-08-07_

Este tópico apresenta uma visão geral das considerações necessárias sobre regiões, locais e links entre locais em sua topologia e sobre como elas são importantes ao implantar o Enterprise Voice. Para obter detalhes que ajudarão a tomar essas decisões, consulte [Configurações de rede para recursos avançados do Enterprise Voice no Lync Server 2013](lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md), na documentação de planejamento.

## Sites e regiões

Primeiro, identifique os sites de sua topologia onde você implantará o Enterprise Voice e as regiões de rede às quais esses sites pertencem. Especificamente, considere como será fornecida a conectividade PSTN (rede telefônica pública comutada) a cada site. Para motivos de gerenciamento e logística, as regiões às quais esses sites pertencem podem ser um fator decisivo. Decida onde os gateways serão implantados localmente, onde os Aparelho de Filial Persistente (SBAs) serão implantados e onde é possível configurar os troncos SIP (localmente ou no site central) para um ITSP (provedor de serviço de telefonia pela Internet).

## Links de rede entre sites

Também é necessário considerar o uso de largura de banda esperado nos links de rede entre seu site central e seus site de filial. Se você tiver, ou planeja implantar, links WAN resilientes entre sites, recomendamos a implantação de um gateway em cada site de filial a fim de fornecer um término DID (discagem direta interna) local para usuários nesses sites. Se você tiver links WAN resilientes, mas a largura de banda em um link WAN provavelmente for restrita, configure o controle de admissão de chamada para esse link. Se você não tiver links WAN resilientes, hospedar menos de 1000 usuários em seu site de filial e não tiver administradores de Lync Server locais treinados e disponíveis, recomendamos a implantação de um Aparelho de Filial Persistente no site de filial. Se você hospedar entre 1000 e 5000 usuários em seu site de filial, não tiver uma conexão WAN resiliente e tiver treinadores Lync Server disponíveis, recomendamos a implantação de um Servidor de Filial Persistente com um pequeno gateway no site de filial. Considere também a habilitação de bypass de mídia em links restritos se você tiver um gateway par que suporte bypass de mídia.

## Consulte Também

#### Conceitos

[Configurações de rede para recursos avançados do Enterprise Voice no Lync Server 2013](lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md)

