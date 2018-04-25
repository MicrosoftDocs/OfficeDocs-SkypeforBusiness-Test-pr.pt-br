---
title: Remover BackCompatSite
TOCTitle: Remover BackCompatSite
ms:assetid: 039650e3-541b-45c2-a682-c4fa08423118
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204637(v=OCS.15)
ms:contentKeyID: 49305708
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover BackCompatSite

 

_**Tópico modificado em:** 2012-09-28_

Depois que todos os pools estão desativados e todos os Servidores de Borda desinstalados, execute o assistente de Mesclagem do Construtor de Topologia para remover o **BackCompatSite** .

## Para remover o site BackCompat do Construtor de Topologia

1.  Abra uma implantação existente do Construtor de Topologia.

2.  No menu **Ação** , clique em **Mesclar Topologia R2 2007** .

3.  Clique em **Avançar** para continuar.

4.  Na página **Especificar Borda de Legado** , certifique-se de que a lista de Servidores de Borda esteja vazia. Caso a lista não esteja vazia, utilize o botão **Remover** para remover todos os Servidores de Borda de legado e, então, clique em **Avançar** .
    
    ![Assistente para Mesclar Topologia, página Especificar a Configuração de Borda](images/JJ204637.fb35a59a-711e-4259-b177-7311df1fed3c(OCS.15).jpg "Assistente para Mesclar Topologia, página Especificar a Configuração de Borda")  

5.  Na página **Especificar configuração de porta SIP Interna** , clique em **Avançar** .

6.  Na página **Resumo** , clique em **Avançar** para começar a mesclar as topologias para remover o site de legado.

7.  Na coluna **Status** , verifique se o valor está como **Sucesso** e, então, clique em **Concluir** para fechar o assistente.

8.  No painel à esquerda do Construtor de Topologia, expanda o BackCompatSite e certifique-se que não há servidores listados.

9.  Clique com o botão direito do mouse em **BackCompatSite** e cliquem, então, em **Excluir** .

10. Em **Construtor de Topologias** , selecione o nó superior do **Lync Server** .

11. No menu **Ação** , selecione **Publicar Topologia** e clique em **Avançar** .

12. Quando o **Assistente de publicação** é concluído, clique em **Finalizar** para fechar o assistente.

