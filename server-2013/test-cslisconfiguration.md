---
title: Test-CsLisConfiguration
TOCTitle: Test-CsLisConfiguration
ms:assetid: 6983d42e-6b93-4365-b0f1-81031d6e251b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398497(v=OCS.15)
ms:contentKeyID: 49306994
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsLisConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Testa a configuração do servidor de informações de local (LIS). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsLisConfiguration -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsLisConfiguration -TargetUri <String> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-WebCredential <PSCredential>] <COMMON PARAMETERS>

    Test-CsLisConfiguration -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-External <SwitchParameter>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-BssId <String>] [-ChassisId <String>] [-Force <SwitchParameter>] [-Mac <String>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-PortId <String>] [-PortIdSubType <InterfaceAlias | InterfaceName | LocallyAssigned>] [-Subnet <String>]

## Exemplos

## EXEMPLO 1

Este exemplo testa a configuração LIS no FQDN atl-cs-001.litwareinc.com. O teste será aprovado caso se possa efetuar uma conexão contendo as credenciais de usuário atuais com o serviço web LIS nesse FQDN. Se for encontrado um local que seja convertido no endereço IP de sub-rede 192.168.0.0, será retornado o endereço desse local.

Para esse comando ser bem-sucedido, deverá existir uma configuração de monitoramento de integridade que contenha os usuários de transição sintética. Para verificar se há uma configuração de monitoramento de integridade, execute o cmdlet **Get-CsHealthMonitoringConfiguration**. Para criar uma nova configuração de monitoramento de integridade, execute o cmdlet **New-CsHealthMonitoringConfiguration**.

    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0

## EXEMPLO 2

Esse exemplo é idêntico ao Exemplo 1, mas com a adição do parâmetro UserSipAddress. Use esse comando quando nenhum usuário de transação sintética tiver sido definido, mas quando o computador em que o comando estiver sendo executado possuir um certificado de servidor.

    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com

## EXEMPLO 3

A primeira linha deste exemplo chama um cmdlet do Windows PowerShell, o cmdlet **Get-Credential**, que solicitará ao usuário um ID de usuário e uma senha. Essas informações serão armazenadas de maneira criptografada na variável $cred.

A segunda linha é idêntica ao comando no Exemplo 2, mas com a adição do parâmetro UserSipAddress. Use esse comando quando nenhum usuário de transação sintética tiver sido definido e quando o computador em que o comando estiver sendo executado não possuir um certificado de servidor.

    $cred = Get-Credential
    Test-CsLisConfiguration -TargetFqdn atl-cs-001.litwareinc.com -Subnet 192.168.0.0 -UserSipAddress sip:kmyer@litwareinc.com -UserCredential $cred

## EXEMPLO 4

A primeira linha deste exemplo chama o cmdlet **Get-Credential**, que solicitará ao usuário um ID de usuário e uma senha. Essas informações serão armazenadas de maneira criptografada na variável $cred.

A linha 2 testa a configuração LIS realizando uma chamada para o URI do serviço web (https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc), com base no endereço SIP do usuário remoto (sip:kmyer@litwareinc.com) e usando as credenciais obtidas na linha 1, passando-as para o parâmetro WebCredential. O teste será aprovado se for possível se efetuar uma conexão contendo as credenciais de usuário fornecidas com o serviço web LIS nesse URI. Se for encontrado um local que seja convertido no endereço IP 192.168.0.0, no endereço MAC 0A-23-00-00-00-AA ou no ID de porta 4500 e ChassisId 0A-23-00-00-00-AA, esse endereço de local será retornado.

Use esse comando quando o computador em que o comando estiver sendo executado não possuir um certificado de servidor.

    $cred = Get-Credential
    Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -WebCredential $cred -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA

## EXEMPLO 5

Esse exemplo é idêntico ao Exemplo 4, exceto pelo fato de que o comando não usa o parâmetro WebCredential (e, portanto, não chama o cmdlet **Get-Credential**). Use esse comando quando o computador em que o comando estiver sendo executado possuir um certificado de servidor.

    Test-CsLisConfiguration -TargetUri https://atl-cs-001.litwareinc.com/locationinformation/lisservice.svc -UserSipAddress sip:kmyer@litwareinc.com -Subnet 192.168.0.0 -Mac 0A-23-00-00-00-AA -PortId 4500 -ChassisId 0A-23-00-00-00-AA

## Descrição detalhada

