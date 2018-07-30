---
title: Atribuir números de recebimento de chamadas em grupo aos usuários
TOCTitle: Atribuir números de recebimento de chamadas em grupo aos usuários
ms:assetid: b8e79275-8e7e-4799-b908-f34f61df22f0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945647(v=OCS.15)
ms:contentKeyID: 52057697
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuir números de recebimento de chamadas em grupo aos usuários

 

_**Tópico modificado em:** 2013-01-30_

Após você adicionar números de grupos de atendimento de chamadas à tabela de órbitas do estacionamento de chamadas, você pode atribuir os grupos a usuários. Utilize a ferramenta do kit de recursos de ativação de recurso de extensão secundário (SEFAUtil) para atribuir grupos de atendimento de chamadas a usuários.

> [!NOTE]  
> Em uma implantação híbrida, não atribua um grupo de atendimento de chamadas a usuários hospedados online. Usuários hospedados online não podem participar de atendimento de chamadas em grupo. Isso significa que suas chamadas não podem ser atendidas por outros usuários, e eles não podem responder chamadas no lugar de outros usuários.

## Para atribuir um grupo de atendimento de chamadas a um usuário

1.  Realize logon no computador em que você instalou a ferramenta SEFAUtil com direitos de administrador.

2.  Na linha de comando, execute:
    
        SEFAUtil.exe sip:<sip address of user> /server:<pool FQDN> /enablegrouppickup:<group number>
    
    Por exemplo:
    
        SEFAUtil.exe katarina@contoso.com /server:pool01.contoso.com /enablegrouppickup:199

## Consulte Também

#### Tarefas

[Habilitar o recebimento de chamadas em grupo para os usuários](lync-server-2013-enable-group-call-pickup-for-users.md)  
[Desabilitar o recebimento de chamadas em grupo para os usuários](lync-server-2013-disable-group-call-pickup-for-users.md)

