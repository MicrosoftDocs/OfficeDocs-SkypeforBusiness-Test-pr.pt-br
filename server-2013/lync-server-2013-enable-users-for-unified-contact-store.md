---
title: 'Lync Server 2013: Habilitar usuários para repositório unificado de contatos'
TOCTitle: Habilitar usuários para repositório unificado de contatos
ms:assetid: 7b46a01f-beb5-4a33-adb0-35f0502b168d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205024(v=OCS.15)
ms:contentKeyID: 49307214
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar usuários para repositório unificado de contatos no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-07_

Ao implantar Lync Server 2013 e publicar a topologia, é habilitado o armazenamento unificado de contatos para todos os usuários por default. Você não precisa tomar qualquer medida adicional para habilitar o armazenamento unificado de contatos depois de implantar Lync Server 2013. Contudo, você pode usar o **Set-CsUserServicesPolicy** cmdlet para definir quais usuários têm o armazenamento unificado de contatos disponível. Você pode habilitar esse recurso globalmente, por local, por tenant ou por indivíduos ou grupos de indivíduos.

## Para permitir o armazenamento unificado de contatos

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Faça qualquer um dos seguintes:
    
      - Para permitir o armazenamento unificado de contatos globalmente a todos os usuários Lync Server , na linha de comando, digite:
        
            Set-CsUserServicesPolicy -Identity global -UcsAllowed $True
    
      - Para permitir o armazenamento unificado de contatos para os usuários em um local específico, digite na linha de comando:
        
            New-CsUserServicesPolicy -Identity site:<site name> -UcsAllowed $True
        
        Por exemplo:
        
            New-CsUserServicesPolicy -Identity site:Redmond -UcsAllowed $True
    
      - Para permitir o armazenamento unificado de contatos por tenant, digite na linha de comando:
        
            Set-CsUserServicesPolicy -Tenant <tenantId> -UcsAllowed $True
        
        Por exemplo:
        
            Set-CsUserServicesPolicy -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -UcsAllowed $True
    
      - Para permitir o armazenamento unificado de contatos para usuários específicos, digite na linha de comando:
        
            New-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $True
            Grant-CsUserServicesPolicy -Identity "<user display name>" -PolicyName <"policy name">
        
        > [!NOTE]  
        > Você também pode alterar o URI do SIP ou o usuário remoto em vez do nome do usuário.        
        Por exemplo:
        
            New-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $True
            Grant-CsUserServicesPolicy -Identity "Ken Myer" -PolicyName "UCS Enabled Users"
        
        > [!NOTE]  
        > No exemplo anterior, o primeiro comando criar uma nova política de acordo com o usuário chamada <em>Usuários do UCS Permitidos</em> , com o sinalizador AcsAllowed definido para True. O segundo comando define a política ao usuário com nome de Ken Myer, o que significa que Ken Myer está autorizado a ter armazenamento unificado de contatos.
