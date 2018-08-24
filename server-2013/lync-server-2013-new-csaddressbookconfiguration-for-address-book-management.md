---
title: New-CsAddressBookConfiguration para Gerenciamento do catálogo de endereços
TOCTitle: New-CsAddressBookConfiguration para Gerenciamento do catálogo de endereços
ms:assetid: a58ddc8c-ae04-4141-b69e-e45374a67d72
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429718(v=OCS.15)
ms:contentKeyID: 49307685
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsAddressBookConfiguration para Gerenciamento do catálogo de endereços

 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros do grupo a seguir estão autorizados a executar o cmdlet New-CsAddressBookConfiguration localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções RBAC (controle de acesso baseado em função) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "New-CsAddressBookConfiguration"}

O cmdlet New-CsAddressBookConfiguration cria uma nova configuração para gerenciar o comportamento do catálogo de Endereços. A capacidade de definir se o Serviço do Catálogo de Endereços cria os arquivos de download de clientes, como e se regras de normalização são usadas, por quanto tempo manter arquivos delta e arquivos delta compactados, o tamanho de arquivos delta antes de incorporar a criação de um novo arquivo completo, em que momento do dia o Catálogo de Endereços de arquivo completo é criado e quais internos devem ser para a sincronização de informações no banco de dados do Usuário são tarefas específicas a este cmdlet.

Por exemplo:

    New-CsAddressBookConfiguration -Identity site:Redmond -KeepDuration 15 -SynchronizePollingInterval 00:10:00

Para uma descrição detalhada do comando completo, consulte o seguinte na principal referência de RTCCmdlets do Windows PowerShell do Lync Server.

## Consulte Também

#### Outros Recursos

[New-CsAddressBookConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAddressBookConfiguration)

