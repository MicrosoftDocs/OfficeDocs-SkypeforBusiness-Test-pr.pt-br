---
title: Mover um único usuário ao pool piloto
TOCTitle: Mover um único usuário ao pool piloto
ms:assetid: 80d5b365-f153-4c61-a148-f9e18ce6e027
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688109(v=OCS.15)
ms:contentKeyID: 49886282
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover um único usuário ao pool piloto

 

_**Tópico modificado em:** 2012-09-28_

Você pode mover um usuário do pool Office Communications Server 2007 R2 para o pool piloto Lync Server 2013 usando Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013. No exemplo abaixo, na coluna de pool Registrar, **\<Office Communications Server\>** está o pool Office Communications Server 2007 R2 e todos os seis usuários estão conectados a este pool. Use os procedimentos a seguir para mover um usuário para seu pool Lync Server 2013 usando Painel de Controle do Lync Server 2013 e Shell de Gerenciamento do Lync Server.

![Procurar usuários de OCS no Painel de Controle do Lync Server](images/JJ688109.d2008fd6-868b-4f26-84cf-57bb69e073d3(OCS.15).jpg "Procurar usuários de OCS no Painel de Controle do Lync Server")

## Para mover um usuário usando o Painel de Controle do Lync Server 2013

1.  Faça o logon no Servidor Front-End com uma conta que seja membro do grupo RTCUniversalServerAdmins ou membro da função administrativa do CsAdministrator ou do CsUserAdministrator .

2.  Abrir o Painel de Controle do Lync Server.

3.  Clique em **Usuários**.

4.  Na guia **Pesquisa de Usuário**, clique no botão **Pesquisar**.

5.  Depois, clique em **Adicionar filtro**.

6.  Crie um filtro onde o **usuário do Office Communications Server** seja igual a **True**.

7.  Clique em **Localizar** e procure por usuários herdados do Office Communications Server 2007 R2.
    
    ![Procurar usuários de OCS no Painel de Controle do Lync Server](images/JJ688109.09528349-7915-41e1-91b4-6ab5c12b1b38(OCS.15).jpg "Procurar usuários de OCS no Painel de Controle do Lync Server")  

8.  Selecione um usuário que você deseja mover para o pool de Lync Server 2013. Nesse exemplo, moveremos o usuário Sara Davis.

9.  No menu **Ação**, selecione **Mover usuários selecionados para o pool**.

10. A partir da lista suspensa, selecione o pool do Lync Server 2013.

11. Clique em **Ação** e, em seguida, em **Mover usuários selecionados para o pool**. Clique em **OK**.
    
    ![Definindo o pool de destinos na a caixa de diálogo Mover Usuários](images/JJ688109.d7dc0759-87c5-4c23-938f-361576621504(OCS.15).jpg "Definindo o pool de destinos na a caixa de diálogo Mover Usuários")  

12. Verifique se o **pool registrador** agora contém uma coluna para o usuário do Lync Server 2013pool, que indica que o usuário foi movido com êxito

## Para mover um usuário utilizando o Shell de Gerenciamento do Lync Server 2013

1.  Abra o Shell de Gerenciamento do Lync Server.

2.  Na linha de comando, digite o seguinte:
    
        Move-CsLegacyUser -Identity "David Pelton" -Target "pool02.contoso.net"

3.  Então, na linha de comando, digite o seguinte:
    
        Get-CsUser -Identity "David Pelton"

4.  A identidade do **RegistrarPool** agora aponta para o pool do Lync Server 2013. A presença dessa identidade confirma que o usuário foi movido com sucesso.
    
    ![Saída do cmdlet Get-CsUser com filtro de identidade](images/JJ205401.bc5d4672-8068-4475-b882-dbd305c801a9(OCS.15).jpg "Saída do cmdlet Get-CsUser com filtro de identidade")  
    
    > [!NOTE]  
    > Para obter detalhes sobre o cmdlet <strong>Get-CsUser</strong>, execute: <strong>Get-Help Get-CsUser –Detailed</strong>
