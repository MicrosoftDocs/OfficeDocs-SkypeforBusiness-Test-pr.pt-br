---
title: Get-CsVoiceNormalizationRule
TOCTitle: Get-CsVoiceNormalizationRule
ms:assetid: 59fe1370-1cec-4cf9-8f65-029a7c2454d1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398393(v=OCS.15)
ms:contentKeyID: 49306813
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoiceNormalizationRule

 

_**Tópico modificado em:** 2015-03-09_

Retorna as informações sobre as regras de normalização de voz usadas na sua organização. As regras de normalização de voz convertem os requisitos de discagem de telefone (por exemplo, discar 9 para acessar uma linha externa) para o formato de número de telefone E.164 usado pelo Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsVoiceNormalizationRule [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoiceNormalizationRule [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Este exemplo recupera todas as regras de normalização de voz definidas para a organização.

    Get-CsVoiceNormalizationRule

## EXEMPLO 2

O Exemplo 2 recupera todas as regras de normalização de voz especificadas para todos os sites.

    Get-CsVoiceNormalizationRule -Filter site*

## EXEMPLO 3

O Exemplo 3 recupera todas as regras de normalização de voz com a letra s em qualquer lugar do escopo. Por exemplo, isto irá retornar todas as regras em nível de site e serviço, além das regras por usuário com um s no nome do escopo, como RedmondEastUsers.

    Get-CsVoiceNormalizationRule -Filter *s*

## EXEMPLO 4

O parâmetro Filter usado os Exemplos 2 e 3 combina somente na parte de escopo da Identidade. Este exemplo executa uma combinação na mesma parte para retornar todas as regras com um Nome contendo a cadeia de caracteres "seattle". Para fazer isto, primeiro chamamos o cmdlet **Get-CsVoiceNormalizationRule** para recuperar todas as regras de normalização para a organização. Nós então canalizamos esta coleção para o cmdlet **Where-Object** para localizar todos os itens na coleção em que a propriedade Nome combina com a cadeia de caracteres "seattle".

    Get-CsVoiceNormalizationRule | Where-Object {$_.Name -match "seattle"}

## Descrição detalhada

Este cmdlet devolve uma regra de normalização de voz denominada ou uma coleção de regras de normalização de voz. Estas regras são uma parte necessária da autorização de telefone e roteamento de chamada. Elas definem os requisitos para converter--ou traduzir--números de um formato interno do Lync Server para um formato padrão (E.164). A compreensão de expressões regulares é útil a fim de definir padrões de números que serão traduzidos.

As mesmas regras acessadas por este cmdlet também podem ser acessadas pela propriedade NormalizationRules devolvida por uma chamada para o cmdlet **Get-CsDialPlan**.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsVoiceNormalizationRule** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoiceNormalizationRule"}

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
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Usa cadeias de caracteres curingas para devolver uma coleção de regras de normalização baseadas em Identity. Observe que o Filter funciona apenas na parte de escopo da Identity, não no nome. Por exemplo, o valor de filtro *lob* retornará todas as regras em escopo global (escopos que contenham as letras lob), mas não uma regra com Identity site:Redmond/lobby, em que lob está apenas na porção de nome da identidade, e não no escopo.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Um identificador único para a regra. Se um valor for especificado para este parâmetro, ele deve estar no formato escopo/nome; por exemplo, site:Redmond/Rule1, em que site:Redmond é o escopo e Rule 1 é o nome.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera a regra de normalização de voz a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

O cmdlet **Get-CsVoiceNormalizationRule** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.Voice.NormalizationRule.

## Consulte Também

#### Outros Recursos

[New-CsVoiceNormalizationRule](new-csvoicenormalizationrule.md)  
[Remove-CsVoiceNormalizationRule](remove-csvoicenormalizationrule.md)  
[Set-CsVoiceNormalizationRule](set-csvoicenormalizationrule.md)  
[Test-CsVoiceNormalizationRule](test-csvoicenormalizationrule.md)  
[Get-CsDialPlan](get-csdialplan.md)

