---
title: 'Lync Server 2013: Herança de permissões está desabilitado em computadores, usuários ou contêiners InetOrgPerson'
TOCTitle: Herança de permissões está desabilitado em computadores, usuários ou contêiners InetOrgPerson
ms:assetid: c472ad21-a93d-4fcb-a3d9-60a2134a87fa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412970(v=OCS.15)
ms:contentKeyID: 49308037
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Herança de permissões está desabilitado em computadores, usuários ou contêiners InetOrgPerson no Lync Server 2013

 

_**Tópico modificado em:** 2014-12-19_

Em uma instância bloqueada dos Serviços de Domínio Active Directory, os objetos de Usuários e Computador são quase sempre colocados em unidades organizacionais específicas com herança de permissões desabilitada para ajudar a proteger a delegação administrativa e para habilitar o uso de GPOs (Objetos de Política de Grupo) para impor políticas de segurança.

A preparação de domínio e ativação do servidor definem as ACEs (entradas de controle de acesso) exigidas pelo Lync Server 2013. Quando a herança de permissões está desabilitada, os grupos de segurança do Lync Server não podem herdar essas ACEs. Quando essas permissões não são herdadas, os grupos de segurança do Lync Server não podem acessar as configurações e os dois problemas a seguir surgem:

  - Para administrar Usuários, InetOrgPersons e Contatos e para operar servidores, os grupos de segurança do Lync Server exigem ACEs definidas pelo procedimento de preparação de domínio nos conjuntos de propriedade de cada usuário, RTC (comunicações em tempo real), Pesquisa de usuário de RTC e Informações públicas. Quando a herança de permissões está desabilitada, os grupos de segurança não herdam essas ACEs e não podem gerenciar servidores ou usuários.

  - Para descobrir servidores e pools, os servidores que executam o Lync Server dependem das ACEs definidas pela ativação em objetos relacionados ao computador, incluindo o objeto Microsoft Container and Server. Quando a herança de permissões está desabilitada, os grupos de segurança, servidores e pools não herdam essas ACEs e não podem beneficiar-se delas.

Para resolver esses problemas, o Lync Server fornece o cmdlet **Grant-CsOuPermission**. Esse cmdlet define as ACEs do Lync Server necessárias diretamente em um contêiner e unidades organizacionais especificadas e nos objetos dentro do contêiner ou unidade organizacional.

## Definir permissões para os objetos Usuário, InetOrgPerson e Contato após executar a preparação do domínio

Em um ambiente bloqueado do Active Directory onde a herança de permissões está desabilitada, a preparação do domínio não define as ACEs necessárias nos contêineres ou unidades organizacionais que possuem os objetos Usuários ou InetOrgPerson dentro do domínio. Nessa situação, é necessário executar o cmdlet **Grant-CsOuPermission** em cada contêiner ou UO que possua objetos Usuário ou InetOrgPerson para os quais a herança de permissões está desabilitada. Se você tiver uma topologia de floresta central, também deverá realizar esse procedimento nos contêineres ou UOs que possuem os objetos de contato. Para obter detalhes sobre as topologias de floresta central, consulte [Topologias do Active Directory suportadas no Lync Server 2013](lync-server-2013-supported-active-directory-topologies.md) na documentação Suporte. O parâmetro ObjectType especifica o tipo de objeto. O parâmetro OU especifica a unidade organizacional.

Esse cmdlet adiciona as ACEs necessárias diretamente nos contêineres ou UO especificadas e nos objetos Usuário ou InetOrgPerson dentro do contêiner.

Você precisa de direitos de usuário equivalentes à associação no grupo Admins. do Domínio a fim de executar esse cmdlet. Se as ACEs do usuário autenticado também tiverem sido removidas do ambiente bloqueado, será necessário atribuir a essa conta ACEs para acesso de leitura nos contêineres ou UOs relevantes no domínio raiz da floresta, conforme descrito em [Permissões de usuário autenticado são removidas no Lync Server 2013](lync-server-2013-authenticated-user-permissions-are-removed.md) ou usar uma conta membro do grupo Administradores de Empresa.

**Para definir as ACEs necessárias para os objetos Usuário, InetOrgPerson e Contato**

1.  Faça logon em um computador associado ao domínio com uma conta que seja membro do grupo Admins. do Domínio ou que possua direitos de usuário equivalentes.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Grant-CsOuPermission -ObjectType <User | Computer | InetOrgPerson | Contact | AppContact | Device> 
        -OU <DN name for the OU container relative to the domain root container DN> [-Domain <Domain FQDN>]
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.
    
    Por exemplo:
    
        Grant-CsOuPermission -ObjectType "User" -OU "cn=Redmond,dc=contoso,dc=net" -Domain "contoso.net"

