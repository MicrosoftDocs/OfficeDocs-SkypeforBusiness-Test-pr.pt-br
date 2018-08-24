---
title: 'Lync Server 2013: Visão geral de bypass de mídia'
TOCTitle: Visão geral de bypass de mídia
ms:assetid: 9ea090b3-f607-46f7-97dd-2510052524e5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412740(v=OCS.15)
ms:contentKeyID: 49307629
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de bypass de mídia no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

O bypass de mídia é útil quando você deseja minimizar o número de Servidores de Mediação implantados. Geralmente, um pool de Servidores de Mediação será implantado em um site central e controlará os gateways em sites locais. Habilitar o bypass de mídia permite que a mídia para chamadas PSTN de clientes em sites locais flua diretamente pelos gateways para estes sites. As rotas da chamada de saída do Lync Server 2013 e as políticas do Enterprise Voice devem ser configuradas adequadamente para que as chamadas PSTN dos clientes em um site local seja roteadas para o gateway adequado.

As redes Wi-Fi geralmente enfrentam uma maior perda de pacotes do que as redes com fio. A recuperação desta perda de pacotes não é algo que geralmente possa ser acomodado por gateways. Assim, recomendamos a avaliação da qualidade da rede Wi-Fi antes de determinar se o bypass deve estar habilitado para uma sub-rede sem fio. Há uma compensação na redução da latência contra a recuperação da perda de pacotes a considerar. RTAudio, um codec disponível para chamadas que não ignorem o Servidor de Mediação, é mais adequado para tratar da perda de pacotes.

Após inserir a estrutura do seu Enterprise Voice, o planejamento do bypass de mídia será aberto.

  - Se você possui uma topologia centralizada sem links WAN para sites de filiais, é possível habilitar o bypass de mídia global, pois é necessário um ajuste refinado.

  - Se você não possui uma topologia distribuída que consiste de uma ou mais regiões de rede e seus sites de filiais associados, determine o seguinte:
    
      - Se os seus colegas do Servidor de Mediação podem suportar as capacidades necessárias para bypass de mídia.
    
      - Quais sites em cada região de rede estão bem conectados.
    
      - Qual combinação de bypass de mídia e controle de admissão de chamada é adequada para sua rede.

Quando o desvio de mídia é habilitado, um ID de desvio exclusivo é gerado automaticamente para uma região de rede e para todos os sites de rede sem limites de largura de banda nessa região. Os sites com limites de largura de banda na região e os sites conectados à região por links WAN com limites de largura de banda obtêm seus próprios IDs de desvio exclusivos.

Quando um usuário faz uma chamada para o PSTN, o Servidor de Mediação compara o ID do desvio da sub-rede do cliente com o ID do desvio da sub-rede do gateway. Se os dois IDs de desvio forem correspondentes, o desvio de mídia será usado para a chamada. Se os IDs de desvio não corresponderem, a mídia para a chamada deverá fluir através do Servidor de Mediação.

Quando um usuário recebe uma chamada do PSTN, o cliente do usuário compara seu ID de desvio com aquele do gateway PSTN. Se os dois IDs de desvio corresponderem, a mídia fluirá diretamente do gateway para o cliente, contornando o Servidor de Mediação.

Apenas o Lync 2010 ou os clientes e dispositivos acima suportam interações de bypass de mídia com um Servidor de Mediação.

> [!IMPORTANT]  
> Além de habilitar o bypass de mídia globalmente, é necessário habilitar o bypass de mídia individualmente em cada tronco PSTN. Se o bypass estiver habilitado globalmente, mas não estiver habilitado para um determinado tronco PSTN, o bypass de mídia não será invocado para qualquer chamada envolvendo aquele tronco PSTN. Além disso, quando o bypass de mídia é definido para <strong>Usar a informação do site e da região</strong> , é necessário associar todas as sub-redes roteáveis com os sites nos quais estão localizadas. Se há sub-redes roteáveis dentro de um site no qual o bypass não é desejado, estas sub-redes devem ser agrupadas dentro de um novo site antes de habilitar o bypass de mídia. Fazer isso garantirá que as sub-redes não roteáveis sejam atribuídas com uma ID de bypass diferente.

## Consulte Também

#### Conceitos

[Modos de bypass de mídia no Lync Server 2013](lync-server-2013-media-bypass-modes.md)  
[Bypass de mídia e controle de admissão de chamadas no Lync Server 2013](lync-server-2013-media-bypass-and-call-admission-control.md)  
[Requisitos técnicos para bypass de mídia no Lync Server 2013](lync-server-2013-technical-requirements-for-media-bypass.md)

