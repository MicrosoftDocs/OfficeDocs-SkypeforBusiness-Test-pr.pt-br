---
title: Configurando Unified Messaging do Microsoft Exchange Server 2013 para caixa postal de Microsoft Lync Server 2013
TOCTitle: Configurando Unified Messaging do Microsoft Exchange Server 2013 para caixa postal de Microsoft Lync Server 2013
ms:assetid: 1be9c4f4-fd8e-4d64-9798-f8737b12e2ab
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687983(v=OCS.15)
ms:contentKeyID: 49886121
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Unified Messaging do Microsoft Exchange Server 2013 para caixa postal de Microsoft Lync Server 2013

 

_**Tópico modificado em:** 2013-02-04_

O Microsoft Lync Server 2013 permite você ter mensagens de caixa postal armazenadas no Microsoft Exchange Server 2013; estas mensagens de caixa postal aparecerão como mensagens de email na Caixa de entrada dos usuários. Esta capacidade também foi entrada nas edições de 2010 do Lync Server e do Exchange. No entanto, o processo de configuração deste "unified messaging" foi simplificado nas edições de 2013 graças a introdução do componente Roteador de Chamadas UM. Este componente é instalado no servidor de Acesso do Cliente do Exchange 2013 e todas as chamadas para o unified messaging do Exchange (como caixa postal) são roteadas primeiro através do Roteador de Chamada e redirecionadas para o servidor de Caixa de correio adequado.

Se você já configurou a autenticação servidor para servidor entre o Lync Server 2013 e o Exchange 2013, você está pronto para configurar o unified messaging. Para fazer isso, você deve primeiro criar e atribuir um novo plano de discagem do unified em seu servidor do Exchange. Por exemplo, estes dois comandos (executar por dentro do Shell de Gerenciamento do Exchange) configuram um novo plano de discagem de 3 dígitos para o Exchange:

    New-UMDialPlan -Name "RedmondDialPlan" -VoIPSecurity "Secured" -NumberOfDigitsInExtension 3 -URIType "SipName" -CountryOrRegionCode 1
    Set-UMDialPlan "RedmondDialPlan" -ConfiguredInCountryOrRegionGroups "Anywhere,*,*,*" -AllowedInCountryOrRegionGroups "Anywhere"

O primeiro comando no exemplo, o parâmetro VoIPSecurity e o valor de parâmetro "Secured" indica que o canal de sinalização é criptografado usando TLS. O URIType "SipName" indica que as mensagens serão enviadas e recebidas usando o protocolo SIP e o CountryOrRegionCode de 1 indica que o plano de discagem se aplica aos EUA.

No segundo comando, o valor do parâmetro para o parâmetro ConfiguredInCountryOrRegionGroups especifica os grupos no país que podem ser usados com este plano de discagem. O valor de parâmetro "Anywhere,\*,\*,\*" define o seguinte:

  - Nome do grupo ("Anywhere")

  - AllowedNumberString (\*, um caractere curinga indicando que qualquer sequência numérica é permitida)

  - DialNumberString (\*, um caractere curinga indicando que qualquer número discado é permitido)

  - TextComment (\*, um caractere curinga indicando que qualquer comando de texto é permitido)

Após criar e configurar o novo plano de discagem, você deve adicionar o novo plano de discagem ao seu servidor do unified messaging e modificar o modo de inicialização do servidor; em particular, você deve definir o modo de inicialização para "Dual". É possível realizar ambas estas tarefas dentro do Shell de Gerenciamento do Exchange:

    Set-UmServer -Identity "atl-exchangeum-001.litwareinc.com" -DialPlans "RedmondDialPlan" -UMStartupMode "Dual"

Após o servidor do unified messaging ter sido configurado, você deve executar a seguir o cmdlet Enable-ExchangeCertificate para garantir que seu certificado do Exchange seja aplicado ao serviço do unified messaging:

    Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "EA5A332496CC05DA69B75B66111C0F78A110D22d" -Services "SMTP","IIS","UM"

Após o certificado ter sido atribuído corretamente, você deve parar e reiniciar o serviço MsExchangeUM no servidor do unified messaging. Este serviço deve ser parado e reiniciado a qualquer momento que você alterar o modo de inicialização.

Após finalizar a configuração do servidor do unified messaging, é possível configurar o Roteador de Chamada UM:

    Set-CsUMCallRouterSettings -Server "atl-exchange-001.litwareinc.com" -UMStartupMode "Dual" -DialPlans "RedmondDialPlan" 
    Enable-ExchangeCertificate -Server "atl-umserver-001.litwareinc.com" -Thumbprint "45BAA32496CC891169B75B9811320F78A1075DDA" -Services "IIS","UMCallRouter"

Como o modo de inicialização foi alterado, você deve parar e reiniciar o serviço do MsExchangeUMCR no computador hospedando o Roteador de Chamada UM.

Para concluir a configuração do unified messaging, você precisa criar uma política de caixa de correio do UM e usar essa política para habilitar os usuários para o unified messaging. É possível criar uma política de caixa de correio usando um comando semelhante ao seguinte:

    New-UMMailboxPolicy -ID "RedmondMailboxPolicy" -AllowedCountryOrRegionGroups "Anywhere"

E é possível habilitar um usuário para unified messaging utilizando um comando semelhante ao seguinte:

    Enable-UMMailbox -Extensions 100 -SIPResourceIdentifier "kenmyer@litwareinc.com" -Identity "litwareinc\kenmyer" -UMMailboxPolicy "RedmondMailboxPolicy"

No comando anterior, o parâmetro Extensions representa o número de extensão telefônica do usuário. Neste exemplo, o usuário possui o número de extensão 100.

Após habilitar esta caixa de correio, o usuário kenmyer@litwareinc.com deve poder usar o Exchange unified messaging. É possível verificar se o usuário pode se conectar ao UM do Exchange executando o cmdlet [Test-CsExUMConnectivity](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsExUMConnectivity) dentro do Shell de Gerenciamento do Lync Server:

    $credential = Get-Credential "litwareinc\kenmyer"
    
    Test-CsExUMConnectivity -TargetFqdn "atl-cs-001.litwareinc.com" -UserSipAddress "sip:kenmyer@litwareinc.com" -UserCredential $credential

Se você possui um segundo usuário habilitado para unified messaging, é possível usar o cmdlet [Test-CsExUMVoiceMail](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsExUMVoiceMail) para verificar se este segundo usuário pode deixar uma mensagem de caixa postal para o primeiro usuário.

    $credential = Get-Credential "litwareinc\pilar"
    
    Test-CsExUMVoiceMail -TargetFqdn "atl-cs-001.litwareinc.com" -ReceiverSipAddress "sip:kenmyer@litwareinc.com" -SenderSipAddress "sip:pilar@litwareinc.com" -SenderCredential $credential

