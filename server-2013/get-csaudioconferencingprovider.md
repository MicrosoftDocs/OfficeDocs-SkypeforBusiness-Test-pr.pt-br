---
title: Get-CsAudioConferencingProvider
TOCTitle: Get-CsAudioConferencingProvider
ms:assetid: 4632e9d0-aa87-459f-ad7e-27125c11da5b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994030(v=OCS.15)
ms:contentKeyID: 52057613
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsAudioConferencingProvider

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os provedores de audioconferência autorizados para uso na organização. Os provedores de audioconferência são empresas de terceiros que fornecem organizações com serviços de conferência.

O cmdlet **Get-CsAudioConferencingProvider** pode ser usado apenas com Microsoft Lync Online.

## Sintaxe

    Get-CsAudioConferencingProvider [[-Identity] <XdsGlobalRelativeIdentity>] [-LocalStore][<CommonParameters>]Get-CsAudioConferencingProvider [-Filter <string>] [-LocalStore] [<CommonParameters>]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 retorna informações sobre todos os provedores de audioconferência disponíveis para uso na sua organização.

    Get-CsAudioConferencingProvider

## Exemplo 2

No Exemplo 2, as informações retornadas são sobre um único provedor de audioconferência: o provedor com a identidade Fabrikam Telecom.

    Get-CsAudioConferencingProvider -Identity "Fabrikam Telecom"

## Exemplo 3

O Exemplo 3 demonstra como os valores curinga (e o parâmetro Filter) podem ser usados para retornar informações sobre provedors de audioconferência. Neste exemplo, o valor de filtro "\*Fabrikam\*" retorna todos os provedores de audioconferência que têm o valor de cadeia de caracteres "Fabrikam" em qualquer lugar da sua identidade.

    Get-CsAudioConferencingProvider -Filter "*Fabrikam*"

## Descrição detalhada

Um provedor de audioconferências é uma empresa de terceiros que oferece serviços de conferências às organizações. Entre outras coisas, os provedores de audioconferências oferecem uma maneira para que usuários de fora do site, e não conectados à rede corporativa ou à Internet, participem da parte de áudio de uma conferência ou reunião. Os provedores de audioconferências oferecem serviços de alta tecnologia, como traduções ao vivo, transcrições e assistência de operador por conferência.

Depois que as organizações contratarem um provedor de audioconferência, os usuários poderão ser atribuídos ao provedor usando o cmdlet **Set-CsUserAcp**. Os administradores podem recuperar informações sobre os provedores de audioconferência disponíveis para eles usando o cmdlet **Get-CsAudioConferencingProvider**.

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
<td><p>Permite que você use caracteres curinga ao indicar o provedor (ou provedores) de audioconferência a ser retornado. Por exemplo, esta sintaxe retorna informações sobre todos o provedores de audioconferência que têm o valor de cadeia de caracteres &quot;fabrikam&quot; em qualquer lugar de sua identidade:</p>
<p>-Filter &quot;*fabrikam*&quot;</p>
<p>Observe que você não pode usar o parâmetro Filter e os parâmetros de identidade no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsGlobalRelativeIdentity</p></td>
<td><p>O identificador exclusivo do provedor de audioconferência a ser retornado. Por exemplo:</p>
<p>-Identity &quot;Fabrikam Telecom&quot;</p>
<p>Se nem o parâmetro Identity nem o parâmetro Filter forem incluídos em um comando, o cmdlet <strong>Get-CsAudioConferencingProvider</strong> retornará informações sobre todos os provedores disponíveis.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados do provedor de audioconferência na réplica local do Repositório de Gerenciamento Central, e não no próprio Repositório de Gerenciamento Central.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Get-CsAudioConferencingProvider** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsAudioConferencingProvider** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.AudioConferencingProvider.AudioConferencingProvider\#Decorated.

## Consulte Também

#### Outros Recursos

[Get-CsUserAcp](get-csuseracp.md)  
[Remove-CsUserAcp](remove-csuseracp.md)  
[Set-CsUserAcp](set-csuseracp.md)

