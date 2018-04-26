---
title: New-CsClientPolicyEntry
TOCTitle: New-CsClientPolicyEntry
ms:assetid: e975d048-4911-4ae6-9446-2a6363726a4a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399046(v=OCS.15)
ms:contentKeyID: 49308470
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# New-CsClientPolicyEntry

 

_**Tópico modificado em:** 2015-03-09_

Adiciona novas opções às políticas de cliente do Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    New-CsClientPolicyEntry -Name <String> -Value <String>

## Exemplos

## EXEMPLO 1

Os comandos exibidos no Exemplo 1 mostram como uma nova entrada de política pode ser adicionada à política de cliente global. Esse exemplo adiciona uma nova opção de feedback ao Lync. Observe que esse exemplo é para fins demonstrativos. Não se deve esperar a possibilidade de executar esses comandos e adicionar uma opção similar de feedback à sua cópia do Lync.

Para adicionar a nova entrada de política, o primeiro comando do exemplo usa o cmdlet **New-CsClientPolicyEntry** para criar uma entrada com o nome OnlineFeedbackURL e o valor http://www.litwareinc.com/feedback. O objeto de entrada de política resultante é armazenado em uma variável denominada $x.

No segundo comando, o cmdlet **Get-CsClientPolicy** é utilizado para criar uma referência de objeto ($y) à política de cliente global. Depois que a referência de objeto for criada, o método Add será usado para adicionar a nova entrada de política à propriedade PolicyEntry. Se PolicyEntry já tiver uma ou mais entradas, o novo valor será simplesmente anexado ao fim dessa coleção.

Finalmente, o último comando no exemplo utiliza o cmdlet **Set-CsClientPolicy** para gravar as alterações na política global real. Se você não chamar o cmdlet **Set-CsClientPolicy**, as alterações existirão apenas na memória e desaparecerão assim que você encerrar a sessão do Windows PowerShell ou excluir a variável $x.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    
    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.Add($x)
    
    Set-CsClientPolicy -Instance $y

## EXEMPLO 2

O Exemplo 2 é uma variação dos comandos mostrados no Exemplo 1. No entanto, neste caso, a nova entrada de política substitui todos os itens que constam da propriedade PolicyEntry da política global. Para isso, o primeiro comando do exemplo cria uma nova entrada de política, que é armazenada em uma variável denominada $x. O segundo comando utiliza o cmdlet **Set-CsClientPolicy** para definir o valor da propriedade PolicyEntry como $x. Depois que a execução do comando for concluída, o único item na propriedade PolicyEntry será a nova entrada. Todos os itens contidos nessa propriedade antes que o cmdlet **Set-CsClientPolicy** fosse chamado serão substituídos pela nova entrada.

    $x = New-CsClientPolicyEntry -Name "OnlineFeedbackURL" -Value "http://www.litwareinc.com/feedback"
    Set-CsClientPolicy -Identity global -PolicyEntry $x

## EXEMPLO 3

O Exemplo 3 mostra como se pode remover uma entrada de política de cliente da política global. Para isso, o primeiro comando no exemplo recupera a política de cliente global e armazena essas informações em uma variável denominada $y.

Depois que a política global tiver sido recuperada, o segundo comando no exemplo usará o método RemoveAt(), para excluir a primeira entrada de política nessa política. A entrada de política que deve ser removida é indicada pelo seu número de índice: a primeira entrada de política possui o número de índice 0, a segunda entrada de política possui o número de índice 1, e assim por diante. A sintaxe RemoveAt(0) significa que a primeira entrada de política será removida.

Assim que a entrada de política tiver sido removida da instância na memória da política global, o cmdlet **Set-CsClientPolicy** será então chamado para gravar essas alterações na instância real da política de cliente global.

    $y = Get-CsClientPolicy -Identity global
    $y.PolicyEntry.RemoveAt(0)
    
    Set-CsClientPolicy -Instance $y 

## EXEMPLO 4

O comando exibido no Exemplo 4 remove todas as entradas de políticas de cliente configuradas na política global. Isso é realizado usando-se o parâmetro PolicyEntry e definindo-se o valor de parâmetro como null ($Null).

    Set-CsClientPolicy -Identity global -PolicyEntry $Null

## Descrição detalhada

As políticas de cliente são o principal mecanismo utilizado pelo Lync Server para gerenciar o software de cliente, como Lync. Ao criar ou configurar uma política de cliente, você se deparará com diversas opções disponíveis. Por exemplo: é possível especificar se as fotos devem ou não ser usadas no Lync, se os emoticons são permitidos ou não nas mensagens instantâneas e se o Lync salva automaticamente ou não as transcrições de sessões de mensagens instantâneas. Essas opções abrangem muitas das definições relacionadas ao cliente que os administradores precisam gerenciar.

No entanto, elas podem não abranger todas as configurações do cliente que os administradores precisam gerenciar. Para adicionar flexibilidade e extensibilidade de gerenciamento, as políticas do cliente contêm uma propriedade denominada PolicyEntry. Esta propriedade, que admite diversos valores, permite que os administradores adicionem novas opções de gerenciamento, que não são chamadas explicitamente nas políticas do clientes. Por exemplo, antes do lançamento da versão beta do Lync Server, os testadores tinham a capacidade de adicionar uma opção de feedback ao Lync. Essa opção foi adicionada como uma nova entrada de política e foi criada usando o cmdlet **New-CsClientPolicyEntry**.

Observe que não é possível criar de maneira arbitrária novas entradas de políticas e esperar que essas entradas gerenciem o Lync ou outros aplicativos clientes. Em vez disso, será necessário aguardar uma notificação da Microsoft, relativa aos nomes e valores que podem ser usados para construir novas entradas de políticas de cliente.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **New-CsClientPolicyEntry** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "New-CsClientPolicyEntry"}

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
<td><p><em>Name</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Nome da nova entrada de política. Por exemplo: -Name &quot;OnlineFeedbackURL&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Value</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Valor a ser atribuído à nova entrada de política. Por exemplo: -Value http://www.litwareinc.com/feedback.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet New-CsClientPolicyEntry não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **New-CsClientPolicyEntry** cria novas instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Client.PolicyEntryType.

## Consulte Também

#### Outros Recursos

[New-CsClientPolicy](new-csclientpolicy.md)  
[Set-CsClientPolicy](set-csclientpolicy.md)

