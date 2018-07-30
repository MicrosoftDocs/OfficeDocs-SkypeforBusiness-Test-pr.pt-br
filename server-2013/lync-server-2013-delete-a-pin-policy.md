---
title: Excluir uma política PIN
TOCTitle: Excluir uma política PIN
ms:assetid: 7c378927-2e41-418e-9721-327021bd2e45
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521020(v=OCS.15)
ms:contentKeyID: 49307232
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir uma política PIN

 

_**Tópico modificado em:** 2013-02-23_

Siga estas etapas para excluir uma política de PIN (número de identificação pessoal).

> [!NOTE]  
> Não é possível excluir a política PIN global.

## Para excluir uma política de PIN em Painel de Controle do Lync Server 2013

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Política de PIN**.

4.  Na página **Política de PIN** e no campo de pesquisa, digite o nome todo ou parcial da política que deseja excluir.

5.  Na lista de políticas, clique na política que você deseja, em **Editar** e em **Excluir**.

6.  Clique em **OK**.

## Remover Políticas de PIN Usando Shell de Gerenciamento do Lync Server e Cmdlets

Você pode excluir políticas de PIN usando Windows PowerShell e o cmdlet Remove-CsPinPolicy. Você pode executar esse cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Remover uma Política de PIN Específica

  - Este comando remove a política de PIN com a Identidade RedmondPinPolicy:
    
        Remove-CsPinPolicy -Identity "RedmondPinPolicy"

## Remover Todas as Políticas de PIN Aplicadas ao Escopo do Site

  - Este comando remove todas as políticas de PIN configuradas no escopo do site:
    
        Get-CsPinPolicy -Filter "site:*" | Remove-CsPinPolicy

## Remover todas as Políticas de PIN que Permitem o Uso de Padrões Comuns

  - Isso remove todas as políticas de PIN que permitem o uso dos padrões comuns:G
    
        et-CsPinPolicy | Where-Object {$_.AllowCommonPatterns -eq $True} | Remove-CsPinPolicy

Para mais informações, veja o tópico de ajuda para [Remove-CsPinPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsPinPolicy) cmdlet.

