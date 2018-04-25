---
title: Mover vários usuários para o pool piloto
TOCTitle: Mover vários usuários para o pool piloto
ms:assetid: 9492797f-2a26-4773-8ad2-97cb53fa68fc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688143(v=OCS.15)
ms:contentKeyID: 49886319
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover vários usuários para o pool piloto

 

_**Tópico modificado em:** 2012-10-02_

Você pode mover vários usuários do seu pool Office Communications Server 2007 R2 para seu pool piloto Lync Server 2013, usando Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013.

## Para mover vários usuários usando o Painel de Controle do Lync Server 2013

1.  Abra **Painel de Controle do Lync Server** .

2.  Na guia **Pesquisa de Usuário**, clique no botão **Pesquisar**.

3.  Depois, clique em **Adicionar filtro**.

4.  Crie um filtro onde o **usuário do Office Communications Server** seja igual a **True**.

5.  Clique em **Localizar** e procure por usuários herdados do Office Communications Server 2007 R2.

6.  Selecione dois usuários que você deseja mover para o pool Lync Server 2013. Neste exemplo, vamos mover os usuários Chen Yang e Claus Hansen.
    
    ![Lista de usuários exibida com base na procura de usuários de OCS](images/JJ688143.76beb4fa-72e0-41ef-b96e-3553e96645c0(OCS.15).jpg "Lista de usuários exibida com base na procura de usuários de OCS")  

7.  No menu **Ação** , selecione **Mover usuários selecionados para o pool** .

8.  A partir da lista suspensa, selecione o pool do Lync Server 2013.

9.  Clique em **Ação** e depois em **Mover usuários selecionados para o pool** . Clique em OK.
    
    ![Mover Usuários, caixa de diálogo de pool de registros de destino](images/JJ205401.8a375003-dc00-4541-b578-4d88f2010601(OCS.15).png "Mover Usuários, caixa de diálogo de pool de registros de destino")  

10. Verifique se a coluna **Pool do Registrador** dos usuários agora contém o pool Lync Server 2013, o que indica que os usuários foram movidos com êxito.

## Para mover vários usuários usando o Shell de Gerenciamento do Lync Server 2013

1.  Abra o Shell de Gerenciamento do Lync Server 2013.

2.  Na linha de comando, digite o seguinte e substitua **User1** e **User2** pelos nomes de usuário específicos que deseja mover e substitua o **pool\_FQDN** pelo nome do pool de destino. Neste exemplo, vamos mover os usuários Hao Chen e Katie Jordan.
    
        Get-CsUser -Filter {DisplayName -eq "User1" -or DisplayName - eq "User2"} | Move-CsLegacyUser -Target "pool_FQDN"
    
    ![Cmdlet de exemplo para mover um usuário legado](images/JJ688143.57cfc28e-3df5-459f-83ef-8b0edf182a25(OCS.15).jpg "Cmdlet de exemplo para mover um usuário legado")  

3.  Na linha de comando, digite o seguinte
    
        Get-CsUser -Identity "User1"

4.  A identidade do **Pool de registradores** deve apontar agora para o pool especificado como **pool\_FQDN** na etapa anterior. A presença dessa identidade confirma que o usuário foi movido com sucesso. Repita a etapa para verificar se o **User2** foi movido.
    
    ![Saída do cmdlet PowerShell Get-UsUser -Identity](images/JJ205096.8ff04c67-37a0-4156-bfbc-28f9f7b137c8(OCS.15).jpg "Saída do cmdlet PowerShell Get-UsUser -Identity")  

## Para mover todos os usuários ao mesmo tempo usando o Shell de Gerenciamento do Lync Server 2013

Neste exemplo, todos os usuários foram devolvidos para o pool Office Communications Server 2007 R2 (pool01.contoso.net). Usando o Shell de Gerenciamento do Lync Server 2013, vamos mover todos os usuários ao mesmo tempo para o pool Lync Server 2013 (pool02.contoso.net).

1.  Abra o **Shell de Gerenciamento do Lync Server 2013**.

2.  Na linha de comando, digite o seguinte:
    
        Get-CsUser -OnOfficeCommunicationServer | Move-CsLegacyUser -Target "pool_FQDN"
    
    ![Cmdlet de exemplo para mover todos os usuários legados em um pool](images/JJ688143.e6a2d578-296e-476c-bd45-d757917ea853(OCS.15).jpg "Cmdlet de exemplo para mover todos os usuários legados em um pool")  

3.  Depois, execute **Get-CsUser** de um dos usuários piloto.
    
        Get-CsUser -Identity "Hao Chen"

4.  A identidade **Pool de registradores** de cada usuário aponta agora para o pool que você especificou como "pool\_FQDN" na etapa anterior. A presença dessa identidade confirma que o usuário foi movido com sucesso.

5.  Além disso, podemos exibir a lista de usuários no Painel de Controle do Lync Server 2013 e verificar que o valor do Pool de registradores aponta agora para o pool Lync Server 2013.
    
    ![Lista de usuários do Painel de Controle do Lync Server 2013](images/JJ205096.3f2e87a7-ec59-43c5-82cb-e770108bfb04(OCS.15).jpg "Lista de usuários do Painel de Controle do Lync Server 2013")

