---
title: Cmdlets de segurança
TOCTitle: Cmdlets de segurança
ms:assetid: 9a6c654d-287d-434e-8d93-409f0d623f5a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398799(v=OCS.15)
ms:contentKeyID: 49307588
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets de segurança

 

_**Tópico modificado em:** 2016-12-08_

Os cmdlets de segurança incluídos no Microsoft Lync Server 2013 são usados principalmente para gerenciar a autenticação e os direitos de usuários e permissões. Uma ampla variedade de cmdlets está disponível para o gerenciamento da autenticação, incluindo cmdlets para autenticação de certificado e de PIN (número de identificação pessoal). Além disso, alguns cmdlets permitem que você use o novo recurso RBAC (controle de acesso baseado na função) para delegar controle administrativo do Lync Server.

## Cmdlets de segurança

Muitas tarefas de gerenciamento que se aplicam a configurações de segurança podem ser executadas a partir do Painel de Controle do Lync Server. Uma grande exceção são os cmdlets de permissão do usuário. No entanto, todas as tarefas de gerenciamento de segurança podem ser executadas usando cmdlets do Shell de Gerenciamento do Lync Server ou de dentro de um script; usar um script permite que você automatize determinadas tarefas. A seguir, uma lista dos cmdlets que estão diretamente relacionados ao gerenciamento das configurações de segurança:

**[Cmdlets de certificado e autenticação no Lync Server 2013](lync-server-2013-certificate-and-authentication-cmdlets.md)**

  -   
    [Get-CsCertificate](get-cscertificate.md)

  -   
    [Import-CsCertificate](import-cscertificate.md)

  -   
    [Remove-CsCertificate](remove-cscertificate.md)

  -   
    [Request-CsCertificate](request-cscertificate.md)

  -   
    [Set-CsCertificate](set-cscertificate.md)

  -   
    [Test-CsCertificateConfiguration](test-cscertificateconfiguration.md)

  -   
    [Get-CsClientCertificate](get-csclientcertificate.md)

  -   
    [Revoke-CsClientCertificate](revoke-csclientcertificate.md)

  -   
    [Lock-CsClientPin](lock-csclientpin.md)

  -   
    [Set-CsClientPin](set-csclientpin.md)

  -   
    [Unlock-CsClientPin](unlock-csclientpin.md)

  -   
    [Get-CsClientPinInfo](get-csclientpininfo.md)

  -   
    [New-CsKerberosAccount](new-cskerberosaccount.md)

  -   
    [Get-CsKerberosAccountAssignment](get-cskerberosaccountassignment.md)

  -   
    [New-CsKerberosAccountAssignment](new-cskerberosaccountassignment.md)

  -   
    [Remove-CsKerberosAccountAssignment](remove-cskerberosaccountassignment.md)

  -   
    [Set-CsKerberosAccountAssignment](set-cskerberosaccountassignment.md)

  -   
    [Test-CsKerberosAccountAssignment](test-cskerberosaccountassignment.md)

  -   
    [Set-CsKerberosAccountPassword](set-cskerberosaccountpassword.md)

  -   
    [Get-CsPinPolicy](get-cspinpolicy.md)

  -   
    [Grant-CsPinPolicy](grant-cspinpolicy.md)

  -   
    [New-CsPinPolicy](new-cspinpolicy.md)

  -   
    [Remove-CsPinPolicy](remove-cspinpolicy.md)

  -   
    [Set-CsPinPolicy](set-cspinpolicy.md)

  -   
    [Get-CsProxyConfiguration](get-csproxyconfiguration.md)

  -   
    [New-CsProxyConfiguration](new-csproxyconfiguration.md)

  -   
    [Remove-CsProxyConfiguration](remove-csproxyconfiguration.md)

  -   
    [Set-CsProxyConfiguration](set-csproxyconfiguration.md)

  -   
    [Get-CsSipDomain](get-cssipdomain.md)

  -   
    [New-CsSipDomain](new-cssipdomain.md)

  -   
    [Remove-CsSipDomain](remove-cssipdomain.md)

  -   
    [Set-CsSipDomain](set-cssipdomain.md)

**[Cmdlets de permissões e direitos de usuário](lync-server-2013-user-rights-and-permissions-cmdlets.md)**

  -   
    [Get-CsAdminRole](get-csadminrole.md)

  -   
    [New-CsAdminRole](new-csadminrole.md)

  -   
    [Remove-CsAdminRole](remove-csadminrole.md)

  -   
    [Set-CsAdminRole](set-csadminrole.md)

  -   
    [Update-CsAdminRole](update-csadminrole.md)

  -   
    [Get-CsAdminRoleAssignment](get-csadminroleassignment.md)

  -   
    [Grant-CsOUPermission](grant-csoupermission.md)

  -   
    [Revoke-CsOUPermission](revoke-csoupermission.md)

  -   
    [Test-CsOUPermission](test-csoupermission.md)

  -   
    [Grant-CsSetupPermission](grant-cssetuppermission.md)

  -   
    [Revoke-CsSetupPermission](revoke-cssetuppermission.md)

  -   
    [Test-CsSetupPermission](test-cssetuppermission.md)

**[Cmdlets de Interoperabilidade](lync-server-2013-interoperability-cmdlets.md)**

  - [Get-CsOAuthConfiguration](get-csoauthconfiguration.md)

  - [Set-CsOAuthConfiguration](set-csoauthconfiguration.md)

  - [Get-CsOAuthServer](get-csoauthserver.md)

  - [New-CsOAuthServer](new-csoauthserver.md)

  - [Remove-CsOAuthServer](remove-csoauthserver.md)

  - [Set-CsOAuthServer](set-csoauthserver.md)

  - [Get-CsPartnerApplication](get-cspartnerapplication.md)

  - [New-CsPartnerApplication](new-cspartnerapplication.md)

  - [Remove-CsPartnerApplication](remove-cspartnerapplication.md)

  - [Set-CsPartnerApplication](set-cspartnerapplication.md)

## Consulte Também

#### Outros Recursos

[Blog do Lync Server PowerShell](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x416)

