---
title: Get-CsPublicProvider
TOCTitle: Get-CsPublicProvider
ms:assetid: c122505d-7209-4dcb-a888-5c73f58fa68a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412945(v=OCS.15)
ms:contentKeyID: 49308007
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsPublicProvider

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os provedores públicos configurados para uso na organização. Um provedor público é uma organização que fornece ao público em geral mensagens instantâneas, presença e serviços relacionados. O Lync Server é enviado com três provedores públicos configurados, mas não habilitados: Yahoo\!, AIM (AOL) e Messenger (MSN). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsPublicProvider [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsPublicProvider [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 retorna um conjunto de todos os provedores públicos que estiverem configurados para uso na organização. Chamar o cmdlet **Get-CsPublicProvider** sem quaisquer parâmetros adicionais sempre retorna o conjunto completo de provedores públicos.

    Get-CsPublicProvider

## EXEMPLO 2

No Exemplo 2, serão retornados todos os provedores públicos que possuem a Identidade (Identity) Messenger. Como as Identidades dos provedores públicos (e dos provedores de hospedagem) devem ser exclusivas, esse comando sempre retornará, no máximo, um único item.

    Get-CsPublicProvider -Identity "Messenger"

## EXEMPLO 3

O Exemplo 3 retorna todos os provedores públicos que possuem uma Identidade que comece com a letra W. Isso é feito incluindo o parâmetro Filter e o valor do filtro "W\*".

    Get-CsPublicProvider -Filter W*

## EXEMPLO 4

O comando exibido no Exemplo 4 retorna um conjunto de todos os provedores públicos que estiverem desabilitados. Para isso, o comando primeiro chama o cmdlet **Get-CsPublicProvider**, para retornar um conjunto de todos os provedores públicos configurados para uso na organização. Esse conjunto é direcionado para o cmdlet **Where-Object**, que seleciona apenas os provedores cuja propriedade Enable for igual a False.

    Get-CsPublicProvider | Where-Object {$_.Enabled -eq $False}

## EXEMPLO 5

O Exemplo 5 retorna todos os provedores públicos cuja propriedade VerificationLevel tiver sido definida como AlwaysUnverifiable ou UseSourceVerification (os níveis de verificação podem ser definidos como AlwaysUnverifiable, UseSourceVerification ou AlwaysVerifiable). Para fazer isso, o comando primeiro chama o cmdlet **Get-CsPublicProvider**, para retornar um conjunto de todos os provedores públicos configurados para uso na organização. Esse conjunto é direcionado para o cmdlet **Where-Object**, que seleciona somente os provedores cuja propriedade VerificationLevel não for igual a AlwaysVerifiable. O resultado: serão selecionados apenas os provedores cuja propriedade VerificationLevel for definida como AlwaysUnverifiable ou UseSourceVerification.

    Get-CsPublicProvider | Where-Object {$_.VerificationLevel -ne "AlwaysVerifiable"}

## Descrição detalhada

A federação é uma forma segundo a qual duas organizações podem definir uma relação de confiança que facilita a comunicação entre si. Quando uma federação é estabelecida, os usuários nas duas organizações podem enviar mensagens instantâneas entre si, se registrar para notificação de presença e se comunicar entre si utilizando aplicativos SIP como o Lync 2013. O Lync Server permite três tipos de federação: 1) federação direta entre uma organização e a outra, 2) federação entre uma organização e um provedor público e 3) federação entre uma organização e um provedor de hospedagem de terceiros.

Um provedor público é uma organização que fornece serviços de comunicação SIP para o público em geral. Quando se estabelece uma relação de federação com um provedor público, a federação é efetivamente estabelecida com qualquer usuário que tenha uma conta hospedada por esse provedor. Por exemplo, se você estabelecer uma federação com o Messenger (MSN), os usuários serão capazes de trocar mensagens instantâneas e informações de presença com qualquer um que tenha uma conta de mensagens instantâneas do Messenger (MSN).

Para estabelecer uma federação com um provedor público, é preciso criar e habilitar um novo provedor público (além disso, o provedor público precisará criar um relacionamento de federação com você). O cmdlet **Get-CsPublicProvider** permite retornar informações sobre os provedores públicos que tiverem sido configurados para uso na organização.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsPublicProvider** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsPublicProvider"}

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
<td><p>Permite utilizar valores curinga para retornar um ou vários provedores públicos. Por exemplo: para retornar um conjunto de todos os provedores públicos que possuem uma Identidade que comece com a letra Y, use a sintaxe: -Filter &quot;Y*&quot;. Para retornar um conjunto de todos os provedores públicos que incluem o valor de cadeia de caracteres &quot;Windows&quot; em qualquer posição de sua Identidade, use a sintaxe: -Filter &quot;*Windows*&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Identificador exclusivo do provedor público a ser retornado. Normalmente, a Identidade é o nome do website que oferece os serviços (por exemplo: Yahoo!, AOL, MSN, etc.).</p>
<p>Não é possível usar caracteres curinga ao especificar a Identidade. Para usar caracteres curinga para retornar um ou vários provedores públicos, use o parâmetro Filter.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados do provedor público na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsPublicProvider** não aceita a entrada por pipeline.

## Tipos de retorno

Retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.DisplayPublicProvider.

## Consulte Também

#### Outros Recursos

[Disable-CsPublicProvider](disable-cspublicprovider.md)  
[Enable-CsPublicProvider](enable-cspublicprovider.md)  
[New-CsPublicProvider](new-cspublicprovider.md)  
[Remove-CsPublicProvider](remove-cspublicprovider.md)  
[Set-CsPublicProvider](set-cspublicprovider.md)

