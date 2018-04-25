---
title: Set-CsConfigurationStoreLocation
TOCTitle: Set-CsConfigurationStoreLocation
ms:assetid: 1c69a872-8e78-4c78-ba27-f20f04dce59f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398258(v=OCS.15)
ms:contentKeyID: 49306055
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsConfigurationStoreLocation

 

_**Tópico modificado em:** 2015-03-09_

Define o ponto de controle de serviço do Active Directory para o Repositório de Gerenciamento Central. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsConfigurationStoreLocation -SqlServerFqdn <Fqdn> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalSettingsDomainController <Fqdn>] [-MirrorSqlInstanceName <String>] [-MirrorSqlServerFqdn <Fqdn>] [-Report <String>] [-SkipLookup <SwitchParameter>] [-SqlInstanceName <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 define o ponto de controle de serviço do Active Directory para o Repositório de Gerenciamento Central do Lync Server. Neste exemplo, o SCP aponta para o computador atl-sql-001.litwareinc.com e para a instância SQL Server Rtc.

    Set-CsConfigurationStoreLocation -SqlServerFqdn atl-sql-001.litwareinc.com -SqlInstanceName Rtc

## EXEMPLO 2

O comando mostrado no Exemplo 2 é uma variação do comando mostrado no Exemplo 1. Esse comando também define o SCP do Active Directory para o Repositório de Gerenciamento Central do Lync Server. Além disso, as informações referentes ao êxito (ou à falha) da operação são registradas no arquivo C:\\Logs\\Store\_Location.html. Esse log é gerado incluindo-se o parâmetro Report seguido do caminho completo do arquivo de log.

    Set-CsConfigurationStoreLocation -SqlServerFqdn atl-sql-001.litwareinc.com -SqlInstanceName Rtc -Report C:\Logs\Store_Location.html

## Descrição detalhada

O Serviços de Domínio Active Directory usa SCPs (pontos de controle de serviço) para ajudar computadores a localizar serviços. Por exemplo, ao instalar o Lync Server, um ponto de controle de serviço é criado fornecendo informações de localização para o Repositório de Gerenciamento Central usado na manutenção de dados do Lync Server. Os computadores que precisam de acesso ao banco de dados se conectam ao Active Directory e usam as informações contidas no SCP para ajudá-los a localizar o computador correto e a instância correta do SQL Server.

Como observado, quando o Lync Server é instalado, um SCP do Repositório de Gerenciamento Central é criado automaticamente. Se precisar mover esse banco de dados para outro computador ou para uma instância diferente do SQL Server, será preciso atualizar o ponto de controle de serviço correspondente. Trata-se de uma tarefa que pode ser realizada usando-se o cmdlet **Set-CsConfigurationStoreLocation**. Ao executá-lo, o cmdlet **Set-CsConfigurationStoreLocation** procura no Active Directory o computador especificado pelo parâmetro SqlServer. Em seguida, o cmdlet define o local de armazenamento como o FQDN desse computador.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsConfigurationStoreLocation** localmente: RTCUniversalServerAdmins.

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
<td><p><em>SqlServerFqdn</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN (nome de domínio totalmente qualificado) do computador no qual o Repositório de Gerenciamento Central foi instalado. Por exemplo: -SqlServer atl-sql-001.litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de mensagens de erro não fatais que possam ocorrer na execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN de um controlador de domínio no qual configurações globais são armazenadas. Se configurações globais estiverem armazenadas no contêiner System do Active Directory, então esse parâmetro deverá apontar para o controlador do domínio raiz. Se as configurações globais forem armazenadas no contêiner Configuration, qualquer controlador de domínio pode ser usado e o parâmetro pode ser omitido.</p></td>
</tr>
<tr class="odd">
<td><p><em>MirrorSqlInstanceName</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Nome da instância do SQL Server contendo as tabelas e os dados do banco de dados de espelho do Lync Server. Por exemplo: -SqlInstanceName &quot;rtc&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>MirrorSqlServerFqdn</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN do computador onde o banco de dados de espelho do Repositório de Gerenciamento Central foi instalado. Por exemplo: -SqlServer atl-mirror-001.litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar um caminho de arquivo para o arquivo de log criado quando o cmdlet é executado. Por exemplo: -Report &quot;C:\Logs\ConfigurationStore.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>SkipLookup</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Se este parâmetro for incluído, o cmdlet <strong>Set-CsConfigurationStoreLocation</strong> não verificará se o computador especificado e a instância especificada do SQL Server estão disponíveis. Em vez disso, ele simplesmente alterará o ponto de controle de serviço.</p>
<p>Se esse parâmetro não for incluído, tanto o computador especificado quanto a instância especificada do SQL Server deverão estar disponíveis para que o SCP possa ser alterado.</p></td>
</tr>
<tr class="odd">
<td><p><em>SqlInstanceName</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Nome da instância do SQL Server que contém as tabelas e os dados do Lync Server. Por exemplo: -SqlInstanceName &quot;rtc&quot;.</p></td>
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

Nenhuma. O cmdlet **Set-CsConfigurationStoreLocation** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Set-CsConfigurationStoreLocation** não retorna nenhum objeto ou valor.

## Consulte Também

#### Outros Recursos

[Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)  
[Remove-CsConfigurationStoreLocation](remove-csconfigurationstorelocation.md)

