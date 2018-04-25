---
title: New-CsCdrConfiguration
TOCTitle: New-CsCdrConfiguration
ms:assetid: e5890ac3-7a6c-4609-a866-84c39b76d3a9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399018(v=OCS.15)
ms:contentKeyID: 49308414
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsCdrConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria um novo conjunto de definições do registro de detalhes das chamadas (CDR). O CDR permite rastrear a utilização de aspectos como as sessões de mensagens instantâneas ponto a ponto, chamadas de telefone via Protocolo VoIP e chamadas de conferências. Esses dados de uso incluem informações sobre os usuários envolvidos na chamadas, o horário e o período da chamada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsCdrConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableCDR <$true | $false>] [-EnablePurging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-KeepCallDetailForDays <UInt32>] [-KeepErrorReportForDays <UInt32>] [-PurgeHourOfDay <UInt32>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando no Exemplo 1 usa o cmdlet **New-CsCdrConfiguration**, para criar um novo conjunto de definições do CDR com a Identidade site:Redmond. Além da Identidade site:Redmond, a propriedade EnableCDR das novas definições também está definida como False. Como as definições têm precedência sobre as definições globais, o CDR não será usado no site de Redmond, independentemente de o CDR ter sido habilitado ou não no escopo global.

    New-CsCdrConfiguration -Identity site:Redmond -EnableCDR $False

## EXEMPLO 2

O Exemplo 2 usa o parâmetro InMemory para demonstrar como você pode criar uma nova coleção de definições de configuração do CDR que existem inicialmente apenas na memória. Para isso, o exemplo usa primeiro o cmdlet **New-CsCdrConfiguration** e o parâmetro InMemory para criar uma coleção virtual de configurações com a Identidade site:Redmond. Esta coleção virtual é armazenada na variável $x. Se a coleção não tiver sido armazenada em uma variável, ela será criada e desaparecerá imediatamente.

Depois que a coleção virtual for criada, o comando mostrado na linha 2 definirá como False ($False) o valor da propriedade EnableCDR. Na linha 3, o cmdlet **Set-CsCdrConfiguration** é usado para transformar a coleção virtual $x em uma coleção real de definições de configuração do CDR, que é aplicada ao site de Redmond. Se o cmdlet **Set-CsCdrConfiguration** não fosse chamado, a coleção virtual desapareceria assim que a sessão do Windows PowerShell fosse encerrada ou a variável $x fosse excluída.

    $x = New-CsCdrConfiguration -Identity site:Redmond -InMemory
    $x.EnableCDR = $False
    Set-CsCdrConfiguration -Instance $x

## Descrição detalhada

O registro de detalhes das chamadas proporciona uma maneira de rastrear o uso de recursos do Lync Server, como chamadas telefônicas VoIP, mensagens instantâneas (IM), transferências de arquivos, conferências de áudio e vídeo (A/V) e sessões de compartilhamento de aplicativos. O CDR (que estará disponível apenas se você tiver implantado o serviço de monitoramento) acompanha as informações de uso: ele registra informações como as partes envolvidas na chamada, a duração da chamada e se os arquivos foram transferidos ou não. (no entanto, o CDR não grava a chamada em si).

O CDR também rastreia informações de erro de chamadas: dados de diagnóstico detalhados de sessões ponto a ponto e de chamadas de conferência.

Como um administrador, você pode determinar se o CDR é usado ou não na sua organização. Se o serviço de monitoramento tiver sido implementado, será possível habilitar ou desabilitar facilmente o CDR. Além disso, você pode tomar esta decisão globalmente (neste caso, o CDR vai ser habilitado ou desabilitado em toda a organização) ou de acordo com o site. Por exemplo: você pode usar o CDR no site de Redmond, mas não no site de Paris.

O cmdlet **New-CsCdrConfiguration** permite criar novas coleções de definições do CDR no escopo de site. (não é possível criar novas definições no escopo global.) Observe que um site pode hospedar apenas uma coleção de definições do CDR. Isso significa que não é possível criar uma nova coleção para o site de Redmond se ele já tiver um conjunto de definições de configuração do CDR. Se você tentar isso, o comando falhará.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsCdrConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsCdrConfiguration"}

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
<td><p>Representa o identificador exclusivo a ser atribuído à nova coleção de definições de configuração do CDR. Como só é possível criar novas coleções no escopo do site, a Identity sempre terá o prefixo &quot;site:&quot; seguido do nome do site; por exemplo &quot;site:Redmond&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>EnableCDR</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indica se o CDR está habilitado ou não. O valor padrão é True.</p></td>
</tr>
<tr class="even">
<td><p><em>EnablePurging</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Indica se os registros do CDR serão excluídos periodicamente ou não do banco de dados do CDR. Se for True (o valor padrão), os registros serão excluídos depois do período de tempo especificado pelas propriedades KeepCallDetailForDays (registros do CDR) e KeepErrorReportForDays (erros do CDR). Se for False, os registros do CDR serão mantidos indefinidamente.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="odd">
<td><p><em>KeepCallDetailForDays</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indica o número de dias que os registros do CDR serão mantidos no banco de dados do CDR. Qualquer registro mais antigo que o número de dias especificado será excluído automaticamente. (observe que a limpeza ocorrerá apenas se a propriedade EnablePurging tiver sido definida como True.)</p>
<p>KeepCallDetailForDays pode ser definido como qualquer valor inteiro entre 1 e 2.562 dias (aproximadamente sete anos). O valor padrão é 60.</p></td>
</tr>
<tr class="even">
<td><p><em>KeepErrorReportForDays</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indica o número de dias que os relatórios de erros do CDR serão mantidos. Qualquer relatório mais antigo do que o número de dias especificado será automaticamente excluído. Os relatórios de CDR são relatórios de diagnósticos, carregados por aplicativos cliente, como o Lync 2013.</p>
<p>É possível definir essa propriedade para qualquer valor inteiro entre 1 e 2.562 dias (aproximadamente sete anos). O valor padrão é 60.</p></td>
</tr>
<tr class="odd">
<td><p><em>PurgeHourOfDay</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.UInt32</p></td>
<td><p>Indica a hora local do dia em que os registros expirados serão excluídos do banco de dados do CDR. A hora do dia é especificada usando-se um relógio de 24 horas, onde 0 representa meia-noite (12:00 AM) e 23 representa 11:00 PM. Observe que é possível especificar apenas a hora do dia. Isso significa que você pode programar a limpeza para ocorrer às 4:00 AM. Mas não pode programá-la para ocorrer às 4:30 AM ou às 4:15 AM. O valor padrão é 2 (2:00 AM). É recomendável não agendar a limpeza para as horas úteis.</p>
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

Nenhuma. O cmdlet **New-CsCdrConfiguration** não aceita a entrada por pipeline.

## Tipos de retorno

Cria instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.CallDetailRecording.CdrSettings.

## Consulte Também

#### Outros Recursos

[Get-CsCdrConfiguration](get-cscdrconfiguration.md)  
[Remove-CsCdrConfiguration](remove-cscdrconfiguration.md)  
[Set-CsCdrConfiguration](set-cscdrconfiguration.md)

