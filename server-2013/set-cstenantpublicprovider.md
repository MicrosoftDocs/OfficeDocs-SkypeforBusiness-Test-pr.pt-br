---
title: Set-CsTenantPublicProvider
TOCTitle: Set-CsTenantPublicProvider
ms:assetid: 8341d801-bfa1-4c5b-9b80-5d503deebaf7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994047(v=OCS.15)
ms:contentKeyID: 52057666
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsTenantPublicProvider

 

_**Tópico modificado em:** 2015-03-09_

Habilita e desabilita a comunicação com os provedores de presença e de mensagens instantâneas de terceiros, como Windows Live, AOL e Yahoo. Quando habilitado, os usuários do Microsoft Lync Online poderão trocar informações de presença e de mensagens instantâneas com os usuários que têm contas no provedor público especificado.

O cmdlet **Set-CsTenantPublicProvider** pode ser usado apenas com Skype for Business Online.

## Sintaxe

    Set-CsTenantPublicProvider -Tenant <String> [-Provider <String[]>] [-Verbose] [-WhatIf] [-Confirm]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 habilita a federação com o Windows Live para o locatário com a ID de locatário bf19b7db-6960-41e5-a139-2aa373474354. Como o Windows Live é o único provedor especificado, os provedores AOL e Yahoo serão desabilitados após a execução do comando.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

## Exemplo 2

No Exemplo 2, dois provedores públicos são habilitados: Windows Live e AOL. Isso significa que somente o provedor público Yahoo será desabilitado para o locatário especificado.

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive","AOL"

## Exemplo 3

O Exemplo 3 mostra como você pode desabilitar todos os provedores públicos de um locatário específico. Isso é feito definindo a propriedade Provider como uma cadeia de caracteres vazia ("").

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""

## Exemplo 4

O comando mostrado no Exemplo 4 desabilita todos os provedores públicos de todos os locatários do Lync Online. Para realizar essa tarefa, primeiro o comando usa o cmdlet **Get-CsTenant** para retornar uma coleção de todos os seus locatários. Essa coleção é, então, conectada ao cmdlet **ForEach-Object**, que chama o cmdlet **Set-CsTenantPublicProvider** com base em cada locatário da coleção e desabilita todos os provedores públicos. Essa última tarefa é realizada por meio da definição da propriedade como uma cadeia de caracteres vazia ("").

    Get-CsTenant | ForEach-Object {Set-CsTenantPublicProvider -Tenant $_.TenantId -Provider ""}

## Descrição detalhada

Os provedores públicos são organizações que fornecem serviços de comunicação SIP para o público geral. Ao estabelecer uma relação entre federações com um provedor público, você estabelece efetivamente a federação com qualquer usuário que tem uma conta hospedada por esse provedor. Por exemplo, se você federar com o Windows Live, seus usuários poderão trocar informações de presença e mensagens instantâneas com qualquer pessoa que tenha uma conta de mensagens instantâneas do Windows Live.

O Lync Online oferece aos administradores a opção de configurar a federação com um ou mais dos seguintes provedores de serviços públicos de mensagens instantâneas e provedores de presença:

  -   
    Windows Live

  -   
    AOL

  -   
    Yahoo\!

O cmdlet **Set-CsTenantPublicProvider** pode ser usado para habilitar ou desabilitar a federação com qualquer um desses provedores públicos. Ao usar esse cmdlet, tenha em mente que cada vez que você executa o cmdlet **Set-CsTenantPublicProvider**, deve especificar todos os provedores que precisam ser habilitados. Por exemplo, suponhamos que os três provedores estjam habilitados e você executa este comando:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "WindowsLive"

Como esperado, isso habilitará o Windows Live, e deixará o AOL e o Yahoo desabilitados.

Agora, suponhamos que você execute em seguida este comando:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL"

Esse comando habilitará o AOL. No entanto, ele desabilitará o Windows Live: isso acontece porque o Windows Live não foi especificado como parte do valor de parâmetro fornecido ao parâmetro Provider. Se você quiser habilitar o AOL e manter o Windows Live habilitado também, especifique o AOL e o Windows Live ao chamar Set-CsTenantPublicProvider:

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider "AOL","WindowsLive"

Para desabilitar a federação nos três provedores, defina a propriedade Provider como uma cadeia de caracteres vazia (""):

    Set-CsTenantPublicProvider -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" -Provider ""

Observe que simplesmente habilitar o status de um provedor público não significa que os usuários podem trocar mensagens instantâneas e informações de presença com usuários que têm contas nesse provedor. Além de habilitar a federação com o próprio provedor, os administradores também devem definir a propriedade AllowPublicUsers das configurações de federação para True. Se essa propriedade for definida como False, não será permitida comunicação com nenhum provedor público, independentemente das configurações do provedor público.

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
<td><p><em>Tenant</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta de locatário cujas configurações de provedor público estão sendo modificadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID de cada um de seus locatários, executando este comando:</p>
<pre><code>Get-CsTenant | Select-Object DisplayName, TenantID</code></pre>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes de executar o comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Provider</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String[]</p></td>
<td><p>Indica o(s) provedor(es) público(s) com os quais os usuários poderão se comunicar. Os valores válidos são:</p>
<p>* AOL</p>
<p>* WindowsLive</p>
<p>* Yahoo</p>
<p>Observe que, ao configurar provedores públicos, qualquer provedor incluído no valor de parâmetro Provider será habilitado para uso, enquanto qualquer provedor não incluído no valor de parâmetro será desabilitado. Por exemplo, esta sintaxe habilita somente o Yahoo, deixando o Windows Live e o AOL desabilitados:</p>
<p>-Provider &quot;AOL&quot;</p>
<p>Você pode habilitar vários provedores separando os nomes do provedor com vírgulas:</p>
<p>-Provider &quot;AOL&quot;,&quot;WindowsLive&quot;</p></td>
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

O cmdlet **Set-CsTenantPublicProvider** aceita instâncias em pipeline do objeto Microsoft.Rtc.Management.Hosted.TenantPICStatus.

## Tipos de retorno

Nenhum. Em vez disso, o cmdlet **Set-CsTenantPublicProvider** modifica instâncias existentes do objeto Microsoft.Rtc.Management.Hosted.TenantPICStatus.

## Consulte Também

#### Outros Recursos

[Get-CsTenantPublicProvider](get-cstenantpublicprovider.md)

