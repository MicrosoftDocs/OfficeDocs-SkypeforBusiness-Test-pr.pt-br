---
title: Gerenciar grupos de agentes dos grupos de resposta
TOCTitle: Gerenciar grupos de agentes dos grupos de resposta
ms:assetid: 36084cdc-38f1-4c45-922f-f81c7e86210c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520976(v=OCS.15)
ms:contentKeyID: 49306358
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar grupos de agentes dos grupos de resposta

 

_**Tópico modificado em:** 2012-10-01_

Um grupo de operadores consiste em um grupo de pessoas designadas para atender às chamadas de um grupo de resposta. Ao criar um grupo de operadores, selecione os operadores que serão atribuídos ao grupo e especifique configurações de grupo adicionais, como o método de roteamento e se um operador pode entrar no grupo e sair dele.

> [!NOTE]  
> Os usuários devem estar habilitados para o Enterprise Voice antes que você possa adicioná-los aos grupos de operadores. Para obter detalhes sobre como habilitar um usuário para o Enterprise Voice, consulte <a href="lync-server-2013-enable-users-for-enterprise-voice.md">Habilitar usuários para Enterprise Voice no Lync Server 2013</a>.

> [!NOTE]  
> Apenas os usuários locais podem ser operadores. Se um operador for movido de local para online, a chamada do grupo de resposta não será mais roteada para ele.

Um operador que deve entrar ou sair do grupo, o que é diferente de entrar ou sair do Lync Server, é chamado de *operador formal*. Os operadores formais precisam entrar no grupo para que possam receber as chamadas roteadas para o grupo. Isso pode ser útil para os operadores que respondem às chamadas do grupo em tempo parcial. Os operadores formais entram e saem de seus grupos clicando em um item de menu do Lync 2013 para abrir o navegador Windows Internet Explorer e exibir um console de página da Web.

Um operador que não precisa entrar ou sair do grupo é denominado *operador informal*. Os operadores informais entram no grupo automaticamente quando entram no Lync Server, e não podem sair do grupo.

> [!IMPORTANT]  
> Quando você atribuir os usuários como operadores do grupo de resposta, informe-os de que, se tiverem o modo de privacidade habilitado, precisarão pesquisar os contatos do &quot;RGS Presence Watcher&quot; e adicioná-los à sua lista de contatos. Os operadores com o modo de privacidade habilitado, mas que não têm o &quot;RGS Presence Watcher&quot; na lista de contatos, não podem receber chamadas para o grupo de resposta. Os operadores que não têm o modo de privacidade habilitado não são afetados.

## Nesta seção

  - [Criar ou modificar um grupo de agente no Lync Server 2013](lync-server-2013-create-or-modify-an-agent-group.md)

  - [Excluir um grupo de agentes](lync-server-2013-delete-an-agent-group.md)

