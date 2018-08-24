---
title: 'Lync Server 2013: Suporte à integração Exchange UM hospedado'
TOCTitle: Suporte à integração Exchange UM hospedado
ms:assetid: c7573ec3-013c-48d9-b59b-2a5427e6da35
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398821(v=OCS.15)
ms:contentKeyID: 49308082
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte à integração Exchange UM hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

O aplicativo ExUM do Lync Server 2013 oferece suporte à integração com o Unificação de Mensagens (UM) do Exchange em um ambiente local, onde o Lync Server 2013 e o UM do Exchange estão instalados localmente na sua empresa, ou com o UM do Exchange hospedado por um provedor de serviços, como mostra o diagrama a seguir.

![Implantação UM do Lync Server Exchange local](images/Gg398821.d6498eb9-87ee-40f3-8ecd-852f91546590(OCS.15).jpg "Implantação UM do Lync Server Exchange local")

Os modos a seguir são suportados:

  - **Modo no local**    Lync Server 2013 e UM do Exchange são implantados em servidores locais dentro de sua empresa.

  - **Modo entre instalações**    Lync Server 2013 é implantado em servidores locais dentro de sua empresa e o UM do Exchange é hospedado na instalação de um provedor de serviços online, como em um data center do Microsoft Exchange Online.

  - **Modo misto**   Sua implantação do Lync Server 2013 tem algumas caixas postais hospedadas em servidores locais executando o Microsoft Exchange Server dentro de sua empresa e algumas caixas postais hospedadas em um data center do serviço Exchange hospedado.
    
    > [!NOTE]  
    > O modo misto pode ser usado como uma solução de transição durante a avaliação e migração em etapas de usuários para o UM do Exchange hospedado ou com uma solução permanente se você optar por manter os serviços do UM do Exchange de alguns usuários no local após a migração de outros.

Para integrar o Lync Server 2013 com o UM do Exchange, hospedado, é necessário configurar um *espaço de endereço SIP compartilhado* (também chamado de um *domínio dividido* ). Nessa configuração, o Lync Server 2013 e o provedor de serviço do UM do Exchange hospedado por terceiros podem acessar o mesmo espaço de endereço de domínio SIP. Para obter detalhes, consulte [Arquitetura de integração do UM do Exchange hospedado no Lync Server 2013](lync-server-2013-hosted-exchange-um-integration-architecture.md) na documentação Planejamento.

