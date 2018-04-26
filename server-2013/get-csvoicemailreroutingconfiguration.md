---
title: Get-CsVoicemailReroutingConfiguration
TOCTitle: Get-CsVoicemailReroutingConfiguration
ms:assetid: 25e401eb-6a84-468f-b0eb-5b794f20b5bc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425732(v=OCS.15)
ms:contentKeyID: 49306164
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Get-CsVoicemailReroutingConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Recupera configurações que oferecem a números de telefone da PSTN (rede telefônica pública comutada) acesso aos recursos de Atendedor Automático e Acesso de Assinante do UM do Exchange. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Get-CsVoicemailReroutingConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

    Get-CsVoicemailReroutingConfiguration [-Filter <String>] <COMMON PARAMETERS>

    COMMON PARAMETERS: [-LocalStore <SwitchParameter>]

## Exemplos

## EXEMPLO 1

Este exemplo recupera todas as configurações de reencaminhamento de caixa postal definidas nesta implementação do Lync Server. Por exemplo, se existirem três escritórios de filiais onde um Aparelho de Filial Persistente foi implementado, o comando retornará três conjuntos de configurações de reencaminhamento de caixa postal.

    Get-CsVoicemailReroutingConfiguration

## EXEMPLO 2

Este exemplo recupera as configurações de reencaminhamento de caixa postal para o site BranchOffice\_Portland.

    Get-CsVoicemailReroutingConfiguration -Identity site:BranchOffice_Portland

## EXEMPLO 3

Este exemplo recupera todas as configurações de reencaminhamento de caixa postal de todos os sites com nomes começando com a cadeia de caracteres BranchOffice (por exemplo, BranchOffice\_Portland, BranchOffice\_Sacramento).

    Get-CsVoicemailReroutingConfiguration -Filter *:BranchOffice*

## EXEMPLO 4

Este exemplo recupera todas as configurações de reencaminhamento de caixa postal que não estejam habilitadas. A primeira parte do comando é uma chamada ao cmdlet **Get-CsVoicemailReroutingConfiguration**, que recupera uma coleção de todas as configurações de reencaminhamento de caixa postal. Esta coleção é então canalizada para o cmdlet **Where-Object**. O cmdlet **Where-Object** restringe a coleção para incluir apenas as configurações que tenham uma propriedade Enabled igual a (-eq) False.

    Get-CsVoicemailReroutingConfiguration | Where-Object {$_.Enabled -eq $False}

## Descrição detalhada

Este cmdlet recupera configurações que determinam para onde as chamadas para o Atendedor Automático e o Acesso de Assinante são encaminhadas quando a conectividade IP do Lync Server no site da filial do servidor de UM do Exchange localizado no data center não estiver disponível.

O Atendedor Automático e o Acesso de Assinante são recursos do UM do Exchange. O recurso Atendedor Automático oferece reconhecimento de voz e DTMF (controle de discagem por tom) para que chamadores externos possam navegar no sistema telefônico de uma empresa e sejam levados ao departamento ou funcionário desejado; ou, no caso do Modo de Recebimento de Mensagens, aceita mensagens para os usuários. Recomendamos a utilização do reencaminhamento de voz no Modo de Recebimento de Mensagens. O Acesso de Assinante permite que usuários internos acessem suas caixas de correio do Microsoft Outlook a partir de um telefone. Os números fornecidos por essas configurações permitem que os chamadores deixem mensagens de voz para usuários do Enterprise Voice (a configuração AutoAttendantNumber) e que esses usuários recuperem a mensagem de voz mesmo se a conectividade IP da implementação do Lync Server no site remoto ao UM do Exchange no data center não estiver disponível (a configuração SubscriberAccessNumber).

Chamado sem parâmetros, este cmdlet retorna todas as configurações de reencaminhamento de caixa postal.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Get-CsVoicemailReroutingConfiguration** localmente: RTCUniversalUserAdmins, RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Get-CsVoicemailReroutingConfiguration"}

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
<td><p>O parâmetro Filter permite recuperar as configurações de um conjunto específico de sites com base na correspondência de curingas.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>O identificador único da configuração que você deseja recuperar. Para este cmdlet, a identidade será Global ou Site:&lt;nomedosite&gt;, onde &lt;nomedosite&gt; é o nome do site ao qual as configurações se aplicam.</p></td>
</tr>
<tr class="odd">
<td><p><em>LocalStore</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Recupera a configuração de encaminhamento de mensagens de voz a partir da réplica local do Repositório de Gerenciamento Central, e não do Repositório de Gerenciamento Central em si.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma.

## Tipos de retorno

Recupera um ou mais objetos do tipo Microsoft.Rtc.Management.WritableConfig.Settings.ExumRouting.VoicemailReroutingConfiguration.

## Consulte Também

#### Outros Recursos

[New-CsVoicemailReroutingConfiguration](new-csvoicemailreroutingconfiguration.md)  
[Remove-CsVoicemailReroutingConfiguration](remove-csvoicemailreroutingconfiguration.md)  
[Set-CsVoicemailReroutingConfiguration](set-csvoicemailreroutingconfiguration.md)

