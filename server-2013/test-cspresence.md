---
title: Test-CsPresence
TOCTitle: Test-CsPresence
ms:assetid: 09a5faf6-4e80-4a3b-ac84-aec9778ee9b5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398148(v=OCS.15)
ms:contentKeyID: 49305822
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPresence

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade de um usuário fazer logon no Lync Server, publicar suas informações de presença, e depois inscrever-se nas informações de presença publicadas por um segundo usuário. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsPresence -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-PublisherSipAddress <String>] [-RegistrarPort <Int32>] [-SubscriberSipAddress <String>] <COMMON PARAMETERS>

    Test-CsPresence -PublisherCredential <PSCredential> -PublisherSipAddress <String> -SubscriberCredential <PSCredential> -SubscriberSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsPresence [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-SubscriberSipAddress <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um par de usuários de testes pré-configurado pode fazer logon no pool atl-cs-001.litwareinc.com; depois que os usuários de teste fazem logon, o cmdlet **Test-CsPresence** verifica se os dois usuários conseguem trocar informações de presença. Esse comando só funcionará se usuários de teste tiverem sido definidos no pool atl-cs-001.litwareinc.com. Se eles tiverem sido definidos, o comando determinará se o primeiro usuário de testes pode fazer logon no sistema, e depois verifica se esse usuário pode trocar informações de presença com o segundo usuário de testes definido para o pool.

Se um Registrador não tiver sido definido, o comando falhará porque não saberá quais usuários empregar ao fazer o teste. Se usuários de testes não tiverem sido definidos para um pool, será preciso incluir os parâmetros SubscriberSipAddress e PublisherSipAddress, além das credenciais correspondentes para os usuários agindo como o assinante de presença e o editor de presença. O cmdlet **Test-CsPresence** conduzirá suas verificações usando os dois usuários especificados.

    Test-CsPresence -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

Os comandos mostrados no Exemplo 2 testam a capacidade de um par de usuários (litwareinc\\pilar e litwareinc\\kenmyer) de fazerem logon no Lync Server e trocarem informações de presença. Para fazer isso, o primeiro comando do exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman (como o nome de logon litwareinc\\pilar foi incluído como parâmetro, a caixa de diálogo Solicitação de Credenciais do Windows PowerShell só exigirá que o administrador digite a senha da conta de Pilar Ackerman). O objeto de credencial resultante é armazenado em uma variável chamada $cred1. O segundo comando faz a mesma coisa, mas retorna um objeto de credencial para a conta de Ken Myer.

Com dois objetos de credencial nas mãos, o terceiro comando do exemplo determina se os dois usuários podem ou não fazer logon no Lync Server e trocar informações de presença. Para realizar essa tarefa, o cmdlet **Test-CsPresence** é chamado, junto com os seguintes parâmetros: TargetFqdn (o FQDN do pool do Registrador); SubscriberSipAddress (o endereço SIP de um usuário de teste); SubscriberCredential (o objeto do Windows PowerShell que contém as credenciais desse usuário); PublisherSipAddress (o endereço SIP do outro usuário de teste); e PublisherCredential (o objeto do Windows PowerShell que contém as credenciais do outro usuário).

    $cred1 = Get-Credential "litwareinc\pilar"
    $cred2 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsPresence -TargetFqdn atl-cs-001.litwareinc.com -SubscriberSipAddress "sip:pilar@litwareinc.com" -SubscriberCredential $cred1 -PublisherSipAddress "sip:kenmyer@litwareinc.com" -PublisherCredential $cred2

## Descrição detalhada

O cmdlet **Test-CsPresence** é um exemplo de uma transação sintética do Lync Server. As transações sintéticas são usadas no Lync Server para verificar se os usuários podem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador, ou ser executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Transações sintéticas costumam ser conduzidas de duas maneiras diferentes. Muitos administradores vão usar os cmdlets **CsHealthMonitoringConfiguration** para configurar usuários de teste para cada um de seus pools de Registrador. Geralmente, são contas de testes, e não contas que pertençam a usuários reais. Com essas contas de usuário configuradas para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool sem ter que especificar as identidades (e fornecer as credenciais) das contas de usuário envolvidas no teste.

Outra opção para os administradores é a de executar uma transação sintética com contas de usuário reais. Por exemplo, se dois usuários não conseguirem trocar mensagens instantâneas, um administrador pode executar uma transação sintética usando as duas contas de usuário em questão (em vez de um par de contas de testes) para tentar diagnosticar e resolver o problema. Se optar por conduzir uma transação sintética usando contas de usuário reais, será necessário fornecer os nomes de logon e as senhas de cada usuário.

O cmdlet **Test-CsPresence** é usado para determinar se um par de usuários de testes pode fazer logon no Lync Server e trocar informações de presença. Para fazer isso, o cmdlet primeiro faz logon dos dois usuários no sistema. Se o logon de ambos tiver êxito, o primeiro usuário de testes solicita o recebimento de informações de presença do segundo usuário. O segundo usuário publica essas informações, e o cmdlet **Test-CsPresence** verifica se as informações foram transmitidas com êxito para o primeiro usuário. Após a troca de informações de presença, os dois usuários de testes são desconectados do Lync Server.

Quem pode executar este cmdlet: Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPresence"}

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
<td><p><em>PublisherCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário para a primeira das duas contas de usuário a serem testadas. O valor passado para PublisherCredential deve ser uma referência de objeto obtida com o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credencial para o usuário litwareinc\kenmyer e armazena esse objeto em uma variável chamada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É preciso fornecer a senha de usuário ao executar este comando.</p>
<p>A credencial de editor não será necessária se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="even">
<td><p><em>SubscriberCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário para a segunda das duas contas de usuário a serem testadas. O valor passado para SubscriberCredential deve ser uma referência de objeto obtida com o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credencial para a usuária litwareinc\pilar e armazena esse objeto em uma variável chamada $y:</p>
<p>$y = Get-Credential &quot;litwareinc\pilar&quot;</p>
<p>É preciso fornecer a senha de usuário ao executar este comando.</p>
<p>A credencial de assinante não será necessária se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>TargetFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
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
<td><p>Cadeia de caracteres</p></td>
<td><p>Quando presente, o resultado detalhado da execução do cmdlet será armazenado na variável especificada. Essa variável inclui um par de métodos – ToHTML e ToXML – que podem ser usados para salvar o resultado em um arquivo HTML ou XML.</p>
<p>Par armazenar o resultado em uma variável de registro em log chamado $TestOutput, use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: Não insira um caractere $ ao especificar o nome da variável. Para salvar a informação armarzenada na variável do registro em log para um arquivo HTML, use um comando semelhante a esse:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar a informação armazenada na variável do registro em log para um arquivo XML, use um comando semelhante a esse:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável chamada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque o caractere $ como um prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="even">
<td><p><em>PublisherSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço SIP da primeira das duas contas de usuário a serem testadas. Por exemplo: -PublisherSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro PublisherSipAddress precisa fazer referência à mesma conta de usuário que PublisherCredential.</p>
<p>O endereço SIP não será necessário se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não será necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>SubscriberSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço SIP da segunda das duas contas de usuário a serem testadas. Por exemplo: -SubscriberSipAddress &quot;sip:pilar@litwareinc.com&quot;. O parâmetro SubscriberSipAddress precisa fazer referência à mesma conta de usuário que SubscriberCredential.</p>
<p>O endereço SIP não será necessário se você estiver realizando o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsPresence** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Test-CsPresence** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsRegistration](test-csregistration.md)

