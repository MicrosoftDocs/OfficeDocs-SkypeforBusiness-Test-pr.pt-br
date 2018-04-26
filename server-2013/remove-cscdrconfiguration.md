---
title: Remove-CsCdrConfiguration
TOCTitle: Remove-CsCdrConfiguration
ms:assetid: 64352746-a03c-434a-9baf-4d9cd630e9da
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398451(v=OCS.15)
ms:contentKeyID: 49306919
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCdrConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Remove a coleção especificada de definições do registro de detalhes das chamadas (CDR). O CDR permite rastrear o uso de aspectos como as sessões de mensagens instantâneas ponto a ponto, chamadas de telefone VoIP e chamadas de conferência. Esses dados de uso incluem informações os usuários envolvidos na chamadas, o horário e o período da chamada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsCdrConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 usa o cmdlet **Remove-CsCdrConfiguration** para remover as configurações do CDR atribuídas ao site de Redmond. A utilização do parâmetro Identity garante que serão removidas apenas as definições atribuídas ao site especificado.

    Remove-CsCdrConfiguration -Identity site:Redmond

## EXEMPLO 2

O comando mostrado no Exemplo 2 remove todas as configurações do CDR que tiverem sido atribuídas no escopo do site. Para realizar isso, o comando primeiramente usa o cmdlet **Get-CsCdrConfiguration** e o parâmetro Filter, para recuperar as definições relevantes do CDR. O valor de cadeia de caracteres "site:\*" garante que apenas as definições que possuírem uma Identidade iniciada pelo valor de cadeia de caracteres "site:" serão retornadas. A coleção filtrada será então canalizada para o cmdlet **Remove-CsCdrConfiguration**, que excluirá todos os itens na coleção.

    Get-CsCdrConfiguration -Filter site:* | Remove-CsCdrConfiguration

## EXEMPLO 3

No Exemplo 3, serão excluídas todas as definições do CDR cuja propriedade KeepCallDetailForDays tiver menos de 30 dias. Para realizar essa tarefa, o comando chama o cmdlet **Get-CsCdrConfiguration** sem nenhum parâmetro, para retornar uma coleção de todas as definições do CDR em uso na organização. Essa coleção será então canalizada para o cmdlet **Where-Object**, que selecionará apenas as definições cuja propriedade KeepCallDetailForDays for menor do que 30 dias. A coleção filtrada será então canalizada para o cmdlet **Remove-CsCdrConfiguration**, que excluirá cada item na coleção.

    Get-CsCdrConfiguration | Where-Object {$_.KeepCallDetailForDays -lt 30} | Remove-CsCdrConfiguration

## Descrição detalhada

O registro de detalhes das chamadas proporciona uma maneira de rastrear o uso de recursos do Lync Server, como chamadas telefônicas VoIP, mensagens instantâneas, transferências de arquivos, conferências de áudio e vídeo, e sessões de compartilhamento de aplicativos. O CDR (que estará disponível apenas se você tiver implantado o serviço de monitoramento) mantém as informações de uso: ele registra informações como as partes envolvidas na chamada, a duração da chamada, se algum arquivo foi transferido, etc. (no entanto, o CDR não realiza uma gravação da própria chamada).

O CDR também rastreia informações de erro de chamadas: dados de diagnóstico detalhados de sessões ponto a ponto e de chamadas de conferência.

Como administrador, você poderá determinar se o CDR será usado ou não na sua organização. Se o Serviço de Monitoramento estiver implantado, é possível habilitar ou desabilitar facilmente o CDR. Além disso, você pode tomar esta decisão globalmente (neste caso, CDR vai ser habilitado ou desabilitado em toda a organização) ou de acordo com o site. Por exemplo: é possível usar o CDR no site de Redmond, mas não no site de Paris.

As definições específicas do site criadas com o cmdlet **New-CsCdrConfiguration** podem ser removidas posteriormente, usando-se o cmdlet **Remove-CsCdrConfiguration**. Quando se removem as definições específicas do site, o CDR do site afetado será automaticamente governado pelas definições globais de configuração do CDR.

Também é possível executar o cmdlet **Remove-CsCdrConfiguration** concomitantemente às configurações globais do CDR. No entanto, como as definições globais não podem ser removidas, elas serão redefinidas para os seus valores padrão. Por exemplo: suponha que você defina como sendo 90 o valor da propriedade KeepCallDetailForDays nas definições globais. Se você executar o cmdlet **Remove-CsCdrConfiguration** concomitantemente às definições globais, essa propriedade será redefinida com o seu valor padrão de 60.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsCdrConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCdrConfiguration"}

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
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identificador exclusivo das definições de configuração do CDR a serem removidas. Para &quot;remover&quot; as definições globais, use esta sintaxe: -Identity global (observe novamente que, na verdade, não é possível remover as definições globais; o que pode ser feito é redefinir as propriedades com os seus valores padrão). Para remover as definições do escopo do site, use uma sintaxe semelhante a esta: -Identity site:Redmond. Não é possível usar caracteres curinga ao se especificar uma Identidade.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
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

Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings. O cmdlet **Remove-CsCdrConfiguration** aceita entradas canalizadas de objetos de configuração do CDR.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet exclui instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings.

## Consulte Também

#### Outros Recursos

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[New-CsCdrConfiguration](new-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

