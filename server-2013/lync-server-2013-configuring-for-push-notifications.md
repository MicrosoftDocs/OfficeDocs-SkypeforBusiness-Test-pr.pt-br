---
title: 'Lync Server 2013: Configurando notificações por push'
TOCTitle: Configurando notificações por push
ms:assetid: d77f2c06-0fe6-45d5-8f08-808ab871b3e0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690047(v=OCS.15)
ms:contentKeyID: 49308265
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando notificações por push no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-12_

Notificações de push no formato de crachás, ícones ou alertas podem ser enviadas para um dispositivo móvel quando o aplicativo móvel estiver inativo. As notificações de push avisam um usuário de eventos como um convite de IM novo ou perdido e caixa postal. O Serviço de Mobilidade do Lync Server 2013 envia notificações para o Serviço de Notificação de Push Lync Server baseado em nuvem, que envia a notificação para o Serviço de Notificação Push da Apple (APNS), para um dispositivo Apple executando o cliente Lync 2010 Mobile; ou o Serviço de Notificação de Push da Microsoft (MPNS), para um dispositivo Windows Phone executando o cliente móvel Lync 2010 Mobile ou Lync 2013.

> [!IMPORTANT]  
> Se você utiliza Windows Phone com cliente móvel Lync 2010 Mobile ou Lync 2013, notificação de push é uma consideração importante.<br />Se você utiliza Lync 2010 Mobile em dispositivos Apple, notificação de push é uma consideração importante.<br />Se você utiliza Lync 2013 móvel em dispositivos Apple, você não precisa mais de notificação de push.

Configure sua topologia para suportar as notificações por push fazendo o seguinte:

  - Se seu ambiente possui um Lync Server 2010 ou Lync Server 2013Servidor de Borda, você precisa adicionar um novo provedor de host, o Microsoft Lync Online, e configurar a federação do provedor de host entre sua organização e o Lync Online.

  - Se seu ambiente tiver um Office Communications Server 2007 R2Servidor de Borda, será necessário configurar a federação direta de SIP com push.lync.com.
    
    > [!NOTE]  
    > Push.lync.com é um domínio do Microsoft Office 365 para o Serviço de Notificação de Push.

  - Para habilitar as notificações por push, você precisa executar o cmdlet **Set-CsPushNotificationConfiguration**. Por padrão, as notificações por push estão desativadas.

  - Teste a configuração de federação e as notificações por push.

## Para configurar para notificações de push com Lync Server 2013 ou Lync Server 2010Servidor de Borda

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server e o Ocscore estão instalados como membro do grupo RtcUniversalServerAdmins.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Adicione um provedor de hospedagem online do Lync Server. Na linha de comando, digite:
    
        New-CsHostingProvider -Identity <unique identifier for Lync Online hosting provider> -Enabled $True -ProxyFqdn <FQDN for the Access Server used by the hosting provider> -VerificationLevel UseSourceVerification
    
    Por exemplo:
    
        New-CsHostingProvider -Identity "LyncOnline" -Enabled $True -ProxyFqdn "sipfed.online.lync.com" -VerificationLevel UseSourceVerification
    
    > [!NOTE]  
    > Não é possível ter mais de um relacionamento de federação com um único provedor de hospedagem. Ou seja, se você já tiver configurado um provedor de hospedagem que tenha um relacionamento de federação com sipfed.online.lync.com, não adicione outro provedor de hospedagem para ele, mesmo se a identidade do provedor de hospedagem for algo além de LyncOnline.

4.  Configure a federação do provedor de hospedagem entre sua organização e o Serviço de Notificação por Push no Lync Online. Na linha de comando, digite:
    
        New-CsAllowedDomain -Identity "push.lync.com"

## Para configurar para notificações de push com Office Communications Server 2007 R2Servidor de Borda

1.  Faça logon no Servidor de Borda como membro do grupo RtcUniversalServerAdmins.

2.  Clique em **Iniciar** , em **Todos os Programas** , em **Ferramentas Administrativas** e clique em **Gerenciamento do Computador** .

3.  Na árvore do console, expanda **Serviços e Aplicativos** , clique com o botão direito do mouse em **Microsoft Office Communications Server 2007 R2** e clique em **Propriedades** .

4.  Na guia **Permitir** , clique em **Adicionar** .

5.  Na caixa de diálogo **Adicionar Parceiro Federado** , execute o seguinte procedimento:
    
      - Em **Nome de domínio do parceiro federado:** , digite **push.lync.com** .
    
      - Em **Servidor de Borda de Acesso do parceiro Federado** , digite **sipfed.online.lync.com**.
    
      - Clique em **OK** .

## Para habilitar as notificações por push

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server e o Ocscore estão instalados como membro da função CsAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Habilite as notificações por push. Na linha de comando, digite:
    
        Set-CsPushNotificationConfiguration -EnableApplePushNotificationService $True -EnableMicrosoftPushNotificationService $True

4.  Habilite a federação. Na linha de comando, digite:
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

## Para testar a federação e as notificações por push

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server e o Ocscore estão instalados como membro da função CsAdministrator.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Teste a configuração de federação. Na linha de comando, digite:
    
        Test-CsFederatedPartner -TargetFqdn <FQDN of Access Edge server used for federated SIP traffic> -Domain <FQDN of federated domain> -ProxyFqdn <FQDN of the Access Edge server used by the federated organization>
    
    Por exemplo:
    
        Test-CsFederatedPartner -TargetFqdn accessproxy.contoso.com -Domain push.lync.com -ProxyFqdn sipfed.online.lync.com

4.  Teste as notificações por push. Na linha de comando, digite:
    
        Test-CsMcxPushNotification -AccessEdgeFqdn <Access Edge service FQDN>
    
    Por exemplo:
    
        Test-CsMcxPushNotification -AccessEdgeFqdn accessproxy.contoso.com

## Consulte Também

#### Outros Recursos

[Test-CsFederatedPartner](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsFederatedPartner)  
[Test-CsMcxPushNotification](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsMcxPushNotification)

