---
title: New-CsNetworkBWAlternatePath
TOCTitle: New-CsNetworkBWAlternatePath
ms:assetid: 9017378e-4583-42bc-9572-aa8e9571cfe3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398732(v=OCS.15)
ms:contentKeyID: 49307459
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsNetworkBWAlternatePath

 

_**Tópico modificado em:** 2015-03-09_

Cria novas definições que especificam se a mídia pode ser encaminhada a caminhos alternativos através da Internet, em conexões com largura de banda restrita. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsNetworkBWAlternatePath -AlternatePath <$true | $false> -BWPolicyModality <Audio | Video>

## Exemplos

## EXEMPLO 1

Este exemplo cria um novo caminho alternativo de largura de banda de rede e atribui essas definições a uma região recém-criada. A primeira linha no exemplo chama o cmdlet **New-CsNetworkBWAlternatePath**, para criar um novo caminho alternativo. Um caminho alternativo tem apenas duas propriedades: BWPolicyModality, que deve ser definida como áudio ou vídeo (áudio, neste exemplo) e AlternatePath, que deve ser True ou False (True, neste exemplo). A saída deste cmdlet, uma referência ao objeto de caminho alternativo recém-criado, é atribuída à variável $a.

Na linha 2 deste exemplo, utiliza-se este caminho alternativo recém-criado para criar a nova região de rede. Para fazer isso, chama-se o cmdlet **New-CsNetworkRegion**, passando a identidade NorthAmerica. Atribui-se um valor ao parâmetro obrigatório CentralSite (neste exemplo, o nome do site central desta região é Redmond-NA-MLS) e, em seguida, especifica-se o parâmetro BWAlternatePaths, passando-o à variável ($a) que contém o objeto de caminho alternativo recém-criado.

    $a = New-CsNetworkBWAlternatePath -BWPolicyModality "audio" -AlternatePath $true
    New-CsNetworkRegion -Identity NorthAmerica -CentralSite Redmond-NA-MLS -BWAlternatePaths $a

## Descrição detalhada

Na configuração de controle de admissão de chamadas (CAC) do Lync Server, existem duas modalidades possíveis: áudio e vídeo. As limitações à largura de banda podem ser definidas em cada uma dessas modalidades. Quando as limitações de largura de banda impedem que uma chamada se complete, é possível que a chamada tome um caminho alternativo através da Internet que permitirá a efetuação da chamada. Este cmdlet permite criar as definições que especificam se uma chamada pode ser encaminhada a um caminho alternativo através da Internet, com base na modalidade. As definições se aplicam por região da configuração do CAC.

Este cmdlet não salva imediatamente as definições recém-criadas. Em vez disso, ele cria as definições na memória. Para aplicar essas definições a uma região dentro da rede, é preciso atribuir a saída do cmdlet a uma variável e utilizá-la como um valor do parâmetro BWAlternatePaths do cmdlet **New-CsNetworkRegion** ou **Set-CsNetworkRegion**. Observe que é possível aplicar essas definições diretamente, utilizando os parâmetros AudioAlternatePath e VideoAlternatePath dos cmdlets **New-CsNetworkRegion** e **Set-CsNetworkRegion**, sem ter de chamar o cmdlet **New-CsNetworkBWAlternatePath** para criar um novo objeto.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsNetworkBWAlternatePath** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsNetworkBWAlternatePath"}

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
<td><p><em>AlternatePath</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Boleano</p></td>
<td><p>A definição do parâmetro como True permite que as chamadas feitas na modalidade de mídia especificada no parâmetro BWPolicyModality (áudio ou vídeo) sejam encaminhadas através de um caminho alternativo, se não houver largura de banda adequada no caminho primário.</p></td>
</tr>
<tr class="even">
<td><p><em>BWPolicyModality</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>BWPolicyModality</p></td>
<td><p>A modalidade à qual se aplicam as definições de caminho alternativo.</p>
<p>Valores válidos: áudio, vídeo</p>
<p>Tipo de dados completos: Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWPolicyModality</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Cria um objeto do tipo Microsoft.Rtc.Management.WritableConfig.Settings.NetworkConfiguration.BWAlternatePathType.

## Consulte Também

#### Outros Recursos

[New-CsNetworkRegion](new-csnetworkregion.md)  
[Set-CsNetworkRegion](set-csnetworkregion.md)

