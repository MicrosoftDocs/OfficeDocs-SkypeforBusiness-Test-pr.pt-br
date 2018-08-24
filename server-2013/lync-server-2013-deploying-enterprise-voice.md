---
title: 'Lync Server 2013: Implantando o Enterprise Voice'
TOCTitle: Implantando o Enterprise Voice
ms:assetid: b5b593a6-ac30-461c-8c8c-0041e2c9ab04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412876(v=OCS.15)
ms:contentKeyID: 49307867
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando o Enterprise Voice no Lync Server 2013 

_**Tópico modificado em:** 2012-10-03_

O Lync Server 2013, Enterprise Voice faz parte da infraestrutura do Lync Server 2013.

A implantação do Enterprise Voice requer que você:

1.  Leia a seção [Planejamento para Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice.md) da documentação Planejamento.

2.  Finalize os planos de recursos e componentes para implantação com essa carga de trabalho.

3.  Execute o Ferramenta de Planejamento para projetar uma topologia que reflete suas decisões sobre implantação.

4.  Abra o design de topologia no Construtor de Topologias, conforme descrito no [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md) na documentação Implantação.
    
    > [!NOTE]  
    > A instalação do Construtor de Topologias faz parte do processo de implantação do pool interno. Para obter detalhes, consulte <a href="lync-server-2013-install-lync-server-administrative-tools.md">Instalar ferramentas administrativas do Lync Server 2013</a> na documentação Implantação.

Além disso, você já deve ter implantando o Lync Server, Enterprise Edition nos sites centrais e filiais que correspondem à topologia de referência escolhida para implantação. Não é possível implantar componentes do Enterprise Voice até que você tenha definido, publicado e instalados os arquivos de pelo menos um pool interno, e você precisa usar o Construtor de Topologias para definir e publicar um pool interno.

Para ver as topologias de referência com exemplos de onde as funções de servidor do Enterprise Voice podem ser implantadas (e como elas se relacionam entre si e com outras funções de servidor do Lync Server 2013), consulte [Topologias de referência no Lync Server 2013](lync-server-2013-reference-topologies.md) na documentação Planejamento.

Para ver uma topologia de referência que ilustra e explica uma amostra de implantação de controle de admissão de chamada, incluindo regiões da rede, sites da rede e sub-redes, consulte [Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013](lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md) na documentação Planejamento.

> [!IMPORTANT]  
> Para implantar o Enterprise Voice em um site central, continue lendo os tópicos nesta seção. Para implantar o Enterprise Voice em um site filial, vá para <a href="lync-server-2013-deploying-branch-sites.md">Implantando sites de filial no Lync Server 2013</a> na documentação Implantação.

Esta seção inclui procedimentos para implantações nas quais um Servidor de mediação é colocado em cada Servidor Front-End ou servidor Standard Edition, conforme recomendado, e também para implantações com um pool de Servidor de mediação autônomo.

Vá para o conteúdo seguinte se você usou o Construtor de Topologias para definir e publicar uma topologia que coloca um Servidor de mediação em cada Servidor Front-End ou servidor Standard Edition, pois o Assistente de Implantação já instalou automaticamente os arquivos para o Servidor de mediação quando você instalou os arquivos para seu pool de Servidores Front-End ou servidor Standard Edition:

  - [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md)

Se você usou o Construtor de Topologias para definir e publicar um Servidor de mediação em um pool autônomo, use o seguinte conteúdo:

  - Verifique se sua topologia atende aos pré-requisitos de software e de ambiente, conforme descrito em [Pré-requisitos do Enterprise Voice para Lync Server 2013](lync-server-2013-enterprise-voice-prerequisites.md).

## Nesta seção

   [Pré-requisitos do Enterprise Voice para Lync Server 2013](lync-server-2013-enterprise-voice-prerequisites.md)

   [Implantando Servidores de Mediação e definindo pares no Lync Server 2013](lync-server-2013-deploying-mediation-servers-and-defining-peers.md)

   [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md)

   [Configurando planos de discagem no Lync Server 2013](lync-server-2013-configuring-dial-plans.md)

   [Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013](lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md)

   [Exportação e importação da configuração de roteamento de voz no Lync Server 2013](lync-server-2013-exporting-and-importing-voice-routing-configuration.md)

   [Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

   [Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)

   [Implantando Exchange UM no local para fornecer correio de voz do Lync Server 2013](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md)

   [Fornecendo caixa postal a usuários do Lync Server 2013 no Exchange UM hospedado](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md)

   [Configurando integração local do Lync Server 2013 com o Exchange Online](lync-server-2013-configuring-on-premises-lync-server-integration-with-exchange-online.md)

   [Implantando recursos avançados de Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-advanced-enterprise-voice-features.md)
    
  - [Sobre regiões de rede, sites e subredes no Lync Server 2013](lync-server-2013-about-network-regions-sites-and-subnets.md)
    
  - [Criar ou modificar uma região de rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-region.md)
    
  - [Criar ou modificar um site da rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-site.md)
    
  - [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md)
    
  - [Configurar controle de admissão de chamada no Lync Server 2013](lync-server-2013-configure-call-admission-control.md)
    
  - [Configurar 9-1-1 Avançado no Lync Server 2013](lync-server-2013-configure-enhanced-9-1-1.md)
    
  - [Configurar bypass de mídia no Lync Server 2013](lync-server-2013-configure-media-bypass.md)

   [Habilitar usuários para Enterprise Voice no Lync Server 2013](lync-server-2013-enable-users-for-enterprise-voice.md)

## Consulte Também

#### Outros Recursos

[Implantando sites de filial no Lync Server 2013](lync-server-2013-deploying-branch-sites.md)  
[Configurando conferência discada no Lync Server 2013](lync-server-2013-configuring-dial-in-conferencing.md)  
[Configurando Estacionamento de Chamadas no Lync Server 2013](lync-server-2013-configuring-call-park.md)  
[Configurando comunicados de números não atribuídos no Lync Server 2013](lync-server-2013-configuring-announcements-for-unassigned-numbers.md)  
[Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md)

