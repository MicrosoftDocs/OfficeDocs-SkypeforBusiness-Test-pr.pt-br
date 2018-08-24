---
title: 'Lync Server 2013: Implantar tipos de endereço IP no Servidor de Mediação'
TOCTitle: Implantar tipos de endereço IP no Servidor de Mediação
ms:assetid: 689ebed5-96ee-4cd4-b7ae-ee2a86a1d9b3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204964(v=OCS.15)
ms:contentKeyID: 49306983
ms.date: 07/28/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantar tipos de endereço IP no Servidor de Mediação para Lync Server 2013

 

_**Tópico modificado em:** 2016-07-28_

Usando a Construtor de Topologias, execute as etapas no seguinte procedimento para implantar tipos de endereço IP em uma Servidor de Mediação.

## Para implantar os tipos de endereço IP em um Servidor de Mediação

  - No Construtor de Topologias, em **Pools de mediação**, clique com o botão direito do mouse no servidor de um pool e selecione **Editar Propriedades**. Como alternativa, selecione o servidor e clique em **Editar Propriedades** no menu **Ação**.

  - Na caixa de diálogo **Editar propriedades**, selecione o tipo de endereço IP que você deseja configurar. Para uma configuração de pilha dual, selecione **Habilitar IPv4** e **Habilitar IPv6**, como mostrado na seguinte imagem.
    
    **Caixa de diálogo Editar Propriedades para o pool de Servidores de Mediação**
    
    ![Página de propriedades gerais do Lync Server com FQDN](images/JJ204964.4e650aca-dbff-4a86-b10d-f0162c032539(OCS.15).png "Página de propriedades gerais do Lync Server com FQDN")
    
      - **Usar todos os endereços IP configurados**. Selecione esta opção se você deseja permitir qualquer endereço IP definido no computador que será usado.
        
        > [!NOTE]  
        > Esta é a opção recomendada para as configurações da versão 6 do IP (IPv6).    
      - **Limitar o uso do serviço para os endereços IP selecionados**. Selecione esta opção para informar um endereço específico a ser usado no novo servidor. Se você selecionar esta opção, terá que inserir um valor para Endereço IP principal.
    
      - **Endereço IP principal**. Insira um endereço IP que o servidor usará para todas as comunicações exceto a PSTN (Rede telefônica pública comutada). O endereço IP inserido deve corresponder ao formato do tipo de endereço selecionado.
    
      - **Endereço IP da PSTN**. Defina um endereço IP da PSTN quando um Servidor de mediação for colocado no Servidor front-end. Este endereço deve ser compatível com o formato do tipo de endereço selecionado.
        
        > [!NOTE]  
        > A instalação de NICs (placas de interface de rede) adicionais para oferecer suporte à configuração do endereço IP da PSTN para Lync Server 2013 não é compatível. Para mais informações sobre configurações de NIC compatíveis para Lync Server 2013, consulte <a href="lync-server-2013-server-hardware-platforms.md">Plataformas de hardware de servidor para Lync Server 2013</a>.