Este cmdlet determina se o serviço web do servidor de informações de local (LIS) pode ser contatado, com base nas informações contidas nos parâmetros fornecidos. Se o serviço web puder ser contatado e se for encontrado um local que corresponda a qualquer um dos parâmetros fornecidos, o teste será considerado aprovado e o local será exibido. Mesmo se o local não for encontrado, se o serviço web puder ser contatado, o teste retornará uma aprovação, mas sem informações de local. Além disso, caso este cmdlet seja chamado sem se fornecer qualquer um dos parâmetros opcionais, o teste será aprovado, contanto que o serviço web possa ser contatado; no entanto, mais uma vez, nenhuma informação de local será retornada.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Test-CsLisConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsConfiguration"}

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
<td><p>O nome de domínio totalmente qualificado (FQDN) (no formato server.litwareinc.com) do servidor que se quer testar.</p>
<p>Esse parâmetro é necessário, a menos que você especifique o parâmetro TargetUri. Nesse caso, não é possível especificar TargetFqdn.</p></td>
</tr>
<tr class="even">
<td><p><em>TargetUri</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O Identificador de Recurso Uniforme (URI) do Serviço de Informações de Local. É possível recuperar o URI do Serviço de Informações de Local, executando-se o seguinte comando: Get-CsService –WebServer | Select-Object LIServiceInternalUri</p>
<p>Caso se especifique o valor deste parâmetro, o parâmetro UserSipAddress também será obrigatório. Se o computador em que você estiver executando o comando não possuir um certificado de servidor, será necessário especificar também o valor do parâmetro WebCredential.</p>
<p>Este parâmetro é obrigatório, a menos que se especifique o parâmetro TargetFqdn.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Um objeto que contém credenciais de usuário para acesso ao Serviço de Informações de Local. Este objeto pode ser recuperado chamando-se o cmdlet <strong>Get-Credential</strong> e fornecendo-se as credenciais apropriadas.</p>
<p>Esse parâmetro será necessário se os parâmetros TargetFqdn e UserSipAddress forem especificados, e se o computador em que estiver executando o cmdlet não possuir um certificado de servidor.</p></td>
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
<td><p><em>BssId</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O Identificador do conjunto de serviços básicos (BSSID) de um ponto de acesso sem fio. Este valor deve estar no formato nn-nn-nn-nn-nn-nn (como 12-34-56-78-90-ab, por exemplo).</p></td>
</tr>
<tr class="even">
<td><p><em>ChassisId</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço MAC (Controle de acesso de mídia) de um comutador de rede. Este valor deve estar no formato nn-nn-nn-nn-nn-nn (como 12-34-56-78-90-ab, por exemplo) ou de um endereço IP.</p></td>
</tr>
<tr class="odd">
<td><p><em>External</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Este parâmetro não recebe apoio do Servidor de informações de local.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Mac</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço MAC do comutador de portas. Este valor deve estar no formato nn-nn-nn-nn-nn-nn (como 12-34-56-78-90-ab, por exemplo).</p></td>
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
<td><p><em>PortId</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O ID da porta associada ao local a ser testado. Ele também pode conter um endereço MAC ou um endereço IP.</p></td>
</tr>
<tr class="odd">
<td><p><em>PortIdSubType</em></p></td>
<td><p>Opcional</p></td>
<td><p>PortIDSubType</p></td>
<td><p>O subtipo da porta. Este valor pode ser inserido como um valor numérico ou uma cadeia de caracteres, mas deve ser um subtipo válido. Os subtipos válidos são:</p>
<p>1: InterfaceAlias</p>
<p>5: InterfaceName</p>
<p>7: LocallyAssigned</p></td>
</tr>
<tr class="even">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>O número da porta do serviço Registrador.</p></td>
</tr>
<tr class="odd">
<td><p><em>Subnet</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço IP de uma sub-rede. Este valor deveria ser digitado como um endereço IPv4 (dígitos separados por pontos, como 192.0.2.0, por exemplo).</p></td>
</tr>
<tr class="even">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>O endereço SIP de um usuário remoto.</p>
<p>Se você especificar um valor para esse parâmetro, o parâmetro TargetFqdn ou TargetUri também será necessário.</p>
<p>Esse parâmetro será necessário quando você especificar o parâmetro TargetFqdn apenas se você não tiver definido os usuários de transações sintéticas. Para ver se os usuários de transações sintéticas foram definidos, execute o cmdlet <strong>Get-CsHealthMonitoringConfiguration</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>WebCredential</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSCredential</p></td>
<td><p>Um objeto que contém credenciais de usuário para acesso ao Serviço de Informações de Local. Este objeto pode ser recuperado chamando-se o cmdlet <strong>Get-Credential</strong> e fornecendo-se as credenciais apropriadas.</p>
<p>Esse parâmetro será necessário se os parâmetros TargetUri e UserSipAddress forem especificados e se o computador em que estiver se executando o comando não possuir um certificado de servidor.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Test-CsLisConfiguration** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Debug-CsLisConfiguration](debug-cslisconfiguration.md)  
[Publish-CsLisConfiguration](publish-cslisconfiguration.md)  
[Unpublish-CsLisConfiguration](unpublish-cslisconfiguration.md)  
[Import-CsLisConfiguration](import-cslisconfiguration.md)  
[Export-CsLisConfiguration](export-cslisconfiguration.md)

