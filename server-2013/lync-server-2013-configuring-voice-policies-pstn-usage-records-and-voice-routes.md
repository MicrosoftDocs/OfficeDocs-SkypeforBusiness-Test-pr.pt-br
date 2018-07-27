---
title: 'Lync Server 2013: Configurando políticas de voz, registros de uso de PSTN e rotas de voz'
TOCTitle: Configurando políticas de voz, registros de uso de PSTN e rotas de voz
ms:assetid: 1e5a15f9-6f42-4dc6-baaa-24daf54afc4d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398272(v=OCS.15)
ms:contentKeyID: 49306080
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-10_

Políticas de voz, registros de uso PSTN e rotas de voz estão totalmente relacionados. Configure as políticas de voz selecionando um conjunto de recursos de chamada e, em seguida, atribuindo à política um conjunto de registros de uso da PSTN, que especificam quais direitos serão autorizados para os usuários ou grupos aos quais foi atribuída a política de voz. As rotas de voz também recebem registros de uso da PSTN, que servem para corresponder as rotas aos usuários que têm autorização para usá-las. Isto é, os usuários podem somente fazer chamadas que utilizem as rotas para as quais exista um registro de uso da PSTN correspondente.

O fluxo de trabalho recomendado para uma nova implantação Enterprise Voice é de começar configurando uma política de voz que inclua os registros de uso PSTN adequados e, então, associar as rotas apropriadas à cada registro de uso PSTN.

> [!NOTE]  
> Você também pode criar políticas de voz com escopo de <em>usuário</em> e atribuí-las a grupos ou usuários individuais.

Para as etapas detalhas para realizar cada uma destas tarefas, consulte os procedimentos nesta seção.

## Nesta seção

  - [Configurando políticas de voz e registros de uso de PSTN para autorizar recursos e privilégios de chamada no Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md)

  - [Exibir registros de uso PSTN no Lync Server 2013](lync-server-2013-view-pstn-usage-records.md)

  - [Configurando rotas de voz para chamadas de saída no Lync Server 2013](lync-server-2013-configuring-voice-routes-for-outbound-calls.md)

  - [Exportação e importação da configuração de roteamento de voz no Lync Server 2013](lync-server-2013-exporting-and-importing-voice-routing-configuration.md)

  - [Publicar alterações pendentes na configuração de roteamento de voz no Lync Server 2013](lync-server-2013-publish-pending-changes-to-the-voice-routing-configuration.md)

  - [Testar roteamento de voz no Lync Server 2013](lync-server-2013-test-voice-routing.md)

