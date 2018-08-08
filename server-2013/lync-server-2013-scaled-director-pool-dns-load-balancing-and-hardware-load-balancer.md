---
title: "Lync Server 2013: Pool de dir. em escala - balanceam. de carga de DNS e hardware"
TOCTitle: Pool de diretores em escala - balanceamento de carga de DNS e balanceador de carga de hardware
ms:assetid: a1f6ffc0-9e6e-4217-a923-025c9679e154
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205142(v=OCS.15)
ms:contentKeyID: 49307659
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pool de diretores em escala - balanceamento de carga de DNS e balanceador de carga de hardware no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-22_

Um Pool de diretores dimensionado, onde há mais de um Diretor implantado para lidar com a capacidade adicional e para fornecer alta disponibilidade, exige balanceamento de carga para distribuir comunicação do cliente e servidor a todos os membros do pool. Um Diretor hospeda serviços web quase da mesma maneira que um Pool de Front-Ends. Para fornecer o balanceamento de carga, você pode usar o balanceamento de carga de hardware, ou balanceamento de carga do DNS (sistema de nomes de domínio) e balanceamento de carga de hardware. O balanceamento de carga de hardware é obrigatório para serviços web e o balanceamento de carga do DNS sozinho não fornece os recursos exigidos pelos serviços web.

Os tópicos a seguir descrevem as considerações de planejamento para implantar um Pool de diretores usando balanceamento de carga de DNS junto com balanceamento de carga de hardware. Se você planeja usar o balanceamento de carga de hardware, mas não o balanceamento de carga do DNS para o Pool de diretores, consulte [Pool de diretores em escala - balanceador de carga de hardware no Lync Server 2013](lync-server-2013-scaled-director-pool-hardware-load-balancer.md), que descreve os requisitos de planejamento dessa topologia.

![Novo Pool de Diretor em Escala](images/JJ205142.35a78a7a-b781-4c8f-951e-168451ba6a65(OCS.15).jpg "Novo Pool de Diretor em Escala")

## Nesta seção

  - [Resumo de certificado - Cargas de DNS e de HLB balanceadas no Lync Server 2013](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Resumo de porta - cargas de DNS e de HLB balanceadas no Lync Server 2013](lync-server-2013-port-summary-dns-and-hlb-load-balanced.md)

  - [Resumo de DNS - Cargas de DNS e de HLB balanceadas no Lync Server 2013](lync-server-2013-dns-summary-dns-and-hlb-load-balanced.md)

