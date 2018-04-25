---
title: Import-CsCertificate
TOCTitle: Import-CsCertificate
ms:assetid: 87bdafce-f4b9-4c44-ad8f-86c2deb680a4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398688(v=OCS.15)
ms:contentKeyID: 49307365
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Import-CsCertificate

 

_**Tópico modificado em:** 2015-03-09_

Importa um certificado para uso com o Lync Server. Se o certificado não for adquirido utilizando-se o cmdlet **Request-CsCertificate**, o certificado deve ser importado antes de ser atribuído a uma função de servidor do Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Import-CsCertificate -Identity <XdsIdentity> -Type <CertType[]> <COMMON PARAMETERS>

    Import-CsCertificate [-PrivateKeyExportable <$true | $false>] <COMMON PARAMETERS>

    COMMON PARAMETERS: -Path <String> [-Confirm [<SwitchParameter>]] [-EffectiveDate <DateTime>] [-Force <SwitchParameter>] [-Password <String>] [-Report <String>] [-Roll <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 importa o certificado C:\\Certificates\\WebServer.pfx. Depois que o comando tiver sido concluído, o certificado estará disponível para ser atribuído a uma função do servidor.

    Import-CsCertificate -Path "C:\Certificates\WebServer.pfx" -PrivateKeyExportable $True

## Descrição detalhada

O Lync Server usa certificados como uma forma de servidores e funções de servidores para verificar as suas identidades; por exemplo, um Servidor de Bordautiliza certificados para verificar se o computador com o qual está se comunicando é realmente um Servidor Front-End e vice-versa. Para implementar plenamente o Lync Server é necessário que os certificados relevantes estejam atribuídos às funções de servidor adequadas.

Para um certificado ser atribuído a uma função Lync Server, é necessário que os certificados sejam conhecidos pelo Lync Server. O cmdlet **Request-CsCertificate** permite que você faça solicitações online e offline para novos certificados. Se uma solicitação online for feita, o certificado será baixado e salvo automaticamente no repositório de certificados; igualmente importante, ele estará imediatamente disponível para uso pelo Lync Server. Se uma solicitação offline for feita, um arquivo de certificado será enviado para você. Neste momento, é possível utilizar o cmdlet **Import-CsCertificate** para importar o certificado, um processo que o torna disponível para atribuição a uma função do servidor do Lync Server.

Quem pode executar esse cmdlet: É necessário que você seja um administrador local para executar o cmdlet **Import-CsCertificate** localmente. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Import-CsCertificate"}

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
<td><p>Caminho completo do arquivo de certificado a ser importado. Por exemplo: –Path &quot;C:\Certificates\WebServer.cer&quot;.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Tipo de certificado que está sendo solicitado. Os tipos de certificado incluem, mas não se limitam a:</p>
<p>* AccessEdgeExternal</p>
<p>* AudioVideoAuthentication</p>
<p>* DataEdgeExternal</p>
<p>* Default</p>
<p>* External</p>
<p>* Internal</p>
<p>* iPadAPNService</p>
<p></p>
<p>* iPhoneAPNService</p>
<p>* LogRetentionService</p>
<p>* MPNService</p>
<p>* OAuthTokenIssuer</p>
<p>* PICWebService</p>
<p>* ProvisionService</p>
<p>* SMPDNSWebService</p>
<p>* TenantAdmin</p>
<p>* UpgradeEngineService</p>
<p>* WebServicesExternal</p>
<p>* WebServicesInternal</p>
<p>* WsFedTokenTransfer</p>
<p>* XMPPServer</p></td>
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
<td><p>Data e hora quando o certificado pode ser usado pela primeira vez. Por exemplo, para configurar um certificado para o primeiro uso as 8:00 horas em 31 de julho de 2012, use essa sintaxe em um servidor executando nas configurações de Idioma e Região Inglês dos EUA:</p>
<p>-EffectiveTime &quot;7/31/2012 8:00 AM&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Password</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Senha associada ao arquivo de certificado.</p></td>
</tr>
<tr class="even">
<td><p><em>PrivateKeyExportable</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Boolean</p></td>
<td><p>Quando ele for definido como True, garante que a parte de chave privada do certificado pode ser lida pela conta de serviços de rede.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar o caminho do arquivo de log criado ao se executar o cmdlet. Por exemplo: -Report &quot;C:\Logs\Certificates.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Roll</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Permite atualizar o certificado especificado na data e hora especificada pelo parâmetro EffectiveDate; isso permite especificar uma data e hora quando o novo certificado se tornar o certificado principal. Observe que seu comando falhará se você especificar o parâmetro Roll sem incluir o parâmetro EffectiveDate.</p></td>
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

Nenhuma. O cmdlet**Import-CsCertificate** não aceita entrada em pipeline.

## Tipos de retorno

Nenhuma.

## Consulte Também

#### Outros Recursos

[Get-CsCertificate](get-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

