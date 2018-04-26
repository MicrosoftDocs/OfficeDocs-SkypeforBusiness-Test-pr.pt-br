---
title: Get-CsTenantLicensingConfiguration
TOCTitle: Get-CsTenantLicensingConfiguration
ms:assetid: 0df23143-f1aa-4850-b0f7-750422762925
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362770(v=OCS.15)
ms:contentKeyID: 56270370
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsTenantLicensingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Indica se as informações sobre licenciamento para o locatário especificado estão disponíveis no Centro de administração do Lync.

Este cmdlet só pode ser usado com o Lync Online.

## Sintaxe

    Get-CsTenantLicensingConfiguration [-Filter] <Object>] [-Identity] <Object>] [-Tenant] <Object>] [-LocalStore]

## Descrição detalhada

O cmdlet Get-CsTenantLicensingConfiguration indica se as informações de licenciamento para o locatário especificado estão disponíveis no Centro de administração do Lync. O cmdlet retorna informações semelhantes a estas:

Identity: Global  
Status: Enabled

Se o Status for igual a Enabled, então as informações de licenciamento estarão disponíveis no Centro de administração do Lync. Caso contrário, as informações de licenciamento não estarão disponíveis no Centro de administração do Lync.

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
<td><p><strong>Filtro</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite que você use caracteres curinga para retornar uma coleção de configurações de licenciamento de locatário. Como cada locatário está limitado a uma única coleção global de configurações de licenciamento, não há necessidade de usar o parâmetro Filtro.</p></td>
</tr>
<tr class="even">
<td><p><strong>Identidade</strong></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Especifica a coleção de configurações de licenciamento de locatário a ser retornada. Como cada locatário está limitado a uma única coleção global de configurações de licenciamento, não há necessidade de incluir esse parâmetro ao chamar o cmdlet Get-CsTenantLicensingConfiguration.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LocalStore</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados de configuração de licenciamento de locatário da réplica local do armazenamento Gerenciamento Central, em vez do próprio Armazenamento Central.</p></td>
</tr>
<tr class="even">
<td><p><strong>Locatário</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta do locatário cujas configurações de licenciamento estão sendo retornadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

O cmdlet Get-CsTenantLicensingConfiguration não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet Get-CsTenantLicensingConfiguration retorna instâncias do objeto Deserialized.Microsoft.Rtc.Management.WritableConfig.Settings.TenantConfiguration.TenantLicensingConfiguration.

## Exemplo

O comando mostrado no Exemplo 1 retorna informações de configuração de licenciamento para o locatário atual:

    Get-CsTenantLicensingConfiguration

