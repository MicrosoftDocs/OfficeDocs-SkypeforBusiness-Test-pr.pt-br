---
title: 'Lync Server 2013: Planejamento de controle de chamada remota'
TOCTitle: Planejamento de controle de chamada remota
ms:assetid: 688a0328-1aa7-449f-b5f7-98c876112ed2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558658(v=OCS.15)
ms:contentKeyID: 49306980
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de controle de chamada remota no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-05_

No Lync Server 2013, o suporte a cenários de controle de chamada remota permite que os usuários controlem telefones PBX (central privada de comutação telefônica) usando o Lync 2013 em seus computadores desktop. Esta seção descreve os recursos de controle de chamada remota e os requisitos para a implantação do controle de chamada remota.

A integração entre um PBX e o Lync Server 2013 permite que usuários habilitados para o controle de chamada remota usem a interface do usuário do Lync 2013 para controlar chamadas em seus telefones PBX das seguintes maneiras:

> [!NOTE]  
> Por fim, os recursos do PBX que hospeda o telefone PBX de um usuário determinam os recursos de controle de chamada remota disponíveis para o usuário.

  - Fazer uma chamada de saída

  - Atender uma chamada recebida

  - Atender uma chamada com uma mensagem instantânea
    
    > [!NOTE]  
    > Ou seja, quando o número de telefone do chamador pode ser associado a um endereço de mensagens instantâneas na GAL (lista de endereços global) da organização, na lista de Contatos do Lync do receptor, ou em uma organização de parceiro federado.

  - Transfira uma chamada

  - Encaminhar uma chamada de entrada

  - Colocar chamadas em espera

  - Alternar entre várias chamadas simultâneas

  - Atender uma segunda chamada enquanto está em uma chamada (isso é, chamada em espera)

  - Discar dígitos DTMF

  - Na janela Conversa, digite observações no programa de anotações Microsoft Office OneNote

Além disso, quando um usuário está habilitado para o controle de chamada remota, o Lync 2013 fornece a ele as seguintes informações de chamada:

  - Identificação de um chamador pelo nome quando o número de telefone do chamador existe na lista de contatos do cliente de mensagens e colaboração do Microsoft Office Outlook do usuário habilitado para o controle de chamada remota, na lista de contatos do Lync ou na GAL (Lista de Endereços Global) da organização.

  - Chamadas de entrada e saída antigas, que são salvas na pasta Histórico da Conversa no Outlook.

  - Notificações de chamadas perdidas, que são enviadas para a pasta Caixa de Entrada do Outlook do usuário, mas geradas somente se o Lync estiver em execução quando a chamada for recebida.

## Controle de Chamada Remota e Enterprise Voice

Embora os recursos de controle de chamada remota sejam separados dos recursos do Enterprise Voice e os usuários não possam ser habilitados para ambos, o Enterprise Voice fornece um subconjunto de recursos que também estão disponíveis para os usuários habilitados para o controle de chamada remota. Se o Enterprise Voice estiver implantado, os usuários habilitados para o controle de chamada remota poderão usar o Lync para acessar os seguintes recursos do Enterprise Voice:

  - Fazer e receber chamadas de áudio para outro cliente do Lync

  - Ingressar na parte de áudio de uma conferência criada por um usuário habilitado para o Enterprise Voice

## Nesta seção

  - [Tarefas de implantação de controle de chamada remota no Lync Server 2013](lync-server-2013-deployment-tasks-for-remote-call-control.md)

