---
title: 'Lync Server 2013: Suporte da Unificação de Mensagens (UM) do Exchange'
TOCTitle: Suporte da Unificação de Mensagens (UM) do Exchange
ms:assetid: 0da62b8d-7416-4fb8-a405-381ca805c53a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398179(v=OCS.15)
ms:contentKeyID: 49305875
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte da Unificação de Mensagens (UM) do Exchange no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

O Lync Server 2013 oferece suporte à integração com o Unificação de Mensagens (UM) do Exchange para combinar mensagens de voz e mensagens de email em uma única infraestrutura de mensagens. No Exchange 2013, o UM do Exchange consiste no serviço do UM do Exchange, que é instalado e executado no servidor da Caixa de Correio, e o Roteador de Chamada de UM, que é instalado e executado no servidor de Acesso do Cliente. Para implantações do Enterprise Voice do Lync Server 2013, o UM do Exchange combina mensagens de voz e mensagens de email em um único repositório acessível a partir de um telefone (ou seja, Outlook Voice Access) ou um computador. UM do Exchange e Lync Server 2013 funcionam em conjunto para fornecer atendimento de chamada, Outlook Voice Access e serviços do Atendedor Automático para usuários do Enterprise Voice.

Além do suporte para integração com implantações no local do UM do Exchange, o Lync Server 2013 oferece suporte à integração com o UM do Exchange hospedado. Isso permite fornecer mensagens de voz aos usuários se você migrar alguns ou todos eles a um provedor de serviço do Exchange hospedado, como o Microsoft Exchange Online.

O Lync Server 2013 suporta as seguintes versões:

  - Microsoft Exchange 2013

  - Microsoft Exchange Server 2010 (obrigatório) ou com o service pack mais recente (recomendado)

  - Microsoft Exchange Server 2007 com Service Pack 1 (SP1) (obrigatório) ou com o service pack mais recente (recomendado)

Você não pode colocar o UM do Exchange com o Lync Server 2013 ou com um banco de dados do Lync Server 2013. Você pode instalar o UM do Exchange e o Lync Server 2013 em florestas separadas.

> [!NOTE]  
> O UM do Exchange pode não ser necessário para implantações do Enterprise Voice que possuem a PBX implantada, pois a PBX pode continuar a fornecer os serviços de caixa postal e outros relacionados a todos os usuários. Se você acabar desativando a PBX [por exemplo, se você implantar o tronco SIP para a conectividade da rede telefônica pública comutada (PSTN)], é preciso reconfigurar o UM do Exchange para oferecer a caixa postal aos usuários que anteriormente usavam o sistema de caixa postal da PBX.

## Nesta seção

  - [Componentes e topologias para o Sistema de Mensagens Instantâneas local no Lync Server 2013](lync-server-2013-components-and-topologies-for-on-premises-unified-messaging.md)

  - [Suporte à integração Exchange UM hospedado no Lync Server 2013](lync-server-2013-support-for-hosted-exchange-um-integration.md)

