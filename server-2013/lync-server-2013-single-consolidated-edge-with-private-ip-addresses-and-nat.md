---
title: 'Lync Server 2013: Única borda consolidada com endereços IP privados e NAT'
TOCTitle: Única borda consolidada com endereços IP privados e NAT
ms:assetid: e1e5189e-f17d-45e9-b177-e0e6f97f8951
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399001(v=OCS.15)
ms:contentKeyID: 49308380
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Única borda consolidada com endereços IP privados e NAT no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Se a sua organização requer suporte para menos de 15.000 conexões de cliente do serviço de Borda de Acesso, 1.000 conexões de cliente ativas do serviço de conferência da Web do Lync Server e 500 sessões de borda A/V simultâneas, e a alta disponibilidade do Servidor de Borda não for importante, esta topologia oferece vantagens de custo de hardware mais baixo e implantação mais simples. Se você precisar de mais capacidade ou alta disponibilidade, precisará implantar a topologia de Servidor de Borda Consolidada Dimensionada. Para obter detalhes, consulte Reference Architecture 2: Scaled Consolidated Edge (DNS Load Balanced).

   [Borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

   [Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

   [Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md)

O guia não mostra o Diretores, uma função do servidor opcional implantada na rede interna entre o Servidores de Borda e seu Pools de Front-Ends ou servidor. Para obter detalhes sobre a topologia para Diretores, consulte [Componentes necessários para o diretor no Lync Server 2013](lync-server-2013-components-required-for-the-director.md). A figura representa um único proxy reverso.

> [!NOTE]  
> A figura mostrada é para orientação e exemplo de endereço IP, mas não é destinada a representar os fluxos de comunicação reais com o tráfego de entrada e saída corretos. A figura representa um alto nível de exibição do possível tráfego. Detalhes para fluxo de tráfego conforme eles pertencem à entrada (portas do ouvinte) e saída (servidores de destino ou clientes) é representado no diagrama de Resumo da porta em cada cenário. Por exemplo, o TCP 443 é realmente apenas entrada (para o proxy reverso ou Borda) e é apenas um fluxo de duas vias por uma perspectiva de protocolo (TCP). Além disso, a figura mostra a natureza do tráfego conforme muda quando o NAT ocorre (endereço de destino é alterado na entrada, endereço de origem é alterado na saída). Exemplo de firewall externo e interno e interfaces do servidor são mostrados apenas para fins de referência. Por fim, o exemplo de gateway padrão e relações de rota são mostrados, onde aplicável. Observe também que o diagrama usa a zona DNS <em>.com</em> para representar a zona DNS externa para o proxy reverso e Servidores de Borda, e a zona DNS <em>.net</em> refere-se à zona DNS interna.

Novo no Microsoft Lync Server 2013 é o suporte para endereço IPv6. Parecido com o endereço IPv4, os endereços IPv6 devem ser atribuídos de forma que os endereços façam parte do seu espaço de endereço IPv6 atribuído. Os endereços neste tópico são apenas para exemplo. Você deve adquirir endereços IPv6 que irão funcionar na sua implantação, ofereça o escopo correta e irá interoperar com endereço interno e externo. O Windows Server oferece um recurso importante para operação IPv6 transicional e comunicação de IPv4 para IPv6 chamada *pilha dupla* . A pilha dupla é uma pilha de rede distinta e separada para IPv4 e IPv6. A pilha dupla permite atribuir endereço para IPv4 e IPv6 simultaneamente e permite o servidor se comunicar com outros hosts e clientes baseados em seus requisitos.

Tipos de endereço comuns que você usará para endereço IPv6 serão os endereços globais IPv6 (semelhante aos endereços IPv4 públicos), endereços locais únicos IPv6 (semelhante aos intervalos de endereço IPv4 privado) e endereços de link local IPv6 (semelhantes aos endereços IP privados automáticos no Windows Server para IPv4)

NAT para IPv6 existe que permite o NAT IPv6 para IPv4 (geralmente chamado como NAT64) e NAT IPv6 para IPv6 (geralmente chamado como NAT66). A existência de tecnologias NAT significa que os cinco cenários apresentados para o Lync ServerServidores de Borda ainda são válidos.


> [!WARNING]
> IPv6 é um tópico complexo e exige planejamento cuidadoso com sua equipe de rede e seu provedor de Internet para garantir que os endereços atribuídos no nível do servidor Windows e no nível do Lync Server 2013 funcionarão como esperado. Consulte os links no final deste tópico para obter recursos adicionais no endereço IPv6 e planejamento.



**Topologia de borda consolidada única**

![Topologia de borda consolidada única](images/Gg399001.d9b889c1-587c-4732-9b68-841186ccff78(OCS.15).jpg "Topologia de borda consolidada única")

> [!IMPORTANT]  
> Se estiver usando CAC, você ainda deve atribuir endereços IPv4 para a interface interna do Servidor de Borda. O CAC usa endereços IPv4 e você deve disponibilizá-los para operar.

## Nesta seção

  - [Resumo de certificado - única borda consolidada com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-certificate-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)

  - [Resumo de porta - única borda consolidada com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-port-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)

  - [Resumo de DNS - única borda consolidada com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-dns-summary-single-consolidated-edge-with-private-ip-addresses-using-nat.md)

## Consulte Também

#### Outros Recursos

[Arquitetura de endereço IP versão 6](http://tools.ietf.org/html/rfc4291)  
[Formato de endereço unicast global IPv6](http://tools.ietf.org/html/rfc3587)  
[Endereços unicast IPv6 locais exclusivos](http://tools.ietf.org/html/rfc4193)

