---
title: Set-CsVoicePolicy
TOCTitle: Set-CsVoicePolicy
ms:assetid: e6035b74-d760-4c48-aa0b-d09d129e0830
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399021(v=OCS.15)
ms:contentKeyID: 49308421
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsVoicePolicy

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma política de voz existente. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsVoicePolicy [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsVoicePolicy [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-AllowCallForwarding <$true | $false>] [-AllowPSTNReRouting <$true | $false>] [-AllowSimulRing <$true | $false>] [-CallForwardingSimulRingUsageType <VoicePolicyUsage | InternalOnly | CustomUsage>] [-Confirm [<SwitchParameter>]] [-CustomCallForwardingSimulRingUsages <PSListModifier>] [-Description <String>] [-EnableBWPolicyOverride <$true | $false>] [-EnableCallPark <$true | $false>] [-EnableCallTransfer <$true | $false>] [-EnableDelegation <$true | $false>] [-EnableMaliciousCallTracing <$true | $false>] [-EnableTeamCall <$true | $false>] [-EnableVoicemailEscapeTimer <$true | $false>] [-Force <SwitchParameter>] [-Name <String>] [-PreventPSTNTollBypass <$true | $false>] [-PstnUsages <PSListModifier>] [-PSTNVoicemailEscapeTimer <Int64>] [-Tenant <Guid>] [-VoiceDeploymentMode <OnPrem | Online | OnlineBasic | OnPremOnlineHybrid>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo define a propriedade AllowSimulRing como False para a política por usuário UserVoicePolicy2, indicando que quaisquer usuários atribuídos a esta política não estarão habilitados para o toque simultâneo, um recurso que determina se um segundo telefone (como um celular) pode ser definido para tocar a cada vez que o telefone do escritório do usuário tocar. Este comando também remove "Local" da lista de usos da PSTN desta política (observe que o parâmetro Identity não é especificado explicitamente. O parâmetro Identity é um parâmetro posicional e, portanto, se o valor da identidade for colocado primeiro na lista de parâmetros, não há necessidade de afirmar explicitamente que ele é a identidade.)

    Set-CsVoicePolicy UserVoicePolicy2 -AllowSimulRing $false -PstnUsages @{remove="Local"}

## EXEMPLO 2

Este exemplo modifica uma política de voz do site de Redmond para que todos os usos do PSTN definidos para a organização sejam aplicados a esta política. A primeira linha deste exemplo chama o cmdlet **Get-CsPstnUsage** para recuperar o conjunto global de usos do PSTN da organização e salvá-lo na variável $a. A segunda linha chama o cmdlet **Set-CsVoicePolicy** para modificar a política de voz do site de Redmond. Um valor é passado ao parâmetro PstnUsages para substituir a lista atual de usos da política pela lista contida no conjunto global de usos do PSTN. Observe a sintaxe do valor de substituição: $a.Usage. Isto se refere à propriedade Usage das configurações de uso do PSTN, que contém a lista de usos do PSTN.

    $a = Get-CsPstnUsage
    Set-CsVoicePolicy -Identity site:Redmond -PstnUsages @{replace=$a.Usage}

## Descrição detalhada

Este cmdlet modifica uma política de voz existente. As políticas de voz são utilizadas para gerenciar tais recursos relacionados ao Enterprise Voice como o toque simultâneo (a capacidade de ter um segundo toque telefônico a cada vez que alguém chamar o seu telefone de escritório) e o encaminhamento de chamadas. Use este cmdlet para alterar as definições que habilitam e desabilitam muitos destes recursos.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsVoicePolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsVoicePolicy"}

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>AllowCallForwarding</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Se este parâmetro for definido como True, os usuários atribuídos a essa política poderão encaminhar chamadas. Se este parâmetro for definido como False, as chamadas não poderão ser encaminhadas.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowPSTNReRouting</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Quando esse parâmetro for definido como True, as chamadas feitas para os números internos abrigados em outro pool serão encaminhadas através da rede telefônica pública comutada (PSTN) quando o pool ou a WAN estiver indisponível.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowSimulRing</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>O toque simultâneo é um recurso que permite que diversos telefones toquem quando um único número for discado. A definição deste parâmetro como True habilitará o toque simultâneo. Se este parâmetro for definido como False, o toque simultâneo não poderá ser configurado para nenhum usuário atribuído a esta política.</p></td>
</tr>
<tr class="even">
<td><p><em>CallForwardingSimulRingUsageType</em></p></td>
<td><p>Opcional</p></td>
<td><p>CallForwardingSimulRingUsageType</p></td>
<td><p>Fornece aos administradores uma maneira de gerenciar o encaminhamento de chamada e toque simultâneo. Os valores permitidos são:</p>
<p>* VoicePolicyUsage – O uso de política de voz padrão é usado para gerenciar o encaminhamento de chamada e o toque simultâneo em todas as chamadas. Esse é o valor padrão.</p>
<p>* InternalOnly – Encaminhamento de chamada e toque simultâneo são limitados às chamadas feitas de um usuário do Lync para outro.</p>
<p>* CustomUsage. Um uso de PSTN personalizado será usado para gerenciar o encaminhamento de chamada e o toque simultâneo. Esse uso precisa ser especificado usando o parâmetro CustomCallForwardingSimulRingUsages.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>CustomCallForwardingSimulRingUsages</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uso de PSTN personalizado usado para gerenciar encaminhamento de chamada e toque simultâneo. Para adicionar um uso personalizado à política de voz, use uma sintaxe parecida com a seguinte:</p>
<p>-CustomCallForwardingSimulRingUsages @{Add=&quot;RedmondPstnUsage&quot;}</p>
<p>Para remover um uso personalizado, use esta sintaxe:</p>
<p>-CustomCallForwardingSimulRingUsages @{Remove=&quot;RedmondPstnUsage&quot;}</p>
<p>Observe que o uso precisa existir antes de poder ser usado com o parâmetro CustomCallForwardingSimulRingUsages.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Uma descrição da política de voz.</p>
<p>Comprimento máximo: 1040 caracteres.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableBWPolicyOverride</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>As políticas podem ser definidas para limitar a largura de banda e definir várias outras propriedades relacionadas à configuração de rede. A definição deste parâmetro como True permitirá a substituição dessas políticas. Em outras palavras, se esse parâmetro for definido como True, nenhuma verificação de largura de banda será realizada e as chamadas serão efetuadas independentemente das definições do controle de admissão de chamadas (CAC).</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCallPark</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>O Aplicativo de Estacionamento de Chamada permite que uma chamada seja mantida (estacionada) em um determinado número de um intervalo de números, para recuperação posterior. A definição desse parâmetro como True habilita esse aplicativo para os usuários que tiverem recebido a atribuição dessa política. Se este parâmetro for definido como False, os usuários atribuídos a esta política não poderão estacionar chamadas que tiverem sido feitas para o seu número de telefone.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCallTransfer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Determina se as chamadas podem ser transferidas para outro número. Se este parâmetro for definido como True, as chamadas poderão ser transferidas; se o parâmetro for definido como False, as chamadas não poderão ser transferidas.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableDelegation</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>A delegação de chamadas permite a um usuário atender a chamadas de outro usuário ou fazer chamadas em nome de outro. Por exemplo, um gerente pode configurar a delegação de chamada para que todas as chamadas de entrada toquem tanto no seu telefone como no telefone de um administrador. A definição deste parâmetro como True permite que os usuários com esta política configurem a delegação de chamadas. A definição deste parâmetro como False desabilita a delegação de chamadas.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableMaliciousCallTracing</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>O rastreamento de chamada maliciosa é um padrão em vigor que rastreia as chamadas que um usuário indicar como sendo maliciosas. Essas chamadas podem ser rastreadas mesmo se o ID do chamador for bloqueado. O rastreamento está disponível somente para as autoridades relevantes, e não para o usuário. A definição desta propriedade como True habilita a capacidade de rastrear as chamadas maliciosas.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableTeamCall</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>A Chamada de equipe permite que um usuário designe um grupo de outros usuários cujos telefones tocarão quando o número desse usuário for chamado. Este recurso é útil em equipes nas quais, por exemplo, qualquer pessoa da equipe pode atender a chamadas feitas pelos clientes. A definição deste parâmetro como True habilita este recurso.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableVoicemailEscapeTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>Quando estiver definido como True, as chamadas para um dispositivo móvel sem resposta serão encaminhadas para a caixa postal da organização em vez da caixa postal do provedor do dispositivo móvel. Se uma chamada for atendida &quot;muito rápido&quot; (ou seja, antes de o valor configurado para a propriedade PSTNVoicemailEscapeTimer passar) o dispositivo móvel será considerado não disponível e a chamada será encaminhada para a caixa postal da organização.</p>
<p>O valor padrão é False.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Um identificador exclusivo que especifica o escopo e, em alguns casos, o nome da política.</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>VoicePolicy</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais. Esse objeto deve ser do tipo VoicePolicy e pode ser recuperado chamando-se o cmdlet <strong>Get-CsVoicePolicy</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Um nome intuitivo que descreve esta política.</p></td>
</tr>
<tr class="odd">
<td><p><em>PreventPSTNTollBypass</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booliano</p></td>
<td><p>As tarifas PSTN são mais comumente conhecidas como tarifas de longa distância. As organizações podem evitar essas tarifas implementando uma solução de Voz sobre o protocolo de Internet (VoIP), que permite aos escritórios se conectarem através de chamadas pela rede. A definição deste parâmetro como True enviará chamadas pela PSTN e incorrerá em tarifas, em vez de utilizar a rede e obter isenção das tarifas.</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de usos da PSTN disponíveis para esta política. O uso da PSTN vincula uma política de voz a uma rota de telefone.</p>
<p>Qualquer valor de cadeia de caracteres pode ser colocado nesta lista, contanto que esse valor exista na lista global de usos da PSTN em vigor. (não são permitidas cadeias de caracteres duplicadas; todas as cadeias de caracteres devem ser exclusivas). A lista de usos da PSTN pode ser recuperada chamando-se o cmdlet <strong>Get-CsPstnUsage</strong>.</p>
<p>Lembre-se de que se você usar esse parâmetro para remover todos os usos da PSTN da política, os usuários que tiverem recebido essa política não poderão fazer chamadas de saída da PSTN.</p></td>
</tr>
<tr class="odd">
<td><p><em>PSTNVoicemailEscapeTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int64</p></td>
<td><p>Quantidade de tempo (em milissegundos) usada para determinar se uma chamada foi atendida &quot;muito rápido&quot;. Se uma resposta for recebida dentro desse intervalo de tempo, o Lync Server assumirá que o dispositivo móvel não está disponível e alternará automaticamente a chamada para o correio de voz da organização. Se nenhuma resposta for recebia antes que o intervalo de tempo seja atingido, a chamada terá permissão de prosseguir.</p>
<p>O valor padrão é 1500 milissegundos.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>Guid</p></td>
<td><p>GUID (identificador global exclusivo) do locatário do Skype for Business Online cuja política de voz deve ser modificada. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="odd">
<td><p><em>VoiceDeploymentMode</em></p></td>
<td><p>Opcional</p></td>
<td><p>VoiceDeploymentMode</p></td>
<td><p>Os valores permitidos são:</p>
<p>* OnPrem</p>
<p>* Online</p>
<p>* OnlineBasic</p>
<p>* OnPremOnlineHybrid</p>
<p>O valor padrão é OnPrem.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.VoicePolicy. Aceita entradas canalizadas de objetos de política de voz.

## Tipos de retorno

Este cmdlet não retorna um valor ou objeto. Em vez disso, ele configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Voice.VoicePolicy.

## Consulte Também

#### Outros Recursos

[New-CsVoicePolicy](new-csvoicepolicy.md)  
[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)  
[Get-CsPstnUsage](get-cspstnusage.md)

