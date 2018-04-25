---
title: Test-CsPstnOutboundCall
TOCTitle: Test-CsPstnOutboundCall
ms:assetid: 12d940c3-8526-4c8f-8dc1-3fe65a3211bc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398207(v=OCS.15)
ms:contentKeyID: 49305943
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsPstnOutboundCall

 

_**Tópico modificado em:** 2015-03-09_

Testa a capacidade de um usuário realizar chamadas para um número de telefone localizado na PSTN (rede telefônica pública comutada). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsPstnOutboundCall -TargetPstnPhoneNumber <String> -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsPstnOutboundCall -TargetFqdn <String> -TargetPstnPhoneNumber <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsPstnOutboundCall [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>]

## Exemplos

## EXEMPLO 1

O Exemplo 1 verifica se um usuário de testes pré-configurado pode fazer logon no pool atl-cs-001.litwareinc.com e em seguida fazer uma chamada telefônica através do gateway PSTN. Esse comando só funcionará se usuários de teste tiverem sido definidos no pool atl-cs-001.litwareinc.com. Se eles tiverem sido definidos, o comando determinará se o primeiro usuário de testes pode fazer logon no sistema e, em caso afirmativo, faz uma chamada telefônica para outro telefone localizado na rede PSTN.

Se usuários de testes não tiverem sido definidos, o comando irá falhar porque não vai saber qual usuário empregar ao fazer o teste. Se usuários de testes não tiverem sido definidos para um pool, será preciso incluir o parâmetro UserSipAddress, além das credenciais correspondentes para a conta de usuário envolvida no teste. O cmdlet **Test-CsPstnOutboundCall** conduzirá suas verificações usando o usuário especificado.

    Test-CsPstnOutboundCall -TargetFqdn atl-cs-001.litwareinc.com -TargetPstnPhoneNumber "+15551234567" 

## EXEMPLO 2

Os comandos mostrados no Exemplo 2 testam a capacidade de um usuário de testes (litwareinc\\kenmyer) de fazer logon no Lync Server e de fazer uma chamada telefônica através do gateway PSTN. Para fazer isso, o primeiro comando do exemplo usa o cmdlet **Get-Credential** para criar um objeto de credencial do Windows PowerShell contendo o nome e a senha do usuário Ken Myer (como o nome de logon litwareinc\\kenmyer foi incluído como parâmetro, a caixa de diálogo Solicitação de Credenciais do Windows PowerShell só exigirá que o administrador digite a senha da conta de Ken Myer). O objeto de credencial resultante é armazenado em uma variável chamada $cred1.

Com o objeto de credencial em mãos, o segundo comando do exemplo determina se o usuário de testes pode ou não fazer logon no Lync Server e em seguida fazer uma chamada telefônica para o número de telefone de destino (+15551234567). Para realizar essa tarefa, o cmdlet **Test-CsPstnOutboundCall** é chamado, junto com os seguintes parâmetros: TargetFqdn (o FQDN do pool do registrador); UserSipAddress (o endereço SIP do usuário que está fazendo a chamada); UserCredential (o objeto do Windows PowerShell que contém as credenciais do usuário de testes); e TargetPstnPhoneNumber (o número de telefone que está sendo chamado).

    $cred1 = Get-Credential "litwareinc\kenmyer"
    
    Test-CsPstnOutboundCall -TargetFqdn atl-cs-001.litwareinc.com -TargetPstnPhoneNumber "+15551234567" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $cred1

## EXEMPLO 3

O Exemplo 3 mostra como o cmdlet **Test-CsPstnOutboundCall** pode ser usado em modo de plataforma de servidor. Neste modo, o endereço SIP do usuário é especificado, mas as credenciais do usuário não são incluídas. Quando executado dessa forma, o Lync Server usa certificados para autenticar o usuário de testes.

    Test-CsPstnOutboundCall -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress sip:kenmyer@litwareinc.com -TargetPstnPhoneNumber "+15551234567"

## Descrição detalhada

O cmdlet **Test-CsPstnOutboundCall** é um exemplo de uma "transação sintética" do Lync Server. As transações sintéticas são usadas no Lync Server para verificar se os usuários podem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador, ou ser executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

Transações sintéticas costumam ser conduzidas de duas maneiras diferentes. Muitos administradores vão usar os cmdlets **CsHealthMonitoringConfiguration** para configurar um usuário de teste para cada um de seus pools de Registrador. Esses usuários de teste são um par de usuários pré-configurados para uso com transações sintéticas (geralmente, são contas de testes, e não contas que pertençam a usuários reais). Com contas de usuário de testes configuradas para um pool, os administradores podem simplesmente executar uma transação sintética nesse pool sem ter que especificar as identidades (e fornecer as credenciais) das contas de usuário envolvidas no teste.

