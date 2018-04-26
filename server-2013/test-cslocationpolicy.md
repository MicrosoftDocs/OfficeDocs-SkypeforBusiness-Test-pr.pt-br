---
title: Test-CsLocationPolicy
TOCTitle: Test-CsLocationPolicy
ms:assetid: 49f7d148-d46d-4bcc-af9d-6a3a0fdde8ee
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425962(v=OCS.15)
ms:contentKeyID: 49306616
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsLocationPolicy

 

_**Tópico modificado em:** 2015-03-09_

Executa um teste para determinar a diretiva de local que será usada com base no critério especificado nos valores do parâmetro. A diretiva de local contém as configurações que irão determinar se o Enhanced 9-1-1 (E9-1-1) será aplicado ou não, e de que maneira. Com o E9-1-1, é possível que o atendente das chamadas de emergência determine a localização geográfica do chamador. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsLocationPolicy -UserCredential <PSCredential> -UserSipAddress <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-TargetFqdn <String>] <COMMON PARAMETERS>

    Test-CsLocationPolicy -TargetFqdn <String> [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] [-RegistrarPort <Int32>] [-UserSipAddress <String>] <COMMON PARAMETERS>

    Test-CsLocationPolicy [-Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-OutLoggerVariable <String>] [-OutVerboseVariable <String>] [-Subnet <String>]

## Exemplos

## EXEMPLO 1

Este exemplo determina a diretiva de local do usuário atual (ou do usuário configurado no momento). O TargetFqdn é necessário.

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com 

## EXEMPLO 2

A primeira linha do Exemplo 2 é uma chamada ao cmdlet **Get-Credential** do Windows PowerShell. Este cmdlet recupera as credenciais de usuário e as retorna como um objeto seguro. O único parâmetro fornecido para este cmdlet é o ID do usuário. A execução deste cmdlet abre uma caixa de diálogo que será pré-populada com o ID de usuário fornecido e que tem uma caixa de texto que permite a digitação da senha do usuário. Essas credenciais de usuário são salvas na variável $cred.

A linha 2 chama o cmdlet **Test-CsLocationPolicy**. Assim como no Exemplo 1, vamos fornecer o FQDN de destino. Porém, neste exemplo, em vez de usar um usuário pré-configurado, vamos executar o teste contra o usuário com endereço SIP kenmyer@litwareinc.com. Passamos este valor com o prefixo sip: para o parâmetro UserSipAddress e as credenciais desse usuário (armazenadas na variável $cred) para o parâmetro UserCredential.

    $cred = Get-Credential "litwareinc\kenmyer"
    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -UserCredential $cred -UserSipAddress "sip:kenmyer@litwareinc.com"

## EXEMPLO 3

Este exemplo é semelhante ao Exemplo 2, mas sem especificar as credenciais de usuário. Quando o cmdlet **Test-CsLocationPolicy** é chamado sem especificar as credenciais de usuário, o certificado de servidor do computador no qual o cmdlet está sendo executado é usado para autenticar e descobrir a diretiva de local do usuário. Se o computador não tiver um certificado de servidor, será preciso especificar as credenciais, como mostra o Exemplo 2. Para descobrir se há um certificado de servidor no computador, chame o cmdlet **Get-CsCertificate**.

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com"

## EXEMPLO 4

Este exemplo determina a diretiva de local da sub-rede com ID de sub-rede 172.15.11.0. Se nenhuma diretiva de local estiver associada à sub-rede, a diretiva de local do usuário configurado atualmente será recuperada.

Observação: Uma diretiva de local é definida em uma sub-rede através da configuração do parâmetro LocationPolicy do cmdlet **Set-CsNetworkSite** como o ID da diretiva de local, e da configuração do parâmetro NetworkSiteId do cmdlet **Set-CsNetworkSubnet** como o ID desse site. Por exemplo:

Set-CsNetworkSite Portland –LocationPolicy Reno

Set-CsNetworkSubnet 175.15.11.0 –NetworkSiteID Portland

    Test-CsLocationPolicy -TargetFqdn atl-cs-001.litwareinc.com -Subnet 172.15.11.0

## Descrição detalhada

A diretiva de local é usada para aplicar configurações que tenham relação com a funcionalidade E9-1-1 e o local do cliente. A diretiva de local determina se um usuário está habilitado ou não para o recurso E9-1-1, e se for o caso, qual será o comportamento em uma chamada de emergência. Por exemplo, a diretiva de local pode ser usada para definir o número da chamada de emergência (911 nos Estados Unidos), se a segurança corporativa deve ser notificada automaticamente e como as chamadas devem ser roteadas. O cmdlet retorna informações sobre a diretiva de local a ser usada quando chamadas forem feitas a partir de um cliente específico em um comutador, sub-rede, pool ou ponto de acesso sem fio específico.

