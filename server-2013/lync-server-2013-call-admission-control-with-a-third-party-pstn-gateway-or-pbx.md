---
title: 'Lync Server 2013: Controle de admissão de chamada com um gateway de PSTN de terceiros ou PBX'
TOCTitle: Controle de admissão de chamada com um gateway de PSTN de terceiros ou PBX
ms:assetid: 95dc4ceb-bcad-48ee-86ec-af911727f853
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398762(v=OCS.15)
ms:contentKeyID: 49307517
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Controle de admissão de chamada no Lync Server 2013 com um gateway de PSTN de terceiros ou PBX

 

_**Tópico modificado em:** 2012-10-20_

Este tópico descreve exemplos de como o controle de admissão de chamada (CAC) pode ser implantado no link entre a interface do gateway do Servidor de Mediação e um gateway de PSTU ou PBX de terceiros.

## Caso 1: CAC entre o Servidor de Mediação e um gateway PSTN

O CAC pode ser implantado no link WAN da interface do gateway do Servidor de Mediação para um PBX de terceiros ou gateway PSTN.

**Caso 1: CAC entre o Servidor de Mediação e um gateway PSTN**

![Caso 1: CAC entre o Gateway PSTN do servidor de mediação](images/Gg398762.4bebf9ee-2732-4ea6-bbe5-0269b2903d8c(OCS.15).jpg "Caso 1: CAC entre o Gateway PSTN do servidor de mediação")

Neste exemplo, o CAC é aplicado entre o Servidor de Mediação e um gateway PSTN. Se um usuário cliente do Lync no Local de Rede 1 fizer uma chamada PSTN através do gateway PSTN para o Local de Rede 2, a mídia fluirá pelo link WAN. Portanto, duas verificações CAC são executadas para cada sessão PSTN:

  - Entre o aplicativo cliente do Lync e o Servidor de Mediação

  - Entre o Servidor de Mediação e o gateway PSTN

Isto funciona para as chamadas PSTN de entrada para um cliente no Local de Rede 1 e para chamadas PSTN de saída provenientes de um aplicativo cliente no Local de Rede 1.

> [!NOTE]  
> Certifique-se de que a sub-rede do IP ao qual o gateway PSTN pertence está configurada e associada ao Local de Rede 2.<br />Certifique-se de que a sub-rede do IP à qual ambas as interfaces do Servidor de Mediação pertencem está configurada e associada ao Local de Rede 1.<br />Para obter detalhes, consulte <a href="lync-server-2013-associate-a-subnet-with-a-network-site.md">Associar uma subrede a um site de rede no Lync Server 2013</a>.

## Caso 2: CAC entre o Servidor de Mediação e um PBX de terceiros com Ponto de Terminação de Mídia

Esta configuração é similar ao Caso 1. Em ambos os casos, o Servidor de Mediação sabe qual dispositivo termina mídia no ponto oposto do link WAN e o endereço IP do gateway PSTN ou PBX com Ponto de Terminação de Mídia (MTP) está configurado no Servidor de Mediação como próximo salto.

**Caso 2: CAC entre o Servidor de Mediação e um PBX de terceiros com MTP**

![Caso 2: CAC entre o PBX do servidor de mediação com MTP](images/Gg398762.1c0b5263-c053-4cca-842f-85dd670760c8(OCS.15).jpg "Caso 2: CAC entre o PBX do servidor de mediação com MTP")

Neste exemplo, o CAC é aplicado entre o Servidor de Mediação e o PBX/MTP. Se um usuário cliente do Lync no Local de Rede 1 fizer uma ligação PSTN através do PBX/MTP localizado no Local de Rede 2, a mídia flui através do link WAN. Portanto, para cada sessão PSTN duas verificações CAC são executadas:

  - Entre o aplicativo cliente do Lync e o Servidor de Mediação

  - Entre o Servidor de Mediação e o PBX/MTP

Isto funciona para ambas, chamadas PSTN de entrada para um cliente no Local de Rede 1 e chamadas PSTN de saída provenientes de um cliente no Local de Rede 1.

> [!NOTE]  
> Certifique-se de que a sub-rede do IP à qual o MTP pertence está configurada e associada ao Local de Rede 2.<br />Certifique-se de que a sub-rede do IP à qual ambas as interfaces do Servidor de Mediação pertencem está configurada e associada ao Local de Rede 1.<br />Para obter detalhes, consulte <a href="lync-server-2013-associate-a-subnet-with-a-network-site.md">Associar uma subrede a um site de rede no Lync Server 2013</a>.

## Caso 3: CAC entre o Servidor de Mediação e um PBX de terceiros sem um Ponto de Terminação de Mídia

O Caso 3 é um ligeiramente diferente dos dois primeiros. Se não houver MTP no PBX de terceiros para uma solicitação de sessão de saída para o PBX de terceiros, o Servidor de Mediação não saberá onde a mídia terminará no limite do PBX. Neste caso, a mídia flui diretamente entre o Servidor de Mediação e o dispositivo de ponto de extremidade de terceiros.

**Caso 3: CAC entre o Servidor de Mediação e um PBX de terceiros sem MTP**

![Caso 3: CAC entre o PBX do servidor de mediação no MTP](images/Gg398762.f4bcf800-3a68-4037-bb3f-adb2fdf50d32(OCS.15).jpg "Caso 3: CAC entre o PBX do servidor de mediação no MTP")

Neste exemplo, se um usuário cliente do Lync no Local de Rede 1 fizer uma ligação para um usuário através do PBX, o Servidor de Mediação consegue realizar verificações CAC somente no trecho de proxy (entre o aplicativo cliente do Lync e o Servidor de Mediação). Como o Servidor de Mediação não tem informações sobre o dispositivo de ponto de extremidade enquanto a sessão está sendo solicitada, verificações CAC não podem ser executadas no link WAN (entre o Servidor de Mediação e um ponto de extremidade de terceiros) antes do estabelecimento da chamada. Depois que a sessão é estabelecida, no entanto, o Servidor de Mediação facilita na contabilização da largura de banda usada no tronco.

Para chamadas provenientes do ponto de extremidade de terceiros, a informação sobre este dispositivo está disponível no momento da solicitação da sessão e a verificação CAC pode ser executada em ambos os lados do Servidor de Mediação.

> [!NOTE]  
> Certifique-se de que a sub-rede do IP à qual os dispositivos de ponto de extremidade pertencem está configurada e associada ao Local de Rede 2.<br />Certifique-se de que a sub-rede do IP à qual ambas as interfaces do Servidor de Mediação pertencem está configurada e associada ao Local de Rede 1.<br />Para obter detalhes, consulte <a href="lync-server-2013-associate-a-subnet-with-a-network-site.md">Associar uma subrede a um site de rede no Lync Server 2013</a>.
