---
title: Trabalhando com parâmetros
TOCTitle: Trabalhando com parâmetros
ms:assetid: 29ebda0f-ae5f-4512-ad59-240c3605b240
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362778(v=OCS.15)
ms:contentKeyID: 56270379
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Trabalhando com parâmetros

 

_**Tópico modificado em:** 2015-06-22_

Ao usar o parâmetro Identidade, talvez você observe que o valor de parâmetro kenmyer@litwareinc.com está incluído em aspas duplas:

    -Identity "kenmyer@litwareinc.com"

Uma das perguntas que as pessoas que não conhecem o Windows PowerShell invariavelmente fazem é esta: quando devo usar aspas duplas e quando não devo usá-las? Não há uma resposta simples à essa pergunta, mas existem algumas regras gerais a serem seguidas:

  - As aspas duplas geralmente não serão necessárias quando o valor de parâmetro for um número. Por exemplo, para limitar o número de usuários retornado pelo cmdlet [Get-CsOnlineUser](get-csonlineuser.md), use esta sintaxe:
    
        -ResultSize 100
    
    Na verdade, você nunca deverá colocar aspas duplas em torno de um número. Se fizer isso, o Windows PowerShell poderá ter dificuldade de interpretar o valor como um número.
    
    De forma semelhante, não inclua vírgulas em um número. Por exemplo, se quiser definir o tamanho do resultado como 10,00, esta sintaxe estaria incorreta:
    
        -ResultSize 10,000
    
    Essa sintaxe criará um erro, uma vez que o Windows PowerShell usa a vírgula como uma maneira de separar valores de argumento. Neste caso, o Windows PowerShell suporá que você está passando dois valores de parâmetro separados: 10 e 00. Como não é possível definir um tamanho de resultado simultaneamente como 10 e 0, ocorre um erro. Use esta sintaxe sem vírgula em seu lugar:
    
        -ResultSize 10000

  - As aspas duplas normalmente não serão necessárias quando o valor de parâmetro for uma data:
    
        -StartDate 1/6/2013
    
    Entretanto, isso só será verdadeiro quando a hora não estiver incluída. Se você incluir a hora (o que significa colocar um espaço em branco entre a data e a hora), então o valor de parâmetro deverá ser colocado entre aspas duplas:
    
        -StartDate "1/6/2013 10:00"
    
    Tenha em mente que o comando anterior é formatado por computadores usando o inglês dos EUA e suas configurações regionais. Se você não estiver usando o inglês dos EUA, deverá formatar datas e horas com base nas configurações do seu computador. Para verificar as configurações regionais usadas pelo Windows PowerShell, execute este comando do prompt do Windows PowerShell:
    
        Get-Host | Select-Object CurrentUICulture

  - Os valores de cadeia de caracteres (como o nome de uma pessoa) normalmente não exigem aspas duplas. As principais exceções ocorrem quando esse valor de cadeia de caracteres inclui caracteres restritos, como um espaço em branco, uma vírgula ou outras pontuações. Por exemplo, esta sintaxe funciona porque a identidade do usuário não inclui qualquer um dos caracteres restritos:
    
        -Identity "kenmyer@litwareinc.com"
    
    Entretanto, este comando falhará porque a Identidade inclui um espaço em branco:
    
        -Identity Ken Myer
    
    O comando anterior falha porque o Windows PowerShell usa espaços em banco para separar parâmetros individuais. Por sua vez, isso significa que o Windows PowerShell acha que o parâmetro Identidade é Ken e que Myer é um parâmetro novo. Como resultado, você obterá a seguinte mensagem de erro:
    
        Get-CsOnlineUser : Não foi encontrados um parâmetro posicional que aceite o argumento "Barros".
    
    Para usar um valor de parâmetro que inclua um espaço em branco (ou uma vírgula ou qualquer outro caractere restrito), coloque esse valor entre aspas duplas:
    
        -Identity "Ken Myer"
    
    Na maioria dos casos, o Windows PowerShell permite que você use aspas simples em vez de aspas duplas. Por exemplo, esta será uma sintaxe válida do Windows PowerShell:
    
        -Identity 'Ken Myer'
    
    Observe, entretanto, que você deverá usar o mesmo tipo de aspas no início e no fim da cadeia de caracteres. Esta não é uma sintaxe válida do Windows PowerShell:
    
        -Identity "Ken Myer'
    
    Se você tentar executar este comando, verá o seguinte exibido no console do Windows PowerShell:
    
    ``` 
    >>
    ```
    
    A seta dupla é uma maneira de solicitar que você conclua seu comando: como você iniciou com aspas duplas, o Windows PowerShell espera que você termine com aspas duplas. Se você obtiver o prompt \>\>, pressione Ctrl-C para cancelar seu comando e tente novamente.

  - As aspas duplas não deveriam ser usadas com valores Boolianos (Verdadeiro/Falso). Observe também que você deverá usar as variáveis $True e $False do Windows PowerShell ao especificar valores Verdadeiro/Falso. Por exemplo:
    
        -EnterpriseVoiceEnabled $Verdadeiro

Também existem determinados parâmetros do Windows PowerShell conhecidos como *parâmetros de opção* que não aceitam valores de parâmetro:

    -WhatIf

