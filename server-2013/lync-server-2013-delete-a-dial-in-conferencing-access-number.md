---
title: Excluir um número de acesso conferência discada
TOCTitle: Excluir um número de acesso conferência discada
ms:assetid: 199c5d9c-0489-4ad5-a7f1-ca59fe0e6ac7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520956(v=OCS.15)
ms:contentKeyID: 49306029
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um número de acesso conferência discada

 

_**Tópico modificado em:** 2013-02-23_

Siga estas etapas para excluir um número de acesso de conferência discada.

## Exclusão de um número de acesso de conferências discadas

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Conferências**, e então em **Número de acesso discado**.

4.  Na página, clique no número de discagem que deseja excluir da lista, clique em **Editar** e clique em **Excluir**.

5.  Clique em **OK**.

## Removendo números de acesso de conferência discada usando cmdlets do Windows PowerShell

Números de acesso de conferência discada também podem ser excluídos usando o Windows PowerShell e o cmdlet **Remove-CsDialInConferencingAccessNumber**. Este cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Removendo um número de acesso de conferência discada específico

  - Este comando exclui o número de acesso de conferência discada com o SIP de Identidade:RedmondDialInAccess@litwareinc.com:
    
        Remove-CsDialInConferencingAccessNumber -Identity "sip:RedmondDialInAccess@litwareinc.com"

## Removendo todos os números de acesso de conferência discada atribuídos a uma região específica

  - Este comando exclui todos os números de acesso de conferência discada associados com a região Noroeste:
    
        Get-CsDialInConferencingAccessNumber -Region "Northwest" | Remove-CsDialInConferencingAccessNumber

## Removendo números de acesso de conferência discada baseados no idioma principal

  - Este comando exclui todos os números de acesso de conferência discada onde italiano é o idioma principal:
    
        Get-CsDialInConferencingAccessNumber | Where-Object {$_.PrimaryLanguage -eq "it-IT"} | Remove-CsDialInConferencingAccessNumber

Para maiores informações, consulte o tópico de ajuda para o cmdlet [Remove-CsDialInConferencingAccessNumber](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsDialInConferencingAccessNumber).

