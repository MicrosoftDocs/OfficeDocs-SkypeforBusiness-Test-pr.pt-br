---
title: "Transição de Serv. de Mediação colocado em conj. c/ Serv. de Mediação autônomo (opc.)"
TOCTitle: "Transição de Serv. de Mediação colocado em conj. c/ Serv. de Mediação autônomo (opc.)"
ms:assetid: 7c3c2fb4-4ff2-47b1-aab3-0aa91472eadb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205026(v=OCS.15)
ms:contentKeyID: 49307225
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Transição de um Servidor de Mediação colocado em conjunto com um Servidor de Mediação autônomo (opcional)

 

_**Tópico modificado em:** 2012-10-19_

Use o procedimento a seguir para fazer a transição do seu Servidor de Mediação, colocado no seu servidor Standard Edition ou no pool de Front-Ends, para um Servidor de Mediação autônomo para uma implantação em um único local.

## Para mudar um Servidor de Mediação colocado para um Servidor de Mediação autônomo

1.  Abrir uma topologia existente do Topology Builder.

2.  No painel à esquerda, navegue até **Pools de mediação**.

3.  Clique com o botão direito em **Pools de mediação** e selecione **Novo Servidor de Mediação**.

4.  Na página **Definir Novo Pool de Mediação**, forneça o FQDN do novo pool do Servidor de Mediação. Selecione também se este será um pool de servidor único ou de vários servidores e clique em **Avançar**.

5.  Selecione o pool do próximo salto do servidor Front-End para o qual no novo Servidor de Mediação roteará chamadas de entrada e clique em **Avançar**.

6.  Selecione o pool de Borda a ser usado pelo Servidor de Mediação e clique em **Avançar**.

7.  Na página **Especificar gateways PSTN**, associe o gateway PSTN anterior ao Servidor de Mediação. Selecione o gateway e clique em **Adicionar**.

8.  Clique em **Concluir** para fechar o assistente **Definir Novo Pool de Mediação**.

9.  No **Topology Builder**, selecione o primeiro nó **Lync Server 2013**.

10. No painel **Ações**, selecione **Publicar Topologia** e conclua o assistente.

11. Siga as etapas em [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md) na documentação de Implantação para instalar os arquivos no novo Servidor de Mediação.

12. Depois que os arquivos estiverem instalados no Servidor de Mediação, volte para o Construtor de Topologias e, no painel à esquerda, navegue até o pool.

13. Clique com o botão direito no pool e selecione **Editar Propriedades**.

14. Sob **Servidor de Mediação**, desmarque a opção **Servidor de Mediação posicionado habilitado** e clique em **OK**.

15. No **Topology Builder**, selecione o primeiro nó **Lync Server 2013**.

16. No menu **Ações**, selecione **Publicar Topologia** e conclua o assistente.

