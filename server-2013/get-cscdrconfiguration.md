---
title: Get-CsCdrConfiguration
TOCTitle: Get-CsCdrConfiguration
ms:assetid: 4af8ffa2-63d3-4873-8dac-5afede090d4f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398298(v=OCS.15)
ms:contentKeyID: 49306630
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCdrConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações a respeito das configurações do registro de detalhes da suas chamadas (CDR). O CDR permite acompanhar o uso de coisas como sessões de mensagens instantâneas ponto a ponto, chamadas de telefone VoIP e chamadas de conferência. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsCdrConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsCdrConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Este exemplo usa o cmdlet **Get-CsCdrConfiguration** para retornar uma coleção de todas as configurações do CDR definidas para uso em sua organização.

    Get-CsCdrConfiguration

## EXEMPLO 2

O Exemplo 2 usa o parâmetro Identity para retornar uma única coleção de configurações de CDR: as configurações com Identidade site:Redmond.

    Get-CsCdrConfiguration -Identity site:Redmond

## EXEMPLO 3

No Exemplo 3, o parâmetro Filter é empregado para retornar todas as configurações do CDR que tenham sido definidas no escopo do site. O valor do filtro "site:\*" retorna todas as configurações de CDR que têm uma Identity que começa com a cadeia de caracteres "site:" Por definição, estas são configurações que foram definidas no escopo do site.

    Get-CsCdrConfiguration -Filter site:*

## EXEMPLO 4

O Exemplo 4 retorna uma coleção de todas as configurações de CDR onde a propriedade KeepCallDetailForDays for menor do que 30 dias. Para fazer isto, o comando primeiro usa o cmdlet **Get-CsCdrConfiguration** para retornar a coleção de todas as configurações de CDR definidas na organização. Essa coleção é então encaminhada para o cmdlet **Where-Object**, que seleciona somente as configurações nas quais o valor de KeepCallDetailForDays seja menor do que 30 dias.

    Get-CsCdrConfiguration | Where-Object {$_.KeepCallDetailForDays -lt 30}

## Descrição detalhada

O CDR (registro de detalhes das chamadas) fornece um meio de acompanhar o uso das capacidades do Lync Server, tais como chamadas telefônicas VoIP, IM (mensagens instantâneas), transferência de arquivos, conferência de A/V (áudio/vídeo) e sessões de compartilhamento de aplicativos. CDR (que está disponível somente se você tiver implementado o serviço de Monitoramento) mantem informações de uso: registra informações tais como as partes envolvidas na ligação, a duração da chamada e se algum arquivo foi transferido. (porém, o CDR não grava a chamada em si).

CDR também acompanha informações de erro da chamada: dados do diagnóstico detalhado para as sessões ponto a ponto e para chamadas de conferência.

Como um administrador, você pode determinar se CDR é usado na sua organização. Se o serviço de Monitoramento tiver sido implementado, você pode habilitar ou desabilitar o CDR. Além disso, você pode fazer esta decisão globalmente (neste caso CDR vai ou ser habilitado ou desabilitado através da organização) ou em uma base de site a site; por exemplo, você pode usar CDR no site Redmond mas não usar CDR no site Paris.

O cmdlet **Get-CsCdrConfiguration** oferece um meio de retornar informações detalhadas sobre como o CDR é usado na sua organização.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsCdrConfiguration** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsCdrConfiguration"}

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
<td><p>Habilita você a usar caracteres curinga a fim de retornar uma coleção de configurações do CDR. Por exemplo, para retornar uma coleção de todas as configurações definidas em escopo de site, use esta sintaxe: -Filter site:*. Para retornar uma coleção de todas as configurações que têm um valor de cadeia de caracteres &quot;Western&quot; em alguma parte de sua Identidade, use a sintaxe: -Filter *Western*.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Indica um identificador único para a coleção de configurações CDR que você quer retornar. Para referir-se a configurações globais, use esta sintaxe: -Identity global. Para referir-se à coleção configurada no escopo do site, use a sintaxe similar a esta: -Identity site:Redmond. Note que você não pode usar curingas quando especificando uma Identity. Se for necessário usar curingas, use o parâmetro Filter.</p>
<p>Se este parâmetro não for especificado, então o cmdlet <strong>Get-CsCdrConfiguration</strong> retorna uma coleção de todas as configurações de CDR atualmente em uso na organização.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Obtém os dados de configuração de CDR a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Get-CsCdrConfiguration** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Get-CsCdrConfiguration** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings.

## Consulte Também

#### Outros Recursos

[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

