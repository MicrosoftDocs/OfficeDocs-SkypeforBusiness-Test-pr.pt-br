---
title: 'Lync Server 2013: Adicionar sites de filial a sua topologia'
TOCTitle: Adicionar sites de filial a sua topologia
ms:assetid: b9c35fb0-0081-4aeb-8f95-ac2fcc6c3335
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412905(v=OCS.15)
ms:contentKeyID: 49307907
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar sites de filial a sua topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-05_

Os sites de filial representam os escritórios de filial físicos que estão conectados aos escritórios principais por um link WAN link. Para adicionar um site de filial à sua topologia do Lync, execute este procedimento no site central.

## Para adicionar sites de filiais à sua topologia

1.  Clique em **Iniciar** , **Todos os programas** , **Microsoft Lync Server** e em **Construtor de topologias do Lync Server** .

2.  Na árvore do console, expanda o site central, clique com o botão direito do mouse em **Sites de filia** e clique em **Novo site de filial** .

3.  Na caixa de diálogo **Definir Novo Site de Filial** , clique em **Nome** e digite o nome do site de filial.

4.  (Opcional) Clique em **Descrição** e digite uma descrição significativa para o site de filial.

5.  Clique em **Avançar** .

6.  (Opcional) Na próxima caixa de diálogo **Definir Novo Site de Filial** , execute uma das seguintes ações:
    
      - Clique em **Cidade** e digite o nome da cidade na qual o site de filial está localizado.
    
      - Clique em **Estado/Região** e digite o nome do estado ou região na qual o site de filial está localizado.
    
      - Clique em **Código do País** e digite o código de chamada de dois dígitos para o país/região no qual o site de filial está localizado.

7.  Clique em **Avançar** e execute uma das seguintes ações:
    
      - Se você estiver usando um Aparelho de Filial Persistente ou um servidor neste site,certifique-se de marcar a caixa de seleção **Abrir o Novo Assistente Persistente quando este assistente fechar** , clique em **Concluir** e siga as direções no assistente que abrir. Para obter mais informações sobre itens do assistente, consulte [Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md).
    
      - Se você não estiver usando um Aparelho de Filial Persistente ou servidores neste site, desmarque a caixa de seleção **Abrir o Novo Assistente Persistente quando este assistente fechar** e clique em **Concluir** .

8.  Repita as etapas anteriores para cada site de filial que você deseja adicionar à topologia.

**Próxima etapa:**

Para Aparelhos de Filial Persistentes ou Servidores: [Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

Para conectividade PSTN não resiliente: [Definir um gateway de PSTN para um site de filial no Lync Server 2013](lync-server-2013-define-a-pstn-gateway-for-a-branch-site.md), [Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md) ou [Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)