Outra opção para os administradores é a de executar uma transação sintética com contas de usuário reais. Por exemplo, se dois usuários não conseguirem trocar mensagens instantâneas, um administrador poderia executar uma transação sintética usando as duas contas de usuário em questão (em vez de um par de contas de testes) para tentar diagnosticar e resolver o problema. Se optar por conduzir uma transação sintética usando contas de usuário reais, será necessário fornecer os nomes de logon e as senhas de cada usuário.

Test-CsPstnOutboundCall também pode ser usado em modo de plataforma de servidor. Nesse caso, só é preciso especificar o endereço SIP de um usuário, e o Lync Server usará certificados para autenticar esse usuário.

Ao executar o cmdlet **Test-CsPstnOutboundCall**, o cmdlet primeiro tenta fazer logon do usuário de testes no Lync Server. Se o logon tiver êxito, o cmdlet tenta fazer uma chamada telefônica através do gateway da PSTN. Essa chamada será feita usando o plano de discagem, a diretiva de voz e outras diretivas e configurações atribuídas à conta de testes. Quando a chamada é atendida, o cmdlet envia códigos DTMF pela rede para verificar a conectividade de mídia.

Ao conduzir seu teste, o cmdlet **Test-CsPstnOutboundCall** fará uma chamada telefônica real: o telefone de destino irá tocar e deve ser atendido para que o teste tenha êxito. Essa chamada também deve ser finalizada manualmente pelo administrador.

Quem pode executar este cmdlet: Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsPstnOutboundCall"}

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
<td><p>Cadeia de caracteres</p></td>
<td><p>O FQDN (nome de domínio totalmente qualificado) do pool a ser testado.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetPstnPhoneNumber</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Número de telefone da PSTN a ser chamado na realização do teste. O número de telefone de destino é melhor especificado com o formato E.164, o que significa que um número será parecido com &quot;+14255551298&quot;, contendo um sinal de adição (+) seguido pelo código de chamada do país/região (1), pelo código de área (425) e pelo número de telefone (5551298). Não use traços, parênteses e demais caracteres ao especificar o número do telefone.</p>
<p>Se não quiser usar o formato E.164, o plano de discagem do usuário de testes será anexado ao número. O Lync Server usará esse plano de discagem para normalizar o número para o formato E.164. Se o número não puder ser normalizado, a chamada não será realizada e o teste irá falhar.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Objeto de credencial de usuário para a conta a ser testada. O valor passado para UserCredential deve ser uma referência de objeto obtida com o cmdlet <strong>Get-Credential</strong>. Por exemplo, este código retorna um objeto de credencial para o usuário litwareinc\kenmyer e o armazena em uma variável chamada $x:</p>
<p>$x = Get-Credential &quot;litwareinc\kenmyer&quot;</p>
<p>É preciso fornecer a senha de usuário ao executar este comando.</p>
<p>Esse parâmetro não é necessário se o comando estiver usando os usuários de testes configurados com os cmdlets CsHealthMonitoringConfiguration. Não é necessário especificar esse parâmetro se o teste estiver sendo realizado em modo de plataforma de servidor. Nesse caso, Lync Server vai tentar autenticar o usuário utilizando certificados.</p></td>
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
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Quando presente, o resultado detalhado ao executar o cmdlet será armazenado na variável especificada. Essa variável inclui um par de métodos – ToHTML e ToXML – que podem ser usados para salvar o resultado como um arquivo HTML ou XML.</p>
<p>Para armazenar o resultado em uma variável de log chamada $TestOutput use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: Não use um caractere $ ao especificar o nome da variável. Para salvar a informação armazenada na variável de log em um arquivo HTML, use um comando semelhante ao seguinte:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar a informação armazenada na variável de log para um arquivo XML, use um comando semelhante ao seguinte:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="odd">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável chamada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque um caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>Porta SIP usada pelo serviço Registrador. Esse parâmetro não será necessário se o Registrador usar a porta padrão 5061.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço SIP da conta de usuário a ser testada. Por exemplo: -SenderSipAddress &quot;sip:kenmyer@litwareinc.com&quot;. O parâmetro UserSipAddress precisa fazer referência à mesma conta de usuário que UserCredential.</p>
<p>Esse parâmetro não é necessário se o comando estiver usando os usuários de testes configurados com os cmdlets CsHealthMonitoringConfiguration.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsPstnOutboundCall** não aceita entradas canalizadas.

## Tipos de retorno

O cmdlet **Test-CsPstnOutboundCall** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Test-CsPstnPeerToPeerCall](test-cspstnpeertopeercall.md)

