---
title: Excluir configurações de Web Service existentes
TOCTitle: Excluir configurações de Web Service existentes
ms:assetid: c2b96f4c-4b07-48e6-9ca6-55bc0e0cf5a1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182582(v=OCS.15)
ms:contentKeyID: 49308023
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir configurações de Web Service existentes

 

_**Tópico modificado em:** 2013-02-23_

Siga estas etapas para excluir uma política de Serviço Web.

## Para excluir uma política de Serviço Web

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsServerAdministrator ou CsAdministrator, faça logon em qualquer computador que está na rede na qual você implantou o Lync Server 2013.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Segurança** e em **Serviço Web**.

4.  Na página **Serviço Web**, e no campo de pesquisa, digite todo ou parte do nome da política que você deseja excluir.

5.  Na lista de políticas, clique na política que você deseja, clique em **Editar** e em **Excluir**.

6.  Clique em **OK**.

## Excluir novas definições de configurações dos serviços da Web usando cmdlets do Shell de Gerenciamento do Lync Server

Também é possível excluir definições de configurações do serviço da Web usando o Shell de Gerenciamento do Lync Server e o cmdlet **Remove-CsWebServiceConfiguration**. É possível executar este cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para excluir um conjunto específico de definições de configuração do serviço da Web

  - O seguinte comando remove as configurações de segurança do Serviço da Web aplicadas ao local Redmond:
    
        Remove-CsWebServiceConfiguration -Identity "site:Redmond"

## Para excluir todas as definições de configuração do Serviço da Web aplicadas ao escopo local

  - O seguinte comando remove todas as configurações de segurança do Serviço da Web aplicadas ao escopo do serviço:
    
        Get-CsWebServiceConfiguration -Filter "service:*" | Remove-CsWebServiceConfiguration

## Para excluir todas as definições de segurança do Serviço da Web que permitem a autenticação de certificado

  - O seguinte comando remove todas as configurações de segurança do Serviço da Web que permitem o uso de autenticação de certificados:
    
        Get-CsWebServiceConfiguration | Where-Object {$_.UseCertificateAuth -eq $True} | Remove-CsWebServiceConfiguration

Para obter detalhes, consulte [Remove-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsWebServiceConfiguration).

## Consulte Também

#### Outros Recursos

[Configurando a segurança no Lync Server 2013](lync-server-2013-configuring-authentication-in-the-lync-server-control-panel.md)

