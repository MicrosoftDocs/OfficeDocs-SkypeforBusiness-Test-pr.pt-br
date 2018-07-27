---
title: Update-CsAddressBook para Gerenciamento de catálogo de endereços
TOCTitle: Update-CsAddressBook para Gerenciamento de catálogo de endereços
ms:assetid: 0ffd2ef8-201c-44aa-8c64-1c7b0eaa7d48
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429695(v=OCS.15)
ms:contentKeyID: 49305907
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsAddressBook para Gerenciamento de catálogo de endereços 

_**Tópico modificado em:** 2012-11-01_

Quem pode executar este cmdlet: por padrão, os membros dos seguintes grupos estão autorizados a executar o cmdlet Update-CsAddressBook localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Update-CsAddressBook"}

O cmdlet Update-CsAddressBook substitui o comando **abserver.exe –syncNow** do Office Communications Server. O objetivo do cmdlet é iniciar uma sincronização imediatamente em vez de esperar pela hora agendada. O primeiro exemplo de comando atualiza todos os Catálogos de Endereços da organização, enquanto o segundo atualiza somente os Catálogos de Endereços associados com o servidor definido.

> [!NOTE]  
> No Lync Server 2013, o Lync Server User Replicator escolherá as alterações do Active Directory e atualizará o banco de dados de usuário do Lync Server baseado em um intervalo configurado. O Lync Server User Replicator também propagará as alterações para o banco de dados RTCab rapidamente sem a necessidade de o administrador executar o cmdlet Update-CSAddressBook. Administradores precisarão executar o cmdlet Update -CSAddressBook somente se o download do arquivo do Catálogo de Endereços estiver habilitado.

Por exemplo:

```
    Update-CsAddressBook
```
```
    Update-CsAddressBook -Fqdn atl-abs-001.contoso.com
```

Para uma descrição detalhada do comando completo, consulte o seguinte na referência principal do Lync Server Windows PowerShell RTCCmdlets.

## Consulte Também

#### Outros Recursos

[Update-CsAddressBook](https://docs.microsoft.com/en-us/powershell/module/skype/Update-CsAddressBook)

