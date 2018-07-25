---
title: Primeiros passos antes de iniciar a migração de usuários do Lync Online para o Lync no local
TOCTitle: Primeiros passos antes de iniciar a migração de usuários do Lync Online para o Lync no local
ms:assetid: 98245b04-ded4-4186-8da3-ba1c554b5c39
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn689118(v=OCS.15)
ms:contentKeyID: 62247359
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Primeiros passos antes de iniciar a migração de usuários do Lync Online para o Lync no local

 

_**Tópico modificado em:** 2016-12-08_

Antes de iniciar a migração dos usuários do Lync Online para seu ambiente local, verifique se os padrões a seguir são verdadeiros:

  - Seu ambiente local do Lync Server deve estar completamente implantado e validado. Para mais informações, consulte [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md).

  - Seu locatário do Lync Online deve estar completamente configurado para Acesso PowerShell remoto.
    
    Para tal, instale antes o módulo Skype for Business Online para Windows PowerShell, disponível em: [http://go.microsoft.com/fwlink/p/?LinkId=391911](http://go.microsoft.com/fwlink/p/?linkid=391911).
    
    Depois de instalar o módulo, você pode estabelecer ~uma sessão remota digitando o cmdlets a seguir em Shell de Gerenciamento do Lync Server:
    
    ```
        Import-Module LyncOnlineConnector
    ```
    ```
        $cred = Get-Credential
    ```
    ```
            $CSSession = New-CsOnlineSession -Credential $cred
    ```
    ```
        Import-PSSession $CSSession -AllowClobber
    ```
    
    Para obter mais informações sobre como estabelecer uma sessão remota do PowerShell com o Skype for Business Online, consulte [Conectando ao Lync Online Usando o Windows PowerShell](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).
    
    Para obter mais informações sobre como usar o módulo Skype for Business Online PowerShell, consulte [Usar o Windows PowerShell para gerenciar o Lync Online](https://docs.microsoft.com/en-us/SkypeForBusiness/set-up-your-computer-for-windows-powershell/set-up-your-computer-for-windows-powershell).

  - Seu Lync Online deve estar configurado para Espaço de Endereço SIP Compartilhado. Para tal, inicie primeiro uma sessão de Powershell remota com o Lync Online. Em seguida, execute o cmdlet a seguir:
    
        Set-CsTenantFederationConfiguration -SharedSipAddressSpace $True

Depois de concluir essas etapas, você pode prosseguir para [Migração dos usuários do Lync Online para o Lync no local](lync-server-2013-migrating-lync-online-users-to-lync-on-premises.md).

