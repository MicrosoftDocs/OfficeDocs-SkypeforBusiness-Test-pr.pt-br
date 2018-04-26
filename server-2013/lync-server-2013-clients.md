---
title: 'Lync Server 2013: Clientes'
TOCTitle: Clientes para Lync Server
ms:assetid: e143ce9b-3624-4066-942d-6c86ad99be91
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398996(v=OCS.15)
ms:contentKeyID: 49308375
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Clientes para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 oferece suporte para vários tipos de software cliente que você pode implantar para os usuários da sua organização, incluindo softwares clientes instalados no computador, clientes baseados na Web e dispositivos móveis. Este tópico explica os diferente clientes que você pode usar. Para obter uma comparação detalhada dos recursos oferecidos pelos clientes do Lync Server 2013, consulte [Tabelas de comparação dos clientes para o Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md).

## Lync 2013

O Lync 2013 é o cliente completo para o Lync Server. A interface do usuário do Lync 2013 foi totalmente reprojetada e inclui recursos recentemente integrados, como o Chat Persistente ( Lync 2010 tinha um cliente separado para funcionalidade de chat), conversações tabuladas, visualização de vídeo e vídeo entre várias partes. Para um resumo das mudanças, consulte [Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

Instalação do cliente Lync 2013 é parte do programa de instalação do Office na mídia de instalação.

## Suplemento de Reunião Online para Lync 2013

O Suplemento de Reunião Online para Lync 2013 suporta o gerenciamento de reunião a partir do cliente de colaboração e mensagem do Microsoft Outlook. O software do Suplemento de Reunião Online para Lync 2013 é instalado automaticamente com o Lync 2013.

## Programador da Web do Lync

O Programador da Web do Lync é uma ferramenta de gerenciamento e programação de reunião baseada na Web para usuários que não possuem acesso ao Microsoft Outlook ou que estão em um sistema operacional não baseado no Windows. Com o Programador da Web do Lync, os usuários podem criar novas reuniões, modificar reuniões existentes e enviar convites usando seu programa de email favorito.

## Lync Web App

O Lync Web App é o cliente de conferência baseado na Web para reuniões do Lync Server 2013. Nesta versão, a adição de áudio e vídeo de computador ao Lync Web App oferece uma experiência de reunião completa para qualquer um que não possui um cliente do Lync instalado localmente. Os participantes da reunião possuem acesso a todos os recursos de compartilhamento e colaboração e controles da reunião do apresentador.

Se o Lync 2013 não estiver instalado em um computador do usuário e o usuário clica em um link de reunião em uma solicitação de reunião, o Lync Web App abre. Também é possível configurar a página Participar da reunião para permitir os usuários participarem de reuniões usando versões anteriores de clientes; consulte [Configurando a página de ingresso na reunião no Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md) na documentação de Implantação.

Por causa das melhorias do Lync Web App, uma versão atualizada do Microsoft Lync 2010 Attendee não está disponível para o Lync Server 2013. O Lync Web App é o cliente de escolha para participantes fora da organização. Com o Lync Web App, nenhuma instalação do cliente local é necessária, embora os recursos de compartilhamento, vídeo e áudio exijam a instalação de um plug-in durante o primeiro uso.

## Lync 2013 Básico

O Lync 2013 Básico é um cliente baixável para clientes com uma implantação do Lync Server 2013 local licenciada e clientes inscritos em um plano do Microsoft Office 365 que não inclui o cliente completo do Lync 2013. O cliente do Lync Básico inclui presença avançada, contatos, IM, reuniões do Lync e funcionalidade de voz básica. Os recursos não suportados no Lync Básico incluem vídeo multipartes, integração do OneNote, suporte VDI, pesquisa de habilidades, gravação, recursos do Enterprise Voice e tratamento de chamada avançado (por exemplo, encaminhamento de chamada e Chamada de Equipe). Para obter detalhes, consulte [Tabelas de comparação dos clientes para o Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md).

## Lync Windows Store App

O Aplicativo Lync Windows Store é um aplicativo Lync otimizado para toque projetado especificamente para Windows 8.1, Windows 8 e Windows RT. Os usuários podem baixar o aplicativo pela Windows Store pesquisando por "Lync." Para obter mais informações, consulte [Tabelas de comparação dos clientes para o Lync Server 2013](lync-server-2013-desktop-client-comparison-tables.md), [Requisitos do Aplicativo Lync da Windows Store para Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md) e [Implantar o Lync Windows Store App no Lync Server 2013](lync-server-2013-deploying-lync-windows-store-app.md).

## Lync 2013 para dispositivos móveis

Aplicativos móveis Lync 2013 agora incluem suporte a voz por IP (VoIP) e vídeo por IP, além de recursos de contatos, presença e IM. Usuários móveis podem optar por comunicar-se com outros via IM, chamadas de voz ou de vídeo utilizando Wi-Fi ou então sua conexão de dados celular. Com um único clique do link de reunião em um item de calendário, usuários móveis podem participar de reuniões via voz ou vídeo em andamento. Para mais informações sobre aplicativos móveis Lync 2013, consulte [Planejamento para clientes móveis no Lync Server 2013](lync-server-2013-planning-for-mobile-clients.md).

## Clientes suportados de versões anteriores

O Lync Server 2013 suporta os seguintes clientes de versões do servidor anteriores. É possível tornar determinados clientes anteriores disponíveis para usuários quando eles participarem de reuniões. Para obter detalhes, consulte [Configurando a página de ingresso na reunião no Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md) na documentação de Implantação.

  - **Lync 2010**    Lync 2010 oferece uma experiência de desktop completa, incluindo IM, presença, voz, vídeo, compartilhamento e telefonia aprimorados. Porém, nenhum dos novos recursos introduzidos em Lync Server 2013 estará disponível até que o cliente do usuário seja atualizado para Lync 2013.

  - O **Lync 2010 Mobile**    Lync Server 2013 suporta todos os aplicativos móveis do Microsoft Lync 2010 Mobile. O Microsoft Lync 2010 Mobile oferece IM, presença avançada e telefonia para os usuários na sua organização se conectando por um smartphone ou telefone com a edição Professional do Windows Mobile. É possível instruir seus usuários a instalarem o Microsoft Lync 2010 Mobile direcionando-os para o aplicativo de mercado de seu celular. Para obter detalhes, consulte “Planejamento de clientes móveis” na documentação do Lync Server 2010 em <http://go.microsoft.com/fwlink/?linkid=235955>.

  - O software **Lync Phone Edition**    Lync Phone Edition para telefones IP inteligentes (por exemplo, telefones com USB) que não foram atualizados para o Lync Server 2013. Lync Phone Edition continua a ser suportado para realizar e receber chamadas, presença avançada e capacidades de áudio do cliente para conferências.

  - **Lync 2010 Attendant**   O programa de gerenciamento de chamadas integrado ao Microsoft Lync 2010 Attendant permite a um recepcionista gerenciar várias conversas ao mesmo tempo através do tratamento de chamada rápido, IM e roteamento na tela.

## Consulte Também

#### Conceitos

[Interoperabilidade do Cliente no Lync 2013](lync-server-2013-client-interoperability-in-lync-2013.md)

