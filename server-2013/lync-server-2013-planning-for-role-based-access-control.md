---
title: 'Lync Server 2013: Planejamento de controle de acesso baseado em função'
TOCTitle: Planejamento de controle de acesso baseado em função (RBAC)
ms:assetid: 41204ba3-ce5b-41a8-a6c3-b444468fa328
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425917(v=OCS.15)
ms:contentKeyID: 49306511
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de controle de acesso baseado em função no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para permitir que você delegue tarefas administrativas ao mesmo tempo em que mantém altos padrões de segurança, o Lync Server 2013 oferece o RBAC (controle de acesso baseado em função). Com o RBAC, o privilégio administrativo é concedido pela atribuição de usuários a funções administrativas. O Lync Server 2013 inclui um valioso conjunto de funções administrativas internas, e também permite que você crie novas funções e especifique uma lista de cmdlets personalizada para cada nova função. Você pode também adicionar scripts de cmdlets às tarefas permitidas para ambas as funções personalizadas e predefinidas do RBAC.

## Melhor segurança e centralização do servidor

Com o RBAC, acesso e autorização baseiam-se precisamente em uma função do Lync Server do usuário. Isso permite uso adequado da prática de segurança de "privilégio mínimo", concedendo a administradores e usuários somente os direitos necessários para seus trabalhos.

> [!IMPORTANT]  
> As restrições do RBAC funcionam apenas em administradores que trabalham remotamente, usando o Painel de Controle do Lync Server ou o Shell de Gerenciamento do Lync Server. Um usuário sentado na frente de um servidor que está executando o Lync Server não é restringido pelo RBAC. Portanto, a segurança física do Lync Server é importante para preservar as restrições do RBAC.

## Funções e escopo

No RBAC, *função* é ativada para utilizar uma lista de cmdlets definidos pelo Lync Server, desenvolvida para ser útil para um determinado tipo de administrador ou técnico. *Escopo* é o conjunto de objetos que os cmdlets definidos em uma função podem operar. Os objetos que o escopo afeta podem ser contas de usuário (agrupadas por unidade organizacional) ou servidores (agrupados por site).

A tabela a seguir lista as funções predefinidas no Lync Server e fornece uma visão geral dos tipos de tarefas que cada uma pode executar. A quarta coluna mostra a função similar do Microsoft Exchange Server para cada função do Lync Server, se houver uma.

