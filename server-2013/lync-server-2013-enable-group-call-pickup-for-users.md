---
title: Habilitar o recebimento de chamadas em grupo para os usuários
TOCTitle: Habilitar o recebimento de chamadas em grupo para os usuários
ms:assetid: 20ec5f41-6ba2-4156-82ed-b91d05b62a6d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945620(v=OCS.15)
ms:contentKeyID: 52057577
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar o recebimento de chamadas em grupo para os usuários

 

_**Tópico modificado em:** 2013-01-30_

Use a ferramenta de kit de recursos SEFAUtil para ativar o Recebimento de chamada de grupo para os usuários. Os usuários devem estar atribuídos a um número de grupo com o tipo GroupPickup na tabela de órbita de estacionamento de chamada para ter o Recebimento de chamada de grupo ativo. Você atribui um número de grupo de recebimento de chamada e ativa o Recebimento de chamada de grupo ao mesmo tempo usando o parâmetro /enablegrouppickup ao executar o SEFAUtil.exe.

## Para ativar o Recebimento de chamada de grupo para um usuário

1.  Faça logon no computador se tiver instalado a ferramenta SEFAUtil com direitos de administrador.

2.  Na linha de comando, execute:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    Por exemplo:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199

## Consulte Também

#### Tarefas

[Atribuir números de recebimento de chamadas em grupo aos usuários](lync-server-2013-assign-group-call-pickup-numbers-to-users.md)  
[Desabilitar o recebimento de chamadas em grupo para os usuários](lync-server-2013-disable-group-call-pickup-for-users.md)

