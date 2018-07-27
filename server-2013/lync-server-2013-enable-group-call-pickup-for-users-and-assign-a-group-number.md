---
title: Habilitar o recebimento de chamadas em grupo para os usuários e atribuir um número de grupo
TOCTitle: Habilitar o recebimento de chamadas em grupo para os usuários e atribuir um número de grupo
ms:assetid: c33bb6c2-d43b-4fb6-a0fa-6d82a7b09abe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945650(v=OCS.15)
ms:contentKeyID: 52057720
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar o recebimento de chamadas em grupo para os usuários e atribuir um número de grupo

 

_**Tópico modificado em:** 2013-01-30_

Após ter adicionado números de grupos de atendimento de chamadas para a tabela de órbitas do estacionamento de chamadas, você atribui os números de grupo a usuários e habilita o atendimento de chamadas em grupo para eles. Utilize a ferramenta do kit de recursos de ativação de recurso de extensão secundário (SEFAUtil) para atribuir grupos de atendimento de chamadas a usuários.

> [!NOTE]  
> Em uma implantação híbrida, não atribua um grupo de atendimento de chamadas a usuários que estejam hospedados online. Usuários hospedados online não podem participar de atendimento de chamadas em grupo. Isso significa que suas chamadas não podem ser atendidas por outros usuários, e eles não podem responder chamadas no lugar de outros usuários.

## Para atribuir um número de grupo a um usuário e habilitá-lo para atendimento de chamadas em grupo

1.  Realize logon no computador em que você instalou a ferramenta SEFAUtil com direitos de administrador.

2.  Na linha de comando, execute:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    Por exemplo, para atribuir o número de grupo 199 a um usuário:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199 

## Consulte Também

#### Tarefas

[Desabilitar o recebimento de chamadas em grupo para os usuários](lync-server-2013-disable-group-call-pickup-for-users.md)

