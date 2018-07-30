---
title: 'Lync Server 2013: Administrando usuários em uma implantação híbrida'
TOCTitle: Administrando usuários em uma implantação híbrida
ms:assetid: 6924ed7b-30a9-4be7-b952-90655625f2c8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204967(v=OCS.15)
ms:contentKeyID: 49306988
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Administrando usuários em uma implantação híbrida do Lync Server 2013

 

_**Tópico modificado em:** 2014-05-29_

Você pode gerenciar as configurações e políticas de usuários para aqueles que foram movidos ao Lync Online por meio de recursos de Gerenciamento de Usuários disponiveis em no portal online Microsoft Office 365. Você deve fazer login usando sua conta de administrador do locatário para executar tarefas administrativas.

## Movendo usuários novamente para o local

> [!IMPORTANT]  
> Esta seção aplica-se apenas a usuários criados e habilitados para Lync no local e movidos de uma implantação local para o Lync Online. Caso queira mover usuários criados no Lync Online (e que nunca foram habilitados para o Lync em implantações locais) consulte, <a href="lync-server-2013-moving-users-from-lync-online-to-lync-on-premises.md">Mover usuários do Lync Online para o Lync no local no Lync Server 2013</a>.

  - Execute os cmdlets a seguir para mover os usuários do Lync Online novamente ao Lync local:
    
        $cred=Get-Credential
    
        Move-CsUser -Identity username@contoso.com -Target localpool.contoso.com -Credential $cred -HostedMigrationOverrideUrl <URL>

O formato da URL específica para o parâmetro **HostedMigrationOverrideUrl** deve ser a URL para o pool no qual o serviço de migração hospedado está sendo executado, no seguinte formato:

*Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc* . Você pode determinar a URL do Serviço de Migração Hospedado exibindo a URL do Painel de Controle do Lync Online da sua conta de inquilino do Office 365.

**Para identificar a URL do Serviço de Migração Hospedada do seu locatário do Office 365**

1.  Faça logon no seu inquilino do Office 365 como um administrador.

2.  Abra o **Centro de administração do Lync** .

3.  Com o **Centro de administração do Lync** exibido, selecione e copie a URL na barra de endereço no **lync.com**. Uma URL de exemplo seria parecida com esta:
    
    `https://webdir0a.online.lync.com/lscp/?language=en-US&tenantID=`

4.  Substitua **webdir** na URL por **admin**, o que resulta no seguinte:
    
    `https://admin0a.online.lync.com`

5.  Anexe a cadeia de caracteres a seguir à URL: **/HostedMigration/hostedmigrationservice.svc**.
    
    A URL resultante, que tem o valor de **HostedMigrationOverrideUrl**, deverá ser parecida com esta:
    
    `https://admin0a.online.lync.com/HostedMigration/hostedmigrationservice.svc`

