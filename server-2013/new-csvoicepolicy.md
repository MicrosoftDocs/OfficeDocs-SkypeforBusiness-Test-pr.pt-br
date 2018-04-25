---
title: New-CsVoicePolicy
TOCTitle: New-CsVoicePolicy
ms:assetid: 3852de89-a604-437a-9fdf-3597b88ce13d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425856(v=OCS.15)
ms:contentKeyID: 49306391
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsVoicePolicy

 

_**Tópico modificado em:** 2015-03-09_

Cria uma nova política de voz. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsVoicePolicy -Identity <XdsIdentity> [-AllowCallForwarding <$true | $false>] [-AllowPSTNReRouting <$true | $false>] [-AllowSimulRing <$true | $false>] [-CallForwardingSimulRingUsageType <VoicePolicyUsage | InternalOnly | CustomUsage>] [-Confirm [<SwitchParameter>]] [-CustomCallForwardingSimulRingUsages <PSListModifier>] [-Description <String>] [-EnableBWPolicyOverride <$true | $false>] [-EnableCallPark <$true | $false>] [-EnableCallTransfer <$true | $false>] [-EnableDelegation <$true | $false>] [-EnableMaliciousCallTracing <$true | $false>] [-EnableTeamCall <$true | $false>] [-EnableVoicemailEscapeTimer <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-Name <String>] [-PreventPSTNTollBypass <$true | $false>] [-PstnUsages <PSListModifier>] [-PSTNVoicemailEscapeTimer <Int64>] [-Tenant <Guid>] [-VoiceDeploymentMode <OnPrem | Online | OnlineBasic | OnPremOnlineHybrid>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 cria uma nova política de voz por usuário com definições padrão, cuja identidade é igual a UserVoicePolicy1.

    New-CsVoicePolicy -Identity UserVoicePolicy1

## EXEMPLO 2

Este exemplo cria uma nova política de voz para cada usuário com a identidade igual a UserVoicePolicy2 e define como False a propriedade AllowSimulRing, indicando que quaisquer usuários aos quais esta política for atribuída não estarão habilitados para o toque simultâneo, um recurso que determina se um segundo telefone (como um celular, por exemplo) pode ser definido para tocar a cada vez que o telefone do escritório do usuário tocar. Este comando também adiciona "Local" à lista de usos da PSTN, que associa esta política de voz a uma rota de voz que também usa o uso da PSTN Local. (observe que o parâmetro Identity não é especificado explicitamente. O parâmetro Identity é um parâmetro posicional e, portanto, se o valor da identidade for colocado primeiro na lista de parâmetros, não há necessidade de afirmar explicitamente que ele é a identidade.)

    New-CsVoicePolicy UserVoicePolicy2 -AllowSimulRing $false -PstnUsages @{add = "Local"}

## EXEMPLO 3

Este exemplo cria uma nova política de voz para o site de Redmond e aplica todos os usos da PSTN definidos por esta política na organização. A primeira linha neste exemplo chama o cmdlet **Get-CsPstnUsage** para recuperar o conjunto global de usos da PSTN da organização e salvá-lo na variável $a. A segunda linha chama o cmdlet **New-CsVoicePolicy** para criar a nova política de voz do site de Redmond. Passa-se um valor ao parâmetro PstnUsages, para adicionar a esta política a lista contida no conjunto global de usos da PSTN. Observe a sintaxe do valor adicionado: $a.Usage. Ela se refere à propriedade Usage das definições de uso da PSTN, que contém a lista de usos da PSTN.

    $a = Get-CsPstnUsage
    New-CsVoicePolicy site:Redmond -PstnUsages @{add = $a.Usage}

## Descrição detalhada

Este cmdlet cria uma nova política de voz. As políticas de voz são utilizadas para gerenciar tais recursos relacionados com o Enterprise Voice como o toque simultâneo (a capacidade de ter um segundo toque telefônico a cada vez que alguém chamar o seu telefone de escritório) e o encaminhamento de chamadas. A política criada por este cmdlet determina se muitos destes recursos estarão habilitados ou desabilitados.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **New-CsVoicePolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsVoicePolicy"}

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
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Um identificador exclusivo que especifica o escopo ou o nome da política. Os valores válidos para este cmdlet são:&lt;nomedosite&gt; (onde &lt;nomedosite&gt; é o nome do site Lync Server ao qual se aplica esta política, como site:Redmond) e uma cadeia de caracteres designando uma política por usuário, como RedmondVoicePolicy. Por padrão, há uma política global.</p></td>
</tr>
<tr class="even">
<td><p><em>AllowCallForwarding</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Se este parâmetro for definido como True, as chamadas poderão ser encaminhadas. Se este parâmetro for definido como False, as chamadas não poderão ser encaminhadas.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowPSTNReRouting</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Quando esse parâmetro for definido como True, as chamadas feitas para os números internos abrigados em outro pool serão encaminhadas através da rede telefônica pública comutada (PSTN) quando o pool ou a WAN estiver indisponível.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>AllowSimulRing</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>O toque simultâneo é um recurso que permite que diversos telefones toquem quando um único número é discado. A definição deste parâmetro como True habilita este recurso. Se este parâmetro for definido como False, o toque simultâneo não poderá ser configurado para nenhum usuário ao qual esta política estiver atribuída.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>CallForwardingSimulRingUsageType</em></p></td>
<td><p>Opcional</p></td>
<td><p>CallForwardingSimulRingUsageType</p></td>
<td><p>Oferece uma forma para os administradores gerenciarem o encaminhamento de chamada e a chamada simultânea. Os valores permitidos são:</p>
<p>* VoicePolicyUsage – O uso da política de voz padrão é usado para gerenciar o encaminhamento de chamada e chamada simultânea em chamadas. Esse é o valor padrõa.</p>
<p>* InternalOnly – Encaminhamento de chamadas e chamada simultânea são limitados para chamadas realizadas de um usuário do Lync para outro.</p>
<p>* CustomUsage. Um uso PSTN personalizado será utilizado para gerenciar o encaminhamento de chamada e chamada simultânea. Esse uso será especificado usando o parâmetro CustomCallForwardingSimulRingUsages.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>CustomCallForwardingSimulRingUsages</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uso PSTN personalizado utilizado para gerenciar o encaminhamento de chamada e chamada simultânea. Para adicionar um uso personalizado para a política de voz use sintaxe semelhante a seguinte:</p>
<p>-CustomCallForwardingSimulRingUsages @{Add=&quot;RedmondPstnUsage&quot;}</p>
<p>Para remover um uso personalizado, use essa sintaxe:</p>
<p>-CustomCallForwardingSimulRingUsages @{Remove=&quot;RedmondPstnUsage&quot;}</p>
<p>Observe que o uso deve existir antes de poder ser usado com o parâmetro CustomCallForwardingSimulRingUsages.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Uma descrição da política de voz.</p>
<p>Comprimento máximo: 1040 caracteres.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableBWPolicyOverride</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>As políticas podem ser definidas para gerenciar a configuração de rede, inclusive para limitar a largura de banda. A definição deste parâmetro como True permitirá a substituição dessas políticas. Em outras palavras, se esse parâmetro for definido como True, nenhuma verificação de largura de banda será realizada e as chamadas serão efetuadas independentemente das definições do controle de admissão de chamadas (CAC).</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCallPark</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>O Aplicativo de Estacionamento de Chamada permite que uma chamada seja mantida (estacionada) em um determinado número de um intervalo de números, para recuperação posterior. A definição deste parâmetro como True habilita o aplicativo. Se este parâmetro for definido como False, os usuários atribuídos a esta política não poderão estacionar chamadas que tiverem sido feitas para o seu número de telefone.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCallTransfer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Determina se as chamadas podem ser transferidas para outro número. Se este parâmetro for definido como True, as chamadas poderão ser transferidas; se o parâmetro for definido como False, as chamadas não poderão ser transferidas.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>EnableDelegation</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>A delegação de chamadas permite a um usuário atender a chamadas de outro usuário ou fazer chamadas em nome de outro. Por exemplo: um gerente pode configurar a delegação de chamadas para que todas as chamadas de entrada toquem tanto no telefone do gerente como no telefone de um administrador. A definição deste parâmetro como True permite que os usuários com esta política configurem a delegação de chamadas. A definição deste parâmetro como False desabilita a delegação de chamadas.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableMaliciousCallTracing</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>O rastreamento de chamada maliciosa é um padrão em vigor que rastreia as chamadas que um usuário indicar como sendo maliciosas. Essas chamadas podem ser rastreadas mesmo se o ID do chamador for bloqueado. O rastreamento está disponível somente para as autoridades apropriadas, e não para o usuário. A definição desta propriedade como True habilita a capacidade de atribuir o rastreamento de chamadas maliciosas.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>EnableTeamCall</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>A Chamada de equipe permite que um usuário designe um grupo de outros usuários cujos telefones tocarão quando o número desse usuário for chamado. Este recurso é útil em equipes nas quais, por exemplo, qualquer pessoa da equipe pode atender a chamadas feitas pelos clientes. A definição deste parâmetro como True habilita este recurso.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableVoicemailEscapeTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Quando definido para True, as chamadas para um dispositivo móvel não respondido serão encaminhadas para uma caixa postal da organização ao invés da caixa postal do provedor de dispositivo móvel. Se uma chamada é respondida &quot;rapidamente&quot; (isto é, antes do valor configurado para a propriedade PSTNVoicemailEscapeTimer ter passado) será assumido que o dispositivo móvel não estará disponível e a chamada será roteada para a caixa postal da organização.</p>
<p>O valor padrão é False.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Name</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Um nome para exibição que descreve esta política.</p>
<p>Padrão: DefaultPolicy</p></td>
</tr>
<tr class="odd">
<td><p><em>PreventPSTNTollBypass</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>As tarifas PSTN são mais comumente conhecidas como tarifas de longa distância. As organizações podem evitar essas tarifas implementando uma solução de Voz sobre o protocolo de Internet (VoIP), que permite aos escritórios se conectarem usando chamadas pela rede. A definição deste parâmetro como True enviará chamadas pela PSTN e incorrerá em tarifas, em vez de utilizar a rede e obter isenção das tarifas.</p>
<p>Padrão: False</p></td>
</tr>
<tr class="even">
<td><p><em>PstnUsages</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>Uma lista de usos da PSTN disponíveis para esta política. O uso da PSTN vincula uma política de voz a uma rota de telefone.</p>
<p>Qualquer valor de cadeia de caracteres pode ser colocado nesta lista, contanto que esse valor exista na lista global de usos da PSTN em vigor. Não são permitidas cadeias de caracteres duplicadas; todas as cadeias de caracteres devem ser exclusivas. A lista de usos da PSTN pode ser recuperada chamando-se o cmdlet <strong>Get-CsPstnUsage</strong>.</p>
<p>Por padrão, esta lista está vazia. Se não for fornecido um valor para este parâmetro, será emitida uma mensagem de aviso informando que os usuários aos quais esta política tiver sido concedida não serão capazes de realizar chamadas de saída da PSTN.</p></td>
</tr>
<tr class="odd">
<td><p><em>PSTNVoicemailEscapeTimer</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int64</p></td>
<td><p>Quantidade de tempo (em milissegundos) usado para determinar se uma chamada será ou não respondida &quot;rapidamente&quot;. Se uma resposta é recebida dentro deste intervalo de tempo, o Lync Server assumirá que o dispositivo móvel não estará disponível e trocará a chamada automaticamente para a caixa postal da organização. Se nenhuma resposta for recebida antes do intervalo de tempo ser atingido, a chamada poderá continuar. O valor padrão é de 1500 milissegundos.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>Guid</p></td>
<td><p>GUID da conta do inquilino do Skype for Business Online para o qual a nova política de voz está sendo criada. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar a ID de inquilino para cada um de seus inquilinos executando esse comando:</p>
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

Nenhuma.

## Tipos de retorno

Este cmdlet cria uma instância do objeto Microsoft.Rtc.Management.WritableConfig.Voice.VoicePolicy.

## Consulte Também

#### Outros Recursos

[Remove-CsVoicePolicy](remove-csvoicepolicy.md)  
[Set-CsVoicePolicy](set-csvoicepolicy.md)  
[Get-CsVoicePolicy](get-csvoicepolicy.md)  
[Grant-CsVoicePolicy](grant-csvoicepolicy.md)  
[Test-CsVoicePolicy](test-csvoicepolicy.md)  
[Get-CsPstnUsage](get-cspstnusage.md)

