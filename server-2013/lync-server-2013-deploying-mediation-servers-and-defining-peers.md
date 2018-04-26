---
title: 'Lync Server 2013: Implantando Servidores de Mediação e definindo pares'
TOCTitle: Implantando Servidores de Mediação e definindo pares
ms:assetid: a684f1da-6671-4011-adf6-2db49e2528e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412780(v=OCS.15)
ms:contentKeyID: 49307707
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando Servidores de Mediação e definindo pares no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

A carga de trabalho do Enterprise Voice, conferência discada e aplicativos avançados do Enterprise Voice ( Aplicativo Grupo de Resposta, Aplicativo de Estacionamento de Chamada, controle de admissão de chamada (CAC), etc.), estão disponíveis no Pools de Front-Ends. Com o Lync Server 2013, a funcionalidade do Servidor de Mediação está integrada no Servidor Front-End. Um Servidor de Mediação separado e autônomo não é mais necessário. Os Pools de Front-Ends podem se comunicar diretamente com gateways separados (um gateway de Rede Telefônica Pública Comutada (PSTN) ou um IP-PBX), removendo a necessidade do Servidor de Mediação em servir como um intermediário.

A única exceção é se você configurar um tronco SIP para se conectar a um Controlador de Borda de Sessão de um Provedor de Serviços de Telefonia e Internet. Para conectar a infraestrutura do seu Enterprise Voice com seu provedor de tronco SIP, um Servidor de Mediação separado deverá ser implantado.

A conexão entre o Lync Server (o componente Servidor de Mediação em um Pool de Front-Ends ou Servidor de Mediação autônomo) e um gateway é definido como uma associação lógica chamada de *tronco* . Os tópicos nesta seção descrevem como definir um tronco e como implantar um Servidor de Mediação autônomo, se você se conectar a um tronco SIP.

## Nesta seção

  - [Definir um Servidor de Mediação no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-a-mediation-server-in-topology-builder.md)

  - [Definir um gateway no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-a-gateway-in-topology-builder.md)

  - [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md)

  - [Definir troncos adicionais no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-additional-trunks-in-topology-builder.md)

## Seções relacionadas

[Configurando conferência discada no Lync Server 2013](lync-server-2013-configuring-dial-in-conferencing.md)

