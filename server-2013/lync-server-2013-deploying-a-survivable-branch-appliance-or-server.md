---
title: 'Lync Server 2013: Implantando Aplicativo ou Servidor de Filial Persistente'
TOCTitle: Implantando Aplicativo ou Servidor de Filial Persistente
ms:assetid: cb780c14-dc5f-41ba-8092-f20ae905bd16
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398849(v=OCS.15)
ms:contentKeyID: 49308123
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando Aplicativo ou Servidor de Filial Persistente com Lync Server 2013

 

_**Tópico modificado em:** 2014-12-10_

O Enterprise Voice resiliente refere-se à resiliência de site de filial, isto é, a capacidade de oferecer serviço do Enterprise Voice contínuo para usuários do site de lote em caso onde o link para o site central se tornar indisponível.

Para sites de filial de pequeno e médio porte (sites de filial com 25 a 1.000 usuários), recomendamos a implantação de um Aparelho de Filial Persistente, que encerrará chamadas PSTN (rede telefônica pública comutada) usando seu gateway PSTN integrado ou um tronco SIP para um provedor de serviço telefônico. Um Aparelho de Filial Persistente é um dispositivo de terceiros que inclui um blade server executando o Sistema operacional Windows Server 2008 R2, o Registrador do Lync Server 2013, o software Servidor de Mediação e um gateway PSTN, tudo em um único chassi de aparelho.

Para sites de filial com 1.000 a 5.000 usuários e nenhum WAN resiliente, recomendamos um Servidor de Filial Persistente conectado a um gateway PSTN ou um tronco SIP a um provedor de serviço telefônico. Um Servidor de Filial Persistente é um computador baseado em Windows Server com um Registrador e software do Servidor de Mediação instalado.

> [!NOTE]  
> Para sites de filial com mais de 5.000 usuários e administradores de Lync Server dedicados, recomendamos uma implantação total do Lync Server 2013, separada do site central.<br />Para obter detalhes sobre como escolher a melhor solução de resiliência para sites de filial em sua organização, incluindo considerações sobre pré-requisitos e planejamento, consulte <a href="lync-server-2013-branch-site-resiliency-requirements.md">Requisitos de resiliência do site da filial para Lync Server 2013</a> na documentação Planejamento.

## Nesta seção

  - [Implantando um servidor ou aparelho de filial persistente com o Lync Server 2013 - Tarefas do site central](lync-server-2013-deploying-a-survivable-branch-appliance-or-server-central-site-tasks.md)

  - [Implantar Servidor ou Aparelho de Filial Persistente com Lync Server 2013 - tarefa de site de filial](lync-server-2013-deploy-a-survivable-branch-appliance-or-server-branch-site-task.md)

  - [Configurando usuários para resiliência de site da filial no Lync Server 2013](lync-server-2013-configuring-users-for-branch-site-resiliency.md)

  - [Usuários domésticos em um Home users on a Aparelho de Filial Persistente ou Servidor no Lync Server 2013](lync-server-2013-home-users-on-a-survivable-branch-appliance-or-server.md)

  - [Anexos: Servidores e Aplicativos de Filial Persistente no Lync Server 2013](lync-server-2013-appendices-survivable-branch-appliances-and-servers.md)

## Consulte Também

#### Outros Recursos

[Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md)