4.  No arquivo de log, procure Resultado da execução **\<Sucesso\>** no final de cada tarefa, a fim de verificar se as permissões foram definidas, e feche a janela do log. Uma alternativa é executar o seguinte comando para determinar se as permissões foram definidas:
    
        Test-CsOuPermission -ObjectType <type of object> 
        -OU <DN name for the OU container relative to the domain root container DN> 
        [-Domain <Domain FQDN>] [-Report <fully qualified path and name of file to create>]
    
    Por exemplo:
    
        Test-CsOuPermission -ObjectType "User" -OU "cn=Redmond,dc=contoso,dc=net" -Domain "contoso.net" -Report "C:\Log\OUPermissionsTest.html"

## Definir permissões para os objetos Computador após executar a preparação do domínio

Em um ambiente bloqueado do Active Directory no qual a herança de permissões está desabilitada, a preparação do domínio não define as ACEs necessárias nos contêineres ou UOs com objetos Computador dentro do domínio. Nessa situação, você precisa executar o cmdlet **Grant-CsOuPermission** em cada contêiner ou UO que tenha computadores executando o Lync Server no qual a herança de permissões esteja desabilitada. O parâmetro ObjectType especifica o tipo de objeto.

Esse procedimento adiciona as ACEs necessárias diretamente nos contêineres especificados.

Você precisa de direitos de usuário equivalentes à associação no grupo Admins. do Domínio a fim de executar esse cmdlet. Se as ACEs do usuário autenticado também tiverem sido removidas, será necessário atribuir a essa conta ACEs para acesso de leitura nos contêineres ou UOs relevantes no domínio raiz da floresta, conforme descrito em [Permissões de usuário autenticado são removidas no Lync Server 2013](lync-server-2013-authenticated-user-permissions-are-removed.md) ou usar uma conta membro do grupo Administradores de Empresa.

**Para definir as ACEs necessárias aos objetos de computador**

1.  Faça logon no computador do domínio com uma conta que seja membro do grupo Admins. do Domínio ou que possua direitos de usuário equivalentes.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Grant-CsOuPermission -ObjectType <Computer> 
        -OU <DN name for the computer OU container relative to the domain root container DN> 
        [-Domain <Domain FQDN>][-Report <fully qualified path and name of output report>]
    
    Se você não especificar o parâmetro Domain, o valor padrão será o domínio local.
    
    Por exemplo:
    
        Grant-CsOuPermission -ObjectType "Computer" -OU "ou=Lync Servers,dc=litwareinc,dc=com" -Report "C:\Logs\OUPermissions.xml"

4.  No arquivo de log de exemplo, C:\\Logs\\OUPermissions.xml, procure por Resultado da Execução **\<Sucesso\>** no final de cada tarefa e verifique se há erros e feche o log. É possível executar o seguinte cmdlet para testar as permissões:
    
        Test-CsOuPermission -ObjectType <type of object> 
        -OU <DN name for the OU container relative to the domain root container DN> [-Domain <Domain FQDN>]
    
    Por exemplo:
    
        Test-CsOuPermission -ObjectType "user","contact" -OU "cn=Bellevue,dc=contoso,dc=net" -Domain "contoso.net"
    
    > [!NOTE]  
    > Se você executar a preparação do domínio no domínio raiz da floresta, em um ambiente do Active Directory bloqueado, lembre-se de que o Lync Server exige acesso aos contêineres Esquema e Configuração do Active Directory.<br />    Se a permissão de usuário autenticado padrão for removida dos contêineres Esquema ou Configuração no AD DS, somente os membros do grupo Administradores de esquemas (para o contêiner Esquema) ou do grupo Administradores de empresa (para o contêiner Configuração) terão permissão para acessar o contêiner especificado. Como Setup.exe, os cmdlets do Shell de Gerenciamento do Lync Server e o Painel de Controle do Lync Server exigem acesso a esses contêineres, a configuração e instalação das ferramentas administrativas falhará, a menos que o usuário que está executando a instalação tenha direitos de usuário equivalentes à associação de grupo Administradores de esquemas e Administradores de empresa.<br />    Para corrigir essa situação, é necessário conceder ao grupo RTCUniversalGlobalWriteGroup acesso de Leitura e Gravação nos contêineres Esquema e Configuração.
