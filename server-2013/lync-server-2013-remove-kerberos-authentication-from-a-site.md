---
title: 'Lync Server 2013: Remover autenticação Kerberos de um site'
TOCTitle: Remover autenticação Kerberos de um site
ms:assetid: 93171b02-bb36-42dc-943d-86d9dde45b59
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398749(v=OCS.15)
ms:contentKeyID: 49307472
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# No Lync Server 2013, remover autenticação Kerberos de um site

 

_**Tópico modificado em:** 2012-01-16_

Para concluir com sucesso este procedimento, você deve ter feito logon como usuário membro do grupo RTCUniversalServerAdmins.

Se for necessário remover a autenticação Kerberos de um site ou desativar um site, você deve remover a atribuição da conta da autenticação Kerberos do site usando o cmdlet **Remove-CsKerberosAccountAssignment**. Use o procedimento a seguir para remover a atribuição da conta da autenticação Kerberos, o que remove a atribuição de todos os computadores no site.


> [!WARNING]
> Se você está desativando a conta habilitada para Kerberos de forma permanente, deve usar os Usuários e Computadores do Active Directory para excluí-la do Serviços de Domínio Active Directory depois de remover a atribuição. Se você planeja usar o objeto no futuro, pode ser desejável manter o objeto do Active Directory.



## Para remover a autenticação Kerberos de um site

1.  Como membro do grupo RTCUniversalServerAdmins, faça logon em um computador do domínio executando o Lync Server 2013 ou em um computador em que as ferramentas administrativas estejam instaladas.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute os dois seguintes comandos:
    
    ```
        Remove-CsKerberosAccountAssignment -Identity "site:SiteName"
    ```
    ```    
        Enable-CsTopology
    ```    
    Por exemplo:
    ```    
        Remove-CsKerberosAccountAssignment -Identity "site:Redmond"
    ```
    ```    
        Enable-CsTopology
    ```    
    > [!IMPORTANT]  
    > Depois de aplicar quaisquer alterações para a autenticação Kerberos, como adicionar ou remover uma conta, você deve executar o <strong>Enable-CsTopology</strong> a partir do prompt de comando do Shell de Gerenciamento do Lync Server.
