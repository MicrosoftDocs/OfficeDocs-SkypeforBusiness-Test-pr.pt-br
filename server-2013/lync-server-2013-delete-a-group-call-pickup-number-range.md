---
title: Excluir um intervalo numérico de recebimento de chamadas em grupo
TOCTitle: Excluir um intervalo numérico de recebimento de chamadas em grupo
ms:assetid: 521891f3-7a5d-45de-92dc-d57025453159
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945629(v=OCS.15)
ms:contentKeyID: 52057629
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um intervalo numérico de recebimento de chamadas em grupo

 

_**Tópico modificado em:** 2013-01-30_

Use o seguinte procedimento para excluir um intervalo de números de recebimento de chamadas de grupo.

## Para excluir um intervalo de números de recebimento de chamadas de grupo

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, digite:
    
        Remove-CsCallParkOrbit -Identity "<group number range name>" 
    
    Por exemplo:
    
        Remove-CsCallParkOrbit -Identity "Redmond call pickup"
    
    > [!NOTE]  
    > Para obter detalhes sobre mais opções, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit">Remove-CsCallParkOrbit</a>.

## Consulte Também

#### Tarefas

[Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas no Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)  

#### Outros Recursos

[Remove-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit)  
[Get-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCallParkOrbit)

