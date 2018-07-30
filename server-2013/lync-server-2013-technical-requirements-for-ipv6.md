---
title: 'Lync Server 2013: Requisitos técnicos para IPv6'
TOCTitle: Requisitos técnicos para IPv6
ms:assetid: caff0123-ce41-4a62-87a0-00b1d118b72b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205278(v=OCS.15)
ms:contentKeyID: 49308117
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos técnicos para IPv6 no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Se você planeja configurar o Lync Server 2013 para IPv6, mantenha os seguintes requisitos em mente:

  - Para usar endereços IPv6 com o Lync Server, você precisa criar um registro DNS para registros que devem ser descobertos e resolvidos para um endereço IPv6. O DNS IPv6 usa um registros de host AAAA (quad-A). Se você usar o IPv4 e o IPv6 na sua implantação, é melhor configurar e manter os registros de host A para IPv4 e registros de host AAAA para IPv6. Mesmo quando passar totalmente sua implantação para o IPv6, você ainda pode precisar de registros de host DNS IPv4 para usuários externos que ainda usam IPv4.
    
    É possível implantar registros de host DNS IPv6 antes de iniciar a usar o IPv6. Se o cliente ou servidor não usar IPv6, o registro não será referenciado. As tecnologias transicionais tomarão a decisão sobre qual registro usar, com base na configuração de tecnologia de transição e políticas.

  - Cada endereço IPv6 possui um escopo. Os três escopos que você pode usar para endereço IPv6 são endereços IPv6 globais (semelhante aos endereços IPv4 públicos), endereços locais exclusivos IPv6 (semelhante aos intervalos de endereço IPv4 provado) e endereços de link local IPv6 (semelhantes aos endereços IP privados automáticos no Windows Server para IPv4). Todos os servidores em um pool devem ter endereços IPv6 com o mesmo escopo.

> [!IMPORTANT]  
> O IPv6 é um tópico complexo e exige planejamento cuidadoso com sua equipe de rede e seu provedor Internet para ajudar a garantir que os endereços atribuídos ao nível Windows Server e ao nível Lync Server 2013 funcionem conforme esperado. Consulte os links no final deste tópico para obter recursos adicionais sobre o endereço IPv6 e planejamento.

## Consulte Também

#### Outros Recursos

[Arquitetura de endereço IP versão 6](http://tools.ietf.org/html/rfc4291)  
[Formato de endereço unicast global IPv6](http://tools.ietf.org/html/rfc3587)  
[Endereços unicast IPv6 locais exclusivos](http://tools.ietf.org/html/rfc4193)

