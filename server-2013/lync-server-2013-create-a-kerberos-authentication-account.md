---
title: 'Lync Server 2013: Criar uma conta de autenticação Kerberos'
TOCTitle: Criar uma conta de autenticação Kerberos
ms:assetid: 63f0cef6-562a-4209-ae25-71f8dc7c7295
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398449(v=OCS.15)
ms:contentKeyID: 49306918
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar uma conta de autenticação Kerberos no Lync Server 2013

 

_**Tópico modificado em:** 2012-01-02_

Para concluir com êxito esse procedimento, você deve estar conectado ao servidor ou domínio no mínimo como membro do grupo Administradores de Domínio.

Você pode criar contas de autenticação Kerberos para cada site ou pode criar uma única conta de autenticação Kerberos e usá-la para todos os sites. Use os cmdlets do Windows PowerShell para criar e gerenciar as contas, incluindo a identificação das contas atribuídas a cada site. O Construtor de Topologias e o Painel de Controle do Lync Server 2013 não exibem contas de autenticação Kerberos. Use o procedimento a seguir para criar uma ou mais contas de usuário a serem usadas para autenticação Kerberos.

## Para criar uma conta Kerberos

1.  Como membro do grupo Administradores de Domínio, faça logon em um computador do domínio que executa o Lync Server 2013 ou em um computador no qual as ferramentas administrativas estão instaladas.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute o seguinte comando:
    
        New-CsKerberosAccount -UserAccount "Domain\UserAccount" -ContainerDN "CN=Users,DC=DomainName,DC=DomainExtension"
    
    Por exemplo:
    
        New-CsKerberosAccount -UserAccount "Contoso\KerbAuth" -ContainerDN "CN=Users,DC=contoso,DC=com"

4.  Confirme se o objeto Computer foi criado abrindo Usuário e Computadores do Active Directory, expanda o contêiner **Usuários** e confirme se o objeto Computer da conta do usuário está no contêiner.