Se nenhum usuário for especificado na chamada a este cmdlet, o usuário configurado atualmente será testado. Para descobrir o usuário configurado atualmente, chame o cmdlet **Get-CsHealthMonitoringConfiguration**. Para definir o usuário configurado, chame o cmdlet **Set-CsHealthMonitoringConfiguration**.

Se uma diretiva de local for encontrada para o usuário ou sub-rede, o teste terá êxito. As informações retornadas por padrão incluem o nome da diretiva de local (se uma diretiva por usuário for atribuída) e se o usuário ou sub-rede está habilitado para E9-1-1. Inclua o parâmetro comum Verbose do Windows PowerShell para recuperar informações adicionais sobre o teste.

É possível testar diretivas de local em usuários ou sub-redes. Se o teste for executado contra uma sub-rede (especificando-se um valor para o parâmetro Subnet), o cmdlet tentará resolver a diretiva de local para essa sub-rede. Se nenhuma diretiva de local for atribuída à sub-rede, a diretiva de local do usuário configurado será recuperada. Se a diretiva de sub-rede for recuperada com êxito, a saída incluirá um valor de LocationPolicyTagID começando com subnet-tagid. Se uma diretiva de local para a sub-rede não for encontrada, LocationPolicyTagID começará com user-tagid.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Test-CsLocationPolicy** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsLocationPolicy"}

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
<td><p>Cadeia</p></td>
<td><p>O FQDN (nome de domínio totalmente qualificado) do pool no qual o usuário ou sub-rede especificado está hospedado. (Se nenhum usuário for especificado, o usuário pré-configurado ou atual será presumido).</p></td>
</tr>
<tr class="even">
<td><p><em>UserCredential</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>PSCredential</p></td>
<td><p>Um objeto contendo o ID de usuário e a senha da conta de usuário cuja diretiva de local está sendo testada. Um objeto de credencial pode ser recuperado chamando-se o cmdlet <strong>Get-Credential</strong>, preenchendo-se as informações apropriadas e salvando-se a saída em uma variável.</p></td>
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
<td><p>Suprime todos os avisos de confirmação que seriam exibidos antes que as alterações sejam feitas.</p></td>
</tr>
<tr class="odd">
<td><p><em>OutLoggerVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Quando presente, o resultado detalhado ao executar o cmdlet será armazenado na variável especificada. Essa variável inclui um par de métodos – ToHTML e ToXML – que pode ser usado para salvar o resultado em um arquivo HTML ou XML.</p>
<p>Para armazenar o resultado em uma variável de registro em log chamada $TestOutput use a seguinte sintaxe:</p>
<p>-OutLoggerVariable TestOutput</p>
<p>Observação: Não insira um caractere $ ao especificar o nome da variável. Para salvar a informação armazenada na variável de registro em log em um arquivo HTML, use o comando semelhante ao seguinte:</p>
<p>$TestOutput.ToHTML() &gt; C:\Logs\TestOutput.html</p>
<p>Para salvar a informação armazenada na variável de registro em log em um arquivo XML, use o comando semelhante ao seguinte:</p>
<p></p>
<p>$TestOutput.ToXML() &gt; C:\Logs\TestOutput.xml</p></td>
</tr>
<tr class="even">
<td><p><em>OutVerboseVariable</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Quando presente, a saída detalhada da execução do cmdlet será armazenada na variável especificada. Por exemplo, para armazenar a saída em uma variável denominada $TestOutput, use a seguinte sintaxe:</p>
<p>-OutVerboseVariable TestOutput</p>
<p>Não coloque um caractere $ como prefixo ao especificar o nome da variável.</p></td>
</tr>
<tr class="odd">
<td><p><em>RegistrarPort</em></p></td>
<td><p>Opcional</p></td>
<td><p>Int32</p></td>
<td><p>O número da porta do servidor Registrador.</p></td>
</tr>
<tr class="even">
<td><p><em>Subnet</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>O ID (endereço IP) da sub-rede na qual você deseja testar a diretiva de local.</p></td>
</tr>
<tr class="odd">
<td><p><em>UserSipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia</p></td>
<td><p>Endereço SIP do usuário, cuja diretiva de local você deseja testar. Deve estar no formato sip:&lt;id do usuário&gt;, como por exemplo, sip:kenmyer@litwareinc.com.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Test-CsLocationPolicy** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[New-CsLocationPolicy](new-cslocationpolicy.md)  
[Remove-CsLocationPolicy](remove-cslocationpolicy.md)  
[Set-CsLocationPolicy](set-cslocationpolicy.md)  
[Get-CsLocationPolicy](get-cslocationpolicy.md)  
[Grant-CsLocationPolicy](grant-cslocationpolicy.md)  
[Get-CsHealthMonitoringConfiguration](get-cshealthmonitoringconfiguration.md)  
[Set-CsHealthMonitoringConfiguration](set-cshealthmonitoringconfiguration.md)  
[Set-CsNetworkSite](set-csnetworksite.md)

