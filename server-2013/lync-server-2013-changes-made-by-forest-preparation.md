---
title: Alterações feitas pela preparação da floresta no Lync Server 2013
TOCTitle: Alterações feitas pela preparação da floresta no Lync Server 2013
ms:assetid: 2e12613e-59f2-4810-a32d-24a9789a4a6e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425791(v=OCS.15)
ms:contentKeyID: 49306252
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações feitas pela preparação da floresta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve os objetos e as configurações globais, além dos grupos universais de serviço e administração criados pela etapa de preparação de floresta.

## Objetos e configurações globais do Active Directory

Se você armazenar as configurações globais no contêiner Configuração (como é o caso para todas as implantações novas do Lync Server 2013), a preparação da floresta usará o contêiner Serviços existente e adicionará um objeto **Serviço de RTC** sob o objeto Configuração\\Serviços. Sob a implantação do Serviço de RTC, a preparação da floresta adiciona um objeto **Configurações Globais** do tipo msRTCSIP-GlobalContainer. O objeto de configurações global armazena todas as configurações que se aplicam à implantação do Lync Server. Se você armazenar as configurações globais no contêiner Sistema, a preparação da floresta usará um contêiner Microsoft sob o contêiner Sistema do domínio raiz e um objeto Serviço de RTC sob o objeto Sistema\\Microsoft.

A preparação de floresta também adiciona um novo objeto **msRTCSIP-Domain** ao domínio raiz no qual o procedimento é executado.

## Grupos universais de serviço e administração do Active Directory

A preparação de floresta cria grupos universais com base no domínio especificado e adiciona entradas de controle de acesso (ACEs) para esses grupos. Essa etapa cria os grupos universais nos contêineres Usuário do domínio especificado.

Os grupos universais permitem que os administradores acessem e gerenciem as configurações e serviços globais. A preparação da floresta adiciona os seguintes tipos de grupos universais:

  - **Grupos administrativos**   Esses grupos definem as funções de administrador para uma rede Lync Server.

  - **Grupos de infraestrutura**   Esses grupos fornecem permissão para acessar áreas específicas da infraestrutura do Lync Server. Eles funcionam como componentes dos grupos administrativos. Não modifique esses grupos ou adicione usuários diretamente a eles.

  - **Grupos de serviço**   Esses grupos são contas de serviço necessárias para acessar diversos serviços do Lync Server.

A tabela seguir descreve os grupos administrativos.

### Grupos administrativos criados durante a preparação da floresta

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo administrativo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCUniversalServerAdmins</p></td>
<td><p>Permite que os membros gerenciem as configurações de servidor e de pool, incluindo todas as funções de servidor, configurações globais e usuários.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalUserAdmins</p></td>
<td><p>Permite que os membros gerenciem configurações de usuário e movam usuários de um servidor ou pool para outro.</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalReadOnlyAdmins</p></td>
<td><p>Permite que os membros leiam configurações de servidor, pool e usuário.</p></td>
</tr>
</tbody>
</table>


A tabela seguir descreve os grupos de infraestrutura.

### Grupos de infraestrutura criados durante a preparação da floresta

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo de infraestrutura</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCUniversalGlobalWriteGroup</p></td>
<td><p>Concede acesso de gravação aos objetos de configuração global para o Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalGlobalReadOnlyGroup</p></td>
<td><p>Concede acesso somente leitura aos objetos de configuração global para o Lync Server.</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalUserReadOnlyGroup</p></td>
<td><p>Concede acesso somente leitura às configurações de usuário do Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalServerReadOnlyGroup</p></td>
<td><p>Concede acesso somente leitura para as configurações do Lync Server. Este grupo não tem acesso às configurações no nível do pool, mas apenas às configurações específicas de um servidor individual.</p></td>
</tr>
<tr class="odd">
<td><p>RTCUniversalSBATechnicians</p></td>
<td><p>Concede acesso somente leitura à configuração do Lync Server e são colocados no grupo Local Administradores de aparelhos de filial persistentes durante a instalação.</p></td>
</tr>
</tbody>
</table>


A tabela seguir descreve os grupos de serviço.

### Grupos de serviço criados durante a preparação da floresta

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Grupo de serviço</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>RTCHSUniversalServices</p></td>
<td><p>Inclui contas de serviço usadas para executar os servidores Servidor Front-End e Standard Edition. Esse grupo permite aos servidores acesso de leitura/gravação para as configurações globais do Lync Server e aos objetos de usuário do Active Directory.</p></td>
</tr>
<tr class="even">
<td><p>RTCComponentUniversalServices</p></td>
<td><p>Inclui contas de serviço usadas para executar os Servidores de Conferência A/V, o Serviços Web, o Servidor de Mediação, o Servidor de Arquivamento e o Servidor de Monitoramento.</p></td>
</tr>
<tr class="odd">
<td><p>RTCProxyUniversalServices</p></td>
<td><p>Inclui contas de serviço usadas para executar os Servidores de Borda do Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>RTCUniversalConfigReplicator</p></td>
<td><p>Inclui servidores que podem participar da replicação do Lync ServerRepositório de Gerenciamento Central.</p></td>
</tr>
<tr class="odd">
<td><p>RTCSBAUniversalServices</p></td>
<td><p>Concede acesso somente leitura ás configurações do Lync Server, mas permite a configuração da instalação de um servidor de filial persistente e da implantação de um aparelho de filial persistente.</p></td>
</tr>
</tbody>
</table>


