---
title: Import-CsConfiguration
TOCTitle: Import-CsConfiguration
ms:assetid: 9a9c27f2-313c-4327-aeed-c47852a831ec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398800(v=OCS.15)
ms:contentKeyID: 49307574
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Importa a topologia, políticas e definições de configuração do seu Lync Server para o Repositório de Gerenciamento Central ou para o computador local. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Import-CsConfiguration -ByteInput <Byte[]> <COMMON PARAMETERS>

    Import-CsConfiguration -FileName <String> <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 importa a topologia atual, as definições de configuração e as diretivas de um arquivo chamado C:\\Config.zip para o Repositório de Gerenciamento Central.

    Import-CsConfiguration -FileName "C:\Config.zip"

## EXEMPLO 2

O Exemplo 2 mostra como os dados podem ser inicialmente replicados para um computador localizado na rede do perímetro. Neste exemplo, os dados de configuração foram exportados para um arquivo chamado Config.zip; esse arquivo foi copiado para a pasta C:\\ no computador localizado na rede do perímetro. Em seguida, o cmdlet Import-CsConfiguration é usado para importar esses dados, com o parâmetro LocalStore fazendo com que sejam importados para o computador local em vez do Repositório de Gerenciamento Central.

    Import-CsConfiguration -FileName "C:\Config.zip" -LocalStore

## EXEMPLO 3

Os dois comandos exibidos no Exemplo 3 exportam a topologia atual, definições de configuração e diretivas, e importam esses dados para o computador local, tudo isso sem usar um arquivo .ZIP. Para isso, o primeiro comando usa o cmdlet **Export-CsConfiguration** e o parâmetro AsBytes para exportar a topologia atual, definições de configuração e diretivas como matriz de byte; essa matriz é armazenada em uma variável chamada $x. No segundo comando, o cmdlet **Import-CsConfiguration** e o parâmetro ByteInput são usados para importar as informações armazenadas em $x. O parâmetro LocalStore faz com que os dados sejam importados para o computador local, em vez do Repositório de Gerenciamento Central. O resultado final é a cópia dos dados do Repositório de Gerenciamento Central para o computador local.

    $x = Export-CsConfiguration -AsBytes
    Import-CsConfiguration -ByteInput $x -LocalStore

## Descrição detalhada

Computadores executando serviços do Lync Server ou funções de servidor precisam ter uma cópia da topologia, das definições de configuração e das diretivas atuais e assim por diante para que funcionem nas funções designadas. O Lync Server é responsável por garantir que essas informações sejam passadas para todos os computadores que precisem delas.

Os cmdlets Import-CsConfiguration cmdlet e Export-CsConfiguration são usados para fazer backup e restaurar sua topologia, definições de configuração e diretivas do Lync Server durante uma atualização do Repositório de Gerenciamento Central. O cmdlet **Export-CsConfiguration** permite exportar dados para um arquivo .ZIP; o cmdlet **Import-CsConfiguration** pode então ser usado para ler o arquivo .ZIP e restaurar a topologia, definições de configuração e diretivas para o Repositório de Gerenciamento Central. Depois disso, os serviços de replicação do Lync Server replicarão as informações restauradas para outros computadores executando serviços.

A capacidade de exportar e importar dados de configuração também é usada na configuração inicial de computadores localizados em sua rede de perímetro (por exemplo, Servidor de Borda). Ao configurar um computador localizado na rede de perímetro, primeiro é necessário realizar uma replicação manual com os cmdlets CsConfiguration: será necessário exportar os dados de configuração usando o cmdlet **Export-CsConfiguration** e em seguida copiar o arquivo .ZIP para o computador na rede de perímetro. Depois disso, o cmdlet **Import-CsConfiguration** e o parâmetro LocalStore podem ser usados para importar os dados. Será necessário fazer isso somente uma vez; desse momento em diante, a replicação acontecerá automaticamente.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Import-CsConfiguration** localmente: RTCUniversalServerAdmins. Além de ser membro de RTCUniversalServerAdmins, você também deve ser um administrador local ou ter permissões de replicador de configurações locais para executar este cmdlet. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsConfiguration"}

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
<td><p><em>ByteInput</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Byte[]</p></td>
<td><p>Lê informações de topologia de uma matriz de byte armazenada em uma variável. Essa matriz de byte é criada com o parâmetro ByteInput ao chamar o cmdlet <strong>Export-CsConfiguration</strong>.</p>
<p>Não é possível usar os parâmetros ByteInput e FileName no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>FileName</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Caminho para o arquivo .ZIP criado por Export-CsConfiguration. Por exemplo: -FileName &quot;C:\Config.zip&quot;. Observe que é necessário incluir o parâmetro FileName ou o parâmetro ByteInput, mas não ambos, ao chamar o cmdlet <strong>Import-CsConfiguration</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Ignora quaisquer prompts que seriam exibidos na ocorrência de um erro não fatal ao executar o comando. Para definir o parâmetro Force como True, use esta sintaxe:</p>
<p>-Force:$True</p></td>
</tr>
<tr class="even">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Copia os dados de configuração para o computador local em vez do Repositório de Gerenciamento Central.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Import-CsConfiguration** não aceita entrada por pipeline.

## Tipos de retorno

O cmdlet **Import-CsConfiguration** não retorna nenhum valor ou objeto.

## Consulte Também

#### Outros Recursos

[Export-CsConfiguration](export-csconfiguration.md)

