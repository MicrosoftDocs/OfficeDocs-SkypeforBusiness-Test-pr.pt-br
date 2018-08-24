---
title: 'Lync Server 2013: Reverter usuários migrados'
TOCTitle: Reverter usuários migrados
ms:assetid: bfabaf0b-9a42-4057-b729-a7ab9eee8c72
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205224(v=OCS.15)
ms:contentKeyID: 49307974
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Reverter usuários migrados no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-07_

Se você precisa reverter para o recurso do repositório de contato unificado, reverta os contatos apenas se você mover o usuário de volta para o Exchange 2010 ou Lync Server 2010. Para reverter, desabilite a política do usuário e execute o cmdlet **Invoke-CsUcsRollback**. Apenas executar o **Invoke-CsUcsRollback** não é suficiente para garantir uma reversão permanente, porque a migração do repositório de contato unificado será iniciada novamente se a política não estiver desabilitada. Por exemplo, se um usuário é revertido porque o Exchange 2013 é revertido para Exchange 2010 e a caixa de correio do usuário é movida para o Exchange 2013, a migração do repositório de contato unificado será iniciada novamente sete dias após a reversão, enquanto o repositório de contato unificado estiver habilitado para o usuário na política de serviços do usuário.

> [!IMPORTANT]  
> O cmdlet <strong>Move-CsUser</strong> reverte automaticamente o repositório de contato do usuário do Exchange 2013 para o Lync Server 2013 nas seguintes situações:<ul>
> 
> <li><p>Quando os usuários são movidos do Lync Server 2013 para o Lync Server 2010.</p></li>
> 
> 
> <li><p>Quando os usuários são migrados entre locais, como quando um usuário é movido do Skype for Business Online para o Lync Server 2013 localmente ou vice-versa.</p></li></ul>


> [!IMPORTANT]  
> Importar os dados do repositório de contato unificado de um banco de dados de backup pode causar com que os dados do repositório de contato unificado e os dados do usuário sejam corrompidos se o modo do repositório de contato unificado mudar entre a exportação e a importação. Por exemplo:<ul>
> 
> <li><p>Se você exportar listas de contatos antes dos contatos do usuário serem migrados para o Exchange 2013 e, após a migração, importar os mesmos dados, os dados do repositório de contato unificado e listas de contatos serão corrompidos.</p></li>
> 
> 
> <li><p>Se você exportar os dados do usuário após migrar usuários para o Exchange 2013, reverter a migração e, por algum motivo, importar os dados após a migração, os dados do repositório de contato unificado e listas de contato serão corrompidos.</p></li></ul>


> [!IMPORTANT]  
> Antes de mover uma caixa de correio do Exchange do Exchange 2013 para o Exchange 2010, o administrador do Exchange deve garantir que o administrador do Lync Server tenha revertido primeiro os contatos do usuário do Lync Server do Exchange 2013 para o Lync Server. Para reverter os contatos do repositório de contato unificado para o Lync Server, consulte o procedimento &quot;Para reverter os contatos do repositório de contato unificado do Exchange 2013 para o Lync Server 2013&quot;, posteriormente nesta seção.

O seguinte procedimento descreve como reverter contatos do usuário. Se você usar o cmdlet **Move-CsUser** para mover usuários entre o Lync Server 2013 e Lync Server 2010, é possível pular estas etapas porque o cmdlet **Move-CsUser** reverte automaticamente o repositório de contato unificado quando move usuários do Lync Server 2013 para o Lync Server 2010. O **Move-CsUser** não desabilita a política do repositório de contato unificado, portanto, a migração para o repositório de contato unificado ocorrerá novamente se o usuário é revertido para o Lync Server 2013.

## Para reverter os contatos do usuário do Lync Server 2013 para o Lync Server 2010

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Desabilite o repositório de contato unificado para os usuários serem revertidos se eles não irão ser migrados novamente após a reversão. (Realize esta etapa apenas se desejar garantir que os usuários não serão migrados novamente no futuro.) Para desabilitar o repositório de contato unificado para usuários individuais, na linha de comando, digite:
    
        Set-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $False
    
    Por exemplo:
    
        Set-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $False

3.  Antes de mover um usuário do Lync Server 2013 para o Lync Server 2010, reverta a Lista de Amigos dos usuários especificados no Lync Server.
    
    > [!IMPORTANT]  
    > Se esta etapa é omitida, a Lista de Amigos será perdida.

4.  Reverta os usuários especificados. Na linha de comando, digite:
    
        Invoke-CsUcsRollback -Identity "<user display name>"
    
    Por exemplo:
    
        Invoke-CsUcsRollback -Identity "Ken Myer"
    
    > [!IMPORTANT]  
    > Não recomendamos usar a opção -Force para forçar a reversão. Se você usar esta opção, os contatos do usuário serão perdidos.

## Para reverter os contatos do repositório de contato unificado do Exchange 2013 para o Lync Server 2013

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Desabilitar o repositório de contato unificado para que os usuários sejam revertidos de forma que eles não serão migrados novamente após a reversão. Para desabilitar o repositório de contato unificado de usuários individuais, na linha de comando, digite:
    
        Set-CsUserServicesPolicy -Identity "<policy name>" -UcsAllowed $False
    
    Por exemplo:
    
        Set-CsUserServicesPolicy -Identity "UCS Enabled Users" -UcsAllowed $False

3.  Reverta os usuários especificados. Na linha de comando, digite:
    
        Invoke-CsUcsRollback -Identity "<user display name>"
    
    Por exemplo:
    
        Invoke-CsUcsRollback -Identity "Ken Myer"
    
    > [!IMPORTANT]  
    > Você deve primeiro reverter o usuário do Lync Server e mover a caixa de correio do Exchange 2013. O administrador do Exchange não pode reverter o Exchange até que a reversão do Lync Server esteja concluída. Não recomendamos usar a opção -Force para forçar a reversão. Se você usar esta opção, os contatos do usuário serão perdidos.

4.  Após reverter o usuário para o Lync Server, o administrador do Exchange pode reverter o usuário do Exchange do Exchange 2013 para o Exchange 2010.

