---
title: Pesquisa para usuários do Lync Server
TOCTitle: Pesquisa para usuários do Lync Server
ms:assetid: 3b9f6f55-d7a9-46ae-8e10-f221ba0d3bb5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429701(v=OCS.15)
ms:contentKeyID: 49306438
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pesquisa para usuários do Lync Server

 

_**Tópico modificado em:** 2014-05-14_

É possível usar os resultados de uma consulta de pesquisa para configurar os usuários do Lync Server 2013. Você pode procurar usuários por nome para exibição, nome, sobrenome, nome da conta do SAM (Gerenciador de Contas de Segurança), endereço SIP ou linha de URI (Uniform Resource Identifier).

É possível procurar usuários usando o Painel de Controle do Lync Server ou o snap-in Usuários e Computadores do Active Directory. O procedimento a seguir descreve como usar o Painel de Controle do Lync Server para pesquisar usuários.

> [!NOTE]  
> Em um ambiente com uma topologia de floresta central, os resultados da pesquisa poderão não ser precisos quando você procurar um usuário pelo endereço de email. Em vez disso, você pode procurar usuários especificando um prefixo de endereço SIP, por exemplo, sip:name, adicionar um filtro de pesquisa e selecionar um endereço SIP que contenha um endereço de email parcial ou usar o cmdlet <strong>Get-CSUser</strong>.

## Para procurar um ou mais usuários

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou a primeira parte do nome para exibição, nome, sobrenome, nome da conta do SAM, endereço SIP ou URI de linha da conta de usuário que você deseja pesquisar e clique em **Localizar**.

5.  (Opcional) Especifique o critério de pesquisa adicional para reduzir os resultados:
    
    1.  Clique no botão de seta de expansão no canto superior direito da tela acima **Resultados da pesquisa**e clique em **Adicionar Filtro**.
    
    2.  Insira a propriedade de usuário digitando-a ou clicando na seta na lista suspensa para selecionar uma propriedade de usuário.
    
    3.  Na lista **Igual a**, clique em **Igual a** ou **Diferente de**.
    
    4.  Na caixa de texto, digite os critérios de pesquisa que você deseja usar para filtrar resultados de pesquisa e clique em **Localizar**.

6.  Os resultados da pesquisa aparecem em **Resultados da Pesquisa**. Você pode selecionar qualquer um ou todos os usuários na lista e executar tarefas de configuração nos usuários selecionados.

## Consulte Também

#### Outros Recursos

[Visualizando Informações sobre contas de usuário habilitadas para Lync Server 2013](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)  
[Habilitando e desabilitando usuários para Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

