---
title: 'Lync Server 2013: Sobre regiões de rede, sites e subredes'
TOCTitle: Sobre regiões de rede, sites e subredes
ms:assetid: 6662123a-d011-408c-a290-92b2a8589943
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398467(v=OCS.15)
ms:contentKeyID: 49306948
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Sobre regiões de rede, sites e subredes no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-24_

Os recursos avançados do Enterprise Voice descritos nesta seção compartilham alguns requisitos de configuração para regiões de rede, locais de rede e subredes. Por exemplo, todos os três recursos avançados requerem que cada subrede na topologia seja associada a um *local de rede* específico e que cada local de rede seja associado a uma *região de rede* .

> [!IMPORTANT]  
> Antes de iniciar a configuração de rede para controle de admissão de chamadas, E9-1-1, ou desvio de mídia, verifique se você revisou as informações adicionais sobre as configurações de rede no tópico <a href="lync-server-2013-network-settings-for-the-advanced-enterprise-voice-features.md">Configurações de rede para recursos avançados do Enterprise Voice no Lync Server 2013</a> na documentação do Planejamento. Para obter mais informações sobre a configuração de rede principalmente em relação ao controle de admissão de chamadas, consulte também <a href="lync-server-2013-defining-your-requirements-for-call-admission-control.md">Definindo seus requisitos de controle de admissão de chamadas no Lync Server 2013</a> na documentação do Planejamento.

O controle de admissão de chamada e o E9-1-1 têm requisitos adicionais de configuração para os sites de rede:

  - O controle de admissão de chamada requer que um um *perfil de política de largura de banda* seja especificado para cada site restrito pelas limitações de largura de banda WAN. Se você planeja implantar o controle de admissão de chamada, deve [Criar perfis da política de largura de banda no Lync Server 2013](lync-server-2013-create-bandwidth-policy-profiles.md) antes de configurar seus sites de rede.

  - O E9-1-1 requer que uma *política local* seja especificada para cada site. Se você planeja implantar o E9-1-1, deve [Criar políticas de localização no Lync Server 2013](lync-server-2013-create-location-policies.md) antes de configurar seus sites de rede.

## Criar ou modificar regiões de rede, sites de rede e sub-redes

Os tópicos a seguir fornecem as etapas para criar ou modificar as regiões de rede e sites de rede, e para associar sub-redes aos sites de rede. Esses tópicos não são específicos para nenhum recurso avançado do Enterprise Voice.

  - [Criar ou modificar uma região de rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-region.md)

  - [Criar ou modificar um site da rede no Lync Server 2013](lync-server-2013-create-or-modify-a-network-site.md)

  - [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md)

