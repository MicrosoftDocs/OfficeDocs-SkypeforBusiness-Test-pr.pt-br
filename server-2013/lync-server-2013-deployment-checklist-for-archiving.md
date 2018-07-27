---
title: 'Lync Server 2013: Lista de verificação da implantação para Arquivamento'
TOCTitle: Lista de verificação da implantação para Arquivamento
ms:assetid: 7479734d-be01-40d9-ad82-320a09d19d04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205009(v=OCS.15)
ms:contentKeyID: 49307122
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação da implantação para Arquivamento no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Arquivamento é automaticamente instalado em cada servidor front-end na implantação do Lync Server 2013, mas você ainda precisa configurá-lo antes de poder usá-lo. As etapas necessário para configurá-lo (resumidas nesta seção) constituem a implantação do Arquivamento.

## Sequência de implantação

O modo de configuração do Arquivamento depende da opção de armazenamento escolhida:

  - Se você usar a integração do Microsoft Exchange para todos os usuários da implantação, não será necessário configurar as políticas de Arquivamento do Lync Server 2013 para todos os usuários. Em vez disso, configure as políticas de retenção no local do Exchange a fim de oferecer suporte ao arquivamento para usuários hospedados no Exchange 2013, com suas caixas de correio em retenção no local. Para obter detalhes sobre a configuração dessas políticas, consulte a documentação do produto Exchange 2013.

  - Caso você não use a integração do Microsoft Exchange para todos os usuários na implantação, será necessário adicionar bancos de dados de Arquivamento do Lync Server (bancos de dados do SQL Server) à sua topologia e em publicá-la em seguida, bem como definir políticas e configurações para seus usuários antes de poder arquivar dados para eles. Você pode implantar os bancos de dados de Arquivamento ao mesmo tempo em que implanta a topologia inicial ou após implantar pelo menos um pool front-end ou servidor Standard Edition. Este documento descreve como implantar os bancos de dados de Arquivamento adicionando-os a uma implantação existente.

Se você habilitar o arquivamento em um pool de Front-Ends ou em um servidor Standard Edition, você deve habilitá-lo em todos os pools e servidores de mesmo tipo na sua implantação. Isso porque os usuários cujas comunicações precisam ser arquivadas podem ser convidados a um grupo de conversação de IM ou a reuniões hospedadas em um pool diferente. Se o arquivamento não estiver habilitado no pool no qual a conversa ou a reunião está hospedada, a sessão completa não poderá ser arquivada. Nesses casos, as IMs com usuários habilitados para arquivamento ainda poderão ser arquivados, menos para arquivos de conteúdo de conferência e eventos de ingresso ou saída de conferências.

> [!IMPORTANT]  
> Se o arquivamento for crucial na sua organização por questões de conformidade, certifique-se de implantar o Arquivamento, configurar políticas e outras opções no nível apropriado e habilitá-las para todos os usuários apropriados antes de habilitar esses usuários ao Lync Server 2013.

## Processo de implantação do Arquivamento

