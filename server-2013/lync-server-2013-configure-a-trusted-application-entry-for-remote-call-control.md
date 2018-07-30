---
title: 'Lync Server 2013: Configurar uma entrada de aplicativo confiável para controle de chamada remota'
TOCTitle: Configurar uma entrada de aplicativo confiável para controle de chamada remota
ms:assetid: 37777f93-8b24-40cf-808e-7c6230eb2132
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558636(v=OCS.15)
ms:contentKeyID: 49306382
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar uma entrada de aplicativo confiável para controle de chamada remota no Lync Server 2013

 

_**Tópico modificado em:** 2015-11-02_

O gateway SIP/CSTA deve ser configurado como um aplicativo confiável para que o Lync Server aplique a rota estática para encaminhar chamadas ao gateway.

> [!IMPORTANT]  
> Se você estivar migrando os usuários de uma versão anterior da implantação do Lync Server, verifique se removeu todas as entradas confiáveis de aplicativo existentes (previamente conhecidas como entradas de host autorizado) criadas para o gateway SIP/CSTA antes de seguir os procedimentos deste tópico. Para obter detalhes, consulte <a href="lync-server-2013-remove-a-legacy-authorized-host-optional.md">Remover um host autorizado herdado no Lync Server 2013 (opcional)</a>.

## Para configurar uma entrada de aplicativo confiável para o gateway SIP/CSTA

1.  Faça o logon no computador em que o Shell de Gerenciamento do Lync Server está instalado, como membro do grupo RTCUniversalServerAdmins ou uma função de controle de acesso baseado em função(RBAC) à qual você atribuiu o cmdlet **New-CsTrustedApplicationPool**.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para criar uma entrada de aplicativo confiável, siga um destes procedimentos:
    
      - Para uma conexão TLS (Transport Layer Security), digite o seguinte no prompt de comando:
        
            New-CsTrustedApplicationPool -Identity <FQDN of the SIP/CSTA gateway> [-Registrar <Service ID or FQDN of the Registrar service>] -Site <Site ID for the site where you want to create the trusted application pool>
        
        Por exemplo:
        
            New-CsTrustedApplicationPool -Identity rccgateway.contoso.net -Registrar registrar1.contoso.net -Site co1 -TreatAsAuthenticated $true -ThrottleAsServer $true
    
      - Para uma conexão TCP (Transmission Control Protocol), digite o seguinte no prompt de comando:
        
            New-CsTrustedApplicationPool -Identity <IP address or FQDN of the SIP/CSTA gateway> [-Registrar <Service ID or FQDN of the Registrar service>] -Site <Site ID for the site where you want to create the trusted application pool>
        
        Por exemplo:
        
            New-CsTrustedApplicationPool -Identity 192.168.0.240 -Registrar registrar1.contoso.net -Site co1 -TreatAsAuthenticated $true -ThrottleAsServer $true

4.  Para adicionar o aplicativo confiável para o pool, siga um destes procedimentos:
    
      - Para uma conexão TLS, digite o seguinte no prompt de comando:
        
            New-CsTrustedApplication -ApplicationID <application name> -TrustedApplicationPoolFqdn <FQDN of the SIP/CSTA gateway> -Port <SIP listening port on the gateway>
        
        Por exemplo:
        
            New-CsTrustedApplication -ApplicationID RccGateway-1 -TrustedApplicationPoolFqdn rccgateway.contoso.net -Port 5065
    
      - Para uma conexão TCP, digite o seguinte no prompt de comando:
        
            New-CsTrustedApplication -ApplicationID <application name> -TrustedApplicationPoolFqdn <IP address or FQDN of the SIP/CSTA gateway> -Port <SIP listening port on the gateway> -EnableTcp
        
        Por exemplo:
        
            New-CsTrustedApplication -ApplicationID RccGateway-1 -TrustedApplicationPoolFqdn 192.169.0.240 -Port 5065 -EnableTcp

5.  Para implementar as alterações publicadas efetuadas na topologia, digite o seguinte no prompt de comando:
    
        Enable-CsTopology

## Consulte Também

#### Tarefas

[Configurar uma rota estática para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md)  
[Definir um endereço SIP de gateway SIP/CSTA no Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md)

