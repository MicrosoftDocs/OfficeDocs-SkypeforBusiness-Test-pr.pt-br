---
title: Planilhas de backup e restauração
TOCTitle: Planilhas de backup e restauração
ms:assetid: 26c78155-0306-41ac-845b-7ad58000a1d6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202169(v=OCS.15)
ms:contentKeyID: 52057584
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planilhas de backup e restauração

 

_**Tópico modificado em:** 2015-03-09_

O plano de backup e restauração para sua organização deve conter detalhes sobre como e quando fazer backup de dados e configurações. É possível usar as planilhas apresentadas aqui para ajudá-lo a documentar essas informações para sua implantação específica e seus requisitos de backup e restauração da sua organização.

Use as seguintes planilhas para registrar as informações necessárias para fazer backup e restaurar o banco de dados, Repositório de Arquivos e informações de configurações para um pool do Lync Server ou Servidor Standard Edition. Mantenha uma ou mais cópias dessas planilhas em um local seguro para que estejam prontamente acessíveis se você precisar restaurar o Lync Server.

> [!NOTE]  
> As planilhas desta seção abordam apenas as informações necessárias para restaurar os dados e as configurações de bancos de dados e servidores do Lync Server. Se você precisa documentar outras informações de restauração, como as informações para a reinstalação de sistemas operacionais e outros softwares, use planos de implantação e planos de backup e restauração da sua organização para abordar esses requisitos.

## Planilha de restauração e backup do banco de dados

Use a tabela a seguir para registrar as informações necessárias para fazer backup e restaurar os bancos de dados do Lync Server.

### Informações do banco de dados para backup e restauração

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Banco de dados</th>
<th>Nome do servidor (FQDN)</th>
<th>Programação de backup</th>
<th>Ferramenta de backup do banco de dados</th>
<th>Conjunto de backup</th>
<th>Destino de backup</th>
<th>Observações</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Banco de dados Rtc no servidor de back-end para dados de usuário</p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
<td><p>Cmdlet <strong>Export-CsUserData</strong></p></td>
<td><p>Nome:</p>
<p>Expiração:</p>
<p>                   </p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
</tr>
<tr class="even">
<td><p>Banco de dados do LcsLog (nome padrão) no servidor do Banco de dados de arquivamento</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>Ferramenta de gerenciamento do SQL Server</p></td>
<td><p>Nome:</p>
<p>Expiração:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Banco de dados do LcsCdr no servidor do Banco de dados de monitoramento para registros de detalhes de chamadas (CDRs)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>Ferramenta de gerenciamento do SQL Server</p></td>
<td><p>Nome:</p>
<p>Expiração:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="even">
<td><p>Banco de dados QoEMetrics no servidor do Banco de dados de monitoramento para dados de Qualidade da Experiência (QoE)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>Ferramenta de gerenciamento do SQL Server</p></td>
<td><p>Nome:</p>
<p>Expiração:</p></td>
<td><p> </p></td>
<td><p> </p></td>
</tr>
<tr class="odd">
<td><p>Banco de dados de Chat Persistente</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>Ferramenta de gerenciamento do SQL Server ou cmdlet <strong>Export-CsPersistentChatData</strong></p></td>
<td><p>Nome:</p>
<p>Validade:</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


Nenhum backup ou restauração necessário dos seguintes bancos de dados:

  - Rtcdyn. Os dados do usuário temporário neste banco de dados não não necessários para a restauração do serviço.

  - Rtcab. O banco de dados do Catálogo de endereços é recriado automaticamente pela Lista de Endereços Global (GAL) no Serviços de Domínio Active Directory.

  - Rgsdyn. O dados de serviço do Grupo de resposta temporário neste banco de dados não são necessários para a restauração do serviço.

  - Cpsdyn. A informação dinâmica para o Aplicativo de Estacionamento de Chamada não é necessária para restauração do serviço.

  - MgcComp. O banco de dados de conformidade para Chat Persistente não é necessário para restauração do serviço.

## Planilha de restauração e backup do repositório de arquivos

Use a tabela a seguir para registrar as informações que necessárias para fazer backup e restaurar os repositórios de arquivos. Os repositórios de arquivos contêm dados como metadados de conteúdo da reunião, logs de conformidade de reunião, logs de atualização para atualizações de dispositivo e arquivos de áudio para o Grupo de Resposta, Estacionamento de Chamada e aplicativos de Anúncio.

### Informações do repositório de arquivos para backup e restauração

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Conteúdo</th>
<th>Nome do servidor (FQDN)</th>
<th>Programação de backup</th>
<th>Ferramenta de backup de sistema de arquivos</th>
<th>Compartilhamento de arquivos a ser realizado o backup*</th>
<th>Destino de backup</th>
<th>Observações</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Repositório de Arquivos do Lync Server</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>Ferramenta de backup padrão, como o Robocopy</p></td>
<td><p>No servidor de arquivos para Enterprise Edition. No Standard Edition por padrão, para implantação do Standard Edition. Geralmente, um por local.</p></td>
<td><p></p></td>
<td><p>Arquivos nomeados <strong>Meeting.Active</strong> não devem ser colocados em backup. Esses arquivos estão em uso e bloqueados durante uma reunião.</p></td>
</tr>
</tbody>
</table>


## Planilha de configurações de backup e restauração

Use a tabela a seguir para registrar as informações necessárias para fazer backup e restaurar as configurações.

### Informações de configurações para backup e restauração

<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Banco de dados</th>
<th>Nome do servidor (FQDN)</th>
<th>Programação de backup</th>
<th>Ferramenta de backup</th>
<th>Nome do arquivo (.xml) de configuração</th>
<th>Local de backup</th>
<th>Observações</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Bancos de dados Xds no Repositório de Gerenciamento Central para configuração de topologia (global)</p></td>
<td><p>                    </p></td>
<td><p>                    </p></td>
<td><p>Cmdlet <strong>Export-CsConfiguration</strong></p></td>
<td><p>                   </p></td>
<td><p>                    </p></td>
<td><p>                   </p></td>
</tr>
<tr class="even">
<td><p>Banco de dados do Lis na informação de localização E9-1-1 (global) do Repositório de Gerenciamento Central</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>Cmdlet <strong>Export-CsLisConfiguration</strong></p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>                    </p></td>
</tr>
<tr class="odd">
<td><p>Banco de dados RgsConfig no servidor back-end para configuração do Grupo de Resposta (pool)</p></td>
<td><p> </p></td>
<td><p> </p></td>
<td><p>Cmdlet <strong>Export-CsRgsConfiguration</strong></p></td>
<td><p></p></td>
<td><p> </p></td>
<td><p>                    </p></td>
</tr>
</tbody>
</table>

