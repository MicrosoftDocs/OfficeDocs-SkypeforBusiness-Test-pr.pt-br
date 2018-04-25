---
title: Test-CsDialInConferencing
TOCTitle: Test-CsDialInConferencing
ms:assetid: e4aedf4f-77ac-4c8b-9613-07f8ea12c041
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399013(v=OCS.15)
ms:contentKeyID: 49308412
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsDialInConferencing

 

_**Tópico modificado em:** 2015-03-09_

O cmdlet **Test-CsDialInConferencing** verifica se um usuário pode participar de uma sessão de conferência discada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsDialInConferencing -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetPstnPhoneNumber <String>] [-UserSipAddress <String>] [-VerifyConferenceJoin <$true | $false>] <COMMON PARAMETERS>

    Test-CsDialInConferencing -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] [-TargetPstnPhoneNumber <String>] [-VerifyConferenceJoin <$true | $false>] <COMMON PARAMETERS>

    Test-CsDialInConferencing [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se o usuário de teste pré-configurado pode participar de uma conferência discada no pool atl-cs-001.litwareinc.com. Esse comando funcionará apenas se tiverem sido definidos usuários de teste para o pool atl-cs-001.litwareinc.com. Se eles tiverem sido definidos, o comando determinará se o primeiro usuário pode fazer logon no Lync Server.

Se os usuários de teste não tiverem sido definidos, o comando falhará porque não vai saber qual usuário empregar ao fazer o logon. Se não tiverem sido definidos os usuários de teste do pool, deve-se incluir o parâmetro UserCredential e as credenciais do usuário que o comando deve empregar ao tentar fazer o logon.

    Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

Os comandos exibidos no Exemplo 2 testam a capacidade de um usuário específico (litwareinc\\pilar) de participar de conferências discadas no pool atl-cs-001.litwareinc.com. Para realizar isso, o primeiro comando no exemplo usa o cmdlet **Get-Credential**, para criar um objeto de credencial Windows PowerShell contendo o nome e a senha da usuária Pilar Ackerman. (como o nome de logon litwareinc\\pilar foi incluído como um parâmetro, o administrador apenas precisa inserir a senha da conta de Pilar Ackerman na caixa de diálogo Solicitação de credenciais do Windows PowerShell). O objeto de credencial resultante será então armazenado em uma variável denominada $cred1.

O segundo comando verifica se a usuária Pilar Ackerman pode fazer logon no pool atl-cs-001.litwareinc.com e participar de uma conferência discada. Para realizar esta tarefa, o cmdlet **Test-CsDialInConferencing** é chamado em conjunto com três parâmetros: TargetFqdn \[o FQDN (nome de domínio totalmente qualificado) do pool de registradores\], UserCredential (o objeto do Windows PowerShell que contém as credenciais da usuária Pilar Ackerman) e UserSipAddress (o endereço SIP correspondente às credenciais de usuário fornecidas).

    $cred1 = Get-Credential "litwareinc\pilar"
    
    Test-CsDialInConferencing -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:pilar@litwareinc.com" -UserCredential $cred1

## Descrição detalhada

O cmdlet **Test-CsDialInConferencing** é um exemplo de uma "transação sintética" do Lync Server. As transações sintéticas são usadas no Lync Server para verificar se os usuários são capazes de concluir tarefas comuns com êxito, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na PSTN (Rede Telefônica Pública Comutada). Esses testes podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Normalmente, as transações sintéticas são conduzidas de duas maneiras diferentes. Muitos administradores usarão os cmdlets **CsHealthMonitoringConfiguration**, para definir os usuários de teste de cada um de seus pools de registradores. Estes usuários de teste são um par de usuários que foram pré-configurados para uso com transações sintéticas. (normalmente, essas são contas de teste e não pertencem a usuários reais). Com usuários de teste configurados para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool, sem ter de especificar as identidades (nem fornecer credenciais) das contas dos usuários envolvidos no teste.

Como alternativa, os administradores podem executar uma transação sintética utilizando contas de usuários reais. Por exemplo, se dois usuários não puderem trocar mensagens instantâneas, um administrador pode executar uma transação sintética usando as duas contas dos usuários em questão (em vez de um par de contas de teste) e tentar diagnosticar e resolver o problema. Se decidir conduzir uma transação sintética usando contas de usuários reais, você terá de fornecer o nome e a senha de logon de cada usuário.

O cmdlet **Test-CsDialInConferencing** trabalha tentando fazer logon de um usuário de teste no sistema (se você estiver utilizando usuários de teste, o cmdlet **Test-CsDialInConferencing** usará a primeira conta de teste configurada para esse pool). Se o logon for bem-sucedido, o cmdlet usará as credenciais e permissões do usuário para tentar os números de acesso à conferência discada disponíveis. O êxito ou a falha de cada tentativa de discagem será anotado e, em seguida, o usuário de teste será desconectado do Lync Server.

O cmdlet **Test-CsDialInConferencing** apenas verifica se as conexões apropriadas podem ser estabelecidas. O cmdlet não faz nenhuma chamada telefônica nem cria conferências discadas nas quais outros usuários podem participar.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Test-CsDialInConferencing** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsDialInConferencing"}

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
<td><p><em>TargetFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Nome do domínio totalmente qualificado (FQDN) do pool a ser testado.</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Management.Automation.PSCredential</p></td>
<td><p>Objeto de credencial do usuário da conta do usuário a ser testada. O valor passado para UserCredential deve ser uma referência de objeto obtida ao se utilizar o cmdlet <strong>Get-Credential</strong>. Por exemplo, esse código retorna um objeto de credenciais para o usuário litwareinc\kenmyer e armazena esse objeto em uma variável denominada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É necessário fornecer ao usuário uma senha ao executar esse comando. Esse parâmetro não é necessário, caso esteja se conduzindo o teste usando as definições de configuração de monitoramento de integridade.</p></td>
</tr>
<tr class="odd">
<td><p><em>Authentication</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.SyntheticTransactions.SipSyntheticTransaction+AuthenticationMechanism</p></td>
<td><p>Tipo de autenticação usada no teste. Os valores permitidos são:</p>
<p>* TrustedServer</p>
<p>* Negotiate</p>
<p>* ClientCertificate</p>
<p>* LiveID</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
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
<td><p>System.String</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque um caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não é necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetPstnPhoneNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Número de um telefone da PSTN que será usado para verificar se os usuários da PSTN podem participar da conferência discada. Por exemplo:</p>
<p>-TargetPstnPhoneNumber &quot;+12065551219&quot;</p>
<p>Observe que TargetPstnPhoneNumber só deverá ser incluído quando você estiver usando o parâmetro VerifyConferenceJoinType.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Endereço SIP da conta do usuário a ser testada. Por exemplo: -UserSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro UserSipAddress precisa fazer referência à mesma conta de usuário que UserCredential. Esse parâmetro não é necessário, caso esteja se conduzindo o teste usando as definições de configuração de monitoramento de integridade.</p></td>
</tr>
<tr class="even">
<td><p><em>VerifyConferenceJoin</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Quando definido como True, verifica se é possível participar da conferência discada usando um telefone da PSTN. Ao realizar este teste, você tem a opção de incluir o TargetPstnPhoneNumber. Se fizer isto, o TargetPstnPhoneNumber deverá especificar o telefone da PSTN a ser usado para participar da conferência. Se o TargetPstnPhoneNumber não estiver incluído, o cmdlet <strong>Test-CsDialInConferencing</strong> usará os números de telefone atribuídos anteriormente à região apropriada da conferência discada.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsDialInConferencing** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Test-CsDialInConferencing** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsAVConference](test-csavconference.md)

