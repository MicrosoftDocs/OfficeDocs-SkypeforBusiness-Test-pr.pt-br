---
title: 'Requisitos de backup e restauração: ferramentas e permissões'
TOCTitle: 'Requisitos de backup e restauração: ferramentas e permissões'
ms:assetid: 35ec2e33-f33e-4f84-9e64-6550fd78aa52
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202171(v=OCS.15)
ms:contentKeyID: 52057596
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de backup e restauração: ferramentas e permissões

 

_**Tópico modificado em:** 2015-03-09_

Este tópico identifica as ferramentas você pode usar para fazer o backup e restauração do Lync Server 2013, as permissões necessárias e se você pode executar comandos remota ou localmente. Especificamente, este tópico foca-se nas ferramentas fornecidas com o Lync Server para backup e restauração.

## Backups

Para fazer backup do Lync Server, use as ferramentas identificadas na tabela a seguir. Todos os comandos que você precisa para fazer o backup do Lync Server podem ter o script gravado e ser executados remotamente.

### Ferramentas para fazer o backup do Lync Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Para fazer o backup:</th>
<th>Use esta ferramenta ou cmdlet:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dados de configuração da topologia (Xds.mdf)</p></td>
<td><p>Export-CsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Dados do serviço de informação da localização (E9-1-1) (Lis.mdf)</p></td>
<td><p>Export-CsLisConfiguration</p></td>
</tr>
<tr class="odd">
<td><p>Dados da configuração do Grupo de Respostas (RgsConfig.mdf)</p></td>
<td><p>Export-CsRgsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Dados persistentes do usuário (banco de dados Rtcxds.mdf)</p>
<p>IDs de conferência</p></td>
<td><p>Export-CsUserData</p></td>
</tr>
<tr class="odd">
<td><ul>
<li><p>Banco de dados de arquivamento (LcsLog.mdf)</p></li>
<li><p>Banco de dados do registro de detalhes da chamada de monitoração (LcsCDR.mdf)</p></li>
<li><p>Banco de dados de QoE de monitoração (QoEMetrics.mdf)</p></li>
</ul></td>
<td><p>Ferramenta de banco de dados do SQL Server, como o SQL Server Management Studio</p></td>
</tr>
<tr class="even">
<td><p>Banco de dados de Chat Persistente (Mgc.mdf)</p></td>
<td><p>Os procedimentos para backup do SQL Server ou Export-CsPersistentChatData. Export-CsPersistentChatData exporta dados de Chat Persistente como um arquivo.</p></td>
</tr>
<tr class="odd">
<td><p>Todos arquivos armazenam: repositório de arquivo do Lync Server, repositório de arquivo de Arquivamento</p>

> [!NOTE]  
> Não faça o backup dos arquivos com o nome <strong>Meeting.Active</strong>. Eles estão em uso e são bloqueados enquanto a reunião ocorre.

</td>
<td><p>Ferramenta de gerenciamento de sistema de arquivos padrão, como o Robocopy.</p></td>
</tr>
</tbody>
</table>


## Restauração

Para restaurar o Lync Server, use as ferramentas na tabela a seguir. Todos os comandos necessários para restaurar o Lync Server podem ter script gravado. Algum deles podem ser executados remotamente, mas outros precisam ser executados localmente, conforme especificado na tabela a seguir.

### Ferramentas para restaurar o Lync Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Para fazer isso:</th>
<th>Use esta ferramenta ou cmdlet:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Crie um computador novo ou limpo</p></td>
<td><ul>
<li><p>Software de instalação do sistema operacional Windows</p></li>
<li><p>Software de instalação do SQL Server</p></li>
<li><p>Certifica o snap-in do Console de Gerenciamento Microsoft (MMC), se estiver restaurando certificados com uma chave privada exportável</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Restaure os dados do repositório de arquivos</p></td>
<td><p>Ferramenta padrão de gerenciamento de sistema de arquivos, como o Robocopy</p></td>
</tr>
<tr class="odd">
<td><p>Recrie bancos de dados vazios e defina permissões para o seguinte:</p>
<ul>
<li><p>Repositório de Gerenciamento Central</p></li>
<li><p>Servidor de Back-End</p></li>
<li><p>Banco de dados de monitoração</p></li>
<li><p>Banco de dados de arquivamento</p></li>
</ul></td>
<td><p>Install-CsDatabase</p></td>
</tr>
<tr class="even">
<td><p>Restaure o ponteiro do Serviços de Domínio Active Directory para o Repositório de Gerenciamento Central</p>

