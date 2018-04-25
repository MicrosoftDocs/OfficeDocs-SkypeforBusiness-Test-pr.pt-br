---
title: Set-CsAnalogDevice
TOCTitle: Set-CsAnalogDevice
ms:assetid: b05e729e-cdef-4c78-8ce7-b183c3208a93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412843(v=OCS.15)
ms:contentKeyID: 49307804
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsAnalogDevice

 

_**Tópico modificado em:** 2015-03-09_

Modifica um dispositivo existente no conjunto de dispositivos analógicos que podem ser gerenciados usando o Lync Server. Um dispositivo analógico é um telefone ou outro dispositivo conectado à PSTN (rede telefônica pública comutada). Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsAnalogDevice -Identity <UserIdParameter> [-AnalogFax <$true | $false>] [-Confirm [<SwitchParameter>]] [-DisplayName <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-Gateway <Fqdn>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 altera o valor da propriedade LineUri do dispositivo analógico com Identity CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com.

    Set-CsAnalogDevice -Identity "CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com" -LineUri "TEL:+14255551298"

## EXEMPLO 2

O comando exibido no Exemplo 2 altera o gateway de todos os dispositivos analógicos que estejam usando o gateway 192.168.0.240 no momento. Para realizar essa tarefa, p cmdlet **Get-CsAnalogDevice** é chamado com o parâmetro Filter; o valor de filtro {Gateway -eq "192.168.0.240"} garante que apenas dispositivos com Gateway igual a (-eq) 192.168.0.240 sejam retornados. Este conjunto é então direcionado para o cmdlet **Set-CsAnalogDevice**, que seleciona cada item no conjunto e altera o valor da propriedade Gateway para 192.168.1.100.

    Get-CsAnalogDevice -Filter {Gateway -eq "192.168.0.240"} | Set-CsAnalogDevice -Gateway "192.168.1.100"

## Descrição detalhada

Dispositivos analógicos incluem telefones, aparelhos de fax, modems e dispositivos TTY/TDD (para comunicação de surdos) conectados à PSTN (rede telefônica pública comutada). Ao contrário de dispositivos que tiram proveito do Enterprise Voice (ou seja, a solução de VoIP oferecida pela Microsoft), os dispositivos analógicos não transmitem informações usando pacotes digitais. Em vez disso, as informações são transmitidas usando um sinal contínuo. Esse sinal costuma ser chamado de sinal analógico, de onde vem o termo "dispositivos analógicos".

Para permitir que administradores gerenciem dispositivos analógicos, o Lync Server permite associar dispositivos analógicos a objetos de contato do Active Directory. Depois que um dispositivo é associado a um objeto de contato, é possível gerenciar o dispositivo analógico atribuindo diretivas e planos de discagem ao contato.

O cmdlet **Set-CsAnalogDevice** oferece uma maneira de modificar as propriedades de objetos de contato associados a dispositivos analógicos. Por exemplo, é possível alterar o nome para exibição do Active Directory do contato ou a linha URI associada ao dispositivo.

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsAnalogDevice** localmente: RTCUniversalUserAdmins. Permissões para executar este cmdlet para sites específicos ou UOs (unidades organizacionais) do Active Directory específicas podem ser atribuídas com o cmdlet **Grant-CsOUPermission**. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) a que esse cmdlet foi atribuído (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsAnalogDevice"}

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
<td><p>UserIdParameter</p></td>
<td><p>Identificador exclusivo para o dispositivo analógico a ser modificado. Os dispositivos analógicos são identificados usando o nome diferenciado do Active Directory do objeto de contato associado. Por padrão, dispositivos analógicos usam um GUID (identificador global exclusivo) como nome comum, ou seja, os dispositivos geralmente terão uma Identidade semelhante a esta: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Isso significa que pode ser mais fácil modificar os dispositivos analógicos usando o cmdlet <strong>Get-CsAnalogDevice</strong> para retornar os objetos de dispositivos analógicos e direcionar esses objetos para o cmdlet <strong>Set-CsAnalogDevice</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>AnalogFax</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Defina como True ($True) se o dispositivo analógico for um aparelho de fax. Defina como False ($False) se o dispositivo não for um aparelho de fax.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Configura o nome para exibição no Active Directory do dispositivo analógico.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Número de telefone exibido no Lync. A propriedade DisplayNumber pode ser formatada conforme a sua preferência; por exemplo, 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; etc.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Fqdn</p></td>
<td><p>Permite sua conexão ao controlador de domínio especificado para modificar as informações de contato. Para conectar a um determinado controlador de domínio, inclua o parâmetro DomainController seguido pelo nome de computador (por exemplo, atl-mcs-001) ou o seu FQDN (nome de domínio totalmente qualificado); por exemplo, atl-mcs-001.litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Quando definido como True ($True), o dispositivo analógico pode ser usado com o Lync.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se o objeto de contato do dispositivo analógico foi habilitado ou não para o Enterprise Voice, a solução de protocolo VoIP oferecida pela Microsoft. Com o Enterprise Voice, chamadas telefônicas podem ser feitas usando a Internet em vez da rede telefônica padrão.</p></td>
</tr>
<tr class="odd">
<td><p><em>ExchangeArchivingPolicy</em></p></td>
<td><p>Opcional</p></td>
<td><p>ExchangeArchivingPolicyOptionsEnum</p></td>
<td><p>Indica se as sessões de mensagem instantânea do contato foram arquivadas. Os valores permitidos são:</p>
<p>* Uninitialized</p>
<p>* UseLyncArchivingPolicy</p>
<p>* ArchivingToExchange</p>
<p>* NoArchiving</p></td>
</tr>
<tr class="even">
<td><p><em>Gateway</em></p></td>
<td><p>Opcional</p></td>
<td><p>Fqdn</p></td>
<td><p>Endereço IP do gateway PSTN a ser usado pelo dispositivo analógico.</p></td>
</tr>
<tr class="odd">
<td><p><em>LineURI</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Número de telefone do dispositivo analógico. A linha URI deve ser especificada usando o formato E.164 e levar o prefixo &quot;TEL:&quot; . Por exemplo: TEL:+14255551297. Qualquer número de ramal deve ser adicionado ao fim da linha URI; por exemplo: TEL:+14255551297; ext=51297.</p></td>
</tr>
<tr class="even">
<td><p><em>PassThru</em></p></td>
<td><p>Opcional</p></td>
<td><p>witchParameter</p></td>
<td><p>Retorna um objeto representando o telefone de área comum.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Identificador exclusivo que permite que o dispositivo analógico se comunique com dispositivos SIP como o Lync 2013. O endereço SIP deve levar o prefixo &quot;sip:&quot;. Por exemplo: sip:bldg14lobby@litwareinc.com.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact. O cmdlet **Set-CsAnalogDevice** aceita instâncias por pipeline do objeto de dispositivo analógico.

## Tipos de retorno

Por padrão, o cmdlet **Set-CsAnalogDevice** não retorna nenhum objeto ou valor. No entanto, se o parâmetro PassThru for incluído, o cmdlet retornará instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADAnalogDeviceContact.

## Consulte Também

#### Outros Recursos

[Get-CsAnalogDevice](get-csanalogdevice.md)  
[Move-CsAnalogDevice](move-csanalogdevice.md)  
[New-CsAnalogDevice](new-csanalogdevice.md)  
[Remove-CsAnalogDevice](remove-csanalogdevice.md)

