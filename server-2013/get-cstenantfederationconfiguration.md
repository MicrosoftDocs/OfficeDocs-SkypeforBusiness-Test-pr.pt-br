---
title: Get-CsTenantFederationConfiguration
TOCTitle: Get-CsTenantFederationConfiguration
ms:assetid: e5f836d0-6066-4c23-9594-6e3f1cbd39ef
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994072(v=OCS.15)
ms:contentKeyID: 52057743
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantFederationConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre as configurações de federação dos locatários do Microsoft Lync Online. As configurações de federação são usadas para determinar com quais domínios (se houver algum) os usuários podem se comunicar.

O cmdlet **Get-CsTenantFederationConfiguration** pode ser usado apenas com Skype for Business Online.

## Sintaxe

    Get-CsTenantFederationConfiguration [[-Identity] <XdsIdentity>] [-Tenant <Nullable`1>] [-LocalStore] [-Verbose] Get-CsTenantFederationConfiguration [-Tenant <Nullable`1>] [-Filter <String>] [-LocalStore] [-Verbose]

## Exemplos

## Exemplo 1

O comando mostrado no Exercício 1 retorna informações de configuração de federação do locatário com a ID de locatário "bf19b7db-6960-41e5-a139-2aa373474354". As IDs de locatário podem ser recuperadas com um comando similar a este:

Get-CsTenant | Select-Object TenantID

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354"

Observe que o parâmetro Tenant é opcional. Você também pode chamar Get-CsTenantFederationConfiguration usando esta sintaxeNo :

    Get-CsTenantFederationConfiguration

## Exemplo 2

No Exemplo 2, as informações são retornadas para todos os domínios encontrados na lista de domínios permitidos da federação para o locatário bf19b7db-6960-41e5-a139-2aa373474354. (A lista de domínios permitidos representa todos os domínios com os quais o locatário tem permissão para federar.) Para fazer isso, primeiro o comando chama o cmdlet **Get-CsTenantFederationConfiguration** para retornar as informações de federação do locatário especificado. Essas informações são, então, conectadas ao cmdlet **Select-Object**, que usa ExpandProperty para "expandir" a propriedade AllowedList. A expansão de uma propriedade significa simplesmente a exibição de todas as informações armazenadas nessa propriedade na tela, em formato de fácil leitura.

    Get-CsTenantFederationConfiguration -Tenant "bf19b7db-6960-41e5-a139-2aa373474354" | Select-Object -ExpandProperty AllowedList

## Exemplo 3

O comando anterior retorna a configuração de federação de todos os locatários atualmente em uso na organização. Para realizar essa tarefa, primeiro o comando chama o cmdlet **Get-CsTenant** sem nenhum parâmetro; isso retornará uma coleção de todos os locatários disponíveis. Essa coleção é, então, conectada ao cmdlet **ForEach-Object**. ForEach-Object chama o cmdlet **Get-CsTenantFederationConfiguration** de cada locatário da coleção, usando o valor de propriedade TenantID (retornado pelo cmdlet **Get-CsTenant**) para representar a ID do locatário.

    Get-CsTenant | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId}

## Exemplo 4

No Exemplo 4, as informações de configuração da federação são retornadas somente para os locatários que não permitem federação com usuários públicos. Para fazer isso, primeiro o comando chama o cmdlet **Get-CsTenant** sem nenhum parâmetro, para retornar uma coleção de todos os locatários configurados para uso na organização. Essa coleção é conectada ao cmdlet **ForEach-Object**, que usa o cmdlet **Get-CsTenantFederationConfiguration** de cada locatário da coleção para retornar informações de configuração da federação. Todo o conjunto de informações de configuração da federação é, então, conectado ao cmdlet **Where-Object**, que escolhe somente os locatários em que a propriedade AllowPublicUsers é (-eq) $False.

    Get-CsTenant | Select-Object TenantId | ForEach-Object {Get-CsTenantFederationConfiguration -Tenant $_.TenantId} | Where-Object {$_.AllowPublicUsers -eq $False}

## Descrição detalhada

Federação é um serviço que permite aos usuários trocarem MI e informações de presença com os usuários de outros domínios. Com Lync Online, os administradores podem usar as definições de configuração da federação para controlar:

  - Se os usuários podem ou não se comunicar com pessoas de outros domínios e se puderem, com quais domínos eles têm permissão para a comunicação.

  - Se os usuários podem ou não se comunicar com pessoas que têm contas na MI pública e provedores de presença, como o Windows Live, AOL e Yahoo.

O cmdlet **Get-CsTenantFederationConfiguration** permite que os administradores obtenham informações de federação dos locatários do Lync Online. Esse cmdlet também pode ser usado para analisar as listas de domínios permitidos e bloqueados, que são usadas para especificar domínios com os quais os usuários podem e não podem se comunicar. No entanto, os administradores devem usar o cmdlet **Get-CsTenantPublicProvider** para ver com quais provedores públicos de mensagens instantâneas e de presença os usuários têm permissão para se comunicar.

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
<td><p>Permite que você use caracteres curinga para retornar uma coleção de configurações de federação de locatário. Como cada locatário está limitado a uma coleção global única de configurações de federação, não é necessáro usar o parâmetro Filter. No entanto, esta é a sintaxe válida para o cmdlet <strong>Get-CsTenantFederationConfiguration</strong>:</p>
<p>Get-CsTenantFederationConfiguration –Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Filter &quot;g*&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Especifica a coleção de configurações de federação de locatário a ser retornada. Como cada locatário é limitado a uma coleção global única de configurações de federação, não é necessário incluir este parâmetro ao chamar o cmdlet <strong>Get-CsTenantFederationConfiguration</strong>. Se você optar pelo uso do parâmetro Tenant, também precisará incluir o parâmetro Tenant. Por exemplo:</p>
<p>Get-CsTenantFederationConfiguration -Tenant &quot;bf19b7db-6960-41e5-a139-2aa373474354&quot; –Identity &quot;global&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados de configuração de federação de locatário na réplica local do Repositório de Gerenciamento Central, e não no próprio Repositório de Gerenciamento Central.</p></td>
</tr>
<tr class="even">
<td><p><em>Tenant</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta do inquilino cujas configurações de federação estão sendo retornadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Se você estiver usando uma sessão remota do Windows PowerShell e estiver conectado apenas ao Skype for Business Online, não terá que incluir o parâmetro Tenant. Ao contrário, o ID do locatário será preenchido automaticamente para você com base nas informações de sua conexão. O parâmetro Tenant é basicamente para usar em uma implantação híbrida.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhum. O cmdlet **Get-CsTenantFederationConfiguration** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsTenantFederationConfiguration** retorna instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.Edge.TenantFederationSettings.

## Consulte Também

#### Outros Recursos

[Set-CsTenantFederationConfiguration](set-cstenantfederationconfiguration.md)

