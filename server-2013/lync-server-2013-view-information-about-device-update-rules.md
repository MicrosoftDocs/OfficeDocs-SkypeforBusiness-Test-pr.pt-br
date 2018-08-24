---
title: Exibir informações sobre as regras de atualização de dispositivo
TOCTitle: Exibir informações sobre as regras de atualização de dispositivo
ms:assetid: d6677ca4-024b-4816-8511-8d7630788107
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994077(v=OCS.15)
ms:contentKeyID: 52057735
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir informações sobre as regras de atualização de dispositivo

 

_**Tópico modificado em:** 2013-02-23_

Visualize detalhes de regras de atualização de dispositivo que já tenham sido importadas, incluindo o tipo, modelo e marca de dispositivos aos quais a atualização se aplica; versão e tipo da atualização, local e pool para ela. Há informações disponíveis para todas as regras de atualização de dispositivos importadas - aquelas com aprovação pendente, implantadas (aprovadas), reimplementadas (restauradas), e aquelas que você decidiu não utilizar (resetar). Acesse essas informações a partir do Painel de Controle do Lync Server ou do Windows PowerShell.

> [!NOTE]  
> Para detalhes sobre como importar, aprovar, resetar, restaurar e remover regras, consulte os tópicos listados em <a href="lync-server-2013-device-update-rules.md">Regras de atualização de dispositivo no Lync Server 2013</a>.

## Para visualizar uma regra de atualização de dispositivo utilizando Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e então clique no botão de navegação **Atualização de Dispositivo**. Regras importadas são listadas na página **Atualização de dispositivos**.

## Visualização das regras de atualização de dispositivo por uso de Cmdlets Windows PowerShell

Informação detalhada sobre todas as regras de atualização do seu dispositivo também podem ser visualizadas pelo uso de Windows PowerShell e do cmdlet **Get-CsDeviceUpdateRule**. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota de Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

## Para visualizar todas as suas regras de atualização de dispositivo

  - O comando a seguir retorna informações sobre todas as regras de atualização de dispositivo configuradas para uso em sua organização:
    
        Get-CsDeviceUpdateRule
    
    O comando retorna informações similares às seguintes, para cada uma de suas regras de atualização de dispositivo:
    
        Identity        : Service:WebServer:pool0.vdomain.com/2de8cbf6-9441-4f61-b755-1e4bef1effde
        Id              : 2de8cbf6-9441-4f61-b755-1e4bef1effde
        DeviceType      : UCPhone
        Brand           : Microsoft
        Model           : CPE
        Revision        : A
        Locale          : ENU
        UpdateType      : CPE
        ApprovedVersion :
        RestoreVersion  :
        PendingVersion  : 4.0.7577.4066

## Para visualizar todas as regras de atualização de dispositivo em um servidor Web específico

  - Para visualizar as regras de atualização de dispositivo em um computador específico, use o parâmetro Filtro seguido da Identidade do servidor e do caractere coringa (\*). Por exemplo:
    
        Get-CsDeviceUpdateRule -Filter "service:WebServer:atl-cs-001.litwareinc.com*"

Para detalhes, consulte o tópico Ajuda para o cmdlet [Get-CsDeviceUpdateRule](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsDeviceUpdateRule).

