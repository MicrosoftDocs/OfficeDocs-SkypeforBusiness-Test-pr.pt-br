---
title: Get-CsProxyConfiguration
TOCTitle: Get-CsProxyConfiguration
ms:assetid: e4836619-026f-4df0-adbd-aa5216e36368
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399011(v=OCS.15)
ms:contentKeyID: 49308400
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsProxyConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre as definições de configuração do servidor de proxy em uso na organização. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsProxyConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsProxyConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 retorna uma coleção de todas as definições de configuração de proxy em uso na organização. Isso é realizado chamando o cmdlet **Get-CsProxyConfiguration** sem nenhum parâmetro.

    Get-CsProxyConfiguration

## EXEMPLO 2

No Exemplo 2, serão retornadas as informações sobre as definições de configuração de proxy que possuírem a Identidade service:EdgeServer:atl-cs-001.litwareinc.com. Como as identidades devem ser exclusivas, este comando nunca retornará mais do que uma coleção de definições.

    Get-CsProxyConfiguration -Identity "service:EdgeServer:atl-cs-001.litwareinc.com"

## EXEMPLO 3

O Exemplo 3 retorna informações sobre todas as configurações de proxy que foram definidas no escopo do site. Para isso, o comando chama o cmdlet **Get-CsProxyConfiguration** e o parâmetro Filter; o valor de filtro "service:\*" garante que apenas as configurações cuja Identidade começa com o valor de cadeia de caracteres "service:" são retornadas.

    Get-CsProxyConfiguration -Filter "service:*"

## EXEMPLO 4

O Exemplo 4 retorna informações sobre as definições de configuração de proxy que não permitem o uso de certificados de cliente como um mecanismo de autenticação. Para realizar esta tarefa, o comando usa primeiro o cmdlet **Get-CsProxyConfiguration** para retornar uma coleção de todas as definições de configuração de proxy em uso. Esta coleção é canalizada ao cmdlet **Where-Object**, que seleciona apenas as configurações cuja propriedade UseCertificateForClientToProxyAuth é igual a False.

    Get-CsProxyConfiguration | Where-Object {$_.UseCertificateForClientToProxyAuth -eq $False}

## EXEMPLO 5

O Exemplo 5 retorna todas as definições de configuração de proxy nas quais o tamanho máximo do corpo de uma mensagem do cliente é inferior a 5.000 quilobytes. Para isso, o comando chama primeiro o cmdlet **Get-CsProxyConfiguration** sem nenhum parâmetro. Isto retorna uma coleção de todas as definições de configuração de proxy em uso. Essa coleção é então canalizada ao cmdlet **Where-Object**, que seleciona apenas as configurações cuja propriedade MaxClientMessageBodySizeKb é inferior a 5.000 quilobytes.

    Get-CsProxyConfiguration | Where-Object {$_.MaxClientMessageBodySizeKb -lt 5000}

## Descrição detalhada

O Lync Server permite gerenciar os servidores proxy através de definições de configuração de servidor proxy. Essas definições, que podem ser aplicadas no escopo global e de serviço (embora apenas para os serviços do Servidor de Borda e de Registrador), permitem controlar itens como os protocolos de autenticação que podem ser utilizados pelos pontos de extremidade cliente e se a compactação será utilizada ou não nas conexões de servidor proxy de entrada e saída. Ao se instalar o Lync Server, é criada automaticamente uma coleção global de definições de configuração de servidor proxy. Conforme observado, é possível criar também coleções adicionais no escopo de serviço.

O cmdlet **Get-CsProxyConfiguration** permite retornar informações sobre qualquer definição de configuração do servidor proxy em uso pela organização.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Get-CsProxyConfiguration** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet tiver sido atribuído (inclusive qualquer função RBAC personalizada que tiver sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsProxyConfiguration"}

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
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Filter</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite utilizar caracteres curinga ao se especificar as definições de configuração de proxy a serem retornadas. Por exemplo, esta sintaxe retorna todas as definições configuradas no escopo de serviço: -Filter &quot;service:*&quot;.</p>
<p>Não é possível utilizar os parâmetros Filter e Identity no mesmo comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identificador exclusivo das definições de configuração do servidor de proxy a serem retornadas. Para retornar as definições globais, use essa sintaxe: -Identity global. Para retornar as definições configuradas no escopo do serviço, utilize uma sintaxe semelhante a esta: -Identity &quot;service:EdgeServer:atl-cs-001.litwareinc.com&quot;. Observe que não é possível utilizar caracteres curinga ao se especificar uma identidade. Se quiser (ou precisar) utilizar caracteres curinga, inclua o parâmetro –Filter no seu lugar.</p>
<p>Se esse parâmetro não for incluído, o cmdlet <strong>Get-CsProxyConfiguration</strong> retornará todas as definições de configuração do servidor de proxy atualmente em uso na organização.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera os dados de configuração de proxy na réplica local do Repositório de Gerenciamento Central, em vez do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Get-CsProxyConfiguration** não aceita a entrada por pipeline.

## Tipos de retorno

O cmdlet **Get-CsProxyConfiguration** retorna as instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Settings.SipProxy.ProxySettings.

## Consulte Também

#### Outros Recursos

[New-CsProxyConfiguration](new-csproxyconfiguration.md)  
[Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)  
[Set-CsProxyConfiguration](set-csproxyconfiguration.md)

