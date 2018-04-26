---
title: Test-CsIM
TOCTitle: Test-CsIM
ms:assetid: 2fdab54c-5ec4-4db5-b29c-a3efaae68f66
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425802(v=OCS.15)
ms:contentKeyID: 49306276
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsIM

 

_**Tópico modificado em:** 2015-03-09_

Testa a habilidade de dois usuários trocarem mensagens instantâneas. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsIM -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsIM -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsIM [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-EmailHost <String>] [-Force <SwitchParameter>] [-IsSsl <$true | $false>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-Password <String>] [-Port <UInt16>] [-TestLegalIntercept <SwitchParameter>] [-Username <String>] [-WaitSeconds <Int16>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um par de usuários de teste pré-definidos pode conectar no pool atl-cs-001.litwareinc.com e, então, trocar mensagens instantâneas. Esse comando só funcionará se usuários de teste tiverem sido definidos no pool atl-cs-001.litwareinc.com. Se tiverem sido, então o comando vai determinar se os dois usuários podem se conectar ao sistema e, se for o caso, se podem trocar mensagens instantâneas. I

Se usuários de testes não tiverem sido definidos, o comando falhará porque não saberá quais usuários empregar ao fazer o teste. Se um Registrador não tiver sido definido para um pool, será necessário incluir os parâmetros SenderSipAddress e ReceiverSipAddress, além das credenciais correspondentes para os usuários envolvidos na sessão de IM. Em seguida, o cmdlet **Test-CsIM** conduzirá suas verificações usando os dois usuários especificados.

    Test-CsIm -TargetFqdn atl-cs-001.litwareinc.com

## EXEMPLO 2

Os comandos mostrados no Exemplo 2 testam a capacidade de um par de usuários (litwareinc\\pilar e litwareinc\\kenmyer) de fazerem logon no Lync Server e trocarem mensagens instantâneas. Para fazer isso, o primeiro comando do exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman (como o nome de logon litwareinc\\pilar foi incluído como parâmetro, a caixa de diálogo Solicitação de Credenciais do Windows PowerShell só exigirá que o administrador digite a senha da conta de Pilar Ackerman). O objeto de credencial resultante é armazenado na variável chamada $cred1. O segundo comando faz a mesma coisa, desta vez retornando o objeto de credencial para a conta Ken Myer.

Com os dois objetos de credencial em mãos, o terceiro comando no exemplo determina se os dois usuários podem conectar ao Lync Server e, então, trocar mensagens instantâneas. Para fazer isso, o cmdlet **Test-CsIM** é chamado, junto como os seguintes parâmetros: TargetFqdn (o FQDN do pool do Registrador); SenderSipAddress (o endereço SIP do primeiro usuário de teste); SenderCredential (o objeto do Windows PowerShell que contém as credenciais desse usuário); -ReceiverSipAddress (o endereço SIP do outro usuário de teste); e ReceiverCredential (o objeto do Windows PowerShell que contém as credenciais do outro usuário).

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsIm -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## Descrição detalhada

O cmdlet **Test-CsIM** é um exemplo de "transação sintética" do Lync Server. As transações sintéticas são usadas no Lync Server para verificar se os usuários podem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador, ou ser executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Transações sintéticas são tipicamente conduzidas de duas formas diferentes. Muitos administradores vão usar os cmdlets **CsHealthMonitoringConfiguration** para configurar um usuário de teste para cada um de seus pools de Registrador. Esses usuários de teste são um par de usuários pré-configurados para uso com transações sintéticas (geralmente, são contas de testes, e não contas que pertençam a usuários reais). Com contas de usuário de testes configuradas para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool sem ter que especificar as identidades (e fornecer as credenciais) das contas de usuário envolvidas no teste.

De forma alternativa, administradores podem executar uma transação sintética usando contas de usuários de verdade. Por exemplo, se dois usuários não conseguem trocar mensagens instantâneas, um administrador pode executar transações sintéticas usando as duas contas de usuário em questão (ao invés de duas contas de teste) para tentar diagnosticar e resolver o problema. Se optar por conduzir uma transação sintética usando contas de usuário reais, será necessário fornecer as credenciais de cada usuário.

O cmdlet **Test-CsIM** primeiro tenta fazer logon de um par de usuários de teste no Lync Server. Presumindo que os dois logons tenham êxito, o cmdlet então inicia uma sessão de IM (mensagens instantâneas) entre os dois usuários de teste (Usuário 1 convida Usuário 2 para uma sessão de IM, e Usuário 2 aceita o convite). Depois de verificar se as mensagens podem ser trocadas entre os dois usuários, o cmdlet **Test-CsIM** então termina a sessão de mensagem instantânea e faz logoff dos dois usuários do sistema.

Quem pode executar este cmdlet: Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsIM"}

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
<p>Você deve fornecer a senha do usuário quando executando este comando.</p>
<p>A credencial de destinatário não será necessária se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário para a segunda das duas contas de usuário a serem testadas. O valor passado para SenderCredential deve ser uma referência de objeto obtida usando-se o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credenciais para o usuário litwareinc\kenmyer e grava este objeto em uma variável chamada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>Você deve fornecer a senha do usuário quando executando este comando.</p>
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
<td><p><em>EmailHost</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Hospeda email para o usuário implantado no teste Legal Intercept. Por exemplo:</p>
<p>-EmailHost &quot;litwareinc.com&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>IsSsl</em></p></td>
<td><p>Opcional</p></td>
<td><p>Booleano</p></td>
<td><p>Quando definido para True, especifica que o teste está sendo conduzido usando o protocolo SSL.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Quando presente, o resltado detalhado na execução do cmdlet será armazenado na variável especificada. Essa variável inclui um par de métodos – ToHTML e ToXML – que pode ser usado para salvar esse resultado em um arquivo HTML ou XML.</p>
<p>Para armazenar o resultado em uma variável de registro em log chamada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: Não insira um caractere $ ao especificar o nome da variável. Para salvar a informação armazenada na variável de registro em log em um arquivo HTML, use um comando semelhante ao seguinte:</p>
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
<td><p><em>Password</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Senha implantada no teste Legal Intercept.</p></td>
</tr>
<tr class="odd">
<td><p><em>Port</em></p></td>
<td><p>Opcional</p></td>
<td><p>UInt16</p></td>
<td><p>Porta usada para o serviço Legal Intercept.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Endereço SIP para a primeira das duas contas de usuário a serem testadas. Por exemplo: -ReceiverSipAddress &quot;sip:jhaas@litwareinc.com&quot;. O parâmetro ReceiverSipAddress deve referenciar a mesma conta de usuário que ReceiverCredential.</p>
<p>O endereço SIP não será necessário se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço de Registrador. Este parâmetro não é obrigatório se o Registrador usa a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Endereço SIP para a segunda das duas contas de usuário a serem testadas. Por exemplo: -SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro SenderSipAddress deve referenciar a mesma conta de usuário de SenderCredential.</p>
<p>O endereço SIP não será necessário se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>TestLegalIntercept</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Quando usado, instrui o Test-CsIM a testar o serviço Legal Intercept para o usuário especificado.</p></td>
</tr>
<tr class="even">
<td><p><em>Username</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Nome de usuário para o usuário implantado no teste Legal Intercept.</p></td>
</tr>
<tr class="odd">
<td><p><em>WaitSeconds</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int16</p></td>
<td><p>Especifica a quantidade de tempo (em segundos) que o sistema deve aguardar pela resposta do serviço Legal Intercept.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsIM** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Test-CsIM** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsGroupIM](test-csgroupim.md)

