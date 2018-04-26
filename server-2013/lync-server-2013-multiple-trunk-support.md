---
title: 'Lync Server 2013: Suporte a vários troncos'
TOCTitle: Suporte a vários troncos
ms:assetid: a1309c09-ad9a-4c54-9650-4e3f5b2a4a00
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205127(v=OCS.15)
ms:contentKeyID: 49307650
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a vários troncos no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

A funcionalidade Lync Server 2013 suporta várias associações entre gateways e Servidor de Mediação. Essas associações são feitas definindo-se um tronco, que é uma associação lógica entre um Pool do servidor de mediação e um gateway de rede de telefone (PSTN), Controlador de Borda de Sessão (SBC), ou IP-PBX. Use o Construtor de Topologias para associar gateways com Servidores de mediação (isto é, troncos).

  - Para atribuir ou remover um tronco no Lync Server 2013 é necessário primeiramente definir um tronco no Construtor de Topologias. Um tronco consiste da seguinte associação: nome de domínio totalmente qualificado (FQDN) do Servidor de Mediação, a porta de escuta do Servidor de Mediação o FQDN do gateway e a porta de escuta do gateway.

  - Para configurar vários troncos, é possível criar várias associações entre o mesmo gateway e o Servidor de Mediação. Isso fornece resiliência adicional à infraestrutura do Enterprise Voice, que é especialmente útil em cenários de interoperações de PBX (private branch exchange).

Quando um tronco é definido, ele precisa ser associado à rota. Para associar um tronco a uma rota, defina um nome simples para o tronco no Construtor de Topologias. Esse nome simples é usado como o nome do tronco no Painel de Controle do Lync Server, onde os troncos podem ser associados com rotas. O nome simples do tronco é usado como nome de gateway do Shell de Gerenciamento do Lync Server.

    New-CsVoiceRoute -Identity <RouteId> -NumberPattern <String> -PstnUsages @{add="<UsageString>"} -PstnGatewayList @{add="<TrunkSimpleName>"}

O administrador deve selecionar um tronco padrão associado ao Servidor de Mediação. Em Construtor de Topologias, clique com o botão direito o Servidor de Mediação associado, e depois em **Propriedades** . Especifique o gateway padrão do Servidor de Mediação.

O diagrama a seguir ilustra os vários troncos que são definidos para cada Servidor de Mediação e gateway.

**Roteamento de tronco M:N**

![Atribuição de diversas árvores.](images/JJ205127.c61cd9a7-d8d9-4e02-83b9-ab62519a48c4(OCS.15).jpg "Atribuição de diversas árvores.")

