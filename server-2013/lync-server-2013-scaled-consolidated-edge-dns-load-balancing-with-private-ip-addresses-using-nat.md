---
title: 'Lync Server 2013: Borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT'
TOCTitle: Borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT
ms:assetid: c7ca4ca8-c639-4d93-86d7-8891170cacbc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398823(v=OCS.15)
ms:contentKeyID: 49308086
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Na topologia de pool de Servidores de Borda, dois ou mais Servidores de Borda são implantados como um pool com balanceamento de carga na rede de perímetro do data center. O balanceamento de carga do DNS é usado para tráfego nas interfaces de Borda internas e externas.

Se sua organização exigir o suporte para mais de 15.000 conexões cliente do serviço Borda de Acesso, 1.000 conexões ativas do cliente do serviço Webconferência do Lync Server ou 500 sessões de Borda A/V simultâneas e/ou a alta disponibilidade do Servidor de Borda for importante, essa topologia oferecerá as vantagens de escalabilidade e suporte a failover.

O guia não mostra o Diretores, uma função do servidor opcional implantada na rede interna entre o Servidores de Borda e seu Pools de Front-Ends ou servidor. Para obter detalhes sobre a topologia para Diretores, consulte [Componentes necessários para o diretor no Lync Server 2013](lync-server-2013-components-required-for-the-director.md). A figura representa um único proxy reverso.

> [!NOTE]  
> A figura mostrada é para orientação e exemplo de endereço IP, mas não é destinada a representar os fluxos de comunicação reais com o tráfego de entrada e saída corretos. A figura representa um alto nível de exibição do possível tráfego. Detalhes para fluxo de tráfego conforme eles pertencem à entrada (portas do ouvinte) e saída (servidores de destino ou clientes) é representado no diagrama de Resumo da porta em cada cenário. Por exemplo, o TCP 443 é realmente apenas entrada (para o proxy reverso ou Borda) e é apenas um fluxo de duas vias por uma perspectiva de protocolo (TCP). Além disso, a figura mostra a natureza do tráfego conforme muda quando o NAT ocorre (endereço de destino é alterado na entrada, endereço de origem é alterado na saída). Exemplo de firewall externo e interno e interfaces do servidor são mostrados apenas para fins de referência. Por fim, o exemplo de gateway padrão e relações de rota são mostrados, onde aplicável. Observe também que o diagrama usa a zona DNS <em>.com</em> para representar a zona DNS externa para o proxy reverso e Servidores de Borda, e a zona DNS <em>.net</em> refere-se à zona DNS interna.

Novo no Microsoft Lync Server 2013 é o suporte para endereço IPv6. Parecido com o endereço IPv4, os endereços IPv6 devem ser atribuídos de forma que os endereços façam parte do seu espaço de endereço IPv6 atribuído. Os endereços neste tópico são apenas para exemplo. Você deve adquirir endereços IPv6 que irão funcionar na sua implantação, ofereça o escopo correta e irá interoperar com endereço interno e externo. O Windows Server oferece um recurso importante para operação IPv6 transicional e comunicação de IPv4 para IPv6 chamada *pilha dupla* . A pilha dupla é uma pilha de rede distinta e separada para IPv4 e IPv6. A pilha dupla permite atribuir endereço para IPv4 e IPv6 simultaneamente e permite o servidor se comunicar com outros hosts e clientes baseados em seus requisitos.

Tipos de endereço comuns que você usará para endereço IPv6 serão os endereços globais IPv6 (semelhante aos endereços IPv4 públicos), endereços locais únicos IPv6 (semelhante aos intervalos de endereço IPv4 privado) e endereços de link local IPv6 (semelhantes aos endereços IP privados automáticos no Windows Server para IPv4)

NAT para IPv6 existe que permite o NAT IPv6 para IPv4 (geralmente chamado como NAT64) e NAT IPv6 para IPv6 (geralmente chamado como NAT66). A existência de tecnologias NAT significa que os cinco cenários apresentados para o Lync ServerServidores de Borda ainda são válidos.


> [!WARNING]
> IPv6 é um tópico complexo e exige planejamento cuidadoso com sua equipe de rede e seu provedor de Internet para garantir que os endereços atribuídos no nível do servidor Windows e no nível do Lync Server 2013 funcionarão como esperado. Consulte os links no final deste tópico para obter recursos adicionais no endereço IPv6 e planejamento.



![DNS LB com IP privado usando NAT](images/Gg398823.899546d4-2eef-44d2-8317-51c5f699cd2a(OCS.15).jpg "DNS LB com IP privado usando NAT")

> [!IMPORTANT]  
> Se estiver usando CAC, você ainda deve atribuir endereços IPv4 para a interface interna do Servidor de Borda. O CAC usa endereços IPv4 e você deve disponibilizá-los para operar.

## Nesta seção

  - [Resumo de certificado - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

  - [Resumo de porta - borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-port-summary-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

  - [Resumo de DNS - borda consolidada dimensionada, balanceamento de carga DNS com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-dns-summary-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

## Consulte Também

#### Outros Recursos

[Arquitetura de endereço IP versão 6](http://tools.ietf.org/html/rfc4291)  
[Formato de endereço unicast global IPv6](http://tools.ietf.org/html/rfc3587)  
[Endereços unicast IPv6 locais exclusivos](http://tools.ietf.org/html/rfc4193)

