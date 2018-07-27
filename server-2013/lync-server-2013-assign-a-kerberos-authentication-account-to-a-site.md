---
title: 'Lync Server 2013: Atribuir uma conta de autenticação Kerberos a um site'
TOCTitle: Atribuir uma conta de autenticação Kerberos a um site
ms:assetid: 3d9c587c-c8b8-4f81-8ed9-1458a31fc292
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425901(v=OCS.15)
ms:contentKeyID: 49306468
ms.date: 04/19/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir uma conta de autenticação Kerberos a um site no Lync Server 2013

 

_**Tópico modificado em:** 2017-04-18_

Para concluir com sucesso este procedimento, você deve ter feito logon como usuário membro do grupo RTCUniversalServerAdmins.

Depois de criar a conta Kerberos, você deve atribuí-la a um site. Este é um site do Lync Server 2013, não do Active Directory. Você pode criar várias contas de autenticação Kerberos por implantação, mas pode atribuir apenas uma conta a um site. Use o procedimento a seguir para atribuir uma conta de autenticação Kerberos criada anteriormente a um site. Para obter detalhes sobre a criação da conta Kerberos, consulte [Criar uma conta de autenticação Kerberos no Lync Server 2013](lync-server-2013-create-a-kerberos-authentication-account.md).

## Para atribuir uma conta de autenticação Kerberos a um site

1.  Como membro do grupo RTCUniversalServerAdmins, faça logon em um computador do domínio executando o Lync Server 2013 ou em um computador em que as ferramentas administrativas estejam instaladas.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute os dois seguintes comandos:
    
    ```
        New-CsKerberosAccountAssignment -UserAccount "Domain\UserAccount" -Identity "site:SiteName"
    ```
    ```    
        Enable-CsTopology
    ```
    
    Por exemplo:
    
    ```
        New-CsKerberosAccountAssignment -UserAccount "contoso\kerbauth" -Identity "site:redmond"
    ```
    ```   
        Enable-CsTopology
    ```
    
    > [!NOTE]  
    > Você deve especificar o parâmetro UserAccount usando o formato Domínio\Usuário. Não há suporte para o formato Usuário@Domínio.extensão para fazer referência a objetos de computador criados para fins de autenticação Kerberos.
        
    > [!IMPORTANT]  
    > Depois de aplicar quaisquer alterações para a autenticação Kerberos, como adicionar ou remover uma conta, você deve executar o <strong>Enable-CsTopology</strong> a partir do prompt de comando do Shell de Gerenciamento do Lync Server.
