---
title: Test-CsP2PAV
TOCTitle: Test-CsP2PAV
ms:assetid: acb01fb7-4685-4f38-a724-8c2ae8e0219a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412821(v=OCS.15)
ms:contentKeyID: 49307772
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsP2PAV

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade de um par de usuários de conduzir uma chamada ponto a ponto de áudio/vídeo. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsP2PAV -ReceiverCredential <PSCredential> -ReceiverSipAddress <String> -SenderCredential <PSCredential> -SenderSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsP2PAV -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-ReceiverSipAddress <String>] [-RegistrarPort <Int32>] [-SenderSipAddress <String>] <COMMON PARAMETERS>

    Test-CsP2PAV [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um par de usuários de teste pré-configurados pode fazer logon no pool atl-cs-001.litwareinc.com e conduzir uma chamada ponto a ponto de áudio/vídeo. Esse comando funcionará apenas se usuários de teste tiverem sido definidos para o pool atl-cs-001.litwareinc.com. Se tiverem sido definidos, o comando determinará se os dois usuários poderão fazer logon no sistema e, em caso afirmativo, poderão conversar usando uma chamada de áudio/vídeo.

Se os usuários de teste não tiverem sido definidos, o comando falhará, porque não saberá quais usuários empregar ao fazer o teste. Se os usuários de teste de um pool não tiverem sido definidos, será necessário incluir os parâmetros SenderSipAddress e ReceiverSipAddress, bem como as credenciais correspondentes aos usuários envolvidos na troca de mensagens instantâneas. O cmdlet **Test-CsP2PAV** conduzirá então suas verificações, usando os dois usuários especificados.

    Test-CsP2PAV -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

Os comandos exibidos no Exemplo 2 testam a capacidade de um par de usuários (litwareinc\\pilar e litwareinc\\kenmyer) de fazer logon no Lync Server e, em seguida, conduzir uma chamada ponto a ponto de áudio/vídeo. Para isso, o primeiro comando no exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman (como o nome de logon litwareinc\\pilar foi incluído como um parâmetro, a caixa de diálogo resultante – Solicitação de credenciais – do Windows PowerShell solicitará apenas que o administrador insira a senha da conta de Pilar Ackerman). O objeto de credencial resultante será então armazenado em uma variável denominada $cred1. O segundo comando fará o mesmo, retornando, desta vez, um objeto de credencial para a conta de Ken Myer.

De posse dos dois objetos de credencial, o terceiro comando no exemplo determinará se os dois usuários podem ou não fazer logon no Lync Server e, em seguida, conduzir uma chamada ponto a ponto de áudio/vídeo. Para realizar essa tarefa, o cmdlet **Test-CsP2PAV** é chamado com os parâmetros a seguir: TargetFqdn (o FQDN do pool de registradores), SenderSipAddress (o endereço SIP do primeiro usuário de teste), SenderCredential (o objeto do Windows PowerShell que contém as credenciais deste usuário), ReceiverSipAddress (o endereço SIP do outro usuário de teste) e ReceiverCredential (o objeto do Windows PowerShell que contém as credenciais do outro usuário).

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsP2PAV -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $cred1 -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -ReceiverCredential $cred2

## Descrição detalhada

O cmdlet **Test-CsP2PAV** é um exemplo de uma "transação sintética" do Lync Server. As transações sintéticas são usadas no Lync Server para se certificar de que os usuários sejam capazes de concluir tarefas comuns com sucesso, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Normalmente, as transações sintéticas são conduzidas de duas maneiras diferentes. Muitos administradores usarão os cmdlets **CsHealthMonitoringConfiguration** para definir os usuários de teste de cada um de seus pools de registradores. Esses usuários de teste são um par de usuários que foram configurados previamente para uso com transações sintéticas (normalmente, essas são contas de teste e não contas que pertencem a usuários reais). Com usuários de teste configurados para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool, sem a necessidade de especificar as identidades (nem fornecer credenciais) das contas dos usuários envolvidos no teste.

Como alternativa, os administradores podem executar uma transação sintética usando contas de usuários reais. Por exemplo, se dois usuários não puderem trocar mensagens instantâneas, um administrador pode executar uma transação sintética usando as duas contas dos usuários em questão (em vez de um par de contas de teste) e tentar diagnosticar e resolver o problema. Se decidir conduzir uma transação sintética usando contas de usuários reais, será necessário fornecer o nome e a senha de logon de cada usuário.

O cmdlet **Test-CsP2PAV** é usado para determinar se dois usuários de teste podem participar de uma conversação ponto a ponto de áudio/vídeo. Para testar esta situação, o cmdlet inicialmente faz o logon dos dois usuários no Lync Server. Presumindo que os dois logons sejam bem-sucedidos, o primeiro usuário convidará o segundo para participar da chamada de áudio/vídeo. O segundo usuário aceitará a chamada, a conexão entre os dois usuários será testada e, em seguida, a chamada será encerrada e os usuários de teste farão o logoff do sistema.

O cmdlet **Test-CsP2PAV** não realiza propriamente uma chamada de áudio/vídeo. Os usuários não trocam informações multimídia entre si. Em vez disso, o cmdlet simplesmente verifica se as conexões apropriadas podem ser feitas e se os dois usuários podem realizar essa chamada.

Quem pode executar esse cmdlet: Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsP2PAV"}

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
<td><p>Objeto de credencial de usuário da primeira das duas contas de usuário a serem testadas. O valor passado para ReceiverCredential deve ser uma referência de objeto obtida utilizando o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credenciais do usuário litwareinc\pilar e armazena esse objeto em uma variável denominada $y:</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>É necessário fornecer ao usuário uma senha ao executar esse comando.</p>
<p>A credencial do destinatário não será necessária, caso o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="even">
<td><p><em>SenderCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário da segunda das duas contas de usuário a serem testadas. O valor passado para SenderCredential deve ser uma referência de objeto obtida utilizando o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credenciais para o usuário litwareinc\kenmyer e armazena esse objeto em uma variável denominada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É necessário fornecer ao usuário uma senha ao executar esse comando.</p>
<p>A credencial do remetente não será necessária, caso se o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
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
<td><p>Endereço SIP para a segunda das duas contas de usuário a serem testadas. Por exemplo: -SenderSipAddres &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro SenderSipAddress deve fazer referência à mesma conta de usuário que SenderCredential.</p>
<p>O endereço SIP não será necessário, caso esteja o teste esteja sendo executado com as definições de configuração de monitoramento de integridade do pool.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsP2PAV** não aceita a entrada direcionada.

## Tipos de retorno

O cmdlet **Test-CsP2PAV** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsAVConference](test-csavconference.md)

