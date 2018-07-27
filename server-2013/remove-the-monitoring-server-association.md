---
title: Remover a associação do servidor de Monitoramento
TOCTitle: Remover a associação do servidor de Monitoramento
ms:assetid: c45b22ae-fc06-484a-a05b-735bd1bb7448
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721877(v=OCS.15)
ms:contentKeyID: 49886400
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover a associação do servidor de Monitoramento

 

_**Tópico modificado em:** 2012-10-04_

Para remover o Servidor de Monitoramento, é preciso alterar ou limpar a dependência dos Pool de Front-Ends, Servidor Front-End, Aparelho de Filial Persistente e Servidor de Filial Persistente associados. Para remover a dependência, você edita as propriedades de Pool de Front-Ends, Servidor Front-End, Aparelho de Filial Persistente e Servidor de Filial Persistente. Depois de limpar a dependência e excluir o servidor no Construtor de Topologias, você é avisado de que o objeto de armazenamento de banco de dados associado no Construtor de Topologias também será excluído.

## Para remover a associação do Servidor de Monitoramento

1.  Abra o servidor de front-end do Lync Server 2013, abra o Construtor de Topologia.

2.  Navegue para o nó Lync Server 2010.

3.  No Construtor de Topologias, expanda **Pools de Front-Ends Enterprise Edition** , **Servidor Front-End Standard Edition** ou **Sites de filiais** , com base em onde o Servidor de Monitoramento está definido.

4.  Se você tiver o Servidor de Filial Persistente associado, expanda **Sites de filiais** , expanda o nome do site da filial e expanda **Aparelhos de Filial Persistente** .
    
    > [!NOTE]  
    > <strong>Aparelhos de Filial Persistente</strong> na interface do usuário aplica-se ao Servidor de Filial Persistente e ao Aparelho de Filial Persistente.

5.  Clique com o botão direito do mouse no pool, servidor ou dispositivo que está associado ao Servidor de Monitoramento e clique em **Editar Propriedades** .

6.  Em **Editar Propriedades** , em **Geral** , em **Associações** , limpe a caixa de seleção **Associar Servidor de Monitoramento** e clique em **OK** .

7.  Repita a etapa anterior para qualquer outro pool, servidor ou dispositivo associado ao Servidor de Monitoramento.

8.  Clique com o botão direito do mouse no Servidor de Monitoramento e, em seguida, clique em **Excluir** .

9.  Em **Excluir Repositórios Dependentes** , clique em **OK** .

10. Publique a topologia, verifique o status de replicação e execute o Assistente de Implantação do Lync Server conforme necessário.

