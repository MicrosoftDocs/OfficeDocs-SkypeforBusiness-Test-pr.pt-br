---
title: New-CsImFilterConfiguration
TOCTitle: New-CsImFilterConfiguration
ms:assetid: 1964cbf9-d7f1-4b4e-99d1-951ac42d82fe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398244(v=OCS.15)
ms:contentKeyID: 49306027
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsImFilterConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Cria uma nova configuração de filtro de mensagens instantâneas (IM). Os filtros de mensagens instantâneas são utilizadas para evitar que os usuários enviem mensagens instantâneas que contenham hyperlinks ativos. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsImFilterConfiguration -Identity <XdsIdentity> [-Action <Allow | Block | Warn>] [-AllowMessage <String>] [-BlockFileExtension <$true | $false>] [-Confirm [<SwitchParameter>]] [-Enabled <$true | $false>] [-Force <SwitchParameter>] [-IgnoreLocal <$true | $false>] [-InMemory <SwitchParameter>] [-Prefixes <PSListModifier>] [-WarnMessage <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

No Exemplo 1, o cmdlet **New-CsImFilterConfiguration** é usado para criar uma nova configuração de filtro de mensagens instantâneas com a identidade site:Redmond. (como nenhum parâmetro adicional foi especificado, essas definições serão criadas utilizando-se os valores padrão.)

    New-CsImFilterConfiguration -Identity site:Redmond

## EXEMPLO 2

Nesse comando, o cmdlet **New-CsImFilterConfiguration** é usado para criar uma nova configuração de filtro de mensagens instantâneas com a identidade site:Redmond. Como o parâmetro Prefixes foi especificado, a nova configuração conterá todos os valores padrão (inclusive os prefixos padrão para filtrar), além de dois prefixos de URI adicionais: rtsp: e urn:. Adiciona-se esses prefixos utilizando-se o modificador da lista de adição, para adicioná-los à lista padrão.

    New-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{add="rtsp:","urn:"}

## EXEMPLO 3

Nesse comando, o cmdlet **New-CsFileTransferFilterConfiguration** é usado para criar uma nova configuração de filtro de mensagens instantâneas com a identidade site:Redmond. Este exemplo é similar ao Exemplo 2, exceto pelo fato de que o modificador da lista de substituição foi utilizado em lugar do modificador da lista de adição. Isto significa que todos os prefixos padrão serão substituídos por estes dois prefixos (rtsp: e urn:). Portanto, somente URIs com os prefixos rtsp: ou urn: serão filtrados nas mensagens instantâneas do site de Redmond.

    New-CsImFilterConfiguration -Identity site:Redmond -Prefixes @{replace="rtsp:","urn:"}

## Descrição detalhada

Ao enviar mensagens instantâneas, os usuários podem incorporar um Identificador de Recurso Uniforme (URI) dentro do texto dessa mensagem, indicando um determinado site ou compartilhamento a outros participantes. O Lync Server pode ser configurado de forma que os hyperlinks com determinados prefixos sejam bloqueados ou não estejam ativos. (em outras palavras, os participantes não podem simplesmente clicar no link e serem levados ao site indicado pelo URI. Eles deverão copiar e colá-lo manualmente em um navegador.)

O cmdlet **New-CsImFilterConfiguration** permite definir uma lista de prefixos de URI que serão filtrados, bem como habilitar e desabilitar completamente a filtragem em um site específico. A chamada do cmdlet **New-CsImFilterConfiguration** somente com a identidade especificada criará uma nova configuração com essa identidade, preenchendo a lista de prefixos desse site com um conjunto de prefixos padrão que serão filtrados.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **New-CsImFilterConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsImFilterConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>XdsIdentity</p></td>
<td><p>Um identificador exclusivo especificando o escopo da configuração de filtro de IM. As definições globais existem por padrão e, portanto, não podem ser recriadas com o cmdlet <strong>New-CsImFilterConfiguration</strong>, mas pode-se criar definições no nível de site especificando-se uma identidade do site:&lt;nomedosite&gt;, onde &lt;nomedosite&gt; é o nome do site ao qual as definições serão aplicadas (por exemplo, site:Redmond).</p>
<p>Tipo de dados completos: Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
</tr>
<tr class="even">
<td><p><em>Action</em></p></td>
<td><p>Opcional</p></td>
<td><p>UrlFilterAction</p></td>
<td><p>O valor deste parâmetro determina a ação que será tomada quando um hyperlink for incluído em uma mensagem instantânea:</p>
<p>Allow - os hyperlinks possuem um caractere sublinhado como prefixo, de forma que os links não estejam mais ativos. Se uma mensagem for especificada na propriedade AllowMessage, essa mensagem será inserida no início de cada mensagem instantânea contendo hyperlinks.</p>
<p>Block - a entrega de mensagens que contêm hyperlinks ativos é bloqueada e o Lync Server envia uma mensagem de erro ao remetente.</p>
<p>Warn - as mensagens que contiverem hyperlinks ativos serão entregues aos participantes aos quais se destinam, juntamente com uma mensagem de aviso que é inserida no início dessas mensagens. A mensagem de aviso pode ser especificada usando-se a propriedade WarnMessage. Se Warn for especificado e nenhum WarnMessage for inserido, a filtragem de mensagens instantâneas será desabilitada, embora as definições da propriedade BlockFileExtension continuem a ser cumpridas.</p>
<p>Padrão: Permitir, a menos que a mensagem tenha mais de 1000 URLs, caso em que o padrão será bloqueado.</p>
<p>Tipo de dados completos: Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.UrlFilterAction</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowMessage</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Se for especificado um valor para este parâmetro, a cadeia de caracteres será inserida no começo de cada mensagem que contém hyperlinks, quando o valor da propriedade Action for definido como Allow. É possível usar essa mensagem para notificar os usuários sobre fatos como os possíveis riscos de clicar em links desconhecidos ou sobre políticas e requisitos importantes de sua organização.</p></td>
</tr>
<tr class="even">
<td><p><em>BlockFileExtension</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Se esse parâmetro for definido como True, será bloqueado um hyperlink que contém um caminho de arquivo com uma extensão especificada pela propriedade Extensions na configuração de filtro de transferência de arquivos aplicável (recuperada chamando-se o cmdlet <strong>Get-CsFileTransferFilterConfiguration</strong>) e será retornada uma mensagem de erro ao remetente. Se esse parâmetro for definido como False, não será feita qualquer verificação especial das extensões de arquivos.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Habilita ou desabilita este recurso. Se esse parâmetro for definido como True, as mensagens instantâneas serão verificadas quanto à presença de hyperlinks e as regras nesta configuração serão aplicadas. Se este parâmetro for definido como False, as mensagens não serão verificadas quanto à presença de hyperlinks.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes de se realizar as alterações.</p></td>
</tr>
<tr class="even">
<td><p><em>IgnoreLocal</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>O valor deste parâmetro controla se a filtragem será realizada nos URIs da Intranet local passados em mensagens instantâneas. Se este parâmetro for definido como True, qualquer URI definido na zona da Intranet do computador local será ignorado (o computador local é o Servidor Front-End que executa o aplicativo Filtro de IM). Se este parâmetro for definido como False, a filtragem especificada será aplicada a todos os hyperlinks.</p>
<p>Padrão: True</p></td>
</tr>
<tr class="odd">
<td><p><em>InMemory</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Cria uma referência de objeto, sem na verdade executar o objeto como uma alteração permanente. Se a saída deste cmdlet for atribuída, chamando-o com este parâmetro a uma variável, você poderá realizar alterações às propriedades da referência do objeto e executar estas alterações, chamando-se o cmdlet coincidente Set- deste cmdlet.</p></td>
</tr>
<tr class="even">
<td><p><em>Prefixes</em></p></td>
<td><p>Opcional</p></td>
<td><p>PSListModifier</p></td>
<td><p>A lista de prefixos de URI que serão filtrados. Qualquer hyperlink incluído em uma mensagem instantânea com um prefixo que corresponda a um dos prefixos nesta lista será filtrado de acordo com as definições especificadas.</p>
<p>Padrão: callto:, file:, ftp., ftp:, gopher:, href, http:, https:, ldap:, mailto:, news:, nntp:, sip:, sips:, tel:, telnet:, www*.</p></td>
</tr>
<tr class="odd">
<td><p><em>WarnMessage</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Esse parâmetro contém a mensagem de aviso que é inserida no início de cada mensagem instantânea que contém hyperlinks quando o valor da propriedade Action for definido como Warn. Normalmente, essa mensagem seria usada para declarar os possíveis riscos de se clicar em links desconhecidos ou para fazer referência a políticas e requisitos importantes de sua organização.</p></td>
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

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.ImFilter.ImFilterConfiguration.

## Consulte Também

#### Outros Recursos

[Remove-CsImFilterConfiguration](remove-csimfilterconfiguration.md)  
[Set-CsImFilterConfiguration](set-csimfilterconfiguration.md)  
[Get-CsImFilterConfiguration](get-csimfilterconfiguration.md)