### Funções administrativas predefinidas

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Função</th>
<th>Tarefas permitidas</th>
<th>Grupo subjacente do Diretório Ativo</th>
<th>Equivalente do Exchange</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CsAdministrator</p></td>
<td><p>Pode executar todas as tarefas administrativas e modificar todas as configurações, incluindo a criação de funções e a atribuição de usuários a funções. Pode expandir uma implantação adicionando novos sites, pools e serviços.</p></td>
<td><p>CSAdministrator</p></td>
<td><p>Gerenciamento de Organização</p></td>
</tr>
<tr class="even">
<td><p>CsUserAdministrator</p></td>
<td><p>Pode habilitar e desabilitar usuários do Lync Server, mover usuários e atribuir políticas existentes a usuários. Não é possível modificar as políticas.</p></td>
<td><p>CSUserAdministrator</p></td>
<td><p>Destinatários de Email</p></td>
</tr>
<tr class="odd">
<td><p>CsVoiceAdministrator</p></td>
<td><p>Pode criar, configurar e gerenciar políticas e configurações relacionadas à voz.</p></td>
<td><p>CSVoiceAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="even">
<td><p>CsServerAdministrator</p></td>
<td><p>Pode gerenciar, monitorar e solucionar problemas de servidores e serviços. Pode impedir novas conexões com servidores, parar e iniciar serviços e aplicar atualizações de software. Não é possível fazer alterações com impacto de configuração global.</p></td>
<td><p>CSServerAdministrator</p></td>
<td><p>Gerenciamento de Servidor</p></td>
</tr>
<tr class="odd">
<td><p>CsViewOnlyAdministrator</p></td>
<td><p>Pode exibir a implantação, incluindo informações de usuário e servidor, para monitorar a integridade da implantação.</p></td>
<td><p>CSViewOnlyAdministrator</p></td>
<td><p>Gerenciamento da Organização Somente para Exibição</p></td>
</tr>
<tr class="even">
<td><p>CsHelpDesk</p></td>
<td><p>Pode exibir a implantação, incluindo propriedades e políticas do usuário. Pode executar tarefas específicas de solução de problemas. Não é possível alterar propriedades ou políticas do usuário, configuração do servidor ou serviços.</p></td>
<td><p>CSHelpDesk</p></td>
<td><p>Assistência Técnica</p></td>
</tr>
<tr class="odd">
<td><p>CsArchivingAdministrator</p></td>
<td><p>Pode modificar a configuração e as políticas de arquivamento.</p></td>
<td><p>CSArchivingAdministrator</p></td>
<td><p>Gerenciamento de Retenção, Bloqueio Legal</p></td>
</tr>
<tr class="even">
<td><p>CsResponseGroupAdministrator</p></td>
<td><p>Pode gerenciar a configuração do aplicativo Grupo de Resposta em um site.</p></td>
<td><p>CSResponseGroupAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="odd">
<td><p>CsLocationAdministrator</p></td>
<td><p>Nível mais baixo de direitos de gerenciamento de E9-1-1 (9-1-1 Avançado), incluindo a criação de locais e identificadores de rede E9-1-1 e associando uns com os outros. Esta função é sempre atribuída com um escopo global.</p></td>
<td><p>CSLocationAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="even">
<td><p>CsResponseGroupManager</p></td>
<td><p>Pode gerenciar grupos de resposta específicos.</p></td>
<td><p>CSResponseGroupManager</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="odd">
<td><p>CsPersistentChatAdministrator</p></td>
<td><p>Pode gerenciar o recurso de Bate-papo Persistente e salas de Bate-papo Persistente específicas.</p></td>
<td><p>CSPersistentChatAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="even">
<td><p>CsAdministrator</p></td>
<td><p>Pode executar todas as tarefas administrativas e modificar todas as configurações, incluindo a criação de funções e a atribuição de usuários a funções. Pode expandir uma implantação adicionando novos sites, pools e serviços.</p></td>
<td><p>CSAdministrator</p></td>
<td><p>Gerenciamento de Organização</p></td>
</tr>
<tr class="odd">
<td><p>CsUserAdministrator</p></td>
<td><p>Pode habilitar e desabilitar usuários do Lync Server, mover usuários e atribuir políticas existentes a usuários. Não é possível modificar as políticas.</p></td>
<td><p>CSUserAdministrator</p></td>
<td><p>Destinatários de Email</p></td>
</tr>
<tr class="even">
<td><p>CsVoiceAdministrator</p></td>
<td><p>Pode criar, configurar e gerenciar políticas e configurações relacionadas à voz.</p></td>
<td><p>CSVoiceAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="odd">
<td><p>CsServerAdministrator</p></td>
<td><p>Pode gerenciar, monitorar e solucionar problemas de servidores e serviços. Pode impedir novas conexões com servidores, parar e iniciar serviços e aplicar atualizações de software. Não é possível fazer alterações com impacto de configuração global.</p></td>
<td><p>CSServerAdministrator</p></td>
<td><p>Gerenciamento de Servidor</p></td>
</tr>
<tr class="even">
<td><p>CsViewOnlyAdministrator</p></td>
<td><p>Pode exibir a implantação, incluindo informações de usuário e servidor, para monitorar a integridade da implantação.</p></td>
<td><p>CSViewOnlyAdministrator</p></td>
<td><p>Gerenciamento da Organização Somente para Exibição</p></td>
</tr>
<tr class="odd">
<td><p>CsHelpDesk</p></td>
<td><p>Pode exibir a implantação, incluindo propriedades e políticas do usuário. Pode executar tarefas específicas de solução de problemas. Não é possível alterar propriedades ou políticas do usuário, configuração do servidor ou serviços.</p></td>
<td><p>CSHelpDesk</p></td>
<td><p>Assistência Técnica</p></td>
</tr>
<tr class="even">
<td><p>CsArchivingAdministrator</p></td>
<td><p>Pode modificar a configuração e as políticas de arquivamento.</p></td>
<td><p>CSArchivingAdministrator</p></td>
<td><p>Gerenciamento de Retenção, Bloqueio Legal</p></td>
</tr>
<tr class="odd">
<td><p>CsResponseGroupAdministrator</p></td>
<td><p>Pode gerenciar a configuração do aplicativo Grupo de Resposta em um site.</p></td>
<td><p>CSResponseGroupAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="even">
<td><p>CsLocationAdministrator</p></td>
<td><p>Nível mais baixo de direitos de gerenciamento de E9-1-1 (9-1-1 Avançado), incluindo a criação de locais e identificadores de rede E9-1-1 e associando uns com os outros. Esta função é sempre atribuída com um escopo global.</p></td>
<td><p>CSLocationAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="odd">
<td><p>CsResponseGroupManager</p></td>
<td><p>Pode gerenciar grupos de resposta específicos.</p></td>
<td><p>CSResponseGroupManager</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
<tr class="even">
<td><p>CsPersistentChatAdministrator</p></td>
<td><p>Pode gerenciar o recurso de Bate-papo Persistente e salas de Bate-papo Persistente específicas.</p></td>
<td><p>CSPersistentChatAdministrator</p></td>
<td><p>NA (Not applicable)</p></td>
</tr>
</tbody>
</table>


