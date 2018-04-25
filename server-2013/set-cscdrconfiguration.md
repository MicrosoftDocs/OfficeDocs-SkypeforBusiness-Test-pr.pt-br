---
title: Set-CsCdrConfiguration
TOCTitle: Set-CsCdrConfiguration
ms:assetid: 977f0d3e-796b-43a3-bc0c-82ea91741c52
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398774(v=OCS.15)
ms:contentKeyID: 49307538
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCdrConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica um conjunto existente de definições do registro de detalhes das chamadas (CDR). O CDR permite rastrear a utilização de aspectos como as sessões de mensagens instantâneas ponto a ponto, chamadas de telefone via Protocolo VoIP e chamadas de conferências. Esses dados de uso incluem informações sobre os usuários envolvidos na chamadas, o horário e o período da chamada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsCdrConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCdrConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EnableCDR <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-KeepCallDetailForDays <UInt32>] [-KeepErrorReportForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 define a hora do dia para excluir registros antigos. Neste caso, a hora é definida como 23 (11:00 da noite, em um relógio de 24 horas). O parâmetro Identity é utilizado para garantir que essas mudanças sejam feitas somente às definições do CDR que possuírem a identidade site:Redmond.

    Set-CsCdrConfiguration -Identity site:Redmond -PurgeHourOfDay 23 

## EXEMPLO 2

O Exemplo 2 é uma variação do comando exibido no Exemplo 1. Neste caso, será modificada a propriedade PurgeHourOfDay de cada coleção de definições de configuração do CDR em uso na organização. Para isso, o comando primeiramente chama o cmdlet **Get-CsCdrConfiguration**, sem qualquer parâmetro, para retornar um conjunto de todas as definições do CDR em uso. Esse conjunto será então direcionado para o cmdlet **Set-CsCdrConfiguration**, que tratará cada item no conjunto e alterará o valor da propriedade PurgeHourOfDay para 11:00 PM (23 hs).

    Get-CsCdrConfiguration | Set-CsCdrConfiguration -PurgeHourOfDay 23 

## EXEMPLO 3

O Exemplo 3 mostra outra variação do comando mostrado no Exemplo 1. Neste exemplo, a propriedade PurgeHourOfDay de todas as definições do CDR que tiverem sido configuradas no escopo de site é alterada. Para isso, o comando primeiro chama o cmdlet **Get-CsCdrConfiguration** com o parâmetro Filter. O valor de filtro "site:\*" garante que apenas as definições do CDR cuja Identidade começar pelo valor de cadeia de caracteres "site:" serão retornadas. O conjunto filtrado será então direcionado para o cmdlet **Set-CsCdrConfiguration**, que modificará a propriedade PurgeHourOfDay de cada item na coleção.

    Get-CsCdrConfiguration -Filter "site:*"| Set-CsCdrConfiguration -PurgeHourOfDay 23

## Descrição detalhada

O registro de detalhes das chamadas proporciona uma maneira de rastrear o uso de recursos do Lync Server, como chamadas telefônicas VoIP, mensagens instantâneas (IM), transferências de arquivos, conferências de áudio e vídeo (A/V) e sessões de compartilhamento de aplicativos. O CDR (que estará disponível apenas se o serviço de monitoramento tiver sido implantado) mantém as informações de utilização: ele registra informações como as partes envolvidas na chamada, a duração da chamada e se houve transferência de arquivos. No entanto, o CDR não grava a chamada em si.

O CDR também rastreia informações de erro de chamadas: dados de diagnóstico detalhados de sessões ponto a ponto e de chamadas de conferência.

Como administrador, você pode determinar se o CDR deve ou não ser usado na organização; assumindo que o Serviço de Monitoramento tenha sido implementado, você pode facilmente habilitar ou desabilitar o CDR. Além disso, você pode tomar essa decisão de forma global (neste caso, o CDR será habilitado ou desabilitado em toda a organização) ou em cada local, individualmente. Por exemplo: é possível utilizar o CDR no site de Redmond, mas não utilizá-lo no site de Paris.

Os administradores também podem gerenciar o banco de dados do CDR. Por exemplo: especificando o número de dias que os registros do CDR serão mantidos antes de serem expurgados do banco de dados. Alterações como essas podem ser feitas usando o cmdlet **Set-CsCdrConfiguration**.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsCdrConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCdrConfiguration"}

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
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>EnableCDR</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indica se o CDR está habilitado ou não. O valor padrão é True.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnablePurging</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indica se os registros do CDR serão ou não excluídos periodicamente do banco de dados do CDR. Se for True (o valor padrão), os registros serão excluídos depois do período de tempo especificado pelas propriedades KeepCallDetailForDays (registros do CDR) e KeepErrorReportForDays (erros do CDR). Se for False, os registros do CDR serão mantidos indefinidamente.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identificador exclusivo atribuído ao conjunto de definições de configuração do CDR. Para fazer referência às definições globais, utilize esta sintaxe: -Identity global. Para fazer referência a um conjunto configurado no escopo do site, use uma sintaxe semelhante a esta: -Identity site:Redmond. Observe que não é possível utilizar caracteres curingas ao especificar uma Identidade.</p>
<p>Se este parâmetro for omitido, o cmdlet <strong>Set-CsCdrConfiguration</strong> modificará as definições globais.</p></td>
</tr>
<tr class="even">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>Objeto CdrSettings</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepCallDetailForDays</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indica o número de dias durante os quais os registros do CDR serão mantidos no banco de dados do CDR. Qualquer registro mais antigo que o número de dias especificado será excluído automaticamente (observe que a limpeza ocorrerá apenas se a propriedade EnablePurging tiver sido definida como True).</p>
<p>É possível definir essa propriedade para qualquer valor inteiro entre 1 e 2.562 dias (aproximadamente sete anos). O valor padrão é 60.</p></td>
</tr>
<tr class="even">
<td><p><em>KeepErrorReportForDays</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indica o número de dias durante os quais os relatórios de erros do CDR serão mantidos. Qualquer relatório mais antigo do que o número de dias especificado será automaticamente excluído. Os relatórios de erros do CDR são relatórios de diagnósticos, carregados por aplicativos cliente, como o Lync 2013.</p>
<p>É possível definir essa propriedade para qualquer valor inteiro entre 1 e 2.562 dias (aproximadamente sete anos). O valor padrão é 60.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indica a hora local do dia em que os registros expirados serão excluídos do banco de dados do CDR. A hora do dia é especificada usando um relógio de 24 horas, onde 0 representa a meia-noite (12:00 A.M.) e 23 representa 11:00 da noite. Observe que é possível especificar apenas a hora do dia. Isso significa que é possível agendar a limpeza para ocorrer às 4:00 da manhã, mas não é possível agendá-la para ocorrer às 4:30 ou às 4:15 da manhã. O valor padrão é 2 (2:00 da manhã). É recomendável não agendar a limpeza para as horas úteis.</p>
<p>A limpeza do banco de dados ocorrerá apenas se a propriedade EnablePurging estiver definida como True.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings. O cmdlet **Set-CsCdrConfiguration** aceita entradas por pipeline de objetos de configuração de registros de detalhes de chamadas.

## Tipos de retorno

O cmdlet **Set-CsCdrConfiguration** não retorna um valor ou objeto. Em vez disso, configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CDRSettings.

## Consulte Também

#### Outros Recursos

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)

