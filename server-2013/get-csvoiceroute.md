---
title: Get-CsVoiceRoute
TOCTitle: Get-CsVoiceRoute
ms:assetid: 422abb2d-bff3-4b9a-b18c-d8202b01f69b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425926(v=OCS.15)
ms:contentKeyID: 49306524
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoiceRoute

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre as rotas de voz configuradas para uso na organização. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsVoiceRoute [-Identity <XdsGlobalRelativeIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceRoute [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Recupera as propriedades de todas as rotas de voz definidas na organização.

    Get-CsVoiceRoute

## EXEMPLO 2

Recupera as propriedades para a rota de voz Route1.

    Get-CsVoiceRoute -Identity Route1

## EXEMPLO 3

Este comando exibe as definições da rota de voz cuja identidade contiver a cadeia de caracteres "test" em qualquer posição do valor. Para localizar a cadeia de caracteres "test" somente no final da identidade, use o valor \*test. Da mesma forma, para localizar a cadeia de caracteres "test" somente se ela ocorrer no início da identidade, especifique o valor test\*.

    Get-CsVoiceRoute -Filter *test*

## EXEMPLO 4

Este comando recupera todas as rotas de voz que não tiveram nenhum gateway PSTN atribuído. Primeiro, todas as rotas de voz são recuperadas usando o cmdlet **Get-CsVoiceRoute**. Estas rotas de voz serão então canalizadas para o cmdlet **Where-Object**. O cmdlet **Where-Object** restringe os resultados da operação Get. Neste caso, procura-se cada rota de voz (representada por $\_) e se verifica a propriedade Conta da propriedade PstnGatewayList. Se a contagem de gateways PSTN for igual a 0, a lista estará vazia e nenhum gateway foi definido para a rota.

    Get-CsVoiceRoute | Where-Object {$_.PstnGatewayList.Count -eq 0}

## Descrição detalhada

Use este cmdlet para recuperar uma ou várias rotas de voz existentes. As rotas de voz contêm instruções que informam ao Lync Server como rotear as chamadas de usuários do Enterprise Voice para números de telefone na PSTN (rede telefônica pública comutada) ou na PBX (Central Privada de Comutação).

Este cmdlet pode ser usado para recuperar as informações das rotas de voz, como gateways PSTN aos quais a rota estiver associada (se houver alguma), quais usos da PSTN estão associados à rota, o padrão do telefone (na forma de uma expressão regular) que identifica os números de telefone aos quais a rota se aplicar e as definições do ID de chamador. O uso da PSTN associa a rota de voz a uma política de voz.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsVoiceRoute** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceRoute"}

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
<td><p>Este parâmetro filtra os resultados da operação Get baseada no valor de caracteres curinga passado para este parâmetro.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>Uma cadeia de caracteres que identifica unicamente a rota de voz. Se nenhuma identificação for fornecida, todas as rotas de voz da organização são devolvidas.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera a rota de voz da réplica local do Repositório de Gerenciamento Central em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Este cmdlet retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.Route.

## Consulte Também

#### Outros Recursos

[New-CsVoiceRoute](new-csvoiceroute.md)  
[Remove-CsVoiceRoute](remove-csvoiceroute.md)  
[Set-CsVoiceRoute](set-csvoiceroute.md)  
[Test-CsVoiceRoute](test-csvoiceroute.md)

