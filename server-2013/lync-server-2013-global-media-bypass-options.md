---
title: Opções de bypass de mídia global no Lync Server 2013
TOCTitle: Opções de bypass de mídia global no Lync Server 2013
ms:assetid: 1bd35f90-8587-48a1-b0c2-095a4053fc77
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398255(v=OCS.15)
ms:contentKeyID: 49306052
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Opções de bypass de mídia global no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

> [!NOTE]  
> Este tópico considera que você já configurou o bypass de mídia para qualquer tronco até um par (gateway PSTN, um IP-PBX ou um Controlador de Borda de Seção em um Provedor de Serviços de Telefonia da Internet) para um site específico ou serviço para o qual você deseja que a mídia ignore o Servidor de mediação.

Além de habilitar o bypass de mídia para conexões individuais de tronco associadas a um par, você deve também habilitá-lo globalmente. As configurações globais de bypass de mídia podem tanto especificar que o bypass de mídia sempre recebe tentativas de chamadas para o PSTN ou que o bypass de mídia é implantado usando o mapeamento de subredes para sites de rede e regiões de rede - similar ao que é feito pelo controle de admissão de chamada, outro recurso de voz avançado. Quando o bypass de mídia e o controle de admissão de chamadas estão ativados a região de rede, o site de rede e as informações da subrede especificadas pelo controle de admissão de chamada são usados automaticamente ao determinar se usam ou não o bypass de mídia. Isso significa que você não pode especificar se o bypass de mídia sempre recebe tentativas de chamada para o PSTN quando o controle de admissão de chamada está ativado.

Este tópico descreve como usar o Painel de Controle do Lync Server e o Shell de Gerenciamento do Lync Server para definir as configurações globais do bypass de mídia.

> [!NOTE]  
> Ao usar estas etapas para configurar o bypass de mídia, pressupõe-se que você possui uma boa conectividade entre os clientes e o par do Servidor de Mediação (por exemplo, um gateway PSTN, um IP-PBX, ou um SBC em um provedor de tronco SIP). Se houver qualquer limitação de largura de banda no link, o bypass de mídia não poderá ser aplicado na chamada. O bypass de mídia não interopera com todos os gateway PSTN, IP-PBX e SBC. A Microsoft testou um conjunto de gateways PSTN e SBCs com parceiros certificados e fez alguns testes com IP-PBXs da Cisco. O bypass de mídia é suportado somente para os produtos e versões listadas no Programa de Interoperabilidade Aberta Microsoft Unified Communications - Lync Server em <a href="http://go.microsoft.com/fwlink/?linkid=214406%26clcid=0x416" class="uri">http://go.microsoft.com/fwlink/?linkid=214406&amp;clcid=0x416</a>.

## Próximas etapas: definir as configurações globais do bypass de mídia

Depois de habilitar o bypass de mídia em quaisquer conexões tronco para um par de sites específicos ou serviços, use o seguinte conteúdo para:

  - Habilitar sempre o bypass de mídia conforme descrito em [Configurar o bypass de mídia para sempre ignorar o Servidor de Mediação](lync-server-2013-configure-media-bypass-to-always-bypass-the-mediation-server.md).

  - Ou, configurar o bypass de mídia para usar o site e informações de região conforme descrito em [Definir as configurações globais de bypass de mídia para usar informações locais e da região](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md).

## Consulte Também

#### Tarefas

[Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md)  

#### Conceitos

[Configurar bypass de mídia no Lync Server 2013](lync-server-2013-configure-media-bypass.md)  
[Bypass de mídia e Servidor de Mediação no Lync Server 2013](lync-server-2013-media-bypass-and-mediation-server.md)

