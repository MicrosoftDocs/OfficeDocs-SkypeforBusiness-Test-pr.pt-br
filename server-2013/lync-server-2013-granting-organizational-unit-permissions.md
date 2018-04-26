---
title: 'Lync Server 2013: Concedendo permissões de unidade organizacional'
TOCTitle: Concedendo permissões de unidade organizacional
ms:assetid: 95ee5ffa-39b1-4d80-87a2-27bb364f7396
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398763(v=OCS.15)
ms:contentKeyID: 49307519
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Concedendo permissões de unidade organizacional no Lync Server 2013

 

_**Tópico modificado em:** 2012-05-14_

Você pode usar o cmdlet **Grant-CsOuPermission** para conceder permissões a objetos em unidades organizacionais especificadas para que os membros dos grupos universais RTC criados pela preparação da floresta possam acessá-los sem serem membros do grupo Administradores de Domínio. As permissões adicionadas à unidade organizacional especificada são as mesmas permissões que o cmdlet **Enable-CsAdDomain** adiciona aos contêineres de computadores e usuários durante a preparação do domínio.

Use o cmdlet **Test-CsOuPermission** para verificar as permissões configuradas usando o cmdlet **Grant-CsOuPermission**.

Você pode usar o cmdlet **Revoke-CsOuPermission** para remover permissões concedidas usando o cmdlet **Grant-CsOuPermission**.

## Para conceder permissões de UO

1.  Faça logon em um computador executando o Lync Server 2013 no domínio em que deseja conceder permissões de UO. Use uma conta que seja membro do grupo Administradores de Domínio ou do grupo Administradores de Empresa se a UO estiver em um domínio filho diferente.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.

## Para verificar permissões de UO

1.  Faça logon em um computador executando o Lync Server 2013 no domínio em que deseja verificar permissões de UO concedidas usando o cmdlet **Grant-CsOuPermission**. Use uma conta que seja membro do grupo Administradores de Domínio ou do grupo Administradores de Empresa se a UO estiver em um domínio filho diferente.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Test-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.

## Para revogar permissões de OU

1.  Faça logon em um computador executando o Lync Server 2013 no domínio em que deseja revogar permissões de UO que foram concedidas pelo cmdlet **Grant-CsOuPermission**. Use uma conta que seja membro do grupo Administradores de Domínio ou do grupo Administradores de Empresa se a UO estiver em um domínio filho diferente.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Revoke-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> -OU <DN of the OU> [-Domain <Domain FQDN>]
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.

