---
title: 'Lync Server 2013: Mover usuários para Lync Online'
TOCTitle: Mover usuários para Lync Online
ms:assetid: 6a523c86-2eac-4fa4-973a-4406872c9a7d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204969(v=OCS.15)
ms:contentKeyID: 49307010
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover usuários para Lync Online no Lync Server 2013

 

_**Tópico modificado em:** 2014-05-29_

Antes de começar a migrar usuários para o Lync Online, faça backup dos dados dos usuários associados às contas a serem migradas. Nem todos os dados de usuário são movidos junto com a conta. Para mais informações, consulte [Requisitos de backup e restauração: dados](lync-server-2013-backup-and-restoration-requirements-data.md).

## Migrar configurações de usuário para o Lync Online

As configurações do usuário são movidas com a conta do usuário. Algumas configurações locais não são movidas com a conta do usuário.

## Movendo usuários piloto para o Lync Online

Antes de começar a mover os usuários para o Lync Online, você pode mover alguns usuários piloto para confirmar se o ambiente está corretamente configurado. Será então possível verificar se os recursos e serviços do Lync funcionam conforme o esperado antes de tentar mover usuários adicionais.

Para mover um usuário local no seu locatário do Skype for Business Online, execute os seguintes cmdlets no Shell de Gerenciamento do Lync Server, usando as credenciais de administrador para o seu locatário do Microsoft Office 365. Substitua "username@contoso.com" pela informação do usuário que você deseja mover.

```
    $creds=Get-Credential
```
```
    Move-CsUser -Identity username@contoso.com -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>
```

O formato da URL específica para o parâmetro **HostedMigrationOverrideUrl** deve ser a URL para o pool no qual o serviço de migração hospedado está sendo executado, no seguinte formato: *Https://\<Pool FQDN\>/HostedMigration/hostedmigrationService.svc* .

Você pode identificar a URL do serviço de migração hospedado visualizando a URL do Painel de Controle do Lync Online da sua conta de locatário do Office 365.

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

## Movendo usuários do Lync Online

É possível mover vários usuários usando o cmdlet [Get-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUser)com o parâmetro -Filtro para selecionar os usuários com uma propriedade específica atribuída às contas dos usuários, como RegistrarPool. Em seguida, você pode canalizar os usuários retornados para o cmdlet [Move-CsUser](https://docs.microsoft.com/en-us/powershell/module/skype/Move-CsUser), conforme mostrado nos exemplos a seguir.

    Get-CsUser -Filter {UserProperty -eq "UserPropertyValue"} | Move-CsUser -Target sipfed.online.lync.com -Credential $creds -HostedMigrationOverrideUrl <URL>

Você também pode usar o parâmetro -OU para recuperar todos os usuários no OU especificado, como mostrado no exemplo a seguir.

    Get-CsUser -OU "cn=hybridusers,cn=contoso.." | Move-CsUser -Target sipfed.online.lync.com -Credentials $creds -HostedMigrationOverrideUrl <URL>

## Verifique as configurações e os recursos do usuário do Lync Online

Você pode verificar que o usuário foi movido com sucesso das seguintes formas:

  - Exibir o status do usuário no Painel de Controle do Lync Online. O indicador visual para usuários no local e online é diferente.

  - Execute o seguinte cmdlet:
    
        Get-CsUser -Identity

