---
title: 'Lync Server 2013: Processo de implantação para o aplicativo Comunicado'
TOCTitle: Processo de implantação para o aplicativo Comunicado
ms:assetid: 72c66249-c4ce-48ce-b1b9-90ebf77d7805
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398545(v=OCS.15)
ms:contentKeyID: 49307095
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação para o aplicativo Comunicado no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção fornece uma visão geral das etapas envolvidas na implantação do Aplicativo Comunicado. Você deve implantar o Enterprise Voice antes de configurar os comunicados. Os componentes exigidos pelo Aplicativo Comunicado são instalados e habilitados quando você implanta o Enterprise Voice.

### Processo de implantação do comunicado

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
<th>Funções</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Definir configurações do comunicado</p></td>
<td><ul>
<li><p>Crie o comunicado através da gravação e carregamento de arquivos de áudio ou usando texto em fala (TTS).</p></li>
<li><p>Configure os intervalos de números não atribuídos na tabela de número não atribuída e os associe com o comunicado adequado.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsViewOnlyAdministrator</p></td>
<td><p><a href="lync-server-2013-create-an-announcement.md">Criar um comunicado no Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-the-unassigned-number-table.md">Configurar a tabela de número não atribuído no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Verifique a implantação do comunicado</p></td>
<td><p>Faça o teste escutando os comunicados para verificar se sua configuração funciona como o esperado.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-announcement-deployment.md">(Opcional) Verificar implantação de Comunicado no Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>

