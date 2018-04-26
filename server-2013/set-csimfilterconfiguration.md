---
title: Set-CsImFilterConfiguration
TOCTitle: Set-CsImFilterConfiguration
ms:assetid: c2b08cc0-8261-4b8b-b2e9-5efa902ceb40
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412960(v=OCS.15)
ms:contentKeyID: 49308022
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsImFilterConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Modifica uma configuração existente de filtro de mensagens instantâneas (IM). As definições do filtro de IM são usadas para evitar que os usuários enviem mensagens instantâneas que contenham hiperlinks clicáveis. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsImFilterConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsImFilterConfiguration [-Instance <PSObject>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Action <Allow | Block | Warn>] [-AllowMessage <String>] [-BlockFileExtension <$true | $false>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-IgnoreLocal <$true | $false>] [-Prefixes <PSListModifier>] [-WarnMessage <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido nesse exemplo desabilita a filtragem de URI da configuração do filtro de IM cuja Identidade for site:Redmond. Para realizar essa tarefa, o parâmetro Enabled é especificado na chamada do cmdlet **Set-CsImFilterConfiguration** com o valor $False.

    Set-CsImFilterConfiguration -Identity site:Redmond -Enabled $False

## EXEMPLO 2

O Exemplo 2 adiciona um novo prefixo de URI (urn:) à lista de prefixos proibidos pela configuração do filtro de IM de site:Redmond. Para adicionar um novo prefixo, o cmdlet **Get-CsImFilterConfiguration** é usado para recuperar a configuração de site:Redmond. O objeto retornado que representar essa configuração será armazenado em uma variável denominada $x. Depois que as definições tiverem sido recuperadas, o método Add() é chamado na linha 2 para adicionar urn: ao conjunto de prefixos armazenados na propriedade Prefixes. Isso altera o valor da referência de objeto $x. Para se alterar a configuração real, a linha 3 chama o cmdlet **Set-CsImFilterConfiguration**, passando $x como o único valor de parâmetro.

    $x = Get-CsImFilterConfiguration -Identity site:Redmond
    $x.Prefixes.Add("urn:")
    Set-CsImFilterConfiguration -Instance $x

## EXEMPLO 3

O Exemplo 3 realiza exatamente a mesma ação que o Exemplo 2, mas em uma linha. Nesse comando, o parâmetro Prefixes do cmdlet **Set-CsImFilterConfiguration** é usado para adicionar urn: à lista de prefixos. O modificador da lista de adição é usado para adicionar esse valor à lista de prefixos.

    Set-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{add="urn:"}

## EXEMPLO 4

Nesse exemplo, o prefixo urn: é removido da lista de prefixos bloqueados pela configuração do filtro de IM de site:Redmond. Esse exemplo é idêntico ao Exemplo 3, mas em vez de chamar o modificador da lista de adição para adicionar um prefixo à lista, o modificador de remoção é chamado para remover um prefixo.

    Set-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{remove="urn:"}

## Descrição detalhada

Ao enviar mensagens instantâneas, os usuários podem incorporar um URI dentro do texto dessa mensagem para referenciar outros participantes na conversa para um determinado site da Web ou compartilhamento. O Lync Server pode ser configurado de forma que os hiperlinks com determinados prefixos sejam bloqueados ou não estejam ativos (em outras palavras, os participantes não podem simplesmente clicar no link e serem levados ao site indicado pelo URI. Eles deverão copiar e colá-lo manualmente em um navegador).

O cmdlet **Set-CsImFilterConfiguration** permite modificar uma lista de prefixos de URI que serão filtrados, bem como habilitar e desabilitar completamente a filtragem, seja globalmente ou em um site específico. Com esse cmdlet, é possível também atualizar diversas mensagens que fornecem avisos aos usuários.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsImFilterConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsImFilterConfiguration"}

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
<td><p><em>Action</em></p></td>
<td><p>Opcional</p></td>
<td><p>UrlFilterAction</p></td>
<td><p>O valor desse parâmetro determina a ação que será tomada quando um hiperlink for incluído em uma mensagem instantânea:</p>
<p>Allow - os hiperlinks possuem um caractere sublinhado como prefixo, de forma que os links não estejam mais ativos. Além disso, se uma mensagem for especificada na propriedade AllowMessage, será inserida uma mensagem de notificação no início de cada mensagem instantânea contendo hiperlinks.</p>
<p>Block - a entrega de mensagens que contêm hiperlinks ativos é bloqueada e o Lync Server envia uma mensagem de erro ao remetente.</p>
<p>Warn - as mensagens que contêm hiperlinks ativos são entregues aos participantes aos quais se destinam, juntamente com uma mensagem de aviso que é inserida no começo dessas mensagens. A mensagem de aviso pode ser especificada usando a propriedade WarnMessage. Se Warn for especificado e nenhum WarnMessage for inserido, a filtragem de mensagens instantâneas será desabilitada, embora as definições da propriedade BlockFileExtension continuem a ser cumpridas.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>AllowMessage</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Se um valor for especificado para esse parâmetro, a cadeia de caracteres será inserida no começo de cada mensagem que contém hiperlinks, quando o valor da propriedade Action for definido como Allow. É possível usar essa mensagem para notificar os usuários sobre fatos como os possíveis riscos de clicar em links desconhecidos ou sobre políticas e requisitos importantes de sua organização.</p></td>
</tr>
<tr class="odd">
<td><p><em>BlockFileExtension</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Se esse parâmetro for definido como True, será bloqueado o será bloqueado que contiver um caminho de arquivo com uma extensão especificada pela propriedade Extensions na classe Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.FileTransferFilterConfiguration (recuperada chamando o cmdlet <strong>Get-CsFileTransferFilterConfiguration</strong>) e será retornada uma mensagem de erro ao remetente. Se esse parâmetro for definido como False, não será feita qualquer verificação especial dos caminhos e das extensões de arquivos.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Habilita ou desabilita esse recurso. Se esse parâmetro for definido como True, as mensagens instantâneas serão verificadas quanto à presença de hiperlinks e as regras nessa configuração serão aplicadas. Se esse parâmetro for definido como False, as mensagens não serão verificadas quanto à presença de hiperlinks.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>XdsIdentity</p></td>
<td><p>O identificador exclusivo das definições de configuração do filtro de mensagens instantâneas que se deseja modificar. Esse valor será global ou do site:&lt;nomedosite&gt;, em que &lt;nomedosite&gt; é o site ao qual se aplica a configuração, como site:Redmond.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreLocal</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>O valor desse parâmetro controla se a filtragem será realizada nos URIs da Intranet local passados em mensagens instantâneas. Se esse parâmetro for definido como True, qualquer URI que for definido na zona da Intranet do computador local será ignorado (o computador local é o Servidor Front-End que executa o aplicativo do Filtro de IM). Se esse parâmetro for definido como False, a filtragem especificada será aplicada a todos os hiperlinks.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Instance</em></p></td>
<td><p>Opcional</p></td>
<td><p>ImFilterConfiguration</p></td>
<td><p>Permite passar uma referência a um objeto para o cmdlet, em vez de definir valores de parâmetros individuais. Esse cmdlet aceita um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration, que pode ser recuperado chamando o cmdlet <strong>Get-CsImFilterConfiguration</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Prefixes</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A lista de prefixos de URI que serão filtrados. Todos os hiperlinks incluídos em uma mensagem instantânea com um prefixo que corresponda a um dos prefixos nessa lista serão filtrados de acordo com as definições especificadas.</p>
<p>Padrão: callto:, file:, ftp., ftp:, gopher:, href, http:, https:, ldap:, mailto:, news:, nntp:, sip:, sips:, tel:, telnet:, www*.</p></td>
</tr>
<tr class="odd">
<td><p><em>WarnMessage</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Esse parâmetro contém a mensagem de aviso que é inserida no início de cada mensagem instantânea que contém hiperlinks quando o valor da propriedade Action for definido como Warn. Normalmente, essa mensagem seria usada para declarar os possíveis riscos de se clicar em links desconhecidos ou para fazer referência a políticas e requisitos importantes de sua organização.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration. Aceita entradas direcionadas de objetos de configuração do filtro de IM.

## Tipos de retorno

O cmdlet **Set-CsImFilterConfiguration** não retorna um valor ou objeto. Em vez disso, configura instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration.

## Consulte Também

#### Outros Recursos

[New-CsImFilterConfiguration](new-csimfilterconfiguration.md)  
[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

