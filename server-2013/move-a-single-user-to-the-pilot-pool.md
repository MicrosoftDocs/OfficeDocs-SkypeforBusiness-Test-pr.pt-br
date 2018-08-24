---
title: Mover um único usuário ao pool piloto
TOCTitle: Mover um único usuário ao pool piloto
ms:assetid: e9de81a8-40dd-4446-81e7-a2b810eaea50
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205401(v=OCS.15)
ms:contentKeyID: 49308476
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover um único usuário ao pool piloto

 

_**Tópico modificado em:** 2012-09-26_

Você pode mover um usuário de seu pool do Lync Server 2010 para o seu pool piloto do Lync Server 2013 usando Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013. No exemplo abaixo, na coluna do pool do Registrador, **pool01.contoso.net** é o pool do Lync Server 2010, e todos os seis usuários estão conectados a este pool. Use os procedimentos a seguir para mover um usuário para o seu pool do Lync Server 2013 usando Painel de Controle do Lync Server 2013 e Shell de Gerenciamento do Lync Server.

## Para mover um usuário usando o Painel de Controle do Lync Server 2013

**Lista de usuários no Painel de Controle do Lync Server 2013**

![Painel de Controle do Lync Server, Caixa de diálogo Mover Usuário](images/JJ205401.a2bce284-0392-4db3-9bb2-9f12699738e7(OCS.15).jpg "Painel de Controle do Lync Server, Caixa de diálogo Mover Usuário")

1.  Faça logon no Servidor Front-end com uma conta que seja membro do grupo de RTCUniversalServerAdmins ou membro da função administrativa do CsAdministrator ou CsUserAdministrator.

2.  Abra o **Painel de Controle do Lync Server**.

3.  Clique em **Usuários**, em Pesquisar e em **Localizar**.

4.  Selecione o usuário que deseja mover para o pool de Lync Server 2013. Neste exemplo, moveremos a usuária Sara Davis.

5.  No menu **Ação**, selecione **Mover usuários selecionados para o pool**.

6.  Na lista suspensa, selecione o pool de Lync Server 2013.

7.  Clique em **Ação** e em **Mover usuários selecionados para o pool**. Clique em **OK**.
    
    ![Mover Usuários, caixa de diálogo de pool de registros de destino](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "Mover Usuários, caixa de diálogo de pool de registros de destino")  

8.  Verifique se a coluna **Pool de registradores** para o usuário agora contém o pool de Lync Server 2013, o que indica que o usuário foi movido com êxito.

## Para mover um usuário usando o Shell de Gerenciamento do Lync Server 2013

1.  Abra o Shell de Gerenciamento do Lync Server.

2.  Na linha de comando, digite o seguinte:
    
        Move-CsUser -Identity "David Pelton" -Target "pool02.contoso.net"

3.  Então, na linha de comando, digite o seguinte:
    
        Get-CsUser -Identity "David Pelton"

4.  A identidade do **RegistrarPool** agora aponta para o pool do Lync Server 2013. A presença dessa identidade confirma que o usuário foi movido com sucesso.
    
    ![Saída do cmdlet Get-CsUser com filtro de identidade](images/JJ205401.bc5d4672-8068-4475-b882-dbd305c801a9(OCS.15).jpg "Saída do cmdlet Get-CsUser com filtro de identidade")  
    
    > [!NOTE]  
    > Para obter detalhes sobre o cmdlet <strong>Get-CsUser</strong>, execute: <strong>Get-Help Get-CsUser –Detailed</strong>
