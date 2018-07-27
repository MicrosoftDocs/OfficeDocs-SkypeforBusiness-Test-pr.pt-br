---
title: Excluir um intervalo de órbita de estacionamento de chamada no Lync Server 2013
TOCTitle: Excluir um intervalo de órbita de estacionamento de chamada no Lync Server 2013
ms:assetid: 85e9f916-062d-450d-ac0a-aeaefc0f7cdc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182546(v=OCS.15)
ms:contentKeyID: 49307345
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um intervalo de órbita de estacionamento de chamada no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-20_

Use um destes procedimentos para excluir um intervalo de órbitas do Estacionamento de Chamada.

## Para usar o Painel de Controle do Lync Server para exclui um intervalo de órbitas do Estacionamento de Chamada

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Recursos de Voz** e em **Estacionamento de Chamada(Call Park)**.

4.  No campo de pesquisa da página **Estacionamento de chamada**, digite todo o nome do intervalo da órbita ou parte que deseja excluir.

5.  Na lista de órbitas, clique na órbita desejada e clique em **Editar** e **Excluir**.

6.  Clique em **OK**.

## Para usar cmdlets para excluir um intervalo de órbita do Estacionamento de Chamada

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, insira:
    
        Remove-CsCallParkOrbit -Identity "<orbit range name>" 
    
    Por exemplo:
    
        Remove-CsCallParkOrbit -Identity "Redmond orbit 1"
    
    > [!NOTE]  
    > Para obter detalhes sobre mais opções, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit">Remove-CsCallParkOrbit</a>.

## Consulte Também

#### Tarefas

[Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas no Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)  

#### Outros Recursos

[Remove-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit)  
[Get-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCallParkOrbit)

