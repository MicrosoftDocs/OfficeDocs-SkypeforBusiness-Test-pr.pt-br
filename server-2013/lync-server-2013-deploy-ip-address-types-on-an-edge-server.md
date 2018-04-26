---
title: 'Lync Server 2013: Implantar tipos de endereço IP em um Servidor de Borda'
TOCTitle: Implantar tipos de endereço IP em um Servidor de Borda
ms:assetid: 6e2fe7e8-6e90-4d1a-8fc5-e3be92c46571
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204984(v=OCS.15)
ms:contentKeyID: 49307052
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar tipos de endereço IP em um Servidor de Borda para Lync Server 2013

 

_**Tópico modificado em:** 2012-06-14_

Usando o Construtor de Topologias, execute as etapas do procedimento a seguir para implantar tipos de endereço IP em um Servidor de Borda.

## Para implantar tipos de endereço IP em um servidor de borda

1.  No Construtor de Topologias, em **Pools de borda** , clique com o botão direito do mouse no servidor em um pool e selecione **Editar Propriedades** (como alternativa, selecione o servidor e clique em **Editar Propriedades** no menu **Ação** ).

2.  Na janela **Editar Propriedades** , selecione a configuração de endereço IP para a qual deseja oferecer suporte. As figuras a seguir mostram uma configuração de pilha dupla para as interfaces interna e externa.
    
    **Interface interna do servidor de borda com pilha dupla**
    
    ![Página de propriedades gerais do Lync Server](images/JJ204984.5b0883ee-b9f2-4a21-91a9-3286d0beb63b(OCS.15).png "Página de propriedades gerais do Lync Server")
    
    **Interface externa do servidor de borda com pilha dupla**
    
    ![Página de configuração externa/de próximo salto do Lync Server](images/JJ204984.2aa00ce2-ba50-40aa-bbf1-78636016daf9(OCS.15).png "Página de configuração externa/de próximo salto do Lync Server")

3.  Para cada tipo de endereço selecionado, você deve fornecer os endereços internos e externos apropriados.

