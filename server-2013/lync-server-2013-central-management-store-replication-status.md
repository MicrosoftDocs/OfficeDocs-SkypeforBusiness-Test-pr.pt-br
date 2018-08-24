---
title: 'Lync Server 2013: Status de replicação do repositório de gerenciamento central'
TOCTitle: Status de replicação do repositório de gerenciamento central
ms:assetid: f514f88d-986b-4e45-b79b-e04a7616c1fe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn720926(v=OCS.15)
ms:contentKeyID: 62240147
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Status de replicação do repositório de gerenciamento central no Lync Server 2013

 

_**Tópico modificado em:** 2015-01-26_

Quando um administrador faz uma alteração de algum tipo no Lync Server (por exemplo, quando um administrador cria uma nova política de voz ou altera os parâmetros de configuração do Servidor do Catálogo de Endereços), essa alteração é registrada no Repositório de Gerenciamento Central. Por sua vez, a alteração deve ser replicada para todos os computadores que executam serviços do Lync Server ou funções de servidor.

Para replicar dados, o Replicador Mestre (executado no Servidor de Gerenciamento Central) cria um instantâneo dos dados de configuração alterados. Uma cópia desse instantâneo é enviada, em seguida, para cada computador que executa serviços do Lync Server ou funções de servidor. Nesses computadores, um agente de replicação recebe o instantâneo e carrega os dados alterados. Em seguida, o agente envia uma mensagem ao Replicador Mestre informando o status recente da replicação.

O cmdlet Get-CsManagementStoreReplicationStatus permite que você verifique o status de replicação para qualquer (ou todos) os computadores Lync Server de sua organização.

Quem pode executar este cmdlet? Por padrão, os membros destes grupos estão autorizados a executar o cmdlet Get-CsManagementStoreReplicationStatus localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins.

Para retornar uma lista de todas as funções RBAC às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC que você tenha criado), execute este comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Get-CsManagementStoreReplicationStatus"}

## Consulte Também

#### Outros Recursos

[Get-CsManagementStoreReplicationStatus](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsManagementStoreReplicationStatus)

