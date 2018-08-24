---
title: Contas de usuário habilitadas para Lync Server 2013
TOCTitle: Contas de usuário habilitadas para Lync Server 2013
ms:assetid: 8021087e-5084-4a39-9fef-ab9376c6d371
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182543(v=OCS.15)
ms:contentKeyID: 49307270
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Contas de usuário habilitadas para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os tópicos desta seção apresentam procedimentos passo a passo para as tarefas que você pode realizar usando Painel de Controle do Lync Server 2013.

> [!IMPORTANT]  
> Não é possível usar o Painel de Controle do Lync Server para gerenciar os usuários que são membros do grupo Administradores de domínio do Active Directory. Para os usuários do grupo Administradores de domínio, você pode usar o Painel de Controle do Lync Server somente para executar operações de somente leitura e pesquisa. Para executar operações de gravação em usuários de Admins. do domínio (por exemplo, habilitar ou desabilitar para o Painel de Controle do Lync Server, alterar as atribuições de pool ou política, as configurações de telefonia, o endereço SIP), você deve usar cmdlets do Windows PowerShell enquanto estiver conectado como um usuário do grupo Administradores de domínio. Para obter detalhes sobre como usar os cmdlets do Windows PowerShell para gerenciar os usuários, consulte <a href="lync-server-2013-lync-server-management-shell.md">Shell de gerenciamento do Lync Server</a>.

Quando você executa qualquer tarefa administrativa do Lync Server 2013 que envolve pesquisar por um usuário ou a filtragem de resultados de pesquisa do usuário, há algumas propriedades de usuário que existem como atributos em Serviços de Domínio Active Directory, mas não são replicados no catálogo global até que o Microsoft Exchange Server é implantado. O Microsoft Exchange, não o Lync Server, marca os seguintes atributos para a duplicação do catálogo global quando ele é instalado:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Informações de usuário</th>
<th>Endereço e Telefone</th>
<th>Organização</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Iniciais</p></td>
<td><p>Endereço</p>
<p>País/região</p>
<p>Pager</p>
<p>FAX</p>
<p>Mobile</p></td>
<td><p>Título</p>
<p>Empresa</p>
<p>Departamento</p>
<p>Office</p></td>
</tr>
</tbody>
</table>


## Nesta seção

  - [Visualizando Informações sobre contas de usuário habilitadas para Lync Server 2013](lync-server-2013-viewing-information-about-user-accounts-enabled-for-lync-server.md)

  - [Habilitando e desabilitando usuários para Lync Server 2013](lync-server-2013-enabling-and-disabling-users-for-lync-server.md)

  - [Gerenciando o Enterprise Voice para usuários](lync-server-2013-managing-enterprise-voice-for-users.md)

  - [Modificando as Propriedades da Conta do Usuário](lync-server-2013-modifying-user-account-properties.md)

  - [Gerenciar política de acesso externo no Lync Server 2013](lync-server-2013-manage-external-access-policy-for-your-organization.md)

  - [Atribuir políticas por usuário no Lync Server 2013](lync-server-2013-assigning-per-user-policies.md)

## Consulte Também

#### Conceitos

[Cmdlets de gerenciamento de usuários](lync-server-2013-user-management-cmdlets.md)  

#### Outros Recursos

[Gerenciando usuários no Lync Server 2013](lync-server-2013-managing-users-in-lync-server.md)

