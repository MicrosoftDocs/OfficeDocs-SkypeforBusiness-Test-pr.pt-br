---
title: Test-CsGroupIM
TOCTitle: Test-CsGroupIM
ms:assetid: 1e73fd7a-5727-4688-8d4c-a3107c3985e9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398273(v=OCS.15)
ms:contentKeyID: 49306082
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsGroupIM

 

_**Tópico modificado em:** 2015-03-09_

Testa a possibilidade de dois usuários realizarem uma conferência de IM (sistema de mensagens instantâneas). O cmdlet **Test-CsGroupIM** é uma "transação sintética": uma simulação de atividades comuns do Lync Server para monitoramento de integridade e desempenho. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsGroupIM -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsGroupIM -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsGroupIM [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-TestJoinLauncher <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um par de usuários de teste pré-configurados pode fazer logon no pool atl-cs-001.litwareinc.com e participar de uma conferência de IM. Esse comando só funcionará se usuários de teste tiverem sido definidos no pool atl-cs-001.litwareinc.com. Se for esse o caso, o comando irá determinar se os dois usuários de teste podem fazer logon no sistema e verificar se esses usuários podem participar de uma conferência do sistema de mensagens instantâneas.

Se usuários de testes não tiverem sido definidos, o comando irá falhar porque não vai saber quais usuários empregar ao fazer o teste. Se usuários de testes não tiverem sido definidos para um pool, será preciso incluir o parâmetro SenderSipAddress e ReceiverSipAddress e as credenciais correspondentes para os usuários envolvidos na sessão de mensagens instantâneas. Em seguida, o cmdlet **Test-CsGroupIM** realizará suas verificações usando os dois usuários especificados.

    Test-CsGroupIm -TargetFqdn atl-cs-001.litwareinc.com

## EXEMPLO 2

Os comandos mostrados no Exemplo 2 testam a capacidade de um par de usuários (litwareinc\\pilar e litwareinc\\kenmyer) de fazerem login no Lync Server e participarem em uma conferência de mensagens instantâneas. Para fazer isso, o primeiro comando do exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman (como o nome de logon litwareinc\\pilar foi incluído como parâmetro, a caixa de diálogo Solicitação de Credenciais do Windows PowerShell resultante só exigirá que o administrador digite a senha da conta de Pilar Ackerman). O objeto de credencial resultante é armazenado em uma variável chamada $cred1. O segundo comando faz a mesma coisa, mas retorna um objeto de credencial para a conta de Ken Myer.

Com os dois objetos de credencial disponíveis, o terceiro comando no exemplo determina se os dois usuários podem ou não fazer logon no Lync Server e, em seguida, participar de uma conferência do sistema de mensagens instantâneas. Para realizar essa tarefa, o cmdlet **Test-CsGroupIM** é chamado, com os seguintes parâmetros: TargetFqdn (FQDN do pool do Registrador); SenderSipAddress (endereço SIP do primeiro usuário); SenderCredential (credenciais de usuário do primeiro usuário); ReceiverSipAddress (endereço SIP do segundo usuário); e ReceiverCredential (credenciais de usuário do segundo usuário).

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsGroupIm -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## Descrição detalhada

O cmdlet **Test-CsGroupIM** é um exemplo de uma transação sintética do Lync Server. As transações sintéticas são usadas no Lync Server para verificar se os usuários podem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador, ou ser executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Transações sintéticas costumam ser conduzidas de duas maneiras diferentes. Muitos administradores vão usar os cmdlets **CsHealthMonitoringConfiguration** para configurar um usuário de teste para cada um de seus pools de Registrador. Esses usuários de teste são um par de usuários pré-configurados para uso com transações sintéticas (geralmente, são contas de testes, e não contas que pertençam a usuários reais). Com contas de usuário de testes configuradas para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool sem ter que especificar as identidades (e fornecer as credenciais) das contas de usuário envolvidas no teste.

Outra opção para os administradores é a de executar uma transação sintética com contas de usuário reais. Por exemplo, se dois usuários não conseguirem trocar mensagens instantâneas, um administrador poderia executar uma transação sintética usando as duas contas de usuário em questão (em vez de um par de contas de testes) para tentar diagnosticar e resolver o problema. Se optar por conduzir uma transação sintética usando contas de usuário reais, será necessário fornecer as credenciais de cada usuário.

O cmdlet **Test-CsGroupIM** permite verificar se os usuários na organização podem realizar conferências. O cmdlet **Test-CsGroupIM** exige duas contas de usuário para realizar seus testes. Se configurar usuários de testes para o pool no qual o teste deverá ser realizado, você não precisará especificar essas contas; em vez disso, o cmdlet **Test-CsGroupIM** usará automaticamente as contas de testes atribuídas ao pool (para detalhes, consulte o tópico de ajuda do cmdlet [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)). Uma opção é realizar o teste usando contas diferentes das atribuídas ao Registrador. Isso permitirá executar testes, mesmo se você não tiver configurado usuários de testes para o pool. Isso também permite testar a possibilidade de dois usuários específicos realizarem uma conferência. Se optar por usar essa abordagem, você precisará fornecer o nome de usuário e a senha de ambos os usuários.

Quando o cmdlet **Test-CsGroupIM** é executado, o cmdlet tenta fazer com que ambos os usuários de testes entrem no Lync Server. Se houver êxito, o cmdlet **Test-CsGroupIM** criará uma nova conferência usando o primeiro usuário de teste e, em seguida, convidará o segundo usuário para ingressar na conferência. Depois de uma troca de mensagens, ambos os usuários são desconectados do sistema. Tudo isso acontece sem nenhuma interação por parte do usuário e sem afetar nenhum usuário real. Por exemplo, suponhamos que a conta de teste sip:kenmyer@litwareinc.com corresponda a um usuário real com uma conta real do Lync Server. Nesse caso, o teste será realizado sem nenhuma interrupção para o Ken Myer real. Por exemplo, mesmo quando a conta de teste Ken Myer fizer logoff do sistema, a pessoa Ken Myer permanecerá conectada. Da mesma forma, o Ken Myer real não receberá um convite para ingressar na conferência. Esse convite será enviado para e aceito pela conta de teste.

O parâmetro Verbose oferece um relatório detalhado de todas as ações realizadas por o cmdlet **Test-CsGroupIM** para concluir seu teste.

Quem pode executar este cmdlet: Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsGroupIM"}

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
<td><p><em>ReceiverCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário para a primeira das duas contas de usuário a serem testadas. O valor passado para ReceiverCredential deve ser uma referência de objeto obtida usando-se o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credencial para a usuária litwareinc\pilar e armazena esse objeto em uma variável chamada $y:</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>É preciso fornecer a senha de usuário ao executar este comando.</p>
<p>A credencial de destinatário não será necessária se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário para a segunda das duas contas de usuário a serem testadas. O valor passado para SenderCredential deve ser uma referência de objeto obtida usando-se o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credencial para o usuário litwareinc\kenmyer e armazena esse objeto em uma variável chamada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É preciso fornecer a senha de usuário ao executar este comando.</p>
<p>A credencial de remetente não será necessária se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia</p></td>
<td><p>O FQDN (nome de domínio totalmente qualificado) do pool a ser testado.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>Opcional</p></td>
<td><p>SipSyntheticTransaction + AuthenticationMechanism</p></td>
<td><p>Tipo de autenticação usada no teste. Os valores permitidos são:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Quando presente, o resultado detalhado ao executar o cmdlet será armazenado na variável especificada. Essa variável inclui um par de métodos – ToHTML e ToXML – e pode ser usado para salvar o resultado em um arquivo HTML ou XML.</p>
<p>Para armazenar o resultado em uma variável de registro em log chamada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: Não insira um caractere $ quando especificar o nome da variável. Para salvar a informação armazenada na variável de registro em log em um arquivo HTML, use um comando semelhante ao seguinte:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar a informação armazenada na variável de registro em log em um arquivo XML, use um comando semelhante ao seguinte:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável chamada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque um caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>O endereço SIP da primeira das duas contas de usuário a serem testadas. Por exemplo: -ReceiverSipAddress &quot;sip:pilar@litwareinc.com&quot;. O parâmetro ReceiverSIPAddress deve referenciar a mesma conta de usuário que ReceiverCredential.</p>
<p>O endereço SIP não será necessário se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não será necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>O endereço SIP da segunda das duas contas de usuário a serem testadas. Por exemplo: -SenderSipAddres &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro SenderSIPAddress deve referenciar a mesma conta de usuário que SenderCredential.</p>
<p>O endereço SIP não será necessário se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>TestJoinLauncher</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Quando presente, testa a capacidade de habilidade do Join Launcher participar de uma conferência AV. O Join Launcher é usado para ajudar os usuários de dispositivos móveis (e, como resultado, os usuários do Serviço de Mobilidade) a fazerem parte das conferências.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsGroupIM** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Test-CsGroupIM** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsIM](test-csim.md)

