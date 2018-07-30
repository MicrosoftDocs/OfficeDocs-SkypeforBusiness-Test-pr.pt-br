---
title: Remover a associação do servidor de Arquivamento
TOCTitle: Remover a associação do servidor de Arquivamento
ms:assetid: dabac157-71ee-4afe-b0b6-4a083d165ffb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721903(v=OCS.15)
ms:contentKeyID: 49886439
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover a associação do servidor de Arquivamento

 

_**Tópico modificado em:** 2012-10-04_

Para remover um Servidor de Arquivamento, você precisará alterar ou limpar a dependência no Pool de Front-Ends, Servidor Front-End, Aparelho de Filial Persistente e Servidor de Filial Persistente associado. Você edita as propriedades do Pool de Front-Ends, do Servidor Front-End, do Aparelho de Filial Persistente e do Servidor de Filial Persistente para remover a dependência. Depois de limpar a dependência e excluir o servidor no Construtor de Topologias, você será notificado de que o objeto de repositório do banco de dados associado no Construtor de Topologias também será excluído.

## Para remover a associação de Servidor de Arquivamento

1.  Abra o servidor de front-end do Lync Server 2013, abra o Construtor de Topologia.

2.  Navegue para o nó Lync Server 2010.

3.  No Construtor de Topologias, expanda **Pools de Enterprise Edition Front End**, **Servidores Standard Edition Front End**, ou **Sites de filiais**, com base em onde o Servidor de Arquivamento está definido.

4.  Se você tiver o Servidor de Filial Persistente associado, expanda **Sites de filiais**, expanda o nome do site da filial e expanda **Aparelhos de Filial Persistente**.
    
    > [!NOTE]  
    > <strong>Aparelhos de Filial Persistente</strong> na interface do usuário aplica-se ao Servidor de Filial Persistente e ao Aparelho de Filial Persistente.

5.  Clique com o botão direito do mouse no pool, servidor ou dispositivo que está associado ao Servidor de Arquivamento, e clique em **Editar Propriedades**.

6.  Em **Editar Propriedades**, em **Geral**, **Associações**, desmarque a caixa de seleção **Associar Servidor de Arquivamento** e clique em **OK**.

7.  Repita a etapa anterior para qualquer outro pool, servidor ou dispositivo associado ao Servidor de Arquivamento que você deseja remover.

8.  Clique com o botão direito do mouse no Servidor de Arquivamento, e, em seguida, clique em **Excluir**.

9.  Em **Excluir Repositórios Dependentes**, clique em **OK**.

10. Publique a topologia, verifique o status de replicação e execute o Assistente de Implantação do Lync Server conforme necessário.

