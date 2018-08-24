---
title: Excluir um grupo de agentes
TOCTitle: Excluir um grupo de agentes
ms:assetid: df385fd1-62f4-42b7-a349-4eb38dea50c8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182597(v=OCS.15)
ms:contentKeyID: 49308355
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um grupo de agentes

 

_**Tópico modificado em:** 2012-11-01_

Use um dos seguintes procedimentos para excluir um grupo de agentes.

## Para usar o Painel de Controle do Lync Server para excluir um grupo de agentes

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Grupos de Resposta** e clique em **Grupo**.

4.  Na página **Grupos de Resposta**, digite todo ou parte do nome do grupo de agentes que você deseja excluir no campo de pesquisa.

5.  Na lista de resultados, clique no grupo que deseja excluir, em **Editar** e em **Excluir**.

6.  Clique em **OK**.

## Para usar cmdlets para excluir um grupo de agentes

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute:
    
        Get-CsRgsAgentGroup -Identity <Application Server service> -Name "<name of agent group>" | Remove-CsRgsAgentGroup
    
    Por exemplo:
    
        Get-CsRgsAgentGroup -Identity service:ApplicationServer:redmond.contoso.com -Name "Human Resources" | Remove-CsRgsAgentGroup

## Consulte Também

#### Tarefas

[Criar ou modificar um grupo de agente no Lync Server 2013](lync-server-2013-create-or-modify-an-agent-group.md)  

#### Outros Recursos

[Remove-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsRgsAgentGroup)  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsRgsAgentGroup)

