---
title: 'Lync Server 2013: Configurar um Servidor de Gerenciamento Central existente'
TOCTitle: Configurar um Servidor de Gerenciamento Central existente
ms:assetid: d715b24a-1256-4a7c-a5ef-1cee41d6b733
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205315(v=OCS.15)
ms:contentKeyID: 49308258
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar um Servidor de Gerenciamento Central existente no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Se você reutilizar um Servidor de Gerenciamento Central de uma implantação existente do Lync Server 2013, você deve executar o procedimento descrito abaixo para garantir que o Painel de Controle do Lync Server e o Windows PowerShell funcionem corretamente.

## Para configurar um Servidor de Gerenciamento Central existente

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Use o cmdlet **Update-CsAdminRole** para atualizar as funções RBAC armazenadas no Servidor de Gerenciamento Central.
    
    > [!NOTE]  
    > Nenhum resultado é esperado a não ser que haja um erro.
