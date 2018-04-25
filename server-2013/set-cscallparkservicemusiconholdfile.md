---
title: Set-CsCallParkServiceMusicOnHoldFile
TOCTitle: Set-CsCallParkServiceMusicOnHoldFile
ms:assetid: af5e7573-4bfd-47b1-a92b-83b06a537158
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412836(v=OCS.15)
ms:contentKeyID: 49307793
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCallParkServiceMusicOnHoldFile

 

_**Tópico modificado em:** 2015-03-09_

Modifica o arquivo de áudio que será reproduzido para chamadores que estiverem em espera em uma chamada estacionada. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsCallParkServiceMusicOnHoldFile -Content <Byte[]> -Service <String> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo define o arquivo SoothingMusic.wma como o arquivo de áudio que será reproduzido para os chamadores cujas chamadas forem estacionadas. A primeira linha deste exemplo é uma chamada ao cmdlet **Get-Content**. Este cmdlet simplesmente lê o conteúdo de um arquivo e o atribui, neste caso, à variável $a. O parâmetro ReadCount recebe o valor 0, de modo que o cmdlet **Get-Content** leia todo o arquivo de uma só vez (em vez de tentar lê-lo linha por linha, o que não se aplica a um arquivo de áudio). O parâmetro Encoding é definido como byte. Isto diz ao cmdlet **Get-Content** que o conteúdo que desejamos ler na variável $a é uma matriz de bytes e não o arquivo de áudio no formato .wma.

A linha 2 neste exemplo é onde o arquivo de áudio é realmente atribuído. O cmdlet **Set-CsCallParkServiceMusicOnHoldFile** é chamado e a ID de serviço no qual o serviço Estacionamento de chamadas estiver sendo executado é especificada. Então o conteúdo do arquivo de áudio lido na variável $a é passado para o parâmetro Content (lembre-se de que este conteúdo deve estar no formato de bytes).

    $a = Get-Content -ReadCount 0 -Encoding byte "C:\MoHFiles\soothingmusic.wma"
    Set-CsCallParkServiceMusicOnHoldFile -Service ApplicationServer:pool0.litwareinc.com -Content $a

## Descrição detalhada

O estacionamento de chamadas é um serviço que permite que um usuário "estacione" uma chamada telefônica recebida. O estacionamento de uma chamada a transfere para um número em um intervalo especificado e imediatamente a coloca em espera. Com base nas definições de configuração especificadas para o serviço Estacionamento de chamadas, a música em espera poderá ser reproduzida ao chamador enquanto a chamada estiver estacionada. Use este cmdlet para modificar o arquivo de áudio (música em espera) que é reproduzido a um chamador estacionado que estiver em espera.

A música de espera será reproduzida somente se a propriedade EnableMusicOnHold do serviço Estacionamento de chamadas tiver sido definida como True. Esta propriedade pode ser verificada chamando o cmdlet **Get-CsCpsConfiguration**. É possível definir a propriedade quando a configuração de Estacionamento de Chamada for criada com o cmdlet **New-CsCpsConfiguration** ou, depois que ela existir, chamando o cmdlet **Set-CsCpsConfiguration**. Esta propriedade é True por padrão.

O Lync Server é enviado com um arquivo padrão de música em espera do serviço Estacionamento de chamadas. Se um arquivo de áudio não for atribuído, o arquivo padrão será usado.

Os arquivos de áudio devem estar no seguinte formato: Windows Media Audio 9, 44 kHz, 16 bits, Mono, CBR, ou 32 kbps.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsCallParkServiceMusicOnHoldFile** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCallParkServiceMusicOnHoldFile"}

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
<td><p><em>Content</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Byte[]</p></td>
<td><p>O conteúdo do arquivo de áudio em formato de bytes.</p>
<p>Use o cmdlet <strong>Get-Content</strong> para recuperar o conteúdo do arquivo de áudio no formato de bytes (para detalhes, consulte a seção Exemplos, neste tópico).</p></td>
</tr>
<tr class="even">
<td><p><em>Service</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>A ID do serviço em que reside o serviço de Estacionamento de Chamada. Por exemplo: ApplicationServer:pool0.litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime qualquer aviso de confirmação que, de outra maneira, seria exibido antes da realização das alterações.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Byte\[\]. Aceita entrada direcionada de uma matriz de bytes que contém o arquivo de música de espera.

## Tipos de retorno

Este cmdlet não retorna um valor.

## Consulte Também

#### Outros Recursos

[New-CsCpsConfiguration](new-cscpsconfiguration.md)  
[Remove-CsCpsConfiguration](remove-cscpsconfiguration.md)  
[Set-CsCpsConfiguration](set-cscpsconfiguration.md)  
[Get-CsCpsConfiguration](get-cscpsconfiguration.md)

