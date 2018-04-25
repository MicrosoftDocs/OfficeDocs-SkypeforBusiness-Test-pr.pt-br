---
title: 'Lync Server 2013: Sites'
TOCTitle: Sites
ms:assetid: 022cb6dd-37e2-4882-a53e-5ddfdbc6f53a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398076(v=OCS.15)
ms:contentKeyID: 49305679
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Sites do Lync Server no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-16_

Em Lync Server, você define *sites* na rede que inclui os componentes do Lync Server Um site é um conjunto de computadores bem conectados por uma rede de alta velocidade e baixa latência, como uma única rede local (LAN) ou duas redes conectadas por uma rede de fibra óptica de alta velocidade. Observe que Lync Server o conceito de sites do Serviços de Domínio Active Directory é diferente do sites Microsoft Exchange Server Seu sites do Lync Server não precisam corresponder aos sites do Active Directory.

## Tipos de Site

Cada site pode ser um *site central* , que contém ao menos um Pool de Front-Ends ou um Servidor Standard Edition, ou um *site de filial* . Cada site de filial é associado com exatamente um site central e os usuários no site de filial conseguem a maior parte de sua funcionalidade Lync Server dos servidores do site central associado.

Cada site de filial contem ao menos um dos seguintes:

  - Um *Aparelho de Filial Persistente (SBA)* , que é um blade server padrão da indústria com um Registrador Lync Server e um Servidor de Mediação sendo executados em Windows Server. O Aparelho de Filial Persistente também contém um gateway de rede telefônica comutada pública (PSTN). O Aparelho de Filial Persistente foi projetado para sites de filial com 25 a 1000 usuários.

  - Um *Servidor de Filial Persistente (SBS)* , um servidor executando Windows Server que atende a requisitos de hardware específicos e no qual foram instalados os softwares de Registrador Lync Server e de Servidor de Mediação. Ele deve se conectar ao gateway PSTN ou tronco SIP para um provedor de serviço telefônico. O Servidor de Filial Sustentável foi projetado para sites de filial com 1000 a 5000 usuários.

  - Um gateway PSTN e opcionalmente um *Servidor de Mediação* . Para detalhes sobre esta e outras funções de servidor, consulte [Funções do servidor no Lync Server 2013](lync-server-2013-server-roles.md).

Uma filial com um link WAN (rede de longa distância) resiliente à um site central pode usar a terceira opção, um gateway PSTN e, opcionalmente, um Servidor de Mediação. Sites de filial com links menos resilientes devem usar um Aparelho de Filial Persistente ou Servidor de Filial Persistente, que oferece resiliência durante falhas da rede de longa distância. Por exemplo, em um site com um Aparelho de Filial Persistente ou Servidor de Filial Persistente implantado, os usuários ainda podem fazer e receber chamadas do Enterprise Voice se a WAN que conecta o site de filial ao site central estiver inoperante. Para detalhes sobre o Aparelho de Filial Persistente, Servidor de Filial Persistente e resiliência, consulte [Planejamento para resiliência do Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md) na documentação de Planejamento.

## Topologias de Site

Sua implantação deve incluir ao menos um site central e pode incluir de nenhum a muitos sites de filial. Cada site de filial é afiliado a um site central. O site central fornece os serviços Lync Server ao site de filial que não estão hospedados localmente no site de filial, como presença e conferência.

Se você possuir vários sites, pode pareá-los juntos nos pools de Front End em diferentes sites para ativar as capacidades de recuperação de desastres. Para detalhes, consulte [Suporte à alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-high-availability-and-disaster-recovery-support.md).

## Consulte Também

#### Conceitos

[Funções do servidor no Lync Server 2013](lync-server-2013-server-roles.md)  
[Suporte à alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-high-availability-and-disaster-recovery-support.md)  

#### Outros Recursos

[Planejamento para resiliência do Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md)

