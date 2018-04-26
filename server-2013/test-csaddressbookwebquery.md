---
title: Test-CsAddressBookWebQuery
TOCTitle: Test-CsAddressBookWebQuery
ms:assetid: 9753dcba-83b3-437b-98f0-2806305a5bbb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398773(v=OCS.15)
ms:contentKeyID: 49307534
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsAddressBookWebQuery

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade do usuário pesquisar e retornar informações do Catálogo de Endereços utilizando o Serviço de Consulta à Web do Catálogo de Endereços. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsAddressBookWebQuery -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsAddressBookWebQuery -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsAddressBookWebQuery -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-TargetSipAddress <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 testa o Serviço de Consulta à Web do Catálogo de Endereços do pool atl-cs-001.litwareinc.com, mediante a procura do contato com o endereço SIP sip:kenmyer@litwareinc.com. Este comando funcionará apenas se usuários de teste do pool atl-cs-001.litwareinc.com tiverem sido definidos. Nesse caso, o comando será executado com as credenciais do primeiro usuário de teste no registrador de monitoramento de integridade do pool.

Caso usuários de teste não tenham sido definidos, o comando falhará. Nessa situação, o parâmetro UserSipAddress e as credenciais do usuário com as quais o comando será executado devem ser incluídos.

    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.litwareinc.com  -TargetSipAddress "sip:kenmyer@litwareinc.com"

## EXEMPLO 2

Os comandos exibidos no Exemplo 2 também testam a disponibilidade do Serviço de Consulta à Web do Catálogo de Endereços; neste caso, entretanto, os comandos são executados com as credenciais do usuário Ken Myer (litwareinc\\kenmyer). Para tal, o primeiro comando utiliza o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha do usuário Ken Myer. Como o nome de logon (litwareinc\\kenmyer) foi incluído como um parâmetro, a caixa de diálogo resultante de Solicitação de Credenciais do Windows PowerShell solicitará apenas que o administrador insira a senha da conta de Ken Myer). O objeto de credencial resultante será então armazenado em uma variável denominada $cred1.

No segundo comando, o cmdlet **Test-CsAddressBookWebQuery** é utilizado para testar o Serviço de Consulta à Web do Catálogo de Endereços do pool atl-cs-001.litwareinc.com. Para executar esse comando com as credenciais do usuário Ken Myer, será incluído o parâmetro UserCredential, juntamente com o valor do parâmetro $cred1. O comando também utiliza o parâmetro TargetSipAddress para especificar que o cmdlet deve procurar o contato no Catálogo de Endereços cujo endereço SIP for sip:kenmyer@litwareinc.com.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsAddressBookWebQuery -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred1 -UserSipAddress "sip:kenmyer@litwareinc.com" -TargetSipAddress "sip:kenmyer@litwareinc.com"

## EXEMPLO 3

O Exemplo 3 mostra como testar o Serviço de Consulta à Web do Catálogo de Endereços para atl-cs-001.litwareinc.com. Para isso, o cmdlet **Test-CsAddressBookWebQuery** é chamado com três parâmetros: TargetUri, que especifica o URI do Serviço de Consulta à Web do Catálogo de Endereços, UserSipAddress, que contém o endereço SIP do Windows PowerShell da conta de usuário que estiver sendo usada no teste e TargetSipAddress, que contém o endereço SIP da conta de usuário que estiver sendo procurada.

    Test-CsAddressBookWebQuery -TargetUri https://atl-cs-001.litwareinc.com/groupexpansion -UserSipAddress "sip:packerman@litwareinc.com" -TargetSipAddress "sip:kenmyer@litwareinc.com"

## Descrição detalhada

O cmdlet **Test-CsAddressBookWebQuery** é um exemplo de uma "transação sintética". As transações sintéticas são usadas no Lync Server para verificar se os usuários são capazes de concluir tarefas comuns com sucesso, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Normalmente, as transações sintéticas são conduzidas de duas maneiras diferentes. Muitos administradores usarão os cmdlets **CsHealthMonitoringConfiguration** para configurar os usuários de teste para cada um de seus pools de registradores. Esses usuários de teste são um par de usuários que foram configurados previamente para uso com transações sintéticas (normalmente, essas são contas de teste e não contas que pertencem a usuários reais). Com usuários de teste configurados para um pool, os administradores podem executar uma transação sintética nesse pool, sem a necessidade de especificar as identidades (nem fornecer credenciais) das contas dos usuários envolvidos no teste.

