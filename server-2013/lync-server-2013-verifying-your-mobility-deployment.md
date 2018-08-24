---
title: 'Lync Server 2013: Verificando sua implantação de mobilidade'
TOCTitle: Verificando sua implantação de mobilidade
ms:assetid: 72f9b4d3-57b0-4705-9480-cfdca313a70c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690024(v=OCS.15)
ms:contentKeyID: 49307101
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificando sua implantação de mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-12_

    Some information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Depois de implantar o Serviço de Mobilidade do Lync Server e o Serviço de Descoberta Automática do Lync Server execute uma transação de teste para verificar se sua implantação funciona corretamente. Você pode executar o **Test-CsUcwaConference** para testar a capacidade de dois usuários que estão usando os clientes móveis do Lync 2013 criarem, participarem e se comunicarem em uma conferência. Para usar essa transação de teste, será necessário ter dois usuários reais ou usuários de teste e suas credenciais completas.

Você usa o **Test-CsMcxP2PIM** para testar o envio de mensagens instantâneas entre dois usuários que estão usando o Lync 2010 Mobile. De forma semelhante ao **Test-CsUcwaConference**, você usa dois usuários atuais ou dois usuários de teste pré-definidos.

## Para testar conferência dos clientes móveis do Lync 2013

1.  Faça logon como um membro da função CsAdministrator em qualquer computador onde Shell de Gerenciamento do Lync Servere Ocscore estejam instalados.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, digite:
    
        Test-CsUcwaConference -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -OrganizerSipAddress sip:<SIP address of test user 1> -OrganizerCredential <test user 1 credentials> -ParticipantSipAddress sip:<SIP address of test user 2> -ParticipantCredential <test user 2 credentials> -v
    
    Você pode definir as credenciais em um script e passá-las para o cmdlet teste. Por exemplo:
    
        $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
        $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
        $testuser1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
        $testuser2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
        Test-CsUcwaConference -TargetFqdn pool01.contoso.com -Authentication Negotiate -OrganizerSipAddress sip:UserName1@contoso.com -OrganizerCredential $testuser1 -ParticipantSipAddress sip:UserName2@contoso.com -ParticipantCredential $testuser2 -v

## Para testar mensagens instantâneas (IM) de pessoa para pessoa do Lync 2010 Mobile

1.  Faça logon como um membro da função CsAdministrator em qualquer computador onde Shell de Gerenciamento do Lync Servere Ocscore estejam instalados.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, digite:
    
        Test-CsMcxP2PIM -TargetFqdn <FQDN of Front End pool> -Authentication <TrustedServer | Negotiate | ClientCertificate | LiveID> -SenderSipAddress sip:<SIP address of test user 1> -SenderCredential <test user 1 credentials> -ReceiverSipAddress sip:<SIP address of test user 2> -ReceiverCredential <test user 2 credentials> -v
    
    Você pode definir as credenciais em um script e passá-las para o cmdlet teste. Por exemplo:
    
        $passwd1 = ConvertTo-SecureString "Password01" -AsPlainText -Force
        $passwd2 = ConvertTo-SecureString "Password02" -AsPlainText -Force
        $tuc1 = New-Object Management.Automation.PSCredential("contoso\UserName1", $passwd1)
        $tuc2 = New-Object Management.Automation.PSCredential("contoso\UserName2", $passwd2)
        Test-CsMcxP2PIM -TargetFqdn pool01.contoso.com -Authentication Negotiate -SenderSipAddress sip:UserName1@contoso.com -SenderCredential $tuc1 -ReceiverSipAddress sip:UserName2@contoso.com -ReceiverCredential $tuc2 -v

## Consulte Também

#### Outros Recursos

[Test-CsMcxP2PIM](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsMcxP2PIM)  
[Test-CsUcwaConference](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUcwaConference)

