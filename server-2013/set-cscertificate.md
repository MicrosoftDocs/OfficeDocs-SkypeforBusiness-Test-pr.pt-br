---
title: Set-CsCertificate
TOCTitle: Set-CsCertificate
ms:assetid: 6da0be05-b257-4258-9d6d-7ddf283f1038
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398518(v=OCS.15)
ms:contentKeyID: 49307038
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCertificate

 

_**Tópico modificado em:** 2015-03-09_

Permite que você atribua um certificado a um servidor ou a uma função de servidor do Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsCertificate -Reference <CertificateReference> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Set-CsCertificate -Identity <XdsIdentity> -Path <String> -Type <CertType[]> [-Password <String>] <COMMON PARAMETERS>

    Set-CsCertificate -Thumbprint <String> -Type <CertType[]> [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-Confirm [<SwitchParameter>]] [-EffectiveDate <DateTime>] [-Force <SwitchParameter>] [-Report <String>] [-Roll <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 atribui o certificado com impressão digital igual a B142918E463981A76503828BB1278391B716280987B à função WebServicesExternal no computador local.

    Set-CsCertificate -Type WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"

## EXEMPLO 2

O Exemplo 2 atribui o certificado com impressão digital igual a B142918E463981A76503828BB1278391B716280987B a três funções diferentes no computador local: Default, WebServicesInternal e WebServicesExternal.

    Set-CsCertificate -Type Default, WebServicesInternal, WebServicesExternal -Thumbprint "B142918E463981A76503828BB1278391B716280987B"

## Descrição detalhada

O Lync Server usa certificados para que servidores e funções de servidores verifiquem suas identidades; por exemplo, um Servidor de Borda usa certificados para verificar se o computador com o qual está se comunicando realmente é um Servidor Front-End e vice-versa. Para implementar integralmente o Lync Server, você precisará ter os certificados apropriados atribuídos às funções de servidor apropriadas.

O cmdlet **Set-CsCertificate** permite que os administradores atribuam um certificado a um servidor ou a uma função de servidor. Observe que você só pode atribuir certificados que já tenham sido configurados para uso no Lync Server. Para identificar certificados disponíveis para atribuição, use o cmdlet **Get-CsCertificate**.

Quem pode executar este cmdlet: Você deve ser um administrador local para executar o cmdlet **Set-CsCertificate** localmente. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCertificate"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Quando definido como Global, permite que o certificado funcione no escopo global. Os certificados globais serão automaticamente copiados e distribuídos para os computadores apropriados.</p></td>
</tr>
<tr class="even">
<td><p><em>Path</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Caminho completo para o arquivo de certificado .PFX.</p></td>
</tr>
<tr class="odd">
<td><p><em>Reference</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertificateReference</p></td>
<td><p>Referência de objeto para um certificado configurado para uso no Lync Server. O comando a seguir retorna uma referência de objeto (a variável $x) representando um certificado com a impressão digital B142918E463981A76503828BB1278391B716280987B:</p>
<p>$x = Get-CsCertificate | Where-Object {$_.Thumbprint –eq &quot;B142918E463981A76503828BB1278391B716280987B&quot;.</p></td>
</tr>
<tr class="even">
<td><p><em>Thumbprint</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.String</p></td>
<td><p>Identificador exclusivo para o certificado. A impressão digital de um certificado é semelhante ao seguinte: B142918E463981A76503828BB1278391B716280987B.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Tipo de certificado que está sendo atribuído. Os tipos de certificado incluem, mas não se limitam a:</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>iPhoneAPNService</p>
<p>iPadAPNService</p>
<p>MPNService</p>
<p>PICWebService (apenas Microsoft Lync Online 2010)</p>
<p>ProvisionService (apenas Microsoft Lync Online 2010)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>Por exemplo, esta sintaxe atribui o certificado padrão (Default): -Type Default.</p>
<p>É possível especificar mais de um tipo em um mesmo comando, separando os tipos de certificados por vírgulas:</p>
<p>-Type Internal,External,Default</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>EffectiveDate</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.DateTime</p></td>
<td><p>Data e hora de quando o certificado pode ser usado pela primeira vez. Por exemplo, para configurar um certificado para primeiro uso às 8h do dia 31.07.12, use esta sintaxe no servidor executando sob as configurações de Região e Idioma Inglês EUA:</p>
<p>-EffectiveTime &quot;7/31/2012 8:00 AM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não fatal que possa surgir ao executar o comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Password</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Senha para o certificado.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite que você registre informações detalhadas sobre os procedimentos realizados pelo cmdlet <strong>Set-CsCertificate</strong>. O valor do parâmetro deve ser o caminho completo até o arquivo HTML a ser gerado; por exemplo: -Report C:\Logs\Certificates.html. Se o arquivo especificado já existir, ele será automaticamente substituído com a nova informação.</p></td>
</tr>
<tr class="odd">
<td><p><em>Roll</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Permite que você atualize o certificado especificado na data e hora especificadas pelo parâmetro EffectiveDate; isso permite que você especifique uma data e hora para tornar o novo certificado o certificado principal. Observe que seu comando falhará se você especificar o parâmetro Roll sem incluir o parâmetro EffectiveDate.</p></td>
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

Microsoft.Rtc.Management.Deployment.CertificateReference.

## Tipos de retorno

O cmdlet **Set-CsCertificate** não retorna quaisquer valores ou objetos.

## Consulte Também

#### Outros Recursos

[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)

