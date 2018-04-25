---
title: Conectar pool piloto aos Servidores de Borda herdados
TOCTitle: Conectar pool piloto aos Servidores de Borda herdados
ms:assetid: 9ed13c41-f3ab-4e1d-beb6-a00152c541e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205136(v=OCS.15)
ms:contentKeyID: 49307614
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conectar pool piloto aos Servidores de Borda herdados

 

_**Tópico modificado em:** 2012-10-02_

Após a implantação do Lync Server 2013, uma rota de federação desse site não está configurada. Para usar essa rota federada que está sendo usada pelo Office Communications Server 2007 R2, o Lync Server 2013 deve ser configurado para usar essa rota.

Para ativar o site do Lync Server 2013 para usar o Diretor e Servidor de Borda do BackCompatSite, use o Construtor de Topologia para associar com o pool de borda antigo.

## Para associar o pool de Borda herdado usando o Construtor de Topologia

1.  Abra a topologia do pool piloto no Construtor de Topologia.

2.  Selecione o site do Lync Server 2013.

3.  No menu **Ação**, clique em **Editar Propriedades**.

4.  Em **Atribuição da rota de federação do site**, selecione **Habilitar federação SIP** e selecione o Diretor do Office Communications Server 2007 R2 ou o Servidor de Borda do Office Communications Server 2007 R2 se nenhum Diretor estiver listado.
    
    ![Caixa de diálogo Editar Propriedades, página Rota de federação](images/JJ205136.bc13014b-3578-4d9e-9ff7-bdd09130b676(OCS.15).jpg "Caixa de diálogo Editar Propriedades, página Rota de federação")  

5.  Clique em **OK** para fechar a página **Editar Propriedades**.

6.  No Construtor de Topologia, no nó Lync Server 2013, navegue até o **servidor do Standard Edition** ou **Pools de front-end do Enterprise Edition**, clique com o botão direito no pool e clique em **Editar propriedades**.

7.  Em **Associações**, marque a caixa de seleção próxima ao **Associar pool de Borda (para componentes de mídia)**.

8.  Na lista, selecione a interface do Servidor de Borda do BackCompatSite.
    
    ![Caixa de diálogo Editar Propriedades, página Geral](images/JJ205136.75045212-03ca-4b82-8337-5dacb487094f(OCS.15).jpg "Caixa de diálogo Editar Propriedades, página Geral")  

9.  Clique em **OK** para fechar a página **Editar Propriedades**.

10. Em **Construtor de Topologias**, selecione o nó superior, **Lync Server**.

11. No painel **Ações**, no menu **Publicar topologia** e em **Avançar**.

12. Quando o **Assistente de publicação** for concluído, clique em **Finalizar**.

