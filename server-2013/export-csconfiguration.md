---
title: Export-CsConfiguration
TOCTitle: Export-CsConfiguration
ms:assetid: 7da7e133-e405-466c-a852-06a4fb678c59
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398627(v=OCS.15)
ms:contentKeyID: 49307245
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Export-CsConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Exporta sua topologia do Lync Server diretivas e configurações para um arquivo. Dentre outras coisas, o arquivo pode ser usado para restaurar essas informações para o Repositório de Gerenciamento Central após uma atualização, uma falha de hardware ou outro problema que resulte em perda de dados. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Export-CsConfiguration [-AsBytes <SwitchParameter>] <COMMON PARAMETERS>

    Export-CsConfiguration -FileName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 exporta os dados do Lync Server a partir do Repositório de Gerenciamento Central para um arquivo chamado C:\\Config.zip.

    Export-CsConfiguration -FileName "C:\Config.zip"

## Descrição detalhada

Computadores executando serviços do Lync Server ou funções de servidor precisam ter uma cópia da topologia atual, das configurações atuais e das diretivas atuais para que funcionem nas funções designadas. O Lync Server é responsável por garantir que essas informações sejam passadas para todos os computadores que precisarem delas.

O cmdlet **Export-CsConfiguration** e o cmdlet **Import-CsConfiguration** são usados para fazer backup e restaurar sua topologia do Lync Server, suas configurações e diretivas durante uma atualização do Repositório de Gerenciamento Central. Os cmdlets **Export-CsConfiguration** permitem exportar dados para um arquivo .ZIP; o cmdlet **Import-CsConfiguration** pode ser usado para ler esse arquivo .ZIP e restaurar a topologia, as configurações e as diretivas para o Repositório de Gerenciamento Central. Depois disso, os serviços de replicação do Lync Server irão replicar as informações restauradas para outros computadores executando os serviços do Lync Server.

A capacidade de exportar e importar dados de configuração também é usada na configuração inicial de computadores localizados em sua rede de perímetro (por exemplo, Servidores de Borda). Ao configurar um computador na rede de perímetro, primeiro é necessário realizar uma replicação manual com os cmdlets CsConfiguration: exporte os dados de configuração usando o cmdlet **Export-CsConfiguration** e em seguida copie o arquivo .ZIP para o computador na rede de perímetro. Depois disso, use o cmdlet **Import-CsConfiguration** e o parâmetro LocalStore para importar os dados. Você só precisará fazer isso uma vez; desse momento em diante, a replicação vai acontecer automaticamente.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Export-CsConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Export-CsConfiguration"}

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
<td><p><em>FileName</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Caminho para o arquivo .ZIP a ser criado na execução do cmdlet <strong>Export-CsConfiguration</strong>. Por exemplo: -FileName &quot;C:\Config.zip&quot;. Observe que é necessário incluir o parâmetro FileName ou os parâmetros AsBytes, mas não ambos, ao chamar o cmdlet <strong>Export-CsConfiguration</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>AsBytes</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Retorna informações de topologia como uma matriz de byte; os dados retornados devem ser armazenados em uma variável para serem usados pelo cmdlet <strong>Import-CsConfiguration</strong>. Não é possível usar AsBytes e FileName no mesmo comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando. Para definir o parâmetro Force como True, use esta sintaxe:</p>
<p>-Force:$True</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Obtém os dados de configuração a partir do computador local, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet**Export-CsConfiguration** não aceita entrada em pipeline.

## Tipos de retorno

Se chamado com o parâmetro AsBytes, o cmdlet **Export-CsConfiguration** retorna informações de configuração na forma de uma matriz de byte.

## Consulte Também

#### Outros Recursos

[Import-CsConfiguration](import-csconfiguration.md)

