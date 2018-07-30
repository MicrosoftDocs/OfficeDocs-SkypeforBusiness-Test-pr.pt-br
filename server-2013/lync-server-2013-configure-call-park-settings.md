---
title: Configurações de estacionamento de chamadas no Lync Server 2013
TOCTitle: Configurações de estacionamento de chamadas no Lync Server 2013
ms:assetid: 3bed9d09-8363-4fff-a220-f0f6d3a81241
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425886(v=OCS.15)
ms:contentKeyID: 49306441
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurações de estacionamento de chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Se não quiser usar as configurações padrão do Estacionamento de Chamada, será possível personalizá-las. Quando você instala o Aplicativo de Estacionamento de Chamada, as configurações globais são definidas por padrão. É possível modificar as configurações globais e também especificar configurações específicas do site. Use o cmdlet **New-CsCpsConfiguration** para criar configurações específicas do site. Use o cmdlet **Set-CsCpsConfiguration** para modificar as configurações existentes.

> [!NOTE]  
> No mínimo, recomendamos configurar a opção <strong>OnTimeoutURI</strong> para o destino de fallback a ser usado quando uma chamada estacionada excede o tempo limite e o retorno de toque falha.

Use os cmdets **New-CsCpsConfiguration** ou **Set-CsCpsConfiguration** para definir qualquer uma das seguintes configurações:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Esta opção:</th>
<th>Especifica:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>CallPickupTimeoutThreshold</strong></p></td>
<td><p>A quantidade de tempo que passa após uma chamada ser estacionada antes que ela toque de volta no telefone no qual foi atendida.</p>
<p>O valor deve ser inserido no formato hh:mm:ss para especificar horas, minutos e segundos. O valor mínimo é 10 segundos e o valor máximo é 10 minutos. O padrão é 00:01:30.</p></td>
</tr>
<tr class="even">
<td><p><strong>EnableMusicOnHold</strong></p></td>
<td><p>Se a música é reproduzida para um chamador enquanto uma chamada está estacionada.</p>
<p>Os valores são True ou False. O padrão é True.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MaxCallPickupAttempts</strong></p></td>
<td><p>O número de vezes que uma chamada estacionada retorna o toque para o telefone de resposta antes de ser encaminhada para o URI (Uniform Resource Identifier) de fallback que é especificado para <strong>OnTimeoutURI</strong>. O padrão é 1.</p></td>
</tr>
<tr class="even">
<td><p><strong>OnTimeoutURI</strong></p></td>
<td><p>O endereço SIP do usuário ou grupo de resposta para o qual uma chamada estacionada não atendida é roteada quando <strong>MaxCallPickupAttempts</strong> é excedido.</p>
<p>O valor deve ser um URI do SIP que começa com a cadeia de caracteres sip:. Por exemplo, sip:bob@contoso.com. O padrão é nenhum endereço de encaminhamento.</p></td>
</tr>
</tbody>
</table>


## Para definir configurações do Estacionamento de Chamada

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        New-CsCpsConfiguration -Identity site:<sitename to apply settings> [-CallPickupTimeoutThreshold <hh:mm:ss>] -[EnableMusicOnHold <$true | $false>] [-MaxCallPickupAttempts <number of rings>] [-OnTimeoutURI sip:<sip URI for routing unanswered call>]
    

    > [!TIP]
    > Use o cmdlet <STRONG>Get-CsSite</STRONG> para identificar o site. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.

    
    Por exemplo:
    
        New-CsCpsConfiguration -Identity site:Redmond1 -CallPickupTimeoutThreshold 00:01:00 -EnableMusicOnHold $false -MaxCallPickupAttempts 2 -OnTimeoutURI sip:bob@contoso.com

## Consulte Também

#### Tarefas

[Personalizar a música de espera do estacionamento de chamada no Lync Server 2013](lync-server-2013-customize-call-park-music-on-hold.md)  

#### Outros Recursos

[New-CsCpsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsCpsConfiguration)  
[Set-CsCpsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCpsConfiguration)  
[Get-CsSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsSite)