Todas as funções predefinidas no Lync Server possuem um escopo global. Para seguir ao menos as práticas de privilégio, você não deve atribuir usuários a funções com escopo global se eles forem administrar apenas um conjunto limitado de servidores ou usuários. Para tal, você pode criar funções que são baseadas em uma função existente, mas com escopo mais limitado.

## Criando uma Função com escopo

Ao criar uma função com escopo limitado (função com escopo), você especifica o escopo junto com a função existente na qual é baseada e o grupo de Diretório ativo a ser atribuído à função. O grupo do Diretório ativo especificado já deve ter sido criado. O cmdlet a seguir é um exemplo de uma criação de função a qual possui os privilégios de uma das funções administrativas predefinidas, mas com escopo limitado. Isso cria uma nova função chamada `Site01 Server Administrators`. A função possui as capacidades da função CsServerAdministrator predefinida, mas apenas servidores localizados no local do Site01. Para que esse cmdlet funcione, o local do Site01 deve já ter sido definido e um grupo de segurança universal chamado `Site01 Server Administrators` já deve existir.

    New-CsAdminRole -Identity "Site01 Server Administrators" -Template CsServerAdministrator -ConfigScopes "site:Site01"

Após a execução desse cmdlet, todos os usuários que são membros do grupo `Site01 Server Administrators` terão privilégios de administrador do servidor para os servidores em Site01. Além disso, todos os usuários que forem adicionados posteriormente a esse grupo de segurança universal também obterão os privilégios dessa função. Observe que a função em si e o grupo de segurança universal ao qual ela é atribuída são chamados `Site01 Server Administrators`.

O exemplo a seguir limita o escopo de usuário, em vez do escopo do servidor. Ele cria uma função `Sales Users Administrator` para administrar as contas de usuário na unidade organizacional de Vendas. O grupo de segurança universal SalesUsersAdministrator já deve ter sido criado para que esse cmdlet funcione.

    New-CsAdminRole -Identity "Sales Users Administrator " -Template CsUserAdministrator -UserScopes "OU:OU=Sales, OU=Lync Tenants, DC=Domain, DC=com"

## Criando uma nova função

