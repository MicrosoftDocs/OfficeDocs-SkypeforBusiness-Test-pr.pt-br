---
title: 'Lync Server 2013: Componentes e topologias para o Servidor de Mediação'
TOCTitle: Componentes e topologias para o Servidor de Mediação
ms:assetid: 71397168-36c3-4d21-b8ef-db6a751634ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398537(v=OCS.15)
ms:contentKeyID: 49307073
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologias para o Servidor de Mediação no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Este tópico descreve os componentes dos quais o Servidor de Mediação depende e as topologias nas quais o Servidor de Mediação pode ser implantado.

## Dependências

O Servidor de Mediação tem as seguintes dependências:

  - **Registrador.** Necessário. O Registrador é o próximo salto para a sinalização em interações do Servidor de Mediação com a rede do Lync Server 2013. Observe que o Servidor de Mediação pode ser colocado em um Servidor Front-End junto com o Registrador, além de ser instalado em um pool autônomo que consiste apenas em Servidor de Mediação. O Registrador é colocado com um Servidor de Mediação e o gateway PSTN em um Aparelho de Filial Persistente.

  - **Monitoring Server.** É opcional, mas altamente recomendável. O Servidor de Monitoramento permite que o Servidor de Mediação registre as métricas de qualidade associadas as suas sessões de mídia.

  - **Servidor de borda.** É necessário para o suporte ao usuário externo. O Servidor de Borda permite que o Servidor de Mediação interaja com os usuários que estão localizados atrás de um firewall ou NAT.

## Topologias

O Servidor de Mediação do Lync Server 2013 é por padrão colocado com uma instância de Registrador em um Servidor Standard Edition, um Pool de Front-Ends ou um Aparelho de Filial Persistente. Todos os Servidor de Mediação em um Pool de Front-Ends devem ser configurados de forma idêntica.

Onde o desempenho for um problema, pode ser preferível implantar um ou mais Servidor de Mediação em um pool independente dedicado. Ou, se você implantar o entroncamento SIP, recomendamos que implante um Pool do servidor de mediação autônomo.

Se você implantar conexões de SIP Diretas a um gateway PSTN qualificado que suporta bypass de mídia e balanceamento de carga DNS, Pool do servidor de mediação autônomo não é necessário, porque os gateways qualificados são capazes de balancear a carga DNS a um pool de Servidor de Mediação e eles podem receber o tráfego de qualquer Servidor de Mediação em um pool.

Nós também recomendamos que você coloque o Servidor de Mediação em um Pool de Front-Ends quando tiver implantado IP-PBXs ou conecte-se a um Controlador de Borda da Sessão (SBC) do Provedor do servidor de telefonia Internet, contanto que as seguintes condições sejam cumpridas:

  - O IP-PBX ou o SBC está configurado para receber tráfego de qualquer Servidor de Mediação no pool e pode direcionar o tráfego uniformemente para todos os Servidor de Mediação no pool.

  - O IP-PBX não suporta bypass de mídia, mas o Pool de Front-Ends hospedando o Servidor de Mediação pode lidar com a transcodificação de voz para chamadas nas quais o bypass de mídia não é aplicável.

É possível usar o Microsoft Lync Server 2013, Ferramenta de Planejamento para avaliar se Pool de Front-Ends onde você deseja posicionar o Servidor de Mediação pode lidar com a carga. Se o seu ambiente não pode cumprir estes requisitos, você deve implantar um Pool do servidor de mediação autônomo.

Para obter detalhes sobre que topologia implantar, consulte [Orientações de implantação para Servidor de Mediação no Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md).

A figura a seguir mostra uma topologia simples que consiste em dois sites conectados por um link WAN. O Servidor de Mediação está colocado no Registrador em um Pool de Front-Ends no Site 1. Os Servidor de Mediação no Site 1 controlam o gateway PSTN no Site 1 e o gateway no Site 2. Nesta topologia, o bypass de mídia está habilitado globalmente para usar as informações do site e da região. Os troncos para cada gateway PSTN (GW1 e GW2) têm o bypass habilitado.

**Exemplo de sites conectados por um link WAN com um Servidor de Mediação no Site 1 e um gateway PSTN no Site 2**

![Topologia de voz com Gateway WAN do servidor de mediação](images/Gg398537.67872e61-1444-447b-918c-abe89abc3004(OCS.15).jpg "Topologia de voz com Gateway WAN do servidor de mediação")

A figura a seguir mostra uma topologia simples onde o Servidor de Mediação está colocado com o Registrador no Pool de Front-Ends no Site 1 e tem uma conexão de SIP Direta para o IP-PBX no Site 1. Nessa figura, o Servidor de Mediação também controla um gateway PSTN no Site 2. Suponha que os usuários do Lync existem nos Sites 1 e 2. Suponha também que o IP-PBX possui um processador de mídia associado que deve ser percorrido por todas as mídias de pontos de extremidade do Lync antes de serem enviadas aos pontos de extremidade de mídia controlados pelo IP-PBX. Nesta topologia, o bypass de mídia está habilitado globalmente para usar as informações do site e da região. Os troncos para o gateway PBX e PSTN têm o bypass de media habilitado.

**Exemplo de sites conectados por um link WAN com um Servidor de Mediação no Site 1 e um PBX no Site 2**

![PBX WAN do servidor de mediação de topologia de voz](images/Gg398537.df6c8a5b-8431-4187-907d-ff5ca26eeeec(OCS.15).jpg "PBX WAN do servidor de mediação de topologia de voz")

Para obter detalhes sobre o planejamento para topologias de PBX, consulte [Orientações de implantação para Servidor de Mediação no Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md)e [Opções de implantação de SIP Direto no Lync Server 2013](lync-server-2013-direct-sip-deployment-options.md).

A última figura neste tópico mostra uma topologia onde o Servidor de Mediação é conectado ao SBC de um Provedor de Serviços de Telefonia. Para obter detalhes sobre as topologias de entroncamento SIP, consulte [Tronco SIP no Lync Server 2013](lync-server-2013-sip-trunking.md).

