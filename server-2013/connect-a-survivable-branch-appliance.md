---
title: Conectar um Aparelho de Filial Persistente
TOCTitle: Conectar um Aparelho de Filial Persistente
ms:assetid: fe3167e2-d1b1-4cd4-bf30-262e0e7d14e8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721948(v=OCS.15)
ms:contentKeyID: 49886496
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conectar um Aparelho de Filial Persistente

 

_**Tópico modificado em:** 2012-10-19_

Cada Aparelho de Filial Persistente (SBA) está associado a um pool Front End que serve como registrador de backup para o SBA. Quando o pool Front End migra para Lync Server 2013, o SBA deve estar desassociado do pool Frond End Lync Server 2010 enquanto o pool é atualizado. Uma vez que o pool tenha migrado para Lync Server 2013, o SBA pode ser associado novamente com o pool Front End atualizado. Isso envolve excluir o SBA da topologia herdada Lync Server 2010 no Construtor de Topologias e, em seguida, adicionando o SBA à topologia Lync Server 2013. Os usuários hospedados no SBA herdado Lync Server 2010 devem primeiramente ser movidos a outro pool Front End antes de remover o SBA da topologia. Uma vez que o SBA for adicionado à topologia de Lync Server 2013, aqueles usuários podem ser movidos de volta ao SBA. As etapas são resumidas abaixo:

1.  Mova os usuários ramificados hospedados no SBA herdado Lync Server 2010 para outro pool Front End.

2.  Remova o SBA da topologia herdada Lync Server 2010 para desconectar o pool Front End existente como um registrador de backup.

3.  Adicione o SBA à topologia Lync Server 2013 e configure esse novo pool Front End como registrador de backup.

4.  Mova os usuários ramificados ao novo SBA Lync Server 2013.

**Adicione Lync Server 2010 SBA Branch Site à sua topologia**

1.  Abra o **Construtor de Topologias**.

2.  No painel esquerdo, clique com o botão direito do mouse em **Locais ramificados** e clique em **Novo local ramificado**.

3.  Na caixa de diálogo **Definir Novo Site de Filial**, clique em **Nome**, e digite o nome do site de filial.

4.  (Opcional) Clique em **Descrição**, e digite uma descrição significativa para o site de filial.

5.  Clique em **Avançar**.

6.  (Opcional) Na próxima caixa de diálogo **Definir Novo Site de Filial**, execute uma das seguintes ações:
    
    1.  Clique em **Cidade**, e digite o nome da cidade na qual o site de filial está localizado.
    
    2.  Clique em **Estado/Região**, e digite o nome do estado ou região no qual o site de filial está localizado.
    
    3.  Clique em **Código do País**, e digite o código de chamada de dois dígitos para o país/região no qual o site de filial está localizado.

7.  Clique em **Avançar**, e execute uma das seguintes ações:
    
    1.  Se você estiver usando um Aparelho de Filial Persistente Lync 2010 ou Servidor nesse site, certifique-se de desmarcar a caixa de seleção **Abrir o Novo Assistente Persistente quando este assistente fechar** e clique em **Concluir**.

8.  Para associar o SBA herdado Lync Server 2010 ao pool Front End Lync Server 2013:
    
    1.  Expanda o local ramificado que foi criado.
    
    2.  Clique com o botão direito do mouse em **Lync Server 2010** e clique em **Novo**.
    
    3.  Clique em **Aparelho de Filial Persistente**

9.  Siga as instruções no assistente que abrir. Para obter informações sobre os itens do assistente, consulte [Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md).
    
    > [!NOTE]  
    > Um Lync Server 2010 Aparelho de Filial Persistente pode ser associado somente a um Repositório de Monitoramento Lync Server 2010.

10. Se você não estiver usando um Aparelho de Filial Persistente ou Servidor nesse site, desmarque a caixa de seleção **Abrir o Novo Assistente Persistente quando este assistente fechar** e clique em **Concluir**.

11. Repita as etapas anteriores para cada site de filial que você deseja adicionar à topologia.

