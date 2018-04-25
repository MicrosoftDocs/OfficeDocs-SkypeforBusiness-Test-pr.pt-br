---
title: Remove-CsConfigurationStoreLocation
TOCTitle: Remove-CsConfigurationStoreLocation
ms:assetid: 141be225-c6e4-4377-913b-ba61528929d4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398214(v=OCS.15)
ms:contentKeyID: 49305965
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsConfigurationStoreLocation

 

_**Tópico modificado em:** 2015-03-09_

Remove o ponto de controle de serviço do Active Directory correspondente ao Repositório de Gerenciamento Central. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsConfigurationStoreLocation [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando apresentado no Exemplo 1 remove o ponto de controle de serviço do Active Directory correspondente ao Repositório de Gerenciamento Central. Para restaurar esse SCP (ou para criar um novo SCP), deve-se executar o cmdlet **Set-CsConfigurationStoreLocation**.

    Remove-CsConfigurationStoreLocation

## EXEMPLO 2

O Exemplo 2 também remove o ponto de controle de serviço do Active Directory correspondente ao Repositório de Gerenciamento Central. Além disso, para excluir o SCP, este comando registra no arquivo de registro C:\\Logs\\Store\_Location.html as informações sobre o sucesso (ou falha) da operação. Para criar esse arquivo de registro, o comando utiliza o parâmetro Report, seguido do caminho do arquivo de registro no qual devem se registrar as informações. Se esse arquivo já existir, seu conteúdo será sobrescrito ao se executar o comando. Se o arquivo não existir, ele será criado ao se executar o comando.

    Remove-CsConfigurationStoreLocation -Report C:\Logs\Store_Location.html

## Descrição detalhada

O Serviços de Domínio Active Directory usa pontos de controle de serviço (SCPs) para ajudar os computadores a localizar serviços. Por exemplo: quando se instala o Lync Server, cria-se um SCP, que fornece informações de localização para o Repositório de Gerenciamento Central que é usado para manter dados do Lync Server. Os computadores que precisam de acesso ao banco de dados se conectam ao Active Directory e usam as informações contidas no SCP para ajudá-los a localizar o computador correto e a instância correta do SQL Server.

Conforme observado, quando se instala o Lync Server, cria-se automaticamente um para o Repositório de Gerenciamento Central. Normalmente, não se deve excluir esse SCP, pois, se ele for excluído, os computadores não conseguirão localizar o banco de dados. Entretanto, pode haver momentos (talvez na resolução de um problema) em que será necessário excluir o SCP. Para isso, use o cmdlet **Remove-CsConfigurationStoreLocation**. Depois que o SCP tiver sido excluído, será possível recriá-lo (ou criar um novo ponto de controle de serviço), utilizando-se o cmdlet **Set-CsConfigurationStoreLocation**.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Remove-CsConfigurationStoreLocation**: RTCUniversalServerAdmins.

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
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>Nome de domínio totalmente qualificado (FQDN) de um controlador de domínio no qual estão armazenadas as definições globais. Se as definições globais estiverem armazenadas no contêiner Sistema do Active Directory, este parâmetro deverá apontar para o controlador de domínio raiz. Se as configurações globais estiverem armazenadas no contêiner Configuração, qualquer controlador de domínio poderá ser utilizado e este parâmetro poderá ser omitido.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar o caminho do arquivo de log criado ao se executar o cmdlet. Por exemplo: -Report &quot;C:\Logs\ConfigurationStore.html&quot;</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Remove-CsConfigurationStoreLocation** não aceita entradas canalizadas.

## Tipos de retorno

O cmdlet **Remove-CsConfigurationStoreLocation** não retorna nenhum objeto ou valor.

## Consulte Também

#### Outros Recursos

[Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

