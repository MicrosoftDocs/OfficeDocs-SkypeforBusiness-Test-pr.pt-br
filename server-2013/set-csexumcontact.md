---
title: Set-CsExUmContact
TOCTitle: Set-CsExUmContact
ms:assetid: c0fe0fdc-6fea-4334-8645-24ffd494db07
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412944(v=OCS.15)
ms:contentKeyID: 49307989
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsExUmContact

 

_**Tópico modificado em:** 2015-03-09_

Modifica um objeto de contato do Atendedor Automático e Acesso de Assinante do Unificação de Mensagens (UM) do Exchange hospedado. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsExUmContact -Identity <UserIdParameter> [-AutoAttendant <$true | $false>] [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

Este exemplo define a propriedade AutoAttendant do contato do UM do Exchange com o endereço SIP exumsa4@fabrikam.com como True. Primeiro o cmdlet **Get-CsExUmContact** é chamado para recuperar o objeto de contato (o nome de exibição do contato no Active Directory, o nome principal do usuário do contato ou o nome de logon do contato também poderiam ter sido usados). Este comando recupera um contato com a Identidade fornecida. Este contato será então passado para o cmdlet **Set-CsExUmContact**, onde o parâmetro AutoAttendant é definido como True.

    Get-CsExUmContact -Identity sip:exumsa4@fabrikam.com | Set-CsExUmContact -AutoAttendant $True

## EXEMPLO 2

Este exemplo é idêntico ao Exemplo 1, mas em vez de recuperar o contato chamando o cmdlet **Get-CsExUmContact** e direcionando o objeto para o cmdlet **Set-CsExUmContact**, fornecemos ao cmdlet **Set-CsExUmContact** a Identidade do contato que desejamos modificar. Observe o formato da Identidade: nesse caso, é usado o nome diferenciado completo do objeto de contato, que inclui um GUID gerado automaticamente (no momento em que o contato foi criado). Em seguida, o parâmetro AutoAttendant do contato é definido como True.

    Set-CsExUmContact -Identity "CN={1bf6208d-2847-45d0-828f-636f14da858b},OU=ExUmContacts,DC=litwareinc,DC=com" -AutoAttendant $True

## Descrição detalhada

O Lync Server funciona com o UM do Exchange para fornecer vários recursos relacionadas a voz, incluindo o Atendedor Automático e o Acesso de Assinante. Quando o UM do Exchange é disponibilizado como um serviço hospedado (e não em uma implementação local), os objetos de contato devem ser criados usando o Windows PowerShell, para aplicar as funcionalidades Acesso de Assinante e Atendedor Automático. Esses objetos são criados chamando o cmdlet **New-CsExUmContact** e podem serem modificados posteriormente usando o cmdlet **Set-CsExUmContact**.

O modo mais fácil de usar este cmdlet consiste em chamar primeiro o cmdlet **Get-CsExUmContact** para recuperar uma instância do objeto de contato que você deseja modificar. Simplesmente direcione a saída do comando do cmdlet **Get-CsExUmContact** para o cmdlet **Set-CsExUmContact** e atribua valores aos parâmetros das propriedades que você deseja modificar (para detalhes, consulte a seção Exemplos, neste tópico). Como alternativa, é possível chamar o cmdlet **Set-CsExUmContact**, passando a ele a Identidade do objeto de contato que você deseja modificar.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Set-CsExUmContact** localmente: RTCUniversalUserAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) às quais esse cmdlet foi atribuído (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsExUmContact"}

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
<td><p>O identificador exclusivo do objeto de contato a ser modificado. As Identidades de contato podem ser especificadas usando um de quatro formatos: 1) O endereço SIP do contato, 2) o Nome Principal Universal do usuário (UPN), 3) o nome de domínio do contato e nome de logon, na forma domínio\logon (por exemplo, litwareinc\exum1) e 4) o nome de exibição do Active Directory do contato (por exemplo, Atendedor Automático da Equipe).</p>
<p>Tipo de dados completos: Microsoft.Rtc.Management.AD.UserIdParameter</p></td>
</tr>
<tr class="even">
<td><p><em>AutoAttendant</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Defina o parâmetro como True se o objeto de contato for um Atendedor Automático. Por padrão, esse parâmetro é definido como False.</p></td>
</tr>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>Uma descrição deste contato. A descrição destina-se ao uso, por administradores, para identificar o tipo de contato (Atendedor Automático ou Acesso de Assinante), o local, provedor ou qualquer outra informação que identifique o objetivo de cada contato do UM do Exchange.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>O número de telefone do contato. Os números de telefone de cada contato devem ser exclusivos (não pode haver dois contatos do UM do Exchange com o mesmo número de telefone). Alterar este valor também modifica o valor da propriedade LineURI.</p>
<p>Este valor pode começar com um sinal de mais (+) e pode conter qualquer número de dígitos. O primeiro dígito não pode ser zero.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Fqdn</p></td>
<td><p>Permite especificar um controlador de domínio. Se nenhum controlador de domínio for especificado, será utilizado o primeiro disponível.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se o contato foi habilitado ou não para o Lync Server. A definição deste parâmetro como False desabilitará o contato, e o Atendente Automático ou Acesso de Assinante associado a este contato deixará de funcionar.</p>
<p>Se uma conta for desabilitada usando o parâmetro Enabled, as informações associadas a esta conta (incluindo as políticas atribuídas de correio de voz hospedadas) serão mantidas. Se a conta for reabilitada posteriormente usando o parâmetro Enabled, as informações sobre a conta associada serão restauradas.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boolean</p></td>
<td><p>Indica se o contato foi habilitado no Enterprise Voice. Se este valor for definido como False, o recurso Atendedor Automático ou Acesso de Assinante associado a este contato não estará mais disponível.</p></td>
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
<td><p><em>PassThru</em></p></td>
<td><p>Opcional</p></td>
<td><p>witchParameter</p></td>
<td><p>Retorna os resultados do comando. Por padrão, esse cmdlet não gera saída.</p></td>
</tr>
<tr class="odd">
<td><p><em>SipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>String</p></td>
<td><p>O endereço SIP do contato. Esse deve ser um novo endereço que não exista como um usuário ou contato no Serviços de Domínio Active Directory.</p>
<p>A alteração deste valor também modificará o endereço SIP armazenado na propriedade OtherIpPhone.</p>
<p>O SipAddress pode ser usado como o valor de Identidade para os comandos do cmdlet <strong>Get-CsExUmContact</strong> para recuperar contatos específicos. Ao chamar este cmdlet, o novo SipAddress será usado; as consultas para o antigo endereço SIP não devolverão um objeto.</p></td>
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

Objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact. Aceita entradas direcionadas dos objetos de contato do UM do Exchange.

## Tipos de retorno

Esse cmdlet modifica um objeto do tipo Microsoft.Rtc.Management.ADConnect.Schema.OCSADExUmContact. Quando o parâmetro PassThru é utilizado, ele também retornará um objeto desse tipo.

## Consulte Também

#### Outros Recursos

[New-CsExUmContact](new-csexumcontact.md)  
[Remove-CsExUmContact](remove-csexumcontact.md)  
[Get-CsExUmContact](get-csexumcontact.md)  
[Move-CsExUmContact](move-csexumcontact.md)

