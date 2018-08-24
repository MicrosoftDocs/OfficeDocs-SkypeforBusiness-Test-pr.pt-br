---
title: "Lync Server 2013: Tecn. de virtualização suportadas e limitações conhecidas"
TOCTitle: Tecnologias de virtualização suportadas e limitações conhecidas
ms:assetid: 6d3d749d-e840-4c05-afae-d6e69e7616aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204982(v=OCS.15)
ms:contentKeyID: 49307040
ms.date: 02/07/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tecnologias de virtualização suportadas e limitações conhecidas no Lync Server 2013

 

_**Tópico modificado em:** 2017-02-06_

O plug-in do VDI do Lync permite chamadas de áudio e vídeo para as tecnologias de virtualização suportadas. Isso amplia a funcionalidade destacada para o Microsoft Lync Server 2010 no whitepaper [Virtualização do cliente no Microsoft Lync 2010](http://go.microsoft.com/fwlink/?linkid=330447). Em conformidade com os regulamentos de telefonia padrão, o suporte para o E911 também está incluído. As seções seguintes descrevem as tecnologias de virtualização suportadas pelo plugin do VDI do Lync e limitações de recursos conhecidos.

## Suporte para Tecnologias de Virtualização

O plugin VDI do Lync suporta a comunicação remota total do desktop no cenário de desktop virtual pessoal, porém não no cenário da sessão do desktop remoto. Esses cenários podem ser descritos como segue:

  - **Com suporte: Áreas de Trabalho Virtuais Personalizadas ou Virtual Desktop Infrastructure (VDI).**  Neste cenário, cada usuário faz logon em uma área de trabalho virtual personalizável e pode salvar arquivos na área de trabalho que persiste entre as sessões. Os Serviços de Área de Trabalho Remota Microsoft, o VMware Horizon View e o Citrix XenDesktop são implementações testadas para uso com o Lync. Para obter informações sobre ambientes VDI específicos do fornecedor e sobre hardware de cliente que foram testados pela Microsoft, consulte [Infraestrutura qualificada para Microsoft Lync](http://go.microsoft.com/fwlink/?linkid=313435).

  - **Sem suporte: Sessões de Área de Trabalho Remota.**   Neste cenário, cada usuário registra-se em sessões de área de trabalho virtual genérica que não podem ser personalizadas. Exemplos de implantações incluem Sessões de Área de Trabalho Remota da Microsoft (RDSH) e Citrix XenApp juntamente com o Citrix Receiver.

O plugin do VDI do Lync não suporta outras tecnologias de virtualização, como virtualização de aplicativo, que permite o uso de um aplicativo sem necessidade de instalação completa do aplicativo localmente. Exemplos de implementações incluem o Citrix XenApp e a Microsoft Application Virtualization (App-V). Aplicação de streaming, comunicação remota de aplicativos e modelos de virtualização mistos (por exemplo, comunicação remota de aplicativos em toda a área de trabalho remota) não são suportados.

Para permitir a extensibilidade, o plugin do VDI do Lync foi projetado para usar APIs independentes de plataforma, chamados Dynamic Virtual Channels (DVCs). Para cenários que não são explicitamente suportados pelo Lync, consulte as instruções de apoio do provedor de soluções do VDI.

## Limitações conhecidas dos recursos

A seguir há algumas limitações conhecidas quando você usa o Lync 2013 em um ambiente de VDI:

  - O suporte aos recursos de delegação de chamadas e anonimato de agente do Grupo de Resposta é limitado.

  - Não há suporte aos seguintes recursos:
    
      - Páginas de ajuste de dispositivo de áudio integrado e dispositivo de vídeo
    
      - Vídeo com modo de exibição múltipla.
    
      - Gravação de conversas.
    
      - Participar de reuniões como anônimo (isto é, participar de reuniões do Lync hospedadas por uma organização que não esteja federadas à sua organização).
    
      - Usar o plug-in de VDI do Lync com um dispositivo do Lync Phone Edition.
    
      - Continuidade de chamadas em caso de indisponibilidade da rede.
    
      - Toques personalizados e recursos de música em espera.

  - O plugin do VDI do Lync não é suportado em um ambiente do Office 365.

