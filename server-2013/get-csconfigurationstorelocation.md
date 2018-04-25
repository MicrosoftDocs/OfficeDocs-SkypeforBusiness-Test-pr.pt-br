---
title: Get-CsConfigurationStoreLocation
TOCTitle: Get-CsConfigurationStoreLocation
ms:assetid: abfda147-02fa-46a5-a988-d83daf4cc455
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412814(v=OCS.15)
ms:contentKeyID: 49307765
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsConfigurationStoreLocation

 

_**Tópico modificado em:** 2015-03-09_

Retorna o local do ponto de controle de serviço do Active Directory para o Repositório de Gerenciamento Central. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsConfigurationStoreLocation [-GlobalSettingsDomainController <Fqdn>] [-Report <String>]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 retorna o caminho do SQL Server para o computador (ou pool) que hospeda o Repositório de Gerenciamento Central.

    Get-CsConfigurationStoreLocation

## EXEMPLO 2

O Exemplo 2 é uma variação do comando exibido no Exemplo 1. No entanto, neste caso, o parâmetro Report foi incluído, para especificar o caminho do relatório gerado quando o cmdlet **Get-CsConfigurationStoreLocation** for executado.

    Get-CsConfigurationStoreLocation -Report "C:\Logs\ConfigurationStore.html"

## Descrição detalhada

O Serviços de Domínio Active Directory usa pontos de controle de serviço (SCPs) para ajudar os computadores a localizar serviços. Por exemplo: quando o Lync Server é instalado, cria-se um ponto de controle de serviço, que oferece informações de local para o Repositório de Gerenciamento Central que é usado para manter dados do Lync Server. Os computadores que precisam de acesso ao banco de dados se conectam ao Active Directory e usam as informações contidas no SCP para ajudá-los a localizar o computador correto e a instância correta do SQL Server.

O cmdlet **Get-CsConfigurationStoreLocation** é usado para retornar o caminho do SQL Server (por exemplo: atl-sql-001.litwareinc.com/rtc) para o computador que estiver executando o Repositório de Gerenciamento Central.

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
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Nome de domínio totalmente qualificado (FQDN) de um controlador de domínio no qual estão armazenadas as definições globais. Se as definições globais estiverem armazenadas no contêiner System do Active Directory, este parâmetro deverá apontar para o controlador de domínio raiz. Se as definições globais estiverem armazenadas no contêiner Configuration, qualquer controlador de domínio poderá ser utilizado e este parâmetro poderá ser omitido.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar o caminho do arquivo de log criado quando o cmdlet for executado. Por exemplo: -Report &quot;C:\Logs\ConfigurationStore.html&quot;</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsConfigurationStoreLocation** não aceita a entrada por pipeline.

## Tipos de retorno

Cadeia de caracteres. O cmdlet **Get-CsConfigurationStoreLocation** retorna o local do repositório de configuração.

## Consulte Também

#### Outros Recursos

[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

