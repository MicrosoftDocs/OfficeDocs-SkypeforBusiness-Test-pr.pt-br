---
title: 'Lync Server 2013: Migrar usuários para o repositório unificado de contatos'
TOCTitle: Migrar usuários para o repositório unificado de contatos
ms:assetid: 215a8ec1-d63e-4fdf-b73d-75aeb9dddb43
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204737(v=OCS.15)
ms:contentKeyID: 49306112
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar usuários para o repositório unificado de contatos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-15_

Os contatos do usuário são migrados automaticamente para o servidor do Exchange 2013 quando o usuário:

  - For atribuído com uma política de serviços do usuário com UcsAllowed definido para True.

  - Tenha sido provisionado com uma caixa de correio do Exchange 2013 e se conectado a ela pelo menos uma vez.

  - Faça o login usando um cliente avançado do Lync 2013.

Se o usuário faz o login com um cliente do Lync 2010 ou anterior ou se o usuário não está conectado a um servidor do Exchange 2013, a política de serviços do usuário é ignorada e os contatos do usuário permanecem no Lync Server.

É possível determinar se os contatos do usuário foram migrados usando um dos seguintes métodos:

  - Verifique a chave do registro no computador cliente:
    
    HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\\<SIP URL\>\\UCS
    
    Se os contatos do usuário estão armazenados no Exchange 2013, esta chave contém um valor do InUCSMode de 2165.

  - Execute o cmdlet **Test-CsUnifiedContactStore**. Na linha de comando do Shell de Gerenciamento do Lync Server, digite:
    
        Test-CsUnifiedContactStore -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetFqdn "atl-cs-001.litwareinc.com"
    
    Se o **Test-CsUnifiedContactStore** tiver êxito, os contatos do usuário foram migrados para o repositório de contatos unificados.

