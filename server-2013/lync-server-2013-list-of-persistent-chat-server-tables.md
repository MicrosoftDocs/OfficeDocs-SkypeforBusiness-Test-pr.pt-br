---
title: 'Lync Server 2013: Tabelas de lista de Servidores de Chat Persistente'
TOCTitle: Tabelas de lista de Servidores de Chat Persistente
ms:assetid: 26c9e271-3516-4d90-b930-70fec4e359ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558628(v=OCS.15)
ms:contentKeyID: 49306187
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tabelas de lista de Servidores de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O esquema de banco de dados do Chat Persistente consiste nas tabelas a seguir.

## Sincronização do Active Directory


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tbladcookie.md">tblADCookie no Lync Server 2013</a></p></td>
<td><p>Contém cookies de sincronização LDAP. Cada linha corresponde a um domínio do Serviços de Domínio Active Directory que o Servidor de Chat Persistente está monitorando ativamente para mudanças. (Apenas os domínios do Active Directory relevantes para o Servidor de Chat Persistente são representados nesta tabela.)</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipalmemberdifference.md">tblPrincipalMemberDifference no Lync Server 2013</a></p></td>
<td><p>Contém alterações de associação de grupo (membros adicionados e removidos) que ainda não foram processados pelas etapas de sincronização posteriores do Active Directory e é uma das tabelas temporárias (junto com a tabela tblADUpdates) usada na primeira etapa da sincronização do Active Directory.</p>
<p>As alterações de associação são armazenadas, processadas ou ambos, somente para grupos listados na tabela tblPrincipal ou que já possuem membros listados.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tbladupdates.md">tblADUpdates no Lync Server 2013</a></p></td>
<td><p>Contém as alterações para Serviços de Domínio Active Directory que ainda não foram processados pelas etapas de Sincronização posteriores do Active Directory e é uma das tabelas temporárias (junto com a tabela tblPrincipalMemberDifference) usada na primeira etapa da Sincronização do Active Directory.</p>
<p>As alterações ao Active Directory são armazenadas, processadas ou ambos, apenas para entidades já listadas na tabela tblPrincipal.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipalmembers.md">tblPrincipalMembers no Lync Server 2013</a></p></td>
<td><p>Contém associações de entidade.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalmeta.md">tblPrincipalMeta no Lync Server 2013</a></p></td>
<td><p>Contém as entidades que precisam ser atualizadas do Active Directory.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblskippedaffiliations.md">tblSkippedAffiliations no Lync Server 2013</a></p></td>
<td><p>Contém afiliações que não podem ser atualizadas por algum motivo, geralmente devido aos erros de acesso do Active Directory.</p>
<p>Esta tabela é apenas para fins informativos. Seu conteúdo não é usado.</p>
<p>As entidades com afiliações que não podem ser atualizadas corretamente são mantidas na tabela tblPrincipalMeta e têm outra chance de serem atualizadas.</p></td>
</tr>
</tbody>
</table>


