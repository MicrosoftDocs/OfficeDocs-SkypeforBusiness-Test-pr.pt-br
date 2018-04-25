---
title: Set-CsCommonAreaPhone
TOCTitle: Set-CsCommonAreaPhone
ms:assetid: 765ab74c-33ca-4b17-ba15-edb2fe559ebb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398579(v=OCS.15)
ms:contentKeyID: 49307150
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Set-CsCommonAreaPhone

 

_**Tópico modificado em:** 2015-03-09_

Modifica os valores de propriedade de um telefone de área comum gerenciado pelo Lync Server. Telefones de área comum são telefones localizados em lobbies de edifícios, lounges para funcionários e demais áreas nas quais possam ser utilizados por várias pessoas diferentes e para vários fins diferentes. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Set-CsCommonAreaPhone -Identity <UserIdParameter> [-Confirm [<SwitchParameter>]] [-Description <String>] [-DisplayName <String>] [-DisplayNumber <String>] [-DomainController <Fqdn>] [-Enabled <$true | $false>] [-EnterpriseVoiceEnabled <$true | $false>] [-ExchangeArchivingPolicy <Uninitialized | UseLyncArchivingPolicy | NoArchiving | ArchivingToExchange>] [-LineURI <String>] [-PassThru <SwitchParameter>] [-SipAddress <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O Exemplo 1 modifica o nome para exibição no Active Directory para o telefone de área comum com o número de telefone 1-425-555-6710. Para isso, o cmdlet **Get-CsCommonAreaPhone** é chamado inicialmente com o parâmetro Filter; o valor de filtro {LineUri -eq "tel:+14255556710"} limita os dados retornados ao telefone de área comum no qual a propriedade LineUri seja igual a tel:+14255556710. Em seguida, o objeto retornado é canalizado para o cmdlet **Set-CsCommonAreaPhone**, que define o valor da propriedade DisplayName como "Employee Lounge".

    Get-CsCommonAreaPhone -Filter {LineUri -eq "tel:+14255556710"} | Set-CsCommonAreaPhone -DisplayName "Employee Lounge"

## EXEMPLO 2

O comando mostrado no Exemplo 2 habilita todos os telefones de área comum configurados atualmente para uso na organização. Para executar esta tarefa, o comando chama o cmdlet **Get-CsCommonAreaPhone**, sem nenhum parâmetro, para retornar uma coleção de todos os telefones de área comum. Em seguida, essa coleção é redirecionada para o cmdlet **Set-CsCommonAreaPhone**, que seleciona cada item da coleção e define a propriedade Enabled como True.

    Get-CsCommonAreaPhone | Set-CsCommonAreaPhone -Enabled $True

## EXEMPLO 3

O Exemplo 3 adiciona uma descrição genérica a todos os telefones de área comum que não tenham um valor atribuído à propriedade Description. Para isso, o cmdlet **Get-CsCommonAreaPhone** é chamado com o parâmetro Filter; o valor de filtro {Description -eq $Null} garante que os únicos itens retornados sejam telefones de área comum nos quais a propriedade Description seja igual a um valor nulo. Em seguida, essa coleção filtrada é redirecionada para o cmdlet **Set-CsCommonAreaPhone**, que atribui a descrição genérica "Common area phone" a cada item da coleção.

    Get-CsCommonAreaPhone -Filter {Description -eq $Null} | Set-CsCommonAreaPhone -Description "Common area phone"

## Descrição detalhada

Telefones de área comum são telefones IP que não estão associados a um usuário individual. Em vez de estarem localizados no escritório de alguém, esses telefones geralmente estão localizados em lobbies de edifícios, cafeterias, lounges para funcionários, salas de reuniões e outros locais que possam receber um grande número de pessoas. Isso é um desafio de gerenciamento para os administradores: o uso de um telefone no Lync Server geralmente é mantido usando-se várias diretivas de voz e planos de discagem, atribuídos a usuários individuais. Os telefones de área comum não são atribuídos a usuários individuais.

Uma solução é criar objetos de contato do Active Directory para todos os seus telefones de área comum (esses objetos de contato podem ser criados com o cmdlet **New-CsCommonAreaPhone**). Assim como as contas de usuário, esses objetos de contato podem ser atribuídos a diretivas e planos de voz. Com isso, é possível manter o controle sobre os telefones de área comum mesmo que esses telefones não estejam associados a um usuário individual. Por exemplo, se você não quiser que as pessoas possam transferir ou estacionar chamadas em um telefone de área comum, crie uma diretiva de voz que proíba a transferência e o estacionamento de chamadas, e atribua essa diretiva ao telefone de área comum. (Ou, o que seria mais correto, atribuir essa diretiva ao objeto de contato que representa o telefone de área comum). Este comando atribui a diretiva de voz CommonAreaPhoneVoicePolicy a todos os seus telefones de área comum:

Get-CsCommonAreaPhone | Grant-CsVoicePolicy –PolicyName "CommonAreaPhoneVoicePolicy"

O cmdlet **Set-CsCommonAreaPhone** oferece uma maneira de modificar as propriedades de objetos de contato associados a telefones de área comum. Dentre outras coisas, é possível alterar o nome para exibição do Active Directory do contato ou a linha URI associada ao telefone. O parâmetro Enabled também pode ser usado para habilitar e desabilitar a conta para uso com o Lync Server.

Além disso, você pode configurar o "compartilhamento" de telefones de área comum usando os cmdlets CsClientPolicy. Quando um telefone é compartilhado, os usuários podem fazer logon no telefone usando suas credenciais do Lync Server. Entre outras coisas, isso permite que os usuários acessem facilmente seus contatos. Para obter mais informações, consulte o tópico de ajuda referente ao cmdlet [Set-CsClientPolicy](set-csclientpolicy.md).

Quem pode executar este cmdlet: Por padrão, membros dos seguintes grupos estão autorizados a executar o cmdlet **Set-CsCommonAreaPhone** localmente: RTCUniversalUserAdmins. Permissões para executar este cmdlet para sites específicos ou OUs (unidades organizacionais) do Active Directory específicas podem ser atribuídas com o cmdlet **Grant-CsOUPermission**. Para retornar uma lista de todas as funções do RBAC (controle de acesso baseado na função) atribuídas a este cmdlet (incluindo eventuais funções personalizadas do RBAC que você mesmo tenha criado), execute o comando a seguir no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Set-CsCommonAreaPhone"}

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
<td><p>Identificador exclusivo do telefone de área comum. Os telefones de área comum são identificados usando-se o nome diferenciado do Active Directory do objeto de contato associado. Por padrão, telefones de área comum usam um GUID (identificador global exclusivo) como nome comum; ou seja, os telefones geralmente terão uma Identidade semelhante a esta: CN={ce84964a-c4da-4622-ad34-c54ff3ed361f},OU=Redmond,DC=Litwareinc,DC=com. Com isso, pode ser mais fácil obter telefones de área comum usando o cmdlet <strong>Get-CsCommonAreaPhone</strong> e canalizando os objetos retornados para o cmdlet <strong>Set-CsCommonAreaPhone</strong>.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Description</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Permite modificar o atributo de descrição do Active Directory para o telefone de área comum. Isso oferece uma maneira de se fornecer informações adicionais sobre o telefone; por exemplo, detalhes sobre quem contatar em caso de problemas com o telefone.</p></td>
</tr>
<tr class="even">
<td><p><em>DisplayName</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Permite a modificação do nome para exibição no Active Directory do telefone de área comum.</p></td>
</tr>
<tr class="odd">
<td><p><em>DisplayNumber</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Número de telefone exibido no Lync. A propriedade DisplayNumber pode ser formatada conforme a sua preferência; por exemplo, 1-800-555-1234; 1-(800)-555-1234; 1.800.555.1234; etc. Ao escolher um número para exibição, tenha em mente que esse número será exibido na tela do telefone de área comum apenas se o número puder ser normalizado (normalização é o processo de tradução de cadeias numéricas em um formato padrão de número de telefone). Se não existir uma regra de normalização para o formato de número de telefone usado na configuração do número para exibição, a tela do telefone de área comum exibirá o valor da propriedade LineUri, e não o valor da propriedade DisplayNumber.</p></td>
</tr>
<tr class="even">
<td><p><em>DomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Fqdn</p></td>
<td><p>Permite sua conexão ao controlador de domínio especificado para modificar as informações de contato. Para conectar a um determinado controlador de domínio, inclua o parâmetro DomainController seguido pelo nome de computador (por exemplo, atl-mcs-001) ou o seu FQDN (nome de domínio totalmente qualificado); por exemplo: atl-mcs-001.litwareinc.com.</p></td>
</tr>
<tr class="odd">
<td><p><em>Enabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boleano</p></td>
<td><p>Indica se o objeto de contato do telefone de área comum foi habilitado ou não para o Lync Server.</p>
<p>Se você desativar um contato usando o parâmetro Enabled, as informações associadas a essa conta (incluindo diretivas atribuídas e se o contato está ou não habilitado para o Enterprise Voice, controle de chamada remota e/ou integração de caixa postal) são retidas. Se a conta for reabilitada posteriormente com o parâmetro Enabled, as informações de conta associadas serão restauradas.</p></td>
</tr>
<tr class="even">
<td><p><em>EnterpriseVoiceEnabled</em></p></td>
<td><p>Opcional</p></td>
<td><p>Boleano</p></td>
<td><p>Indica se o objeto de contato do telefone de área comum foi habilitado ou não para o Enterprise Voice, a solução de protocolo VoIP oferecida pela Microsoft. Com o Enterprise Voice, chamadas telefônicas podem ser feitas usando a Internet em vez da rede telefônica padrão.</p></td>
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
<td><p><em>LineURI</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Número de telefone do telefone de área comum. A linha URI deve ser especificada usando o formato E.164 e receber o prefixo &quot;TEL:&quot; . Por exemplo: TEL:+14255551297. Qualquer número de ramal deve ser adicionado ao fim da linha URI; por exemplo: TEL:+14255551297; ext=51297.</p></td>
</tr>
<tr class="odd">
<td><p><em>PassThru</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Retorna um objeto representando o telefone de área comum.</p></td>
</tr>
<tr class="even">
<td><p><em>SipAddress</em></p></td>
<td><p>Opcional</p></td>
<td><p>Cadeia de caracteres</p></td>
<td><p>Identificador exclusivo que permite que o telefone de área comum se comunique com dispositivos SIP como o Lync. O endereço SIP deve levar o prefixo sip: e incluir um domínio SIP válido. Por exemplo: sip:bldg14lobby@litwareinc.com.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact.

## Tipos de retorno

Por padrão, o cmdlet **Set-CsCommonAreaPhone** não retorna nenhum objeto ou valor. No entanto, se o parâmetro PassThru for incluído, o cmdlet irá retornar instâncias do objeto Microsoft.Rtc.Management.ADConnect.Schema.OCSADCommonAreaPhoneContact object.

## Consulte Também

#### Outros Recursos

[Get-CsCommonAreaPhone](get-cscommonareaphone.md)  
[Move-CsCommonAreaPhone](move-cscommonareaphone.md)  
[New-CsCommonAreaPhone](new-cscommonareaphone.md)  
[Remove-CsCommonAreaPhone](remove-cscommonareaphone.md)

