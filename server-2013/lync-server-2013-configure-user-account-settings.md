---
title: 'Lync Server 2013: Definir configurações de conta do usuário'
TOCTitle: Definir configurações de conta do usuário
ms:assetid: b7c74ecc-b924-4efc-8a56-3a5f94a9ef13
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412896(v=OCS.15)
ms:contentKeyID: 49307886
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir configurações de conta do usuário no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Os usuários de discagem digitam o número de telefone ou a extensão e um PIN para ingressar nas conferências como usuários autenticados. O **URI da Linha** de telefonia especificado nas contas de usuário no Lync Server é necessário para autenticação.

O procedimento neste tópico descreve como atribuir um **URI da Linha** para uma única conta de usuário. Se você precisar atribuir um **URI da Linha** para várias contas de usuário, poderá criar um script que usa o cmdlet **Set-CsUser**. Para obter detalhes sobre como usar um exemplo de script para atribuir um **URI da Linha** para várias contas de de usuário, consulte "Assign Line URIs to Multiple Users" em [http://go.microsoft.com/fwlink/p/?linkId=196945](http://go.microsoft.com/fwlink/p/?linkid=196945).

## Para configurar as definições de conta de usuário

1.  Faça logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-UserAdministrator** ou **CsAdministrator** .

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** .

4.  No campo de pesquisa, digite o nome do usuário que você deseja configurar para conferência discada ou clique em **Adicionar filtro** para especificar os campos de pesquisa e clique em **Localizar** .

5.  Clique duas vezes no nome do usuário para abrir a caixa de diálogo **Editar Lync Server Usuário**.

6.  Em **Telefonia** , no campo **URI da Linha** , digite um número de telefone exclusivo e normalizado (por exemplo, tel:+14255550200).
    
    > [!NOTE]  
    > Você pode especificar o <strong>URI de linha</strong> somente se a <strong>Telefonia</strong> estiver definida como <strong>Somente PC para PC</strong> , <strong>Enterprise Voice</strong> , <strong>Controle de chamada remota</strong> ou <strong>Somente controle de chamada remota</strong> .

7.  Clique em **Confirmar** .

