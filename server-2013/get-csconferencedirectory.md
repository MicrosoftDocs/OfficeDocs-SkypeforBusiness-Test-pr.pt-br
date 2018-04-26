---
title: Get-CsConferenceDirectory
TOCTitle: Get-CsConferenceDirectory
ms:assetid: 2b7927ab-c6b3-42ce-9c27-9825cd47fd77
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425771(v=OCS.15)
ms:contentKeyID: 49306220
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConferenceDirectory

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os diretórios de conferências configurados para uso na organização. Os diretórios de conferência são usados para ajudar usuários de conferência discada a localizar informações de conferência. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsConferenceDirectory [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsConferenceDirectory [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 retorna informações sobre todos os diretórios de conferências configurados para uso na organização.

    Get-CsConferenceDirectory

## EXEMPLO 2

O Exemplo 2 retorna informações sobre o diretório de conferências com a Identity 2. Como as identidades devem ser exclusivas, o comando jamais retornará mais de um diretório de conferências único.

    Get-CsConferenceDirectory -Identity 2

## EXEMPLO 3

O Exemplo 3 retorna todos os diretórios de conferências hospedados no serviço UserServer:atl-cs-001.litwareinc.com. Para isso, o comando chama inicialmente o cmdlet **Get-CsConferenceDirectory** sem nenhum parâmetro para retornar uma coleção de todos os diretórios de conferências encontrados na organização. Em seguida, essa coleção é redirecionada para o cmdlet **Where-Object**, que só seleciona os diretórios nos quais ServiceID corresponda ao valor de cadeia de caracteres "UserServer:atl-cs-001.litwareinc.com".

    Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "UserServer:atl-cs-001.litwareinc.com"}

## Descrição detalhada

Quando você cria um URI de conferência discada, esses URIs recebem endereços SIP exclusivos. No entanto, é difícil traduzir endereços SIP em dispositivos sem reconhecimento de SIP; por exemplo, um telefone da PSTN (rede telefônica pública comutada) não pode traduzir um endereço SIP. Por isso, o Lync Server usa diretórios de conferências como uma forma de ajudar esses dispositivos a localizar e a se conectar a conferências discadas. Isso é feito criando-se um diretório de conferências SIP associado a cada URI de conferência discada e identificado por um valor inteiro diferente de um URI SIP. Assim, telefones PSTN e outros dispositivos podem usar esses números (em vez de um URI SIP) ao se conectarem a conferências; o número do diretório é incluído na identificação da conferência PSTN inserida pelos usuários durante a conexão com uma conferência discada.

O cmdlet **Get-CsConferenceDirectory** permite retornar informações sobre todos os diretórios de conferências configurados para uso na organização.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsConferenceDirectory** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsConferenceDirectory"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite usar curingas para especificar a Identity do diretório de conferências (ou diretórios) a ser retornado. Como as Identidades de diretório são numéricas, esse parâmetro pode ter um valor mínimo. No entanto, essa sintaxe retornará todos os diretórios de conferências com uma Identity que comece com o número 3: -Filter &quot;3*&quot;.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Identificador numérico (por exemplo, 7) do diretório de conferências a ser retornado. Se esse parâmetro for omitido, o cmdlet <strong>Get-CsConferenceDirectory</strong> retornará informações sobre todos os diretórios de conferências em uso na organização.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Obtém os dados de diretório de conferência a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsConferenceDirectory** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Get-CsConferenceDirectory** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.PstnConf.ConferenceDirectories.

## Consulte Também

#### Outros Recursos

[Move-CsConferenceDirectory](move-csconferencedirectory.md)  
[New-CsConferenceDirectory](new-csconferencedirectory.md)  
[Remove-CsConferenceDirectory](remove-csconferencedirectory.md)

