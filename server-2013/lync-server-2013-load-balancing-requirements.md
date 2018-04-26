---
title: Requisitos de balanceamento de carga para Lync Server 2013
TOCTitle: Requisitos de balanceamento de carga para Lync Server 2013
ms:assetid: 84489328-64a4-486c-9384-a3e5c8ed9c8b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615011(v=OCS.15)
ms:contentKeyID: 49307327
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de balanceamento de carga para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-05_

Se tiver os pools Pools de Front-Ends, Diretor ou Servidor de Borda, será necessário implantar o balanceamento de carga para esses pools. O balanceamento de carga distribui o tráfego entre os servidores em um pool.

O Lync Server 2013 oferece suporte a dois tipos de soluções de balanceamento de carga para tráfego do cliente para o servidor: balanceamento de carga de DNS e balanceamento de carga de hardware. O balanceamento de carga DNS oferece várias vantagens, incluindo administração mais simples, solução de problemas mais eficiente e a capacidade de isolar grande parte do tráfego do Lync Server de quaisquer possíveis problemas do balanceador de carga de hardware.

Decida que solução de balanceamento de carga é apropriada para cada pool de sua implantação, considerando as seguintes restrições:

  - A interface de Borda interna e externa devem usar o mesmo tipo de balanceamento de carga. Não é possível usar o balanceamento de carga DNS em uma interface e o balanceamento de carga de hardware em outra.

  - Alguns tipos de tráfego exigem um balanceador de carga de hardware. Por exemplo, o tráfego HTTP requer um balanceador de carga de hardware em vez do balanceamento de carga DNS. O balanceamento de carga DNS não funciona com o tráfego web de cliente-servidor.

Para obter mais detalhes sobre como escolher uma solução de balanceador de carga de hardware [Requisitos do balanceador de carga do hardware para Lync Server 2013](lync-server-2013-hardware-load-balancer-requirements.md).

Se optar por usar o balanceamento de carga DNS para um pool, mas ainda for necessário implementar balanceadores de carga de hardware para o tráfego, como o tráfego HTTP, a administração dos balanceadores de carga de hardware é bastante simplificada. Por exemplo, a configuração do balanceador de carga de hardware será mais simples, pois gerenciará somente os tráfegos HTTP e HTTPS enquanto os demais protocolos serão gerenciados pelo balanceamento de carga DNS. Para obter detalhes, consulte [Balanceamento de carga DNS no Lync Server 2013](lync-server-2013-dns-load-balancing.md).

Para o tráfego entre sevidores, o Lync Server 2013 usa o balanceamento de carga por topologia. Os servidores leem a topologia publicada em Repositório de Gerenciamento Central para obter os FQDNs dos servidores na topologia e automaticamente distribui o tráfego entre os servidores. Os administradores não precisam configurar nem gerenciar esse tipo de balanceamento de carga.

Se estiver usando o balanceamento de carga DNS e for necessário bloquear o tráfego de um computador específico, não basta remover as entradas do endereço IP do FQDN do pool. É necessário remover também a entrada de DNS do computador.

