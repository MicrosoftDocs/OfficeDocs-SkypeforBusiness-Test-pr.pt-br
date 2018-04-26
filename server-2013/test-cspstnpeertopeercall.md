---
title: Test-CsPstnPeerToPeerCall
TOCTitle: Test-CsPstnPeerToPeerCall
ms:assetid: 839cf83f-b667-4cbe-b1ab-28f54a8a9d0b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398662(v=OCS.15)
ms:contentKeyID: 49307320
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPstnPeerToPeerCall

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade de um par de usuários realizar uma chamada ponto a ponto através do gateway da rede telefônica pública comutada (PSTN). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsPstnPeerToPeerCall -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsPstnPeerToPeerCall -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsPstnPeerToPeerCall [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um par de usuários de teste pré-configurados consegue efetuar o logon no pool atl-cs-001.litwareinc.com. Após o logon, o cmdlet **Test-CsPstnPeerToPeerCall** verificará se os dois usuários conseguem efetuar uma chamada ponto a ponto utilizando o gateway PSTN. Esse comando funcionará apenas se usuários de teste tiverem sido definidos para o pool atl-cs-001.litwareinc.com. Em caso positivo, o comando determinará se o primeiro usuário de teste pode efetuar o logon no sistema e verificará se este usuário pode chamar o segundo usuário definido para o pool.

Se um dos usuários de teste não tiver sido definido, o comando falhará, porque não saberá quais usuários empregar ao fazer o teste. Se não houver usuários de teste definidos no pool e o modo plataforma de servidor não estiver sendo executado, deverão se incluir os parâmetros SenderSipAddress e ReceiverSipAddress, além das credenciais correspondentes aos usuários servindo como contas de teste. O cmdlet **Test-CsPstnPeerToPeerCall** realizará as verificações utilizando os dois usuários especificados.

    Test-CsPstnPeerToPeerCall -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

Os comandos mostrados no Exemplo 2 testam a capacidade de um par de usuários (litwareinc\\pilar e litwareinc\\kenmyer) efetuar o logon no Lync Server e realizar uma chamada ponto a ponto utilizando o gateway PSTN. Para isso, o primeiro comando no exemplo usa o cmdlet **Get-Credential**, para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman. (como o nome de logon litwareinc\\pilar foi incluído como um parâmetro, a caixa de diálogo resultante – Solicitação de credenciais – do Windows PowerShell solicitará apenas que o administrador insira a senha da conta de Pilar Ackerman). O objeto de credencial resultante será então armazenado em uma variável denominada $cred1. O segundo comando fará o mesmo, retornando, desta vez, um objeto de credencial para a conta de Ken Myer.

Obtidos os dois objetos de credencial, o terceiro comando no exemplo determinará se os dois usuários podem efetuar o logon no Lync Server e realizar uma chamada ponto a ponto utilizando o gateway PSTN. Para realizar esta tarefa, chama-se o cmdlet **Test-CsPstnPeerToPeerCall**, juntamente com os seguintes parâmetros: TargetFqdn (o FQDN do pool de registradores), SenderSipAddress (o endereço SIP do primeiro usuário de teste), SenderCredential (o objeto do Windows PowerShell que contém as credenciais deste usuário), ReceiverSipAddress (o endereço SIP do outro usuário de teste) e ReceiverCredential (o objeto do Windows PowerShell que contém as credenciais do outro usuário).

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsPstnPeerToPeerCall -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:jhaas@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## EXEMPLO 3

O Exemplo 3 mostra como o cmdlet Test-CsPstnPeerToPeerCall pode ser usado no modo plataforma do servidor. Neste modo, especificam-se os endereços SIP dos usuários de teste, mas não se incluem as credenciais dos usuários. Quando executado desta forma, o Lync Server usa certificados para autenticar os dois usuários de teste.

    Test-CsPstnPeerToPeerCall -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:jhaas@litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" 

## Descrição detalhada

O cmdlet**Test-CsPstnPeerToPeerCall** é um exemplo de uma "transação sintética" do Lync Server. As transações sintéticas são usadas no Lync Server para se certificar de que os usuários sejam capazes de concluir tarefas comuns com sucesso, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na rede telefônica pública comutada (PSTN). Esses testes podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Normalmente, as transações sintéticas são conduzidas de duas maneiras diferentes. Muitos administradores usarão os cmdlets **CsHealthMonitoringConfiguration**, para definir os usuários de teste de cada um de seus pools de registradores. Estes usuários de teste são um par de usuários que foram pré-configurados para uso com transações sintéticas. (normalmente, essas são contas de teste e não pertencem a usuários reais). Com usuários de teste configurados para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool, sem ter de especificar as identidades (nem fornecer credenciais) das contas dos usuários envolvidos no teste.

Como alternativa, os administradores podem executar uma transação sintética utilizando contas de usuários reais. Por exemplo, se dois usuários não puderem trocar mensagens instantâneas, um administrador pode executar uma transação sintética usando as duas contas dos usuários em questão (em vez de um par de contas de teste) e tentar diagnosticar e resolver o problema. Se decidir conduzir uma transação sintética usando contas de usuários reais, você terá de fornecer o nome e a senha de logon de cada usuário.

O cmdlet **Test-CsPstnPeerToPeerCall** também pode ser usado no modo plataforma de servidor. Neste caso, será necessário apenas especificar o endereço SIP dos usuários, e o Lync Server utilizará certificados para autenticá-los.

Quando se chama **Test-CsPstnPeerToPeerCall**, o cmdlet primeiramente tentará efetuar o logon dos dois usuários de teste no Lync Server. Assumindo-se que os logons tenham tido sucesso, o cmdlet fará então o usuário 1 tentar chamar o usuário 2 utilizando o gateway PSTN. O cmdlet **Test-CsPstnPeerToPeerCall** fará esta chamada utilizando o plano de discagem, a política de voz e outras políticas e configurações atribuídas ao usuário de teste. Se o teste ocorrer como o planejado, o cmdlet verificará se o usuário 2 conseguiu atender à chamada e efetuará o logoff das duas contas.

O cmdlet **Test-CsPstnPeerToPeerCall** faz uma chamada telefônica real, que verifica se uma conexão pode ser estabelecida e transmite códigos de multifrequência de tom dual (DTMF) ao longo da rede, para determinar se é possível enviar mídia pela conexão. No entanto, a chamada será atendida pelo próprio cmdlet, e nenhum encerramento manual da chamada será necessário. (ou seja, ninguém precisará atender e desligar o telefone para o qual tiver sido feita ligação).

Quem pode executar esse cmdlet: Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPstnPeerToPeerCall"}

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
<td><p>Objeto de credencial de usuário da primeira das duas contas de usuário a serem testadas. O valor passado para ReceiverCredential deve ser uma referência de objeto obtida ao se utilizar o cmdlet <strong>Get-Credential</strong>. Por exemplo: esse código retorna um objeto de credenciais correspondente ao usuário litwareinc\pilar e armazena esse objeto em uma variável denominada $y:</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>É necessário fornecer a senha do usuário para executar este comando.</p>
<p>A credencial do destinatário não é necessária, caso se esteja executando o teste com a configuração de monitoramento de integridade do pool ou no modo plataforma do servidor.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário da segunda das duas contas de usuário a serem testadas. O valor passado para SenderCredential deve ser uma referência de objeto obtida ao se utilizar o cmdlet <strong>Get-Credential</strong>. Por exemplo: este código retorna um objeto de credenciais do usuário litwareinc\kenmyer e o armazena em uma variável denominada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É necessário fornecer a senha do usuário para executar este comando.</p>
<p>A credencial do remetente não é necessária, caso esteja se executando o teste com a configuração de monitoramento de integridade do pool ou no modo plataforma do servidor.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Nome do domínio totalmente qualificado (FQDN) do pool a ser testado.</p></td>
</tr>
<tr class="even">
<td><p><em>Authentication</em></p></td>
<td><p>Opcional</p></td>
<td><p>SipSyntheticTransaction AuthenticationMechanism</p></td>
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
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Essa variável inclui um dois métodos – ToHTML e ToXML – que podem ser usados para salvar a saída em um arquivo HTML ou XML.</p>
<p>Para armazenar a saída em uma variável de agente denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: não use um caractere $ ao especificar o nome da variável. Para salvar as informações armazenadas na variável do agente de log em um arquivo HTML, use um comando parecido com o seguinte:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar as informações armazenadas na variável de agente em um arquivo XML, use um comando semelhante a este:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque um caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Endereço SIP da primeira das duas contas de usuário a serem testadas. Por exemplo: -ReceiverSipAddress &quot;sip:pilar@litwareinc.com&quot;. O parâmetro ReceiverSIPAddress deve fazer referência à mesma conta de usuário que ReceiverCredential.</p>
<p>O endereço SIP não será necessário, caso se esteja executando o teste com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP utilizada pelo serviço Registrador. Este parâmetro não será obrigatório se o Registrador utilizar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Endereço SIP para a segunda das duas contas de usuário a serem testadas. Por exemplo: -SenderSipAddress &quot;sip:kenmyer@litwareinc.com.&quot; O parâmetro SenderSIPAddress deve fazer referência à mesma conta de usuário que SenderCredential.</p>
<p>O endereço SIP não será necessário, caso esteja se executando o teste com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet**Test-CsPstnPeerToPeerCall** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Test-CsPstnPeerToPeerCall** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsPstnOutboundCall](test-cspstnoutboundcall.md)

