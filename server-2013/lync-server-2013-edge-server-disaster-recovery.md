---
title: 'Lync Server 2013: Recuperação de desastres do servidor de borda'
TOCTitle: Recuperação de desastres do servidor de borda
ms:assetid: 05ec8d26-d167-4a6f-a966-a1f8873cf974
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687960(v=OCS.15)
ms:contentKeyID: 49886089
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recuperação de desastres do servidor de borda no Lync Server 2013

 

_**Tópico modificado em:** 2014-03-12_

Assim como ocorre com outras funções de servidor, a melhor maneira de fornecer alta disponibilidade para seus Servidores de Borda é implantar múltiplos Servidores de borda em pools em cada site. Se um Servidor de Borda ficar inativo, os outros servidores no pool continuarão a fornecer serviços de Borda.

Para habilitar procedimentos de recuperação de desastre, é necessário ter pools de Servidor de Borda separados implantados em sites separados. Não é necessário parear explicitamente os pools de Borda da mesma forma que você faz com os pools Front-End, mas ter vários pools de Borda ainda fornece a disponibilidade para continuar caso um pool de Borda inteiro fique inativo. As seções a seguir fornecem detalhes sobre recuperação de desastre para as diversas funções dos Servidores de Borda.

## Acesso remoto

Se houver vários sites, cada um com um pool de servidores de Borda, e um pool de Borda inteiro falhar, os serviços de acesso remoto continuarão funcionando sem que um administrador precise agir. Ao criar pools de Borda em sites diferentes, você não poderá usar o mesmo FQDN. Cada pool de Borda deverá ter FQDNs exclusivos (interno e externo). Os pools de Borda não usam regras de publicação de proxy reverso para falar com os servidores Front End. O failover automático ocorre quando o cliente consulta novamente os registros do serviço DNS de acesso remoto e os usuários remotos são roteados para os servidores de Borda em outro local. O cliente tenta todos os FQDNs de Borda externos de acordo com a prioridade dos registros de serviidor do DNS.

> [!NOTE]  
> Para que o failover funcione corretamente, verifique se o firewall permite que os servidores Front End de cada pool se comuniquem com todos os servidores de Borda.

## Federação

Para relacionamentos de federação com outras organizações executando Lync Server, as solicitações de federação de entrada continuarão a funcionar contanto que você tenha configurado cada pool de Borda para ter uma prioridade diferente nos registros SRV. Quaisquer solicitações de federação que chegarem até um pool de Borda inativo falharão e se conectarão a um pool de Borda em execução.

A federação de saída sempre é configurada por meio de um pool de Borda ou Servidor de Borda publicado na organização. Se esse pool de Borda estiver inativo, será necessário usar o Construtor de Topologia para alterar a rota de federação de saída a fim de usar um pool de Borda que ainda está em execução. Para obter detalhes, consulte [Failover do pool de Borda usado para federação do Servidor Lync no Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-lync-server-federation.md)

## Federação XMPP

Para federação XMPP, o tráfego de saída e de entrada falhará se o pool de Borda designado como o gateway de federação XMPP ficar inativo. Para fazer a federação XMPP funcionar novamente, é necessário alterar a federação XMPP a fim de usar um pool de Borda diferente. Para obter detalhes, consulte [Failover do pool de Borda usado para federação de XMPP no Lync Server 2013](lync-server-2013-failing-over-the-edge-pool-used-for-xmpp-federation.md).

## Pool de Borda falha, mas o pool Front-End ainda está em execução

Se um pool de Borda falhar em um site, mas o pool Front-End nesse site ainda estiver em execução, será necessário alterar o pool Front-End a fim de usar um pool de Borda diferente em um site diferente, enquanto o primeiro pool de Borda está inativo. Para obter mais informações, consulte [Alterando o Pool de borda associado ao pool Front-End no Lync Server 2013](lync-server-2013-changing-the-edge-pool-associated-with-a-front-end-pool.md).

