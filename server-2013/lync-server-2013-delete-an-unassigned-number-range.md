---
title: Excluir um intervalo de número não atribuído no Lync Server 2013
TOCTitle: Excluir um intervalo de número não atribuído no Lync Server 2013
ms:assetid: a8141bfb-b94d-4d0f-a7a9-2e60d10b103a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182565(v=OCS.15)
ms:contentKeyID: 49307723
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um intervalo de número não atribuído no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Use um dos seguintes procedimentos para excluir um intervalo de números não atribuídos para Comunicados.

## Para usar o Painel de Controle do Lync Server para excluir um intervalo de números não atribuídos

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Recursos de Voz** e em **Número Não Atribuído**.

4.  Na página **Número Não Atribuído**, no campo de pesquisa, digite todo ou parte do nome do intervalo numérico não atribuído que deseja excluir.

5.  Na lista de resultados de intervalos de número, clique no nome, clique em **Editar** e depois, clique em **Excluir**.

6.  Clique em **Confirmar tudo**.

## Para usar Cmdlets para excluir um intervalo de números não atribuídos

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, digite:
    
        Remove-CsUnassignedNumber -Identity "<name of unassigned number range>" 
    
    Por exemplo:
    
        Remove-CsUnassignedNumber -Identity "Unassigned range 1"
    
    > [!NOTE]  
    > Para detalhes sobre mais opções, consulte <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCallParkOrbit">Remove-CsCallParkOrbit</a>.

## Consulte Também

#### Tarefas

[Criar ou modificar um intervalo de números não atribuídos no Lync Server 2013](lync-server-2013-create-or-modify-an-unassigned-number-range.md)  

#### Outros Recursos

[Remove-CsUnassignedNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsUnassignedNumber)  
[Get-CsUnassignedNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUnassignedNumber)

