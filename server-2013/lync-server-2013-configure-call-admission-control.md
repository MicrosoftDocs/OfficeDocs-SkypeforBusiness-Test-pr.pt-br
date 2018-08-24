---
title: 'Lync Server 2013: Configurar controle de admissão de chamada'
TOCTitle: Configurar controle de admissão de chamada
ms:assetid: ce3e6e71-1e33-4cff-849a-c0468e61fef6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398870(v=OCS.15)
ms:contentKeyID: 49308156
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar controle de admissão de chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

O controle de admissão de chamadas é uma solução que determina se uma sessão em tempo real pode ou não ser estabelecida com base na largura de banda disponível, para ajudar a evitar uma qualidade audiovisual ruim para os usuários em redes congestionadas. O controle de admissão de chamadas controla o tráfego em tempo real somente de áudio e vídeo e não afeta o tráfego de dados. O controle de admissão de chamadas pode rotear a chamada através de um caminho da Internet quando o caminho WAN padrão não tem a largura de banda necessária. Para obter detalhes, consulte [Planejamento para controle de admissão de chamada no Lync Server 2013](lync-server-2013-planning-for-call-admission-control.md) na documentação de Planejamento.

Esta seção fornece um conjunto de procedimentos de exemplo que ilustram como implantar e gerenciar o CAC em sua rede.

> [!IMPORTANT]  
> Antes de começar a implantação do CAC, é necessário coletar todas as informações necessárias para a topologia de rede de sua empresa, conforme descrito em <a href="lync-server-2013-example-of-gathering-your-requirements-for-call-admission-control.md">Exemplo: Coletando seus requisitos para controle de admissão de chamada no Lync Server 2013</a> na documentação Planejamento. Certifique-se também de que os componentes de CAC tenham sido instalados e ativados, conforme descrito em <a href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013</a> ou Definir e Configurar um servidor SE na documentação de Implantação.

> [!NOTE]  
> Todos os exemplos de implantação e gerenciamento de CAC nesta seção são executados usando o Shell de Gerenciamento do Lync Server. Como alternativa, também é possível usar a seção <strong>Configuração de Rede</strong> do Painel de Controle do Lync Server para gerenciar o CAC.

## Nesta seção

  - [Configurar regiões de rede para CAC no Lync Server 2013](lync-server-2013-configure-network-regions-for-cac.md)

  - [Criar perfis da política de largura de banda no Lync Server 2013](lync-server-2013-create-bandwidth-policy-profiles.md)

  - [Configurar locais de rede para CAC no Lync Server 2013](lync-server-2013-configure-network-sites-for-cac.md)

  - [Associar subredes com locais de rede para o CAC no Lync Server 2013](lync-server-2013-associate-subnets-with-network-sites-for-cac.md)

  - [Criar links de região de rede no Lync Server 2013](lync-server-2013-create-network-region-links.md)

  - [Criar roteamentos de interregião de rede no Lync Server 2013](lync-server-2013;-create-network-interregion-routes.md)

  - [Criar políticas entre locais de rede no Lync Server 2013](lync-server-2013-create-network-intersite-policies.md)

  - [Habilitar o controle de admissão de chamadas no Lync Server 2013](lync-server-2013-enable-call-admission-control.md)

  - [Lista de verificação da implantação do controle de admissão de chamadas para Lync Server 2013](lync-server-2013-call-admission-control-deployment-checklist.md)

