---
title: Mover objetos de Contato de Unificação de Mensagens do Exchange
TOCTitle: Mover objetos de Contato de Unificação de Mensagens do Exchange
ms:assetid: 35c7e987-41b5-4798-b617-3303f20e52e3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688022(v=OCS.15)
ms:contentKeyID: 49886176
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover objetos de Contato de Unificação de Mensagens do Exchange

 

_**Tópico modificado em:** 2012-10-19_

Para migrar os objetos de contato do AA (Atendedor Automático) ou SA (Acesso de Assinante) para a implantação do Lync Server 2013 , é preciso primeiro mover os objetos da implantação do Office Communications Server 2007 R2 herdada para a nova implantação do Lync Server 2013 usando os cmdlets **Get-CsExUmContact** e **Move-CsExUmContact**. No Exchange Server, execute o script **ExchUCUtil**Windows PowerShell para fazer o seguinte com o pool do Lync recém-implantado:

  - Adicioná-lo aos gateways IP de unificação de mensagens

  - Adicioná-lo aos grupos de busca de unificação de mensagens

> [!NOTE]  
> Para usar os cmdlets <strong>Get-CsExUmContact</strong> e <strong>Move-CsExUmContact</strong>, é preciso ser membro do grupo RTCUniversalUserAdmins e ter permissão de OU (unidade organizacional) para a OU em que os objetos de contato estão armazenados. A permissão de OU pode ser concedida usando o cmdlet <strong>Grant-OUPermission</strong>.

## Para mover objetos de contato usando o Shell de Gerenciamento do Lync Server

1.  Abra o Shell de Gerenciamento do Lync Server.

2.  Para cada pool registrado com UM do Exchange (em que pool1.contoso.net é um pool da implantação do Office Communications Server 2007 R2 e pool2.contoso.net é o pool da implantação do Lync Server 2013) na linha de comando, digite o seguinte:
    
        Get-CsExUmContact -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsExUmContact -Target pool02.contoso.net
    
    Para verificar se os objetos de contato foram movidos, execute o cmdlet **Get-CsExumContact** e confirme se **RegistrarPool** indica agora o novo pool.

## Para executar o script ExchUCUtil Windows PowerShell

1.  Faça logon no servidor UM do Exchange como usuário com privilégios de administrador de organização do Exchange.

2.  Navegue para o script ExchUCUtil do Windows PowerShell
    
    No Exchange 2007, o ExchUCUtil.ps1 está localizado em: **%Arquivos de programa%\\Microsoft\\Exchange Server\\Scripts\\ExchUCUtil.ps1**
    
    No Exchange 2010, o ExchUCUtil.ps1 está localizado em: **%Arquivos de programa%\\Microsoft\\Exchange Server\\V14\\Scripts\\ExchUCUtil.ps1**

3.  Se o Exchange estiver implantado em uma única floresta, digite:
    
        exchucutil.ps1
    
    Se o Exchange estiver implantado em várias florestas, digite:
    
        exchucutil.ps1 -Forest:" <forest FQDN>"
    
    onde *FQDN da floresta* especifica a floresta na qual o Lync Server 2013 está implantado.
    
    > [!IMPORTANT]  
    > Certifique-se de reiniciar o serviço de <strong>Front-End do Lync Server</strong> (rtcsrv.exe) <em>depois</em> de executar exchucutil.ps1. Caso contrário, o Lync Server 2013 não detectará a unificação de mensagens.
