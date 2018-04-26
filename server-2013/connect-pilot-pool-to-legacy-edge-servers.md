---
title: Conectar pool piloto aos Servidores de Borda herdados
TOCTitle: Conectar pool piloto aos Servidores de Borda herdados
ms:assetid: c3b67220-5705-47f6-852e-415204f3626c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721875(v=OCS.15)
ms:contentKeyID: 49886395
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conectar pool piloto aos Servidores de Borda herdados

 

_**Tópico modificado em:** 2012-09-29_

Após implantar o Lync Server 2013, você precisa configurar uma rota de federação para seu local. Para poder usar a rota federada que está sendo usada pelo Lync Server 2010, o Lync Server 2013 deve ser configurado para usar esta rota.

Para habilitar o local do Lync Server 2013 para usar o Diretor e o Servidor de Borda da implantação do Lync Server 2010, use o Construtor de Topologia para associar o pool de Borda herdado.

## Para associar o pool de Borda herdado usando o Construtor de Topologia

1.  Abra o **Construtor de Topologias**.

2.  Selecione seu local, que está diretamente abaixo do nó do **Lync Server**.

3.  No menu **Ações**, clique em **Editar Propriedades**.

4.  No painel esquerdo, selecione **Rota de federação**.

5.  Em **Atribuição da rota de federação local**, selecione **Habilitar federação SIP** e selecione o Diretor do Lync Server 2010 ou o Servidor de Borda do Lync Server 2010 se nenhum Diretor estiver listado.
    
    ![Editar Propriedades, página Rota de Federação](images/JJ721875.5f1d04c3-c724-426d-b27d-3fe89c6c5cfb(OCS.15).jpg "Editar Propriedades, página Rota de Federação")  

6.  Clique em **OK** para fechar a página **Editar Propriedades**.

7.  No Construtor de Topologia, no nó Lync Server 2013, navegue para o **servidor do Standard Edition** ou **Pools de front-end do Enterprise Edition**, clique com o botão direito no pool e clique em **Editar propriedades**.

8.  Em **Associações**, marque a caixa de seleção próxima ao **Associar pool de Borda (para componentes de mídia)**.

9.  Na lista, selecione o Servidor de Borda herdado.
    
    ![Caixa de diálogo Editar Propriedades, selecionando a Borda legada](images/JJ721875.feae8156-540e-4804-bb0a-2b5736ec2900(OCS.15).jpg "Caixa de diálogo Editar Propriedades, selecionando a Borda legada")  

10. Clique em **OK** para fechar a página **Editar Propriedades**.

11. No **Construtor de Topologias**, selecione o nó superior, **Lync Server**.

12. No painel **Ações**, no menu **Publicar topologia** e em **Avançar**.

13. Quando o **Assistente de publicação** for concluído, clique em **Finalizar**.

