---
title: Adicionar Aparelho de Filial Persistente do Lync Server 2013 a sua topologia
TOCTitle: Adicionar Aparelho de Filial Persistente do Lync Server 2013 a sua topologia
ms:assetid: d3142a37-4606-456d-8ea9-6cc0e51e55f3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721896(v=OCS.15)
ms:contentKeyID: 49886426
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionar Aparelho de Filial Persistente do Lync Server 2013 a sua topologia

 

_**Tópico modificado em:** 2012-10-07_

O Microsoft Lync Server 2013Aparelho de Filial Persistente (SBA) não pode ser associado a um Microsoft Lync Server 2010Pool de Front-Ends como o Registrador de backup. O SBA deve ser associado com um Microsoft Lync Server 2013Pool de Front-Ends. Estas etapas assumem um Microsoft Lync Server 2013 SBA. Realize este procedimento no site central.

## Para adicionar sites de filiais com o Microsoft Lync Server 2013 SBA à sua topologia

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Na árvore do console, expanda o site central, expanda em **Sites de filiais** e clique em **Novo Site de Filial** .

3.  Na caixa de diálogo **Definir Novo Site de Filial** , clique em **Nome** e digite um nome para o novo site de filial.

4.  (Opcional) Clique em **Descrição** e digite uma descrição significativa para o site de filial.

5.  Clique em **Avançar** .

6.  (Opcional) Na próxima caixa de diálogo **Definir Novo Site de Filial** , execute uma das seguintes ações:
    
      - Clique em **Cidade** e digite o nome da cidade na qual o site de filial está localizado.
    
      - Clique em **Estado/Região** e digite o nome do estado ou região na qual o site de filial está localizado.
    
      - Clique em **Código do País** e digite o código de chamada de dois dígitos para o país/região no qual o site de filial está localizado.

7.  Clique em **Avançar** e execute uma das seguintes ações:
    
      - Se estiver usando um Aparelho de Filial Persistente ou Servidor de Filial Persistente neste site, certifique-se de que a caixa de seleção **Abrir o Assistente de novo persistente quando o assistente fechar** está marcada.
    
      - Se você não estiver usando um Aparelho de Filial Persistente ou Servidor de Filial Persistente neste site, desmarque a caixa de seleção **Abrir o Assistente de novo persistente quando o assistente fechar** .
    
      - Clique em **Concluir** e siga as orientações no assistente aberto. Para obter informações sobre itens do assistente, consulte [Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md).

8.  Repita as etapas anteriores para cada site de filial que você deseja adicionar à topologia.

## Consulte Também

#### Tarefas

[Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)  
[Definir um gateway de PSTN para um site de filial no Lync Server 2013](lync-server-2013-define-a-pstn-gateway-for-a-branch-site.md)  
[Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)  
[Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)

