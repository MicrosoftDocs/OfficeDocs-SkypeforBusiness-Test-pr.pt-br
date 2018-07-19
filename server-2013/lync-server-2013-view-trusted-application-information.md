---
title: Exibir Informações de Aplicativos Confiáveis
TOCTitle: Exibir Informações de Aplicativos Confiáveis
ms:assetid: 7b916323-96fb-4308-bc95-c178de41a3d3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688103(v=OCS.15)
ms:contentKeyID: 49886275
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Informações de Aplicativos Confiáveis

 

_**Tópico modificado em:** 2015-03-30_

Use o procedimento a seguir para visualizar Shell de Gerenciamento do Lync Server 2013 informações confiáveis de aplicativo em Shell de Gerenciamento do Lync Server.

## Visualizar Informações de Aplicativos Confiáveis Usando Shell de Gerenciamento do Lync Server Cmdlets

Você pode ver informações sobre seus aplicativos confiáveis usando Shell de Gerenciamento do Lync Server e **Get-CsTrustedApplication** cmdlet. Esse cmdlet pode ser executado de Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para ver aplicativos confiáveis

  - Para ver todos os seus aplicativos confiáveis, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsConferenceDisclaimer
    
    Esse comando retorna informações semelhantes às seguintes para cada aplicativo confiável:
    
        Identity               : CN={5dedf4b0-a590-49b3-80cf-f16f914bbef9},CN=Application Contacts,CN=RTC
                                 Service,CN=Services,CN=Configuration,DC=litware,DC=com
        RegistrarPool          : 487279971
        HomeServer             : CN=Lc Services,CN=Microsoft,CN=co1:2,CN=Pools,CN=RTC
                                 Service,CN=Services,CN=Configuration,DC=litware,DC=com
        OwnerUrn               : urn:application:helpdesk
        SipAddress             : sip:RtcApplication-dbf5142f-2bb2-4c4f-9531-b7fea45c5000@litware.com
        DisplayName            :
        DisplayNumber          :
        LineURI                :
        PrimaryLanguage        : 0
        SecondaryLanguages     : {}
        EnterpriseVoiceEnabled : True
        ExUmEnabled            : False
        Enabled                : True

Para detalhes, consulte [Get-CsTrustedApplication](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTrustedApplication).

