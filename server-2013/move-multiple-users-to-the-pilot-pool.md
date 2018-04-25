---
title: Mover vários usuários para o pool piloto
TOCTitle: Mover vários usuários para o pool piloto
ms:assetid: 90d0590c-922c-4933-b778-9dd850b59310
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205096(v=OCS.15)
ms:contentKeyID: 49307468
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover vários usuários para o pool piloto

 

_**Tópico modificado em:** 2012-10-02_

Você pode mover vários usuários do seu pool Lync Server 2010 para seu pool piloto Lync Server 2013, usando Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Para mover vários usuários usando o Painel de Controle do Lync Server 2013

1.  Abra **Painel de Controle do Lync Server**.

2.  Clique em **Usuários**, em Pesquisar e em **Localizar**.

3.  Selecione dois usuários que você deseja mover para o pool Lync Server 2013. Neste exemplo, vamos mover os usuários Chen Yang e Claus Hansen.
    
    ![Mover usuários para o pool de registro específico](images/JJ205096.70d510e1-8e6b-40a5-a80b-27cbc63fc337(OCS.15).jpg "Mover usuários para o pool de registro específico")  

4.  No menu **Ação**, selecione **Mover usuários selecionados para o pool**.

5.  A partir da lista suspensa, selecione o pool do Lync Server 2013.

6.  Clique em **Ação** e depois em **Mover usuários selecionados para o pool**. Clique em OK.
    
    ![Mover Usuários, caixa de diálogo de pool de registros de destino](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "Mover Usuários, caixa de diálogo de pool de registros de destino")  

7.  Verifique se a coluna **Pool do Registrador** dos usuários agora contém o pool Lync Server 2013, o que indica que os usuários foram movidos com êxito.

## Para mover vários usuários utilizando o Shell de Gerenciamento do Lync Server 2013

1.  Abra o Shell de Gerenciamento do Lync Server 2013.

2.  Na linha de comando, digite o seguinte e substitua **User1** e **User2** pelos nomes de usuário específicos que deseja mover e substitua o **pool\_FQDN** pelo nome do pool de destino. Neste exemplo, vamos mover os usuários Hao Chen e Katie Jordan.
    
        Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsUser -Target "pool_FQDN"
    
    ![Exemplo de cmdlet PowerShell Get-CsUser](images/JJ205096.767ff9fc-755d-4a80-a710-5b1367aecbe0(OCS.15).jpg "Exemplo de cmdlet PowerShell Get-CsUser")  

3.  Na linha de comando, digite o seguinte
    
        Get-CsUser -Identity "User1"

4.  A identidade do **Pool de registradores** deve apontar agora para o pool especificado como **pool\_FQDN** na etapa anterior. A presença dessa identidade confirma que o usuário foi movido com sucesso. Repita a etapa para verificar se o **User2** foi movido.
    
    ![Saída do cmdlet PowerShell Get-UsUser -Identity](images/JJ205096.8ff04c67-37a0-4156-bfbc-28f9f7b137c8(OCS.15).jpg "Saída do cmdlet PowerShell Get-UsUser -Identity")  

## Para mover todos os usuários ao mesmo tempo usando o Shell de Gerenciamento do Lync Server 2013

Neste exemplo, todos os usuários foram devolvidos para o pool Lync Server 2010 (pool01.contoso.net). Usando o Shell de Gerenciamento do Lync Server 2013, vamos mover todos os usuários ao mesmo tempo para o pool Lync Server 2013 (pool02.contoso.net).

1.  Abra o **Shell de Gerenciamento do Lync Server 2013**.

2.  Na linha de comando, digite o seguinte:
    
        Get-CsUser -OnLyncServer | Move-CsUser -Target "pool_FQDN"
    
    ![Cmdlet PowerShell e resultados no Shell de Gerenciamento](images/JJ205096.1e57ccb1-9378-4dc7-82b7-dcaa63a285c6(OCS.15).png "Cmdlet PowerShell e resultados no Shell de Gerenciamento")  

3.  Depois, execute **Get-CsUser** de um dos usuários piloto.
    
        Get-CsUser -Identity "Hao Chen"

4.  A identidade **Pool de registradores** de cada usuário aponta agora para o pool que você especificou como "pool\_FQDN" na etapa anterior. A presença dessa identidade confirma que o usuário foi movido com sucesso.

5.  Além disso, podemos exibir a lista de usuários no Painel de Controle do Lync Server 2013 e verificar que o valor do Pool de registradores aponta agora para o pool Lync Server 2013.
    
    ![Lista de usuários do Painel de Controle do Lync Server 2013](images/JJ205096.3f2e87a7-ec59-43c5-82cb-e770108bfb04(OCS.15).jpg "Lista de usuários do Painel de Controle do Lync Server 2013")

