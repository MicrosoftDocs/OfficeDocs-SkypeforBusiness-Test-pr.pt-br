---
title: Get-CsCertificate
TOCTitle: Get-CsCertificate
ms:assetid: 15b8f019-1d00-4389-9abe-18deb8cbf2ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398227(v=OCS.15)
ms:contentKeyID: 49305986
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsCertificate

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre certificados nos computadores locais que tenham sido configurados para uso com o Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsCertificate [-Identity <XdsIdentity>] [-Report <String>] [-Type <CertType[]>]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 retorna informações sobre os certificados atribuídos no momento a componentes do Lync Server. Isso é feito chamando-se o cmdlet **Get-CsCertificate** sem parâmetros adicionais.

    Get-CsCertificate

## EXEMPLO 2

O Exemplo 2 recupera todos os certificados do Lync Server usados para serviços Web internos. Para fazer isso, o parâmetro Type é incluído, junto com o valor de parâmetro WebServicesInternal.

    Get-CsCertificate -Type WebServicesInternal

## EXEMPLO 3

O Exemplo 3 retorna todos os certificados do Lync Server que expiram antes de 1º de setembro de 2011. Para executar esta tarefa, o comando primeiro usa o cmdlet **Get-CsCertificate** para retornar uma coleção de todos os certificados do Lync Server em uso atualmente. Em seguida, a coleção é canalizada para o cmdlet **Where-Object**, que seleciona apenas os certificados que expirem antes de 1º de setembro de 2011. A data especificada neste exemplo (9/1/2011) usa o formato Inglês (Estados Unidos) para valores de data e hora. As datas devem ser especificadas em um formato compatível com suas opções regionais e de idioma.

    Get-CsCertificate | Where-Object {$_.NotAfter -lt "9/1/2012"}

## EXEMPLO 4

O Exemplo 4 retorna informações sobre todos os certificados do Lync Server emitidos pela CA (autoridade de certificação) MyCa. Para fazer isso, o comando primeiro chama o cmdlet **Get-CsCertificate** sem nenhum parâmetro para retornar uma coleção de todos os certificados em uso no momento. Em seguida, essa coleção é canalizada para o cmdlet **Where-Object**, que seleciona todos os certificados que tenham a propriedade Issuer (emissor) igual a (-eq) "Cn=MyCa".

    Get-CsCertificate | Where-Object {$_.Issuer -eq "Cn=MyCa"}

## EXEMPLO 5

O comando mostrado no Exemplo 5 retorna todos os certificados do Lync Server nos quais a propriedade Subject tenha sido definida como CN=atl-cs-001.litwareinc.com. Para isso, usa-se o cmdlet **Get-CsCertificate**, para retornar uma coleção de todos os certificados do Lync Server, e canaliza-se essa coleção para o cmdlet **Where-Object**. O cmdlet **Where-Object**, por sua vez, seleciona apenas os certificados com a propriedade Subject igual a "CN=atl-cs-001.litwareinc.com".

    Get-CsCertificate | Where-Object {$_.Subject -eq "CN=atl-cs-001.litwareinc.com"}

## Descrição detalhada

O Lync Server usa certificados para que servidores e funções de servidores verifiquem suas identidades; por exemplo, um Servidor de Borda usa certificados para verificar se o computador com o qual está se comunicando realmente é um Servidor Front-End e vice-versa. Para implementar completamente o Lync Server, é preciso ter os certificados apropriados atribuídos às funções de servidor apropriadas.

O cmdlet **Get-CsCertificate** oferece uma forma de se obter informações detalhadas sobre os certificados que foram configurados para uso com o Lync Server. Observe que o cmdlet só retorna informações sobre certificados do Lync Server. Se um certificado não tiver sido configurado para uso com o Lync Server (usando o cmdlet **Set-CsCertificate**), esse certificado não será retornando quando o cmdlet **Get-CsCertificate** for executado.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsCertificate** localmente: RTCUniversalServerAdmins.

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
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Permite recuperar certificados configurados no escopo global (certificados globais são copiados e distribuídos para os computadores adequados). Use essa sintaxe para retornar informações sobre os certificados globais:</p>
<p>Get-CsCertificate –Identity &quot;global&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite a gravação de informações detalhadas sobre os procedimentos conduzidos pelo cmdlet <strong>Get-CsCertificate</strong>. O valor do parâmetro deve ser o caminho completo para o arquivo HTML que será gerado. Por exemplo: -Report C:\Logs\Certificates.html. Se o arquivo especificado já existir, ele será automaticamente substituído com a nova informação.</p></td>
</tr>
<tr class="odd">
<td><p><em>Type</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Tipo de certificado que está sendo solicitado. Os tipos de certificado incluem, mas não se limitam a:</p>
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
<p>Por exemplo, esta sintaxe retorna informações sobre o certificado padrão (Default): -Type Default.</p>
<p>É possível especificar mais de um tipo em um mesmo comando, separando os tipos de certificados por vírgulas:</p>
<p>-Type Internal,External,Default</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsCertificate** não aceita entradas canalizadas.

## Tipos de retorno

O cmdlet **Get-CsCertificate** retorna instâncias do objeto Microsoft.Rtc.Management.Deployment.CertificateReference.

## Consulte Também

#### Outros Recursos

[Import-CsCertificate](import-cscertificate.md)  
[Remove-CsCertificate](remove-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