> [!NOTE]  
> Se você perder o ponto de conexão de serviço a qualquer momento, você pode executar este cmdlet novamente.

</td>
<td><p>Set-CsConfigurationStoreLocation</p></td>
</tr>
<tr class="odd">
<td><p>Importe a topologia, políticas e configurações para o Repositório de Gerenciamento Central (Xds.mdf)</p></td>
<td><p>Import-CsConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Publique e ative a topologia</p></td>
<td><p>Construtor de Topologias</p>
<p>- ou -</p>
<p>Publish-CsTopology e Enable-CsTopology</p></td>
</tr>
<tr class="odd">
<td><p>Ative a última topologia publicada</p></td>
<td><p>Enable-CsTopology</p></td>
</tr>
<tr class="even">
<td><p>Reinstale os componentes do Lync Server</p></td>
<td><p>Configuração do Lync Server</p>

> [!NOTE]  
> Localizado na pasta ou mídia de instalação do Lync Server em \setup\amd64\Setup.exe.</td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="odd">
<td><p>Restaure os dados informação da localização (E9-1-1) (Lis.mdf)</p></td>
<td><p>Import-CsLisConfiguration</p></td>
</tr>
<tr class="even">
<td><p>Restaure os dados persistentes do usuário (Rtcxds.mdf)</p></td>
<td><p>Import-CsUserData</p></td>
</tr>
<tr class="odd">
<td><p>Dados da configuração do Grupo de Respostas (RgsConfig.mdf)</p></td>
<td><p>Import-CsRgsConfiguration</p>

> [!NOTE]  
> Se a configuração estiver sendo restaurada em um pool implantado recentemente que não possui dados de Grupo de Resposta no banco de dados, use a opção –OverwriteOwner. Use essa opção mesmo se os dados sendo restaurados estiverem em um pool com o mesmo nome de domínio totalmente qualificado (FQDN). Caso contrário, a importação não terá sucesso devido aos objetos de contatos para os Grupos de Resposta já existirem no .

</td>
</tr>
<tr class="even">
<td><p>Restaure os bancos de dados a seguir:</p>
<ul>
<li><p>Banco de dados de arquivamento (LcsLog.mdf)</p></li>
<li><p>Bancos de dados de monitoração: banco de dados de registro de detalhes da chamada (LcsCDR.mdf) e banco de dados de QoE (QoEMetrics.mdf)</p></li>
</ul></td>
<td><p>Ferramentas de gerenciamento de banco de dados do SQL Server</p></td>
</tr>
<tr class="odd">
<td><p>Banco de dados de Chat Persistente (Mgs.mdf)</p></td>
<td><p>Os procedimentos de restauração do SQL Server ou Import-CsPersistentChatData. Você pode usar o Import-CsPersistentChatData com um arquivo criado pelo Export-CsPersistentChatData, e os dados serão importados para o banco de dados de Chat Persistente.</p></td>
</tr>
</tbody>
</table>


## Permissões exigidas

Os usuários devem ser membro do grupo **RTCUniversalServerAdmins** para efetuar todos os comandos descritos neste tópico. A maior parte dos comandos para restauração e backup não suportam o controle de acesso com base em função (RBAC). Duas exceções são os cmdlets de Chat Persistente Export-CsPersistentChatData e Import-CsPersistentChatData, que devem ser executados por um usuário que é membro do grupo CsPersistentChatAdministrator. Para executar o Assistente de Implantação do Lync Server, um usuário deve, ainda, ser membro do grupo de Administradores Locais.