Em seguida, a preparação de floresta adiciona os grupos de serviço e administração aos grupos de infraestrutura apropriados, da seguinte maneira:

  - RTCUniversalServerAdmins é adicionado a RTCUniversalGlobalReadOnlyGroup, RTCUniversalGlobalWriteGroup, RTCUniversalServerReadOnlyGroup e RTCUniversalUserReadOnlyGroup.

  - RTCUniversalUserAdmins é adicionado como membro de RTCUniversalGlobalReadOnlyGroup, RTCUniversalServerReadOnlyGroup e RTCUniversalUserReadOnlyGroup.

  - RTCHSUniversalServices, RTCComponentUniversalServices e RTCUniversalReadOnlyAdmins são adicionados como membros de RTCUniversalGlobalReadOnlyGroup, RTCUniversalServerReadOnlyGroup e RTCUniversalUserReadOnlyGroup.

A preparação da floresta também cria os seguintes grupos RBAC (controle de acesso baseado na função):

  - CSAdministrator

  - CSArchivingAdministrator

  - CSHelpDesk

  - CSLocationAdministrator

  - CSResponseGroupAdministrator

  - CSServerAdministrator

  - CSUserAdministrator

  - CSViewOnlyAdministrator

  - CSVoiceAdministrator

  - CsPersistentChatAdministator

  - CsResponseGroupManager

Para obter detalhes sobre as funções de RBAC e as tarefas permitidas para cada, consulte [Planejamento de controle de acesso baseado em função no Lync Server 2013](lync-server-2013-planning-for-role-based-access-control.md) na documentação Planejamento.

A preparação de floresta cria ACEs particulares e públicas. Ela cria ACEs privados no contêiner de configurações globais usados por Lync Server. Esse contêiner é usado somente por Lync Server e está localizado no contêiner Configuração ou no contêiner Sistema no domínio raiz, dependendo de onde você armazenou as configurações globais. As ACEs públicas criadas pela preparação de floresta estão listadas na tabela a seguir.

### ACEs públicas criadas pela preparação de floresta

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>ACE</th>
<th>RTCUniversalGlobalReadOnlyGroup</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ler o contêiner Sistema do domínio raiz (não herdado)<strong>*</strong></p></td>
<td><p>X</p></td>
</tr>
<tr class="even">
<td><p>Ler o contêiner DisplaySpecifiers de Configuração (não herdado)</p></td>
<td><p>X</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> <strong>*</strong>As ACEs que não são herdadas não concedem acesso aos objetos filho desses contêineres. As ACEs que são herdadas concedem acesso aos objetos filho desses contêineres.

No contêiner Configuração, no contexto de nomenclatura de configuração, a preparação de floresta executa as seguintes tarefas:

  - Adiciona uma entrada **{AB255F23-2DBD-4bb6-891D-38754AC280EF}** para a página **Propriedade RTC** dos atributos adminContextMenu e adminPropertyPages do especificador de exibição de idioma para usuários, contatos e InetOrgPersons (por exemplo, CN=user-Display,CN=409,CN=DisplaySpecifiers).

  - Adiciona um objeto **RTCPropertySet** do tipo **controlAccessRight** em **Extended-Rights**, que se aplica às classes Usuário e Contato.

  - Adiciona um objeto **RTCUserSearchPropertySet** do tipo **controlAccessRight** em **Extended-Rights**, que se aplica às classes Usuário, Contato, UO e DomainDNS.

  - Adiciona **msRTCSIP-PrimaryUserAddress** sob o atributo **extraColumns** do especificador de exibição da UO (unidade organizacional) de cada idioma (por exemplo, CN=organizationalUnit-Display,CN=409,CN=DisplaySpecifiers) e copia os valores do atributo **extraColumns** da exibição padrão (por exemplo, CN=default-Display, CN=409,CN=DisplaySpecifiers).

  - Adiciona os atributos de filtragem **msRTCSIP-PrimaryUserAddress**, **msRTCSIP-PrimaryHomeServer** e **msRTCSIP-UserEnabled** sob o atributo **attributeDisplayNames** do especificador de exibição de cada idioma para os objetos Usuários, Contatos e InetOrgPerson (por exemplo, em inglês: CN=user-Display,CN=409,CN=DisplaySpecifiers).

