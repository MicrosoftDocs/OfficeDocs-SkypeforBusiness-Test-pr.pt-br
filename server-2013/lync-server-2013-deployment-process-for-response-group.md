---
title: 'Lync Server 2013: Processo de implatação para Grupo de Resposta'
TOCTitle: Processo de implatação para Grupo de Resposta
ms:assetid: d390c8a1-dc6e-44d8-b386-2be1fca9877c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205270(v=OCS.15)
ms:contentKeyID: 49308197
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implatação para Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção fornece uma visão geral das etapas e fases envolvidas na implantação do Aplicativo Grupo de Resposta.

### Processo de implantação do grupo de resposta

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
<th>Permissões</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Instalar o Aplicativo Grupo de Resposta</p></td>
<td><p>O Aplicativo Grupo de Resposta é instalado e ativado por padrão ao implantar o Enterprise Voice.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploying-enterprise-voice.md">Implantando o Enterprise Voice no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Instala componentes do Grupo de Resposta</p></td>
<td><p>Os cmdlets do Lync Server, os agentes do Painel de Controle do Lync Server, Ferramenta de Configuração de Grupo de Resposta, se conectam e desconectam do console e o serviço da Web do Cliente do Grupo de Resposta são instalados como parte do Web Services. O Web Services é instalado ao implantar um pool do Enterprise Edition ou um Servidor Standard Edition.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploying-lync-server.md">Implantando o Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Habilita os usuários do Lync 2013 e do Enterprise Voice</p></td>
<td><p>Habilita os usuários que serão agentes do Lync Server e Enterprise Voice. Os usuários devem ser habilitados antes de adicioná-los a grupos de agente. Geralmente, os usuários são habilitados para Lync Server durante a implantação do Enterprise Edition ou Servidor Standard Edition. Os usuários são habilitados para Enterprise Voice durante a implantação do Enterprise Voice.</p></td>
<td><p>RTCUniversalUserAdmins</p>
<p>CsUserAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-disable-or-re-enable-user-account-for-lync-server.md">Habilitar ou reabilitar uma conta de usuário para o Lync Server</a></p>
<p><a href="lync-server-2013-enable-users-for-enterprise-voice.md">Habilitar usuários para Enterprise Voice no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Criar e configura grupos de resposta, que consistem de grupos de agentes, filas e fluxos de trabalho</p></td>
<td><ol>
<li><p>Use o Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server para fazer o seguinte:</p>
<ol>
<li><p>Criar e configurar grupos de agentes.</p></li>
<li><p>Criar e configurar filas.</p></li>
</ol></li>
<li><p>Opcionalmente, use o Shell de Gerenciamento do Lync Server para criar horas comerciais e feriados dos grupos de resposta predefinidos.</p></li>
<li><p>Use o Ferramenta de Configuração de Grupo de Resposta ou Shell de Gerenciamento do Lync Server para criar fluxos de trabalho (fluxos de chamada coletivos ou de resposta de voz interativa (IVR)), incluindo o horário comercial e feriados do grupo de resposta personalizada.</p>

> [!NOTE]  
> É possível acessar o Ferramenta de Configuração de Grupo de Resposta através do Painel de Controle do Lync Server.

</li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsResponseGroupManager</p></td>
<td><p><a href="lync-server-2013-create-response-group-agent-groups.md">Criar grupos de agente do Grupo de Resposta no Lync Server 2013</a></p>
<p><a href="lync-server-2013-create-response-group-queues.md">Criar filas do Grupo de Resposta no Lync Server 2013</a></p>
<p><a href="lync-server-2013-optional-define-response-group-business-hours.md">(Opcional) Definir horário comercial do Grupo de Resposta no Lync Server 2013</a></p>
<p><a href="lync-server-2013-optional-define-response-group-holiday-sets.md">(Opcional) Definir os conjuntos de feriados do grupo de resposta no Lync Server 2013</a></p>
<p><a href="lync-server-2013-create-or-modify-a-workflow.md">Criar ou modificar um fluxo de trabalho</a></p></td>
</tr>
<tr class="odd">
<td><p>(Opcional) Personalizar configurações a nível de aplicativo</p></td>
<td><p>Use o Shell de Gerenciamento do Lync Server para personalizar a configuração de música em espera padrão, o arquivo de áudio da música em espera padrão, o período de toque do agente e a configuração do contexto da chamada.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-managing-application-level-response-group-settings.md">Gerenciando configurações do grupo de resposta a nível do aplicativo</a></p></td>
</tr>
<tr class="even">
<td><p>(Opcional) Delega o gerenciamento dos grupos de resposta</p></td>
<td><p>Atribui usuários com a função CsResponseGroupManager para delegar a configuração dos grupos de resposta. Os gerentes do Grupo de Resposta podem configurar os grupos de resposta atribuídos a eles.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verificar a implantação do grupo de respostas</p></td>
<td><p>Teste responder chamadas para seu fluxo de trabalho de resposta de voz interativa e grupo coletivo para garantir que sua configuração funcione como esperado.</p></td>
<td><p>-</p></td>
<td><p>-</p></td>
</tr>
</tbody>
</table>

