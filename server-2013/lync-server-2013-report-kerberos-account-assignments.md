---
title: 'Lync Server 2013: Relatar atribuições da conta Kerberos'
TOCTitle: Relatar atribuições da conta Kerberos
ms:assetid: 523231f6-81b3-454b-996d-663d9bd5cf83
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398343(v=OCS.15)
ms:contentKeyID: 49306706
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Relatar atribuições da conta Kerberos no Lync Server 2013

 

_**Tópico modificado em:** 2012-01-16_

Para concluir com sucesso este procedimento, você deve ter feito logon como usuário membro do grupo RTCUniversalServerAdmins.

Você pode usar o cmdlet **Get-CsKerberosAccountAssignment** para consultar informações sobre as atribuições de conta de autenticação Kerberos e relatar as informações sobre as atribuições atuais em sua implantação.

## Para consultar as atribuições da conta de autenticação Kerberos de um site

1.  Como membro do grupo RTCUniversalServerAdmins, faça logon em um computador do domínio executando o Lync Server 2013 ou em um computador em que as ferramentas administrativas estejam instaladas.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute um dos seguintes comandos:
    
      - Para consultar todas as atribuições de conta de autenticação Kerberos em sua organização e retornar as informações de atribuição sobre cada um deles, execute o cmdlet sem parâmetros:
        
            Get-CsKerberosAccountAssignment
    
      - Para consultar todas as atribuições de conta de autenticação Kerberos em sua implantação e retornar as informações de atribuição sobre cada um deles, execute o cmdlet com o parâmetro Identity:
        
            Get-CsKerberosAccountAssignment -Identity "site:SiteName"
        
        Por exemplo:
        
            Get-CsKerberosAccountAssignment -Identity "site:Redmond"
    
      - Para consultar todas as atribuições de conta de autenticação Kerberos em um único site e retornar as informações de atribuição sobre cada um deles, execute o cmdlet com o parâmetro Filter:
        
            Get-CsKerberosAccountAssignment -Filter "SiteName"
        
        Por exemplo:
        
            Get-CsKerberosAccountAssignment -Filter "*Redmond"
        
        > [!NOTE]  
        > Especificar * SiteName para o parâmetro Filter retorna as informações sobre todos os sites que contêm o nome do site especificado em qualquer lugar no identificador de site (por exemplo, todos os sites que contêm a cadeia de caracteres Redmond no identificador de site).
