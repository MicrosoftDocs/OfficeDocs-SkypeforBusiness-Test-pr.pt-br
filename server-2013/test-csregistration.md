---
title: Test-CsRegistration
TOCTitle: Test-CsRegistration
ms:assetid: 9e38cb36-c97a-43f2-97fe-64759f663be2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412737(v=OCS.15)
ms:contentKeyID: 49307625
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsRegistration

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade de um usuário de fazer logon no Lync Server. O cmdlet **Test-CsRegistration** é uma "transação sintética": uma simulação de atividades comuns do Lync Server para monitoramento de integridade e desempenho. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsRegistration -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsRegistration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsRegistration [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 testa o serviço Registrador para o pool atl-cs-001.litwareinc.com. Esse comando só funcionará se usuários de teste tiverem sido definidos no pool atl-cs-001.litwareinc.com. Se eles tiverem sido definidos, o comando determinará se o primeiro usuário de teste é capaz de fazer logon no Lync Server.

Se usuários de testes não tiverem sido definidos, o comando falhará porque não saberá qual usuário empregar para fazer logon. Se nenhum usuário de teste tiver sido definido para um pool, será preciso incluir o parâmetro UserSipAddress e as credenciais do usuário que o comando deve usar ao tentar fazer logon.

    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

Os comandos mostrados no Exemplo 2 testam a capacidade de um usuário específico (litwareinc\\pilar) de fazer logon no Lync Server. Para fazer isso, o primeiro comando do exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman (como o nome de logon litwareinc\\pilar foi incluído como parâmetro, a caixa de diálogo Solicitação de Credenciais do Windows PowerShell só exigirá que o administrador digite a senha da conta de Pilar Ackerman). O objeto de credencial resultante é então armazenado em uma variável chamada $cred1.

Em seguida, o segundo comando verifica se esse usuário pode fazer logon no pool atl-cs-001.litwareinc.com. Para realizar essa tarefa, o cmdlet **Test-CsRegistration** é chamado, com três parâmetros: TargetFqdn (o FQDN do pool do Registrador); UserCredential (o objeto do Windows PowerShell que contém as credenciais da usuária Pilar Ackerman); e UserSipAddress (o endereço SIP correspondente às credenciais de usuário fornecidas).

    $cred1 = Get-Credential "litwareinc\pilar"
    
    Test-CsRegistration -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:pilar@litwareinc.com"

## Descrição detalhada

O cmdlet **Test-CsRegistration** é um exemplo de uma "transação sintética" do Lync Server. Transações sintéticas são usadas no Lync Server para verificar se os usuários podem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador, ou ser executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Transações sintéticas costumam ser conduzidas de duas maneiras diferentes. Muitos administradores utilizarão os cmdlets CsHealthMonitoringConfiguration para configurar usuários de teste para cada um de seus pools de Registrador. Esses usuários de teste são um par de usuários pré-configurados para uso com transações sintéticas (geralmente, são contas de testes, e não contas que pertençam a usuários reais). Com contas de usuário de testes configuradas para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool sem a necessidade de especificar as identidades (e fornecer as credenciais) das contas de usuário envolvidas no teste.

Outra opção para os administradores é a de executar uma transação sintética com contas de usuário reais. Por exemplo, se dois usuários não conseguirem trocar mensagens instantâneas, um administrador poderia executar uma transação sintética usando as duas contas de usuário em questão (em vez de um par de contas de testes) para tentar diagnosticar e resolver o problema. Se optar por conduzir uma transação sintética usando contas de usuário reais, será necessário fornecer os nomes de logon e as senhas de cada usuário.

O cmdlet **Test-CsRegistration** permite verificar se os usuários da sua organização podem fazer logon no Lync Server. Para realizar essa verificação, o cmdlet **Test-CsRegistration** exige uma única conta de teste. Se usuários de teste foram configurados para o pool no qual o teste será conduzido, não será necessário especificar uma conta; em vez disso, o cmdlet **Test-CsRegistration** usará automaticamente a primeira conta de teste atribuída ao pool (para detalhes, consulte o tópico de Ajuda do cmdlet [New-CsHealthMonitoringConfiguration](new-cshealthmonitoringconfiguration.md)). Uma alternativa é conduzir o teste usando uma conta que não tenha sido atribuída ao pool. Isso permitirá executar testes, mesmo se você não tiver configurado usuários de teste. Também permite testar a capacidade de um usuário específico de fazer logon no Lync Server (se optar por esta abordagem, será preciso fornecer o nome de usuário e a senha da conta que está sendo testada).

Ao executar o cmdlet **Test-CsRegistration**, ele tenta fazer logon do usuário de teste no Lync Server e, se tiver êxito, desconecta esse usuário de teste do sistema. Tudo isso acontece sem a interação do usuário, e sem afetar os usuários reais. Por exemplo, suponha que a conta de teste sip:kenmyer@litwareinc.com corresponda a um usuário real com uma conta real do Lync Server. Nesse caso, o teste será conduzido sem prejuízo algum ao verdadeiro Ken Myer. Quando a conta de teste de Ken Myer fizer logoff do sistema, a pessoa Ken Myer continuará conectada.

Com o parâmetro Verbose é possível obter um relato detalhado de todas as ações realizadas pelo cmdlet **Test-CsRegistration** para a conclusão do seu teste.

Quem pode executar este cmdlet: Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsRegistration"}

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
<td><p><em>TargetFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>String</p></td>
<td><p>O FQDN (nome de domínio totalmente qualificado) do pool a ser testado.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credenciais de usuário para a conta a ser testada. O valor passado para UserCredential deve ser uma referência de objeto obtida com o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credencial para o usuário litwareinc\kenmyer e armazena esse objeto em uma variável chamada</p>
<p>$x: $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É preciso fornecer a senha de usuário ao executar este comando. Esse parâmetro não será necessário se você estiver conduzindo o teste sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>Opcional</p></td>
<td><p>SipSyntheticTransaction AuthenticationMechanism</p></td>
<td><p>Tipo de autenticação usada no teste. Os valores permitidos são:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Essa variável inclui um dois métodos – ToHTML e ToXML – que podem ser usados para salvar a saída em um arquivo HTML ou XML.</p>
<p>Para armazenar a saída em uma variável de agente denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: não use um caractere $ ao especificar o nome da variável. Para salvar as informações armazenadas na variável do agente de log em um arquivo HTML, use um comando parecido com o seguinte:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar as informações armazenadas na variável de agente em um arquivo XML, use um comando semelhante a este:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não use um caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não será necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>O endereço SIP da conta de usuário a ser testada; por exemplo: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro UserSipAddress precisa fazer referência à mesma conta de usuário que UserCredential. Esse parâmetro não será necessário se o teste estiver sendo conduzido sob a configuração de monitoramento de integridade do pool.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Test-CsRegistration** não aceita entrada por pipeline.

## Tipos de retorno

O cmdlet **Test-CsRegistration** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

