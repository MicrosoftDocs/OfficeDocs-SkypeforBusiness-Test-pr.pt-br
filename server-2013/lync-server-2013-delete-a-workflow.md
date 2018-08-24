---
title: Excluir um fluxo de trabalho
TOCTitle: Excluir um fluxo de trabalho
ms:assetid: 0469a6b8-ce1e-459b-bc3d-4c8adf2d97d5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520944(v=OCS.15)
ms:contentKeyID: 49305719
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um fluxo de trabalho

 

_**Tópico modificado em:** 2012-11-01_

Use um dos procedimentos a seguir para excluir um fluxo de trabalho.

## Para usar Painel de Controle do Lync Server exclua um fluxo de trabalho

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Grupos de Resposta** e clique em **Fluxo de Trabalho**.

4.  Na página do **Fluxo de Trabalho**, clique em **Criar ou editar um fluxo de trabalho**.

5.  No campo de pesquisa **Selecionar um Serviço**, insira parte ou todo o nome do serviço de **ApplicationServer** que hospeda o fluxo de trabalho que você quer excluir.

6.  Na lista de serviços, clique no serviço desejado e clique em **OK**.
    
    > [!NOTE]  
    > A página da Web do Ferramenta de Configuração de Grupo de Resposta é aberta. Você também pode abrir a página da Web do Ferramenta de Configuração de Grupo de Resposta a partir de um navegador, conectando ao <strong>https://<em>&lt;webPoolFqdn&gt;</em>/RgsConfig</strong>.

7.  Sob **Gerenciar um Fluxo de Trabalho Existente**, localize o fluxo de trabalho que você quer excluir e, sob **Ação**, clique em **Excluir**.

8.  Clique em **Sim**.

## Para usar cmdlets para excluir um fluxo de trabalho

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Na linha de comando, execute:
    
        Get-CsRgsWorkflow -Identity <Application Server service> -Name "<name of workflow>" | Remove-CsRgsWorkflow
    
    Por exemplo:
    
        Get-CsRgsWorkflow -Identity service:ApplicationServer:redmond.contoso.com -Name "Help Desk" | Remove-CsRgsWorkflow

