---
title: Test-CsAVConference
TOCTitle: Test-CsAVConference
ms:assetid: a1492563-9a97-44ac-b19a-8d5972cdd062
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412749(v=OCS.15)
ms:contentKeyID: 49307651
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAVConference

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade de um par de usuários de participar de uma conferência de áudio/vídeo (A/V). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsAVConference -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAVConference -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsAVConference [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-TestJoinLauncher <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um par de usuários de teste preconfigurados pode fazer logon no pool atl-cs-001.litwareinc.com e depois participar de uma conferência de áudio/vídeo. Esse comando funcionará apenas se os usuários de teste tiverem sido definidos para o pool atl-cs-001.litwareinc.com. Se eles tiverem sido definidos, o comando determinará se os dois usuários podem fazer logon no sistema. Se puderem, o primeiro usuário de teste criará uma conferência de áudio/vídeo e convidará o segundo usuário a participar da conferência. O cmdlet então verificará se os dois usuários de teste puderam ou não estabelecer uma conexão bem-sucedida.

Se os usuários de teste não tiverem sido definidos, o comando falhará porque não saberá quais usuários empregar ao fazer o teste. Se os usuários de teste de um pool não tiverem sido definidos, será necessário incluir os parâmetros SenderSipAddress e ReceiverSipAddress, bem como as credenciais correspondentes aos usuários envolvidos na troca de mensagens instantâneas. O cmdlet **Test-CsAVConference** conduzirá então suas verificações, usando os dois usuários especificados.

    Test-CsAVConference -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

Os comandos exibidos no Exemplo 2 testam a possibilidade de um par de usuários (litwareinc\\pilar e litwareinc\\kenmyer) de fazer logon no Lync Server e, em seguida, participar de uma conferência de A/V. Para isso, o primeiro comando no exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman (como o nome de logon litwareinc\\pilar foi incluído como um parâmetro, a caixa de diálogo resultante – Solicitação de credenciais – do Windows PowerShell solicitará apenas que o administrador insira a senha da conta de Pilar Ackerman). O objeto de credencial resultante será então armazenado em uma variável denominada $cred1. O segundo comando fará o mesmo, retornando, desta vez, um objeto de credencial para a conta de Ken Myer.

De posse dos dois objetos de credencial, o terceiro comando no exemplo determina se os dois usuários podem ou não fazer logon no Lync Server e, em seguida, participar de uma conferência de A/V. Para realizar essa tarefa, o cmdlet **Test-CsAVConference** é chamado com os seguintes parâmetros: TargetFqdn (o FQDN do pool de Registradores), SenderSipAddress (o endereço SIP do primeiro usuário de teste), SenderCredential (o objeto do Windows PowerShell que contém as credenciais deste usuário), ReceiverSipAddress (o endereço SIP do outro usuário de teste) e ReceiverCredential (o objeto do Windows PowerShell que contém as credenciais do outro usuário).

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAVConference -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## Descrição detalhada

O cmdlet **Test-CsAVConference** é um exemplo de uma "transação sintética". As transações sintéticas são usadas no Lync Server para verificar se os usuários são capazes de concluir tarefas comuns com sucesso, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Normalmente, as transações sintéticas são conduzidas de duas maneiras diferentes. Muitos administradores usarão os cmdlets **CsHealthMonitoringConfiguration** para definir os usuários de teste de cada um de seus pools de registradores. Esses usuários de teste são um par de usuários que foram configurados previamente para uso com transações sintéticas (normalmente, essas são contas de teste e não contas que pertencem a usuários reais). Com usuários de teste configurados para um pool, os administradores podem executar uma transação sintética nesse pool, sem a necessidade de especificar as identidades (nem fornecer credenciais) das contas dos usuários envolvidos no teste.

Como alternativa, os administradores podem executar uma transação sintética utilizando contas de usuários reais. Por exemplo, se dois usuários não puderem trocar mensagens instantâneas, um administrador pode executar uma transação sintética usando as duas contas dos usuários em questão (em vez de um par de contas de teste) e tentar diagnosticar e solucionar o problema. Se decidir conduzir uma transação sintética usando contas de usuários reais, será necessário fornecer o nome e a senha de logon de cada usuário.

O cmdlet **Test-CsAVConference** verifica se dois usuários de teste podem conduzir uma conferência de áudio/vídeo. Quando o cmdlet for executado, os dois usuários serão registrados no sistema. Depois que eles se conectarem com êxito, o primeiro usuário criará uma conferência de A/V e aguardará até que o segundo usuário participe da conferência. Depois de uma breve troca de dados, a conferência é excluída e os dois usuários de teste fazem logoff.

Na verdade, o cmdlet **Test-CsAVConference** não conduz uma conferência de áudio/vídeo entre os dois usuários de teste. Em vez disso, o cmdlet verifica se os dois usuários podem estabelecer as conexões necessárias para realizar essa conferência.

Quem pode executar esse cmdlet: Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAVConference"}

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
<td><p>Objeto de credencial de usuário da primeira das duas contas de usuário a serem testadas. O valor passado para ReceiverCredential deve ser uma referência de objeto obtida utilizando o cmdlet <strong>Get-Credential</strong>. Por exemplo: esse código retorna um objeto de credenciais correspondente ao usuário litwareinc\pilar e o armazena em uma variável denominada $y:</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>É necessário fornecer uma senha de usuário ao executar esse comando.</p>
<p>A credencial do destinatário não será necessária, caso o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário da segunda das duas contas de usuário a serem testadas. O valor passado para SenderCredential deve ser uma referência de objeto obtida utilizando o cmdlet <strong>Get-Credential</strong>. Por exemplo, esse código retorna um objeto de credenciais para o usuário litwareinc\kenmyer e o armazena em uma variável denominada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É necessário fornecer uma senha de usuário ao executar esse comando.</p>
<p>A credencial do remetente não será necessária, caso o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>String</p></td>
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
<td><p>String</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Essa variável inclui um dois métodos – ToHTML e ToXML – que podem ser usados para salvar a saída em um arquivo HTML ou XML.</p>
<p>Para armazenar a saída em uma variável de agente denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: não use o caractere $ ao especificar o nome da variável. Para salvar as informações armazenadas na variável do agente de log em um arquivo HTML, use um comando parecido com o seguinte:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar as informações armazenadas na variável de agente em um arquivo XML, use um comando semelhante a este:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque o caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="even">
<td><p><em>ReceiverSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Endereço SIP da primeira das duas contas de usuário a serem testadas. Por exemplo: -ReceiverSipAddress &quot;sip:pilar@litwareinc.com&quot;. O parâmetro ReceiverSipAddress deve fazer referência à mesma conta de usuário que ReceiverCredential.</p>
<p>O endereço SIP não será necessário, caso o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não é necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Endereço SIP para a segunda das duas contas de usuário a serem testadas. Por exemplo: -SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro SenderSipAddress deve referenciar a mesma conta de usuário de SenderCredential.</p>
<p>O endereço SIP não será necessário, caso o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>TestJoinLauncher</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Quando presente, testa a capacidade do Iniciador de Ingresso de participar de uma conferência de AV. O Iniciador de Ingresso é usado para ajudar os usuários de dispositivos móveis (e, como resultado, usuários do Serviço de Mobilidade) a fazer parte das conferências.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Test-CsAVConference** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Get-CsAVEdgeConfiguration](get-csavedgeconfiguration.md)  
[Test-CsDialInConferencing](test-csdialinconferencing.md)

