---
title: Excluir as configurações do Registrador existente
TOCTitle: Excluir as configurações do Registrador existente
ms:assetid: ae43cd75-cae4-4f78-b037-779a2cdb583b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182571(v=OCS.15)
ms:contentKeyID: 49307785
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir as configurações do Registrador existente

 

_**Tópico modificado em:** 2013-02-23_

Siga estas etapas para excluir um Registrador Avançado.

## Para excluir um Registrador Avançado.

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Segurança** e em **Registrador Avançado**.

4.  Na página **Registrador Avançado** e no campo de pesquisa, digite todo ou parte do nome do Registrador Avançado que você deseja excluir.

5.  Na lista, clique no Registrador Avançado desejado, clique em **Editar** e em **Excluir**.

6.  Clique em **OK**.

## Removendo definições de configuração do registrador usando os cmdlets do Shell de Gerenciamento do Lync Server

Também é possível excluir as definições de configuração do Registrador usando o Shell de Gerenciamento do Lync Server e o cmdlet **Remove-CsProxyConfiguration**. Você pode executar esse cmdlet pelo Shell de Gerenciamento do Lync Server 2013 ou por uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover um conjunto específico de configurações de segurança do Registrador

  - O seguinte comando remove as configurações de segurança do Registrador aplicadas ao servidor de borda atl-edge-011.litwareinc.com:
    
        Remove-CsProxyConfiguration -Identity service:EdgeServer:atl-edge-011.litwareinc.com

## Para remover todas as configurações de segurança do Registrador aplicadas ao escopo do site

  - O seguinte comando remove todas as configurações de segurança do Registrador aplicadas ao serviço registrador:
    
        Get-CsProxyConfiguration -Filter "service:Registrar:*" | Remove-CsProxyConfiguration

## Para remover todas as configurações de segurança do Registrador que permitem a autenticação de NTLM

  - O seguinte comando exclui todas as configurações de segurança do Registrador que permite o uso de NTLM para autenticação do cliente:
    
        Get-CsProxyConfiguration | Where-Object {$_.UseNtlmForClientToProxyAuth -eq $True}| Remove-CsProxyConfiguration

Para obter detalhes, consulte [Remove-CsProxyConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsProxyConfiguration).