A tabela a seguir fornece uma visão geral das etapas necessárias para implantar o arquivamento em uma topologia existente.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Funções e associações de grupo</th>
<th>Documentação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Instalar os pré-requisitos de hardware e software</strong></p></td>
<td><ul><li><p>Para usar a integração do Microsoft Exchange (usando o Exchange 2013 para armazenamento de arquivamento para alguns ou todos os usuários), você precisa de uma implantação do Exchange 2013 existente.</p></li><li><p>Para usar bancos de dados de Arquivamento separados (usando bancos de dados do SQL Server) para armazenamento de arquivamento para alguns ou todos os usuários, SQL Server no servidor que armazenará os dados de arquivamento.</p></li></ul>
<div class="alert">
> [!NOTE]  
> O Arquivamento é executado nos servidores front-end de um pool Enterprise e servidores Standard Edition. Não há requisitos adicionais de hardware e software além daqueles para instalar esses servidores.
</div></td>
<td><p>Usuário do domínio que é membro do grupo local de administradores.</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Hardware suportado para Lync Server 2013</a> na documentação de capacidade de suporte.</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Suporte a software e à infraestrutura de servidor no Lync Server 2013</a> na documentação de capacidade de suporte.</p>
<p><a href="lync-server-2013-technical-requirements-for-archiving.md">Requisitos técnicos de Arquivamento no Lync Server 2013</a> na documentação Planejamento.</p>
<p><a href="lync-server-2013-setting-up-systems-and-infrastructure-for-archiving.md">Configurando sistemas e a infraestrutura para arquivamento no Lync Server 2013</a> na documentação Implantação.</p>
<p><a href="lync-server-2013-exchange-and-sharepoint-integration-support.md">Suporte a Servidor Exchange e à integração com SharePoint no Lync Server 2013</a> na documentação de capacidade de suporte.</p></td>
</tr>
<tr class="even">
<td><p><strong>Crie a topologia interna apropriada para oferecer suporte ao arquivamento (apenas se não estiver usando a integração do Microsoft Exchange para todos os usuários na implantação)</strong></p></td>
<td><p>Execute o Construtor de Topologias para adicionar bancos de dados de Arquivamento do Lync Server 2013 (bancos de dados do SQL Server) à topologia e publicá-la em seguida.</p></td>
<td><p>Para definir a topologia a fim de incorporar bancos de dados de Arquivamento, uma conta que é membro do grupo local de usuários.</p>
<p>Para publicar a topologia, uma conta que é membro do grupo de administradores do domínio e do grupo do RTCUniversalServerAdmins, e que tem permissões de controle total (ler/escrever/modificar) sobre o compartilhamento do arquivo a ser usado para o repositório de arquivos do Lync Server 2013 (de forma que o Construtor de Topologias possa configurar os DACLs requeridos).</p></td>
<td><p><a href="lync-server-2013-adding-archiving-databases-to-an-existing-lync-server-2013-deployment.md">Adicionando o Arquivamento de Bancos de Dados à Implantação Existente do Lync Server 2013</a> na documentação Implantação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Configurar autenticação servidor a servidor (somente se estiver usando a integração do Microsoft Exchange)</strong></p></td>
<td><p>Configure os servidores para habilitar a autenticação entre Lync Server 2013 e Exchange 2013. Recomendamos executar <strong>Test-CsExchangeStorageConnectivity testuser_sipUri -Folder Dumpster</strong> para validar a conectividade do armazenamento de Arquivamento do Exchange antes de habilitar o arquivamento.</p></td>
<td><p>Uma conta com permissões adequadas para gerenciar certificados nos servidores.</p></td>
<td><p><a href="lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md">Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013</a> na documentação de Implantação ou na documentação de Operações.</p></td>
</tr>
<tr class="even">
<td><p><strong>Definir políticas e configurações de arquivamento</strong></p></td>
<td><p>Configure o arquivamento, inclusive se a integração do Microsoft Exchange deve ser usada, a política global e qualquer política de site e usuário (quando não estiver usando a integração do Microsoft Exchange para todos os armazenamentos de dados) e opções específicas de arquivamento, como modo essencial e exportação e limpeza de dados.</p>
<p>Se estiver usando a integração do Microsoft Exchange, configure as políticas de retenção no local do Exchange conforme apropriado.</p></td>
<td><p>Grupo RTCUniversalServerAdmins (somente Windows PowerShell) ou atribua usuários à função CSArchivingAdministrator ou CSAdministrator.</p></td>
<td><p><a href="lync-server-2013-configuring-support-for-archiving.md">Configurando o suporte para arquivamento no Lync Server 2013</a> na documentação Implantação.</p>
<p>Documentação do produto Exchange (se estiver usando a integração do Microsoft Exchange).</p></td>
</tr>
</tbody>
</table>


## Implantando o Lync Server e o Microsoft Exchange em florestas diferentes

Se o Microsoft Exchange Servernão estiver implantado na mesma floresta do Lync Server, você deverá verificar se os seguintes atributos do Active Directory do Exchange estão sincronizados com a floresta onde o Lync Server está implantado:

1.  msExchUserHoldPolicies

2.  proxyAddresses

Este é um atributo com vários valores. Ao sincronizá-lo, você deve mesclar os valores, não substitui-los, de modo a garantir que os valores existentes não sejam perdidos.

