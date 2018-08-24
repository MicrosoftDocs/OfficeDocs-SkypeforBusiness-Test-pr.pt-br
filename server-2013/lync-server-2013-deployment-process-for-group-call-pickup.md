---
title: Processo de implantação do recebimento de chamadas em grupo
TOCTitle: Processo de implantação do recebimento de chamadas em grupo
ms:assetid: 082daeac-e667-4e2d-b78d-8e0901f9f0e9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945615(v=OCS.15)
ms:contentKeyID: 52057550
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação do recebimento de chamadas em grupo

 

_**Tópico modificado em:** 2015-03-09_

Esta seção oferece uma visão geral das etapas envolvidas na implantação do Recebimento de chamada de grupo. Você deve implantar o Enterprise Edition ou Standard Edition com o Enterprise Voice antes de configurar o Recebimento de chamada de grupo. Os componentes exigidos pelo Recebimento de chamada de grupo estão instalados e habilitados ao implantar o Enterprise Voice.

### Processo de implantação do Recebimento de chamada de grupo

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
<th>Grupos e funções necessários</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Ative a ferramenta de kit de recursos SEFAUtil na topologia</p></td>
<td><ol>
<li><p>Use o cmdlet <strong>New-CsTrustedApplicationPool</strong> para criar um novo pool de aplicativo confiável.</p></li>
<li><p>Use o cmdlet <strong>New-CsTrustedApplication</strong> para especificar a ferramenta SEFAUtil como aplicativo confiável.</p></li>
<li><p>Execute o cmdlet <strong>Enable-CsTopology</strong> para ativar a topologia.</p></li>
<li><p>Instale as ferramentas do kit de recursos em um Servidor Front-End que está no pool de aplicativo confiável criado na etapa 1.</p></li>
<li><p>Verifique se o SEFAUtil está executando corretamente ao executá-lo para exibir as configurações de encaminhamento de chamada de um usuário na implantação.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-deploy-the-sefautil-tool.md">Implantar a ferramenta SEFAUtil</a></p></td>
</tr>
<tr class="even">
<td><p>Configure os intervalos de número para recebimento de chamada na tabela de órbita de estacionamento de chamada</p></td>
<td><p>Use o cmdlet <strong>New-CSCallParkOrbit</strong> para criar faixas de número de recebimento de chamada na tabela de órbita de estacionamento de chamada e atribua as intervalos de recebimento de chamada ao tipo GroupPickup.</p>

> [!NOTE]  
> Você deve usar o Shell de Gerenciamento do Lync Server para criar, modificar, remover e visualizar os intervalos de números de recebimento de chamadas de grupo na tabela da órbita de estacionamento de chamadas. Os intervalos de números do recebimento de chamadas de grupo não estão disponíveis no Painel de Controle do Lync Server.


> [!NOTE]  
> Para uma integração perfeita aos planos de discagem existentes, os intervalos de número são normalmente configurados como um bloco de ramais virtuais. A atribuição dos números de Discagem Direta de Entrada (DID) como números de intervalos na tabela de órbita de estacionamento de chamada não é suportada.

</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-call-pickup-group-numbers.md">Configurar os números do recebimento de chamadas em grupo</a></p></td>
</tr>
<tr class="odd">
<td><p>Atribua um número de recebimento de chamada aos usuários e ative o Recebimento de chamada de grupo aos usuários</p></td>
<td><p>Use o parâmetro /enablegrouppickup na ferramenta de kit de recursos SEFAUtil para ativar o Recebimento de chamada de grupo e atribuir um número de recebimento de chamada para os usuários.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-enable-group-call-pickup-for-users-and-assign-a-group-number.md">Habilitar o recebimento de chamadas em grupo para os usuários e atribuir um número de grupo</a></p></td>
</tr>
<tr class="even">
<td><p>Notifique os usuários do número de recebimento de chamada atribuído e qualquer outro número de interesse</p></td>
<td><p>Por qualquer usuário poder recuperar uma chamada feita a um usuário de Recebimento de chamada de grupo, os usuários podem querer monitorar mais de um grupo.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-communicate-group-call-pickup-assignment-to-users.md">Comunicar a atribuição do recebimento de chamadas de grupo aos usuários</a></p></td>
</tr>
<tr class="odd">
<td><p>Verifique a implantação de Recebimento de chamada de grupo</p></td>
<td><p>Teste fazer e receber chamadas para garantir que a configuração funcione conforme o esperado.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-the-group-call-pickup-deployment.md">(Opcional) Verificar a implantação do recebimento de chamadas em grupo</a></p></td>
</tr>
</tbody>
</table>

