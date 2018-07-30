---
title: 'Lync Server 2013: Borda consolidada em escala com balanceadores de carga de hardware'
TOCTitle: Borda consolidada em escala com balanceadores de carga de hardware
ms:assetid: 6783e225-9677-415a-8731-0bf2e2c4cf8b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398478(v=OCS.15)
ms:contentKeyID: 49306958
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Na topologia do Pool de borda, dois ou mais Servidores de Borda são implantados como um pool com balanceamento de carga na rede de perímetro do data center. O balanceamento de carga de hardware é usado para tráfego nas interfaces interna e externa do Servidor de Borda.

Se sua organização precisar de suporte a mais de 15 mil conexões de cliente do Serviço de Borda de Acesso, mil conexões de cliente do Serviço de Borda de Webconferência ativas ou 500 sessões simultâneas do Serviço de Borda A/V, e a alta disponibilidade do Servidor de Borda for importante, essa topologia oferecerá as vantagens do suporte a escalabilidade e o failover.

A figura não mostra Diretores, uma função de servidor opcional implantada na rede interna entre os Servidores de Borda e seus Pools de Front-Ends ou servidor. Para obter detalhes sobre a topologia para Diretores, consulte [Componentes necessários para o diretor no Lync Server 2013](lync-server-2013-components-required-for-the-director.md).

> [!NOTE]  
> A figura mostrada tem fins de orientação e exemplificação do endereçamento IP, mas não representa fluxos reais de comunicação com o tráfego de entrada e saída correto. A figura representa uma visão geral do tráfego possível. Detalhes do fluxo de tráfego e se são de entrada (para as portas de escuta) e saída (para os servidores ou clientes de destino) são representados no diagrama Resumo de Portas em cada cenário. Por exemplo, TCP 443 é somente de entrada (para o Servidor de Borda ou o proxy reverso) e só é um fluxo bidirecional do ponto de vista do protocolo (TCP). Além disso, a figura mostra a natureza do tráfego à medida que muda quando a NAT (conversão de endereços de rede) ocorre (o endereço de destino é alterado na entrada e o endereço de origem é alterado na saída). O firewall externo e interno e interfaces de servidor de exemplo são mostrados somente para fins de referência. Por fim, um gateway padrão e relações de rota de exemplo são mostrados quando aplicável. Observe também que o diagrama usa a zona DNS <em>.com</em> para representar a zona DNS externa para o proxy reverso e o Servidores de Borda, assim como a zona DNS <em>.net</em> refere-se à zona DNS interna.

Novo no Microsoft Lync Server 2013 é o suporte para endereço IPv6. Parecido com o endereço IPv4, os endereços IPv6 devem ser atribuídos de forma que os endereços façam parte do seu espaço de endereço IPv6 atribuído. Os endereços neste tópico são apenas para exemplo. Você deve adquirir endereços IPv6 que irão funcionar na sua implantação, ofereça o escopo correta e irá interoperar com endereço interno e externo. O Windows Server oferece um recurso importante para operação IPv6 transicional e comunicação de IPv4 para IPv6 chamada *pilha dupla* . A pilha dupla é uma pilha de rede distinta e separada para IPv4 e IPv6. A pilha dupla permite atribuir endereço para IPv4 e IPv6 simultaneamente e permite o servidor se comunicar com outros hosts e clientes baseados em seus requisitos.

Tipos de endereço comuns que você usará para endereço IPv6 serão os endereços globais IPv6 (semelhante aos endereços IPv4 públicos), endereços locais únicos IPv6 (semelhante aos intervalos de endereço IPv4 privado) e endereços de link local IPv6 (semelhantes aos endereços IP privados automáticos no Windows Server para IPv4)

NAT para IPv6 existe que permite o NAT IPv6 para IPv4 (geralmente chamado como NAT64) e NAT IPv6 para IPv6 (geralmente chamado como NAT66). A existência de tecnologias NAT significa que os cinco cenários apresentados para o Lync ServerServidores de Borda ainda são válidos.


> [!WARNING]
> IPv6 é um tópico complexo e exige planejamento cuidadoso com sua equipe de rede e seu provedor de Internet para garantir que os endereços atribuídos no nível do servidor Windows e no nível do Lync Server 2013 funcionarão como esperado. Consulte os links no final deste tópico para obter recursos adicionais no endereço IPv6 e planejamento.



**Configuração do balanceador de carga de hardware**

Para obter detalhes, consulte a seção “Requisitos do balanceador de carga de hardware para borda A/V” nos [Componentes obrigatórios para acesso de usuário externo no Lync Server 2013](lync-server-2013-components-required-for-external-user-access.md).

**Topologia de borda consolidada dimensionada (com balanceamento de carga de hardware)**

![Topologia de borda consolidada dimensionada](images/Gg398478.3a57cd0d-8de4-4ecc-a783-4dff5b3456a2(OCS.15).jpg "Topologia de borda consolidada dimensionada")

> [!IMPORTANT]  
> Se estiver usando CAC, você ainda deve atribuir endereços IPv4 para a interface interna do Servidor de Borda. O CAC usa endereços IPv4 e você deve disponibilizá-los para operar.

## Nesta seção

  - [Resumo de certificado - Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-certificate-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

  - [Resumo de porta - borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-port-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

  - [Resumo de DNS - borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-dns-summary-scaled-consolidated-edge-with-hardware-load-balancers.md)

## Consulte Também

#### Outros Recursos

[Arquitetura de endereço IP versão 6](http://tools.ietf.org/html/rfc4291)  
[Formato de endereço unicast global IPv6](http://tools.ietf.org/html/rfc3587)  
[Endereços unicast IPv6 locais exclusivos](http://tools.ietf.org/html/rfc4193)

