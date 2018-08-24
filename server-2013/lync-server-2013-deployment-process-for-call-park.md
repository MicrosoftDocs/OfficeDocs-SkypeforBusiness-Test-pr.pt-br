---
title: 'Lync Server 2013: Processo de implantação para Estacionamento de Chamada'
TOCTitle: Processo de implantação para Estacionamento de Chamada
ms:assetid: 2000d672-a85f-4262-9d69-0bee9ae3709a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398283(v=OCS.15)
ms:contentKeyID: 49306109
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação para Estacionamento de Chamada no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção oferece uma visão geral das etapas envolvidas na implantação do Aplicativo de Estacionamento de Chamada. Você deve implantar o Enterprise Edition ou Standard Edition com o Enterprise Voice antes de configurar o Estacionamento de Chamada. Os componentes exigidos pelo Estacionamento de Chamada estão instalados e habilitados ao implantar o Enterprise Voice.

### Implantação do Processo de Estacionamento de Chamada

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
<td><p>Configure os intervalos de órbita de estacionamento de chamada na tabela de órbita</p></td>
<td><p>Use o cmdlet Painel de Controle do Lync Server ou <strong>New-CSCallParkOrbit</strong> para criar os intervalos de órbita na tabela de órbita de estacionamento de chamada e associe-a com o Serviço de aplicativos que hospeda o Aplicativo de Estacionamento de Chamada.</p>

> [!NOTE]  
> Para uma integração perfeita aos planos de discagem existentes, os intervalos de órbitas são normalmente considerados como um bloco de ramais virtuais. A atribuição dos números DID (Discagem Direta de Entrada) como números de órbita na tabela de órbita de estacionamento de chamada não é suportada.

</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-create-or-modify-a-call-park-orbit-range.md">Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure o Estacionamento de Chamada</p></td>
<td><p>Use o cmdlet <strong>Set-CsCpsConfiguration</strong> para definir as configurações do Estacionamento de Chamada. Como mínimo, recomendamos que você configure a opção <strong>OnTimeoutURI</strong> para definir o destino de fallback para usar quando uma chamada estacionada esgota. Também é possível definir as seguintes configurações:</p>
<ul>
<li><p>(Opcional) <strong>EnableMusicOnHold</strong> para ativar ou desativar música em espera.</p></li>
<li><p>(Opcional) <strong>MaxCallPickupAttempts</strong> para determinar o número de vezes que uma chamada estacionada toca novamente no telefone de atendimento, antes de ser encaminhada para o URI (Uniform Resource Identifier) de fallback.</p></li>
<li><p>(Opcional) <strong>CallPickupTimeoutThreshold</strong> para determinar o tempo decorrido depois que a chamada foi estacionada, antes que toque novamente no telefone em que foi atendida.</p></li>
</ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-call-park-settings.md">Configurações de estacionamento de chamadas no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Opcionalmente, personalize a música em espera</p></td>
<td><p>Use o cmdlet <strong>Set-CsCallParkServiceMusicOnHoldFile</strong> para personalizar e carregar um arquivo de áudio, se você não deseja usar a música em espera padrão.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-customize-call-park-music-on-hold.md">Personalizar a música de espera do estacionamento de chamada no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure a política de voz para habilitar o Estacionamento de Chamada para os usuários</p></td>
<td><p>Use o cmdlet Painel de Controle do Lync Server ou <strong>Set-CSVoicePolicy</strong> com a opção <strong>EnableCallPark</strong> para habilitar o Estacionamento de Chamada para usuários na política de voz.</p>

> [!NOTE]  
> Por padrão, o Estacionamento de Chamada está desativado para todos os usuários.


> [!NOTE]  
> Se você tiver diversas políticas de voz, veja se a propriedade EnableCallPark está configurada para cada política, não somente para a padrão.

</td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsUserAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-enable-call-park-for-users.md">Habilitar Estacionamento de Chamadas para usuários no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verifique as regras de normalização para o Estacionamento de Chamada</p></td>
<td><p>Órbitas de estacionamento de chamadas não devem ser normalizadas. Verifique se suas regras de normalização não incluem nenhum intervalo de órbita. Se necessário, crie regras adicionais de normalização para evitar órbitas normalizadas.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-verify-normalization-rules-for-call-park.md">Verificar regras de normalização para Estacionamento de Chamadas no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Verifique sua implantação do Estacionamento de Chamada</p></td>
<td><p>Teste estacionar e recuperar chamadas para verificar se a configuração funciona como esperado.</p></td>
<td><p>-</p></td>
<td><p><a href="lync-server-2013-optional-verify-call-park-deployment.md">(Opcional) Verificar implantação de Estacionamento de Chamadas no Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>