Não só os valores de parâmetro não são obrigatórios ao usar um parâmetro de opção, mas a inclusão de um valor de parâmetro realmente vai gerar um erro. Por exemplo, se você tentar executar este comando:

    -WhatIf $Verdadeiro

O comando falhará com uma mensagem de erro semelhante a esta:

    Set-CsUserAcp : Não foi encontrado um parâmetro posicional que aceite o argumento "Verdadeiro".

Sua capacidade de gerenciar o Skype for Business Online usando o Windows PowerShell exige que você saiba que cmdlets estão disponíveis para uso. Você também deverá saber que parâmetros estão disponíveis para cada cmdlet, e deverá saber o *tipo de dados* de cada parâmetro (ou seja, se o parâmetro aceitará um valor de data, um valor de cadeia de caracteres, um número e assim por diante). Essas informações (junto com vários exemplos de como usar os cmdlets) podem ser encontradas nos tópicos da Ajuda para os cmdlets do Skype for Business Online . Por exemplo, estes são os parâmetros disponíveis para uso com o cmdlet [Set-CsTenantPublicProvider](set-cstenantpublicprovider.md):

![Parâmetros de um cmdlet PowerShell específico](images/Dn362778.ead7add1-eec3-4fa4-8bbe-9aa72bb7a1ae(OCS.15).png "Parâmetros de um cmdlet PowerShell específico")

Como você pode ver, a tabela de parâmetros oferece uma descrição do cmdlet; indica se o parâmetro é necessário (obrigatório) ou opcional e diz a você qual é o tipo de dados de cada parâmetro. Observe que o tipo de dados mostrado na tabela é o tipo de dados oficial usado pelo .NET Framework. Isso significa que o tipo de dados é mostrado como System.Management.Automation.SwitchParameter em vez de simplesmente Parâmetro de Opção. Veja um guia rápido dos tipos de dados mais comumente usados por cmdlets do Skype for Business Online:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
<td><p>Um valor de cadeia de caracteres que representa a Identidade de um usuário. Normalmente, esse será os endereços UPN ou SIP do usuário:</p>
<pre><code>-Identity &quot;kenmyer@litwareinc.com&quot;</code></pre></td>
</tr>
<tr class="even">
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Um FQDN é um nome de domínio totalmente qualificado. Por exemplo:</p>
<pre><code>-Fqdn &quot;atl-lync-001.litwareinc.com&quot;</code></pre></td>
</tr>
<tr class="odd">
<td><p>System.Boolean</p></td>
<td><p>Um valor Booliano é um valor Verdadeiro/Falso. Lembre-se, você deve usar as variáveis $True e $False do Windows PowerShell ao especificar valores Boolianos:</p>
<pre><code>-Enabled $Verdadeiro -EnterpriseVoiceEnabled $Falso</code></pre></td>
</tr>
<tr class="even">
<td><p>System.Guid</p></td>
<td><p>GUID é o acrônimo de <em>identificar global exclusivo</em>, um identificador exclusivo que, no Skype for Business Online, é atribuído a cada locatário do Skype for Business Online. Por exemplo:</p>
<pre><code>-Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</code></pre>
<p>Você pode recuperar o GUID atribuído a seus locatários do Skype for Business Online usando este comando:</p>
<pre><code>Get-CsTenant | Select-Object TenantId</code></pre></td>
</tr>
<tr class="odd">
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Os parâmetros de opção são chamados assim porque podem ser ativados ou desativados. Caso o parâmetro esteja presente, então a opção será ativada; caso o parâmetro não esteja presente, a opção será desativada. Por exemplo, para usar o parâmetro Confirmar para exigir confirmação antes de executar um comando, inclua o parâmetro Confirmar (sem um valor de parâmetro) como parte do comando. Por exemplo:</p>
<pre><code>Remove-CsUserAcp -Identity &quot;Ken Myer&quot; -Confirm</code></pre>
<p>Se não quiser exigir confirmação, então não inclua o parâmetro Confirmar:</p>
<pre><code>Remove-CsUserAcp -Identity &quot;Ken Myer&quot;</code></pre></td>
</tr>
<tr class="even">
<td><p>System.String</p></td>
<td><p>Um valor de cadeia de caracteres é um valor alfanumérico; ou seja, ele pode conter (em geral) qualquer caractere que possa ser digitado em um teclado. Por exemplo:</p>
<pre><code>-Password &quot;abc123%&amp;*&quot;</code></pre>
<p>É uma boa ideia colocar dois valores de cadeia de caracteres entre aspas duplas. Isso não é obrigatório. Entretanto, será obrigatório se o seu valor de cadeia de caracteres contiver um espaço em branco ou uma vírgula, ou se for uma palavra-chave reservada do Windows PowerShell (uma palavra-chave é um comando ou outro elemento que faça parte da própria linguagem do Windows PowerShell. Por exemplo, “If” e “End” são palavras-chave do Windows PowerShell. Para obter mais informações, digite o seguinte comando no prompt de comando do Windows PowerShell:</p>
<p>Get-Help about_Reserved_Words</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Uma introdução ao Windows PowerShell e ao Lync Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