Para criar uma função que possui acesso a um conjunto de cmdlets que não estão em uma das funções predefinidas ou para um conjunto de scripts ou módulos, você pode começar utilizando uma das funções predefinidas como modelo. Observe que os scripts e módulos com a função que devem estar aptos a ser executados devem ser armazenados nos seguintes locais:

  - O caminho do módulo do Lync, que é por padrão C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\Modules\\Lync

  - O caminho do script do usuário, que é por padrão C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\AdminScripts

Para criar uma nova função, utilize o cmdlet **New-CsAdminRole**. Antes de executar **New-CsAdminRole** , você deve primeiro criar o grupo de segurança universal subjacente que será associado a esta função.

Os seguintes cmdlets servem como um exemplo de criação de nova função. Eles criam um novo tipo de função chamado `MyHelpDeskScriptRole`. A nova função possui as capacidades da função CsHelpDesk predefinida e pode, adicionalmente, executar funções em um script chamado “testscript”.

    New-CsAdminRole -Identity "MyHelpDeskScriptRole" -Template CsHelpDesk -ScriptModules @{Add="testScript.ps1"}

Para que esse cmdlet funcione, você deve primeiro criar o grupo de segurança universal MyHelpDeskScriptRole.

Depois que esse cmdlet é executado, você pode atribuir usuários diretamente a essa função (neste caso, eles possuem escopo global) ou criar uma função com escopo com base nessa função, como explicado em Criando uma função com escopo, anteriormente neste documento.

## Atribuindo funções a usuários

Cada função Lync Server é associada a um grupo de segurança universal do Diretório ativo subjacente. Qualquer usuário adicionado ao grupo subjacente recebe as capacidades de tal função.

Os exemplos nas seções precedentes criaram uma nova função e atribuíram um grupo de segurança universal existente para a nova função. Para atribuir uma função existente a um ou mais usuários, adicione tais usuários ao grupo associado com tal função. Você pode adicionar usuários individuais e grupos de segurança universais a esses grupos.

Por exemplo, a função **CsAdministrator** é automaticamente concedida ao grupo de segurança universal **Administradores CS** no Diretório ativo. Esse grupo de segurança universal é criado no Diretório ativo quando você implanta Lync Server. Para conceder esse privilégio a um usuário ou grupo, você pode simplesmente adicioná-los ao grupo **Administradores CS** .

Um usuário pode receber várias funções do RBAC ao ser adicionado aos grupos subjacentes do Active Directory que correspondem a cada função.

Observe que quando você cria uma função, os usuários que posteriormente são adicionados ao grupo subjacente do Active Directory ganham os recursos dessa função.

## Modificando as capacidades de uma função

Você pode modificar a lista de cmdlets e scripts que uma função pode executar. Você pode modificar tanto os cmdlets quanto scripts que as funções personalizadas podem executar, mas pode apenas modificar os scripts para funções predefinidas. Cada cmdlet que você digita pode adicionar, remover ou substituir cmdlets ou scripts.

Para modificar uma função, utilize o cmdlet **Set-CsAdminRole** . O cmdlet a seguir remove um script da função.

    Set-CsAdminRole -Identity "MyHelpDeskScriptRole" -ScriptModules @{Remove="testScript.ps1"}

## Planejando o RBAC

Para cada pessoa que receberá qualquer tipo de direito administrativo para a sua implantação Lync Server, considere exatamente quais tarefas eles precisam efetuar e, então, atribua-os a funções com o menor privilégio e escopo necessário para o trabalho. Se necessário, você pode usar o cmdlet **Set-CsAdminRole** para criar uma nova função com com apenas os cmdlets necessários para as tarefas dessa pessoa.

Os usuários que têm a função CsAdministrator podem criar todos os tipos de funções, incluindo funções baseadas no CsAdministrator e atribuir usuários a elas. A melhor prática é atribuir a função CsAdministrator a um conjunto muito pequeno de usuários confiáveis.