Como alternativa, os administradores podem executar uma transação sintética utilizando contas de usuários reais. Por exemplo, se dois usuários não puderem trocar mensagens instantâneas, um administrador pode executar uma transação sintética usando as duas contas dos usuários em questão (em vez de um par de contas de teste) e tentar diagnosticar e solucionar o problema. Se decidir conduzir uma transação sintética usando contas de usuários reais, será necessário fornecer o nome e a senha de logon de cada usuário.

O cmdlet **Test-CsAddressBookWebQuery** fornece aos administradores uma maneira de verificar se os usuários podem utilizar o Serviço de Consulta à Web do Catálogo de Endereços para pesquisar um contato específico. Quando executado, o cmdlet **Test-CsAddressBookWebQuery** se conectará primeiro ao serviço Web Ticket, para obter autenticação. Se a autenticação for bem-sucedida, o cmdlet então se conectará ao Serviço de Consulta à Web do Catálogo de Endereços e pesquisará o contato especificado. Se o contato for localizado, o cmdlet tentará retornar essas informações para o computador local. O teste será marcado como bem-sucedido apenas se todas as etapas forem concluídas.

Quem pode executar esse cmdlet: Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsAddressBookWebQuery"}

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
<td><p>O nome de domínio totalmente qualificado (FQDN) do pool do registrador no qual o Serviço de Consulta à Web do Catálogo de Endereços será testado. Por exemplo: -TargetFqdn &quot;atl-cs-001.litwareinc.com&quot;.</p>
<p>Observe que não é possível utilizar os parâmetros TargetUri e TargetFqdn no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>String</p></td>
<td><p>O Identificador de Recurso Uniforme (URI) do Serviço de Consulta à Web do Catálogo de Endereços. Por exemplo: -TargetUri &quot;https://atl-cs-001.litwareinc.com/groupexpansion&quot;.</p>
<p>Observe que não é possível utilizar os parâmetros TargetUri e TargetFqdn no mesmo comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>O objeto de credencial do usuário da conta a ser utilizada no teste. O valor passado para UserCredential deve ser uma referência de objeto obtida utilizando o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credenciais do usuário litwareinc\kenmyer e armazena esse objeto em uma variável denominada</p>
<p>$x: $x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>Ao se executar esse comando, é necessário fornecer a senha do usuário.</p></td>
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
<td><p><em>External</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Permite verificar se os usuários externos podem usar o Serviço de Consulta à Web do Catálogo de Endereços.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
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
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque o caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não é necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Endereço SIP do contato a ser retornado pelo Serviço de Consulta à Web do Catálogo de Endereços. Por exemplo: -TargetSipAddress &quot;sip:kenmyer@litwareinc.com&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Endereço SIP do usuário a ser utilizado no teste. Se esse parâmetro não for especificado, o cmdlet <strong>Test-CsAddressBookWebQuery</strong> conduzirá as suas verificações usando as definições de configuração de monitoramento de integridade correspondentes ao pool testado.</p></td>
</tr>
<tr class="even">
<td><p><em>WebCredential</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSCredential</p></td>
<td><p>Um objeto que contém credenciais de usuário para acesso ao serviço de Informações de Local. Esse objeto pode ser recuperado chamando o cmdlet <strong>Get-Credential</strong> e fornecendo as credenciais apropriadas.</p>
<p>Esse parâmetro será necessário se os parâmetros TargetUri e UserSipAddress forem especificados e se o computador em que o comando estiver sendo executado não possuir um certificado de servidor.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsAddressBookWebQuery** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Test-CsAddressBookWebQuery** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsAddressBookService](test-csaddressbookservice.md)  
[Update-CsAddressBook](update-csaddressbook.md)

