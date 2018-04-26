---
title: 'Lync Server 2013: Concedendo permissões de configuração'
TOCTitle: Concedendo permissões de configuração
ms:assetid: 15982bfe-6844-44f6-815a-72dcaf0e4d21
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398225(v=OCS.15)
ms:contentKeyID: 49305982
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Concedendo permissões de configuração no Lync Server 2013

 

_**Tópico modificado em:** 2012-08-27_

Você pode usar o cmdlet **Grant-CsSetupPermission** para adicionar as permissões de Leitura, Gravação, ReadSPN e WriteSPN ao grupo RTCUniversalServerAdmins para uma unidade organizacional (UO) específica do Active Directory. Então, membros do grupo RTCUniversalServerAdmins dessa UO podem instalar servidores executando o Lync Server 2013 no domínio específico sem serem membros do grupo Admins. do domínio.

Use o cmdlet **Test-CsSetupPermission** para verificar as permissões configuradas usando o cmdlet **Grant-CsSetupPermission**.

Você pode usar o cmdlet **Revoke-CsSetupPermission** para remover permissões concedidas usando o cmdlet **Grant-CsSetupPermission**.

## Para conceder permissões de configuração

1.  Faça logon em um computador que esteja executando o Lync Server 2013 no domínio em que você deseja conceder permissões de configuração. Use uma conta que seja membro do grupo Admins. de Domínio ou do grupo Admins. da Empresa se a UO estiver em um domínio filho diferente.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Grant-CsSetupPermission -ComputerOu <DN of the OU or container where the computer objects that will run Lync Server reside > [-Domain <Domain FQDN>]
    
    Você pode especificar o parâmetro ComputerOu como relativo ao contexto de nomenclatura padrão do domínio específico (por exemplo, CN=computers). De outro modo, você pode especificar esse parâmetro como o nome diferenciado (DN) de UO completo (por exemplo, "CN=computers,DC=Contoso,DC=com"). No último caso, você de especificar um DN de OU que seja consistente com o domínio especificado.
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.

## Para verificar as permissões de configuração

1.  Faça logon em um computador que esteja executando o Lync Server 2013 no domínio no qual você deseja verificar as permissões de configuração que você concedeu usando o cmdlet **Grant-CsSetupPermission**. Use uma conta que seja membro do grupo Admins. de Domínio ou do grupo Admins. da Empresa se a UO estiver em um domínio filho diferente.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Test-CsSetupPermission -ComputerOu <DN of the OU or container where the computer objects that will run Lync Server reside> [-Domain <Domain FQDN>]
    
    Você pode especificar o parâmetro ComputerOu como relativo ao contexto de nomenclatura padrão do domínio específico (por exemplo, CN=computers). De outro modo, você pode especificar esse parâmetro como o nome diferenciado (DN) de UO completo (por exemplo, "CN=computers,DC=Contoso,DC=com"). No último caso, você de especificar um DN de OU que seja consistente com o domínio especificado.
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.

## Para revogar as permissões de configuração

1.  Faça logon em um computador que esteja executando o Lync Server 2013 no domínio no qual você deseja revogar as permissões de configuração concedidas pelo cmdlet **Grant-CsSetupPermission**. Use uma conta que seja membro do grupo Admins. de Domínio ou do grupo Admins. da Empresa se a UO estiver em um domínio filho diferente.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Revoke-CsSetupPermission -ComputerOu <DN of the OU or container where the computer objects that will run Lync Server reside > [-Domain <Domain FQDN>]
    
    Você pode especificar o parâmetro ComputerOu como relativo ao contexto de nomenclatura padrão do domínio específico (por exemplo, CN=computers). De outro modo, você pode especificar esse parâmetro como o nome diferenciado (DN) de UO completo (por exemplo, "CN=computers,DC=Contoso,DC=com"). No último caso, você de especificar um DN de OU que seja consistente com o domínio especificado.
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.

