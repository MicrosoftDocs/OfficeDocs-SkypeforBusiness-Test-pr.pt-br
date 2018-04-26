---
title: Uma introdução ao Windows PowerShell e ao Lync Online
TOCTitle: Uma introdução ao Windows PowerShell e ao Lync Online
ms:assetid: 4b4cf534-c950-4d6c-abd9-d3d0e6f53bb7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362785(v=OCS.15)
ms:contentKeyID: 56270388
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Uma introdução ao Windows PowerShell e ao Lync Online

 

_**Tópico modificado em:** 2015-06-22_

O Windows PowerShell é um shell de comando e uma linguagem de script que pode ser usado para gerenciar o Skype for Business Online. Em vez de usar o Centro de administração gráfico do Skype for Business Online para gerenciar o Skype for Business Online, você pode gerenciar alternativamente o produto usando comandos de linha de comando semelhantes a este:

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

Além de executar comandos simples como o exemplo anterior (que retorna informações sobre o usuário no UPN pauloneves@litwareinc.com), usuários com mais experiência no Windows PowerShell também podem organizar esses comandos em scripts. Esses scripts podem ser usados para automatizar processo e/ou realizar tarefas repetitivas.

Como regra geral, qualquer tarefa que você possa executar usando o Centro de administração do Skype for Business Online também pode ser executada usando o Windows PowerShell. Por exemplo, você pode usar o Centro de administração para gerenciar notificações de telefone celular, também conhecidas como *notificações por push*. As notificações por push permitem que você envie notificações sobre eventos (por exemplo, novas mensagens instantâneas ou nova caixa postal) para dispositivos móveis como iPhones e Windows Phones. Essas notificações podem ser recebidas no dispositivo móvel mesmo se o aplicativo do Lync nesses dispositivos esteja sendo executado em segundo plano.

Como gerenciar notificações por push? Uma maneira é usar o Centro de administração do Skype for Business Online, onde você pode habilitar ou desabilitar notificações por push selecionando a opção apropriada na guia **organização**:

![LyncOnlinePowerShell\_Push\_Notifications](images/Dn362807.0a6ec1f5-1999-427f-880b-0587c98d7670(OCS.15).png "LyncOnlinePowerShell_Push_Notifications")

Você também pode habilitar ou desabilitar notificações por push usando uma sessão remota do Windows PowerShell e o cmdlet [Set-CsPushNotificationConfiguration](set-cspushnotificationconfiguration.md). Por exemplo, este comando desabilita notificações por push para iPhones e Windows Phones:

    Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $False -EnableMicrosoftPushNotificationService $False

Como você pode ver, os parâmetros (ou seja, EnableApplePushNotificationService e EnableMicrosoftPushNotificationService), usados com o cmdlet **Set-CsPushNotificationConfiguration**, correspondem às opções disponíveis no Centro de administração do Skype for Business Online:

![Associação mostrada entre as opções do Lync / cmdlet PS](images/Dn362785.f20086fd-3b51-4bbf-8d81-e643d9bf3a2e(OCS.15).png "Associação mostrada entre as opções do Lync / cmdlet PS")

Em suma, você pode usar o Centro de administração ou um cmdlet do Windows PowerShell e os parâmetros apropriados para gerenciar notificações por push. Ambas as abordagens funcionam, e ambas funcionam igualmente bem.

<table>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Para obter definições de termos específicos do Windows PowerShell, como <em>cmdlet</em>, <em>parâmetro</em>, <em>valor de parâmetro</em> e <em>argumento</em>, consulte <a href="windows-powershell-cmdlets-parameters-and-parameter-values-in-skype-for-business-online.md">Cmdlets, parâmetros e valores de parâmetro do Windows PowerShell</a>.</td>
</tr>
</tbody>
</table>


Isso traz uma pergunta óbvia: se o Centro de administração do Skype for Business Online e o Windows PowerShell oferecem exatamente a mesma funcionalidade, por que você deveria optar por uma em detrimento da outra? Na verdade, por que você deveria optar por digitar comandos no Windows PowerShell, em vez de simplesmente marcar ou desmarcar caixas de seleção no Centro de administração?

Em um caso simples como o do exemplo anterior, decidir que abordagem usar resume-se à preferência pessoal: algumas pessoas preferem usar uma interface gráfica de usuário, enquanto outras preferem uma ferramenta de linha de comando como o Windows PowerShell. Entretanto, em alguns casos, o Windows PowerShell oferece a maneira mais eficiente de executar uma tarefa de gerenciamento ou a única maneira de executar uma tarefa de gerenciamento. Por exemplo, o Centro de administração do Skype for Business Online permite que você personalize convites para reunião:

![Configurações de convite de reunião do do centro de administração do Lync](images/Dn362785.3fb00c33-0bd4-46dd-beb1-8f71e24cf630(OCS.15).png "Configurações de convite de reunião do do centro de administração do Lync")

Você pode fazer essas personalizações usando o cmdlet [Set-CsMeetingConfiguration](set-csmeetingconfiguration.md). No entanto, o cmdlet **Set-CsMeetingConfiguration** também inclui opções não disponíveis no Centro de administração do Skype for Business Online. Por exemplo, se alguém em sua organização ingressar em uma reunião, automaticamente será configurado como um apresentador de reunião, por padrão. Essa configuração não pode ser alterada usando o Centro de administração do Skype for Business Online — somente por meio do Windows PowerShell e o cmdlet **Set-CsMeetingConfiguration**. Especificamente, esse comando define a propriedade DesignateAsPresenter como Nenhum, o que significa que somente o organizador da reunião será configurado como apresentador ao ingressar na reunião:

    Set-CsMeetingConfiguration -DesignateAsPresenter "Everyone"

Para obter mais detalhes sobre o uso do Windows PowerShell, consulte estes tópicos:

  - [Cmdlets, parâmetros e valores de parâmetro do Windows PowerShell](windows-powershell-cmdlets-parameters-and-parameter-values-in-skype-for-business-online.md)

  - [Trabalhando com parâmetros](working-with-parameters-in-skype-for-business-online.md)

  - [Parâmetros obrigatórios e opcionais](mandatory-and-optional-parameters-in-skype-for-business-online.md)

  - [Parâmetros vs. Propriedades](parameters-vs-properties-in-skype-for-business-online.md)

  - [Combinar cmdlets do Lync Online com outros cmdlets do Windows PowerShell](combining-skype-for-business-online-cmdlets-with-other-windows-powershell-cmdlets-in.md)

  - [Mais Ajuda para usar o Windows PowerShell](more-help-for-using-windows-powershell-in-skype-for-business-online.md)

