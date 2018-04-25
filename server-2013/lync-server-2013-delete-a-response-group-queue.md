---
title: Excluir uma fila de grupo de resposta
TOCTitle: Excluir uma fila de grupo de resposta
ms:assetid: 67c7a489-8c5f-4c6b-9387-9d4c11d43695
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521008(v=OCS.15)
ms:contentKeyID: 49306966
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir uma fila de grupo de resposta

 

_**Tópico modificado em:** 2012-11-01_

Use um dos procedimentos a seguir para excluir uma fila.

## Para usar o Painel de Controle do Lync Server para excluir uma fila

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Grupos de Resposta** e em **Fila**.

4.  No campo de pesquisa, digite parte ou todo o nome da fila que você deseja excluir.

5.  Na lista de filas, clique na fila desejada, clique em **Editar** e em **Excluir**.

6.  Clique em **OK**.

## Para usar cmdlets para excluir uma fila

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute:
    
        Get-CsRgsQueue -Identity <Application Server service> -Name "<name of queue>" | Remove-CsRgsQueue
    
    Por exemplo:
    
        Get-CsRgsQueue -Identity service:ApplicationServer:redmond.contoso.com -Name "Help Desk" | Remove-CsRgsQueue

