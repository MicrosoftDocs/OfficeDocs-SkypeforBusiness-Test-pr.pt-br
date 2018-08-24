---
title: Desabilitar o recebimento de chamadas em grupo para os usuários
TOCTitle: Desabilitar o recebimento de chamadas em grupo para os usuários
ms:assetid: 91b06f9e-2840-45a2-bbb3-6a29179b9a9f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945638(v=OCS.15)
ms:contentKeyID: 52057678
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Desabilitar o recebimento de chamadas em grupo para os usuários

 

_**Tópico modificado em:** 2013-01-30_

Use o seguinte procedimento para desativar o recebimento de chamadas de grupo para um usuário.

> [!NOTE]  
> Quando você desativa o recebimento de chamadas de grupo para um usuário, o número de recebimento de chamadas de grupo que foi atribuído ao usuário não será retido. Se subsequentemente você quiser ativar novamente o recebimento de chamadas de grupo para esse usuário, será necessário atribuir o número de recebimento de chamadas de grupo novamente com o parâmetro /enablegrouppickup.

## Para desativar o recebimento de chamadas de grupo para um usuário.

1.  Faça logon no computador se tiver instalado a ferramenta SEFAUtil com direitos de administrador.

2.  Na linha de comando, execute:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /disablegrouppickup
    
    Por exemplo:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /disablegrouppickup

## Consulte Também

#### Tarefas

[Atribuir números de recebimento de chamadas em grupo aos usuários](lync-server-2013-assign-group-call-pickup-numbers-to-users.md)  
[Habilitar o recebimento de chamadas em grupo para os usuários](lync-server-2013-enable-group-call-pickup-for-users.md)