## Entidades, afiliações, nós, escopos e funções


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipaltype.md">tblPrincipalType no Lync Server 2013</a></p></td>
<td><p>Contém tipos de entidades para categorizar o que está na tabela tblPrincipal. Esta tabela é estática. É configurada durante a criação do banco de dados e não muda.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblprincipal.md">tblPrincipal no Lync Server 2013</a></p></td>
<td><p>Contém todas as entidades (usuários, pastas, grupos e assim por diante). O Servidor de Chat Persistente lida com isto como uma lista plana heterogênea. Várias colunas são baseadas no tipo de cada entidade.</p>
<p>A maioria destas entidades são copiadas em cache de objetos armazenados no Active Directory. Criar a cópia em cache na tabela Entidades destes objetos do Active Directory é referido como <em>provisionamento</em> .</p>
<p>Algumas entidades são criadas mais agressivamente do que outras e alguns objetos do Active Directory são ignorados.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalaffiliations.md">tblPrincipalAffiliations no Lync Server 2013</a></p></td>
<td><p>Contém afiliações de entidades que descrevem associações nos grupos de segurança do Active Directory, recipientes do Active Directory e assim por diante.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblnode.md">tblNode no Lync Server 2013</a></p></td>
<td><p>Contém o nó de categoria, conforme gerenciado no Painel de Controle do Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblroletype.md">tblRoleType no Lync Server 2013</a></p></td>
<td><p>Contém tipos de função e seus conjuntos de permissões associadas. A tabela de pesquisa é estática.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblscopeprincipal.md">tblScopePrincipal no Lync Server 2013</a></p></td>
<td><p>Contém escopos atribuídos aos nós.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalrole.md">tblPrincipalRole no Lync Server 2013</a></p></td>
<td><p>Contêm funções atribuídas aos nós.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblsiopwhitelist.md">tblSiopWhiteList no Lync Server 2013</a></p></td>
<td><p>Contém os suplementos registrados que podem ser associados aos nós.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblenumattribute.md">tblEnumAttribute no Lync Server 2013</a></p></td>
<td><p>Contém apenas os atributos de &quot;Visibility&quot; e &quot;Behavior&quot; codificados usados na tabela tblNode.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblenumvalue.md">tblEnumValue no Lync Server 2013</a></p></td>
<td><p>Contém os valores dos atributos &quot;Visibility&quot; e &quot;Behavior&quot; codificados usados na tabela tblNode.</p></td>
</tr>
</tbody>
</table>


## Convites, bate-papos e outro suporte ao cliente


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblprincipalinvites.md">tblPrincipalInvites no Lync Server 2013</a></p></td>
<td><p>Contém convites para todos os usuários configurados no sistema para todos os nós com Convidar automaticamente habilitado.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblchat.md">tblChat no Lync Server 2013</a></p></td>
<td><p>Contém todas as mensagens de bate-papo.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tbllastinviteid.md">tblLastInviteId no Lync Server 2013</a></p></td>
<td><p>Contém a última ID de convite gerada (e usada na tabela tblPrincipalInvites) para cada usuário.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tbllastchatid.md">tblLastChatId no Lync Server 2013</a></p></td>
<td><p>Contém a última ID de bate-papo gerada (e usada na tabela tblChat) para cada usuário.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblpreference.md">tblPreference no Lync Server 2013</a></p></td>
<td><p>Contém preferências do cliente usuário (usado apenas por clientes herdados).</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblfiletoken.md">tblFileToken no Lync Server 2013</a></p></td>
<td><p>Contém tokens temporários para fins de transferência de arquivo. Cada vez que um arquivo é carregado ou baixado, o serviço do Chat Persistente gera um token que o cliente usa para acessar o repositório de arquivos de serviço da Web.</p></td>
</tr>
</tbody>
</table>


## Suporte a servidor


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tabela</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="lync-server-2013-tblserveridentity.md">tblServerIdentity no Lync Server 2013</a></p></td>
<td><p>Contém os servidores ativos no Pool de Servidor de Chat Persistente.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tbladminlock.md">tblAdminLock no Lync Server 2013</a></p></td>
<td><p>Contém o bloqueio do administrador para executar alguns comandos do administrador. A entrada de revisão do sistema na tabela tblSystemRevision é incrementada após cada liberação do bloqueio.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblsystemrevision.md">tblSystemRevision no Lync Server 2013</a></p></td>
<td><p>Contém a entrada do número de revisão usada (juntamente com a tabela tblAdminLock) para obter consistência em vários clientes.</p></td>
</tr>
<tr class="even">
<td><p><a href="lync-server-2013-tblactivepeers.md">tblActivePeers no Lync Server 2013</a></p></td>
<td><p>Contém as conexões ponto a ponto atual entre os serviços do Chat Persistente.</p></td>
</tr>
<tr class="odd">
<td><p><a href="lync-server-2013-tblconfig.md">tblConfig no Lync Server 2013</a></p></td>
<td><p>Contém a configuração não suportada do Servidor de Chat Persistente.</p></td>
</tr>
</tbody>
</table>

