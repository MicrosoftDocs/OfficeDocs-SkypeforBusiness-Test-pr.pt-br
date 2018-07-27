---
title: 'Lync Server 2013: Implantar tipos de endereço IP em um Servidor Front-End Server'
TOCTitle: Implantar tipos de endereço IP em um Servidor Front-End Server
ms:assetid: b6c8e0f9-ec8e-4a4e-a525-756f9cd6b9d0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205191(v=OCS.15)
ms:contentKeyID: 49307879
ms.date: 07/28/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar tipos de endereço IP em um Servidor Front-End Server para Lync Server 2013

 

_**Tópico modificado em:** 2016-07-28_

Usando a Construtor de Topologias, execute as etapas no seguinte procedimento para implantar tipos de endereço IP em uma Servidor Front-End.

## Implantar tipos de endereço IP em um Servidor front-end

1.  Em **Pools de front-end do Enterprise Edition** , clique com o botão direito em um servidor de um pool e selecione **Editar propriedades** . (Como alternativa, selecione o servidor e clique em **Editar propriedades** no menu **Ação** ).

2.  Na caixa de diálogo **Editar propriedades** , selecione o tipo de endereço IP que você deseja configurar. Para uma configuração de pilha dual, selecione **Habilitar IPv4** e **Habilitar IPv6** , como mostrado na seguinte imagem.
    
    **Editar a caixa de diálogo Propriedades do pool do servidor front-end**
    
    ![Caixa de diálogo Propriedades de Edição de Servidor Front-End](images/JJ205191.737a9d71-c0bc-4a54-9608-9e028dacc814(OCS.15).png "Caixa de diálogo Propriedades de Edição de Servidor Front-End")
    
      - **Usar todos os endereços IP configurados**. Selecione esta opção se você deseja permitir qualquer endereço IP definido no computador que será usado.
        
        > [!NOTE]  
        > Esta é a opção recomendada para as configurações da versão 6 do IP (IPv6).    
      - **Limitar uso de serviços para selecionar endereços IP**. Selecione esta opção para especificar um endereço específico para usar um novo servidor. Se você selecionar esta opção, é necessário inserir um valor para o **Endereço IP principal** .
    
      - **Endereço IP principal**. Insira um endereço IP que o servidor usará para todas as comunicações exceto a PSTN (Rede telefônica pública comutada). O endereço IP inserido deve corresponder ao formato do tipo de endereço selecionado.
    
      - **Endereço IP da PSTN**. Defina um endereço IP da PSTN quando um Servidor de mediação for colocado no Servidor front-end. Este endereço deve ser compatível com o formato do tipo de endereço selecionado.

