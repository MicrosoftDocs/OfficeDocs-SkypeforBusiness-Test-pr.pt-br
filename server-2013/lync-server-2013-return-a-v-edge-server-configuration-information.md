---
title: Retornar Informações de Configuração do Servidor de Borda A/V
TOCTitle: Retornar Informações de Configuração do Servidor de Borda A/V
ms:assetid: b041f5a4-2387-4075-846c-ec4f99640903
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721850(v=OCS.15)
ms:contentKeyID: 49886365
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Retornar Informações de Configuração do Servidor de Borda A/V

 

_**Tópico modificado em:** 2012-11-01_

O serviço de borda de A/V fornece uma maneira para que usuários internos (usuários que entraram na rede de sua organização) compartilhem áudio e vídeo com usuários externos (usuários que não estão conectados à rede de sua organização). O serviço de borda de A/V é gerenciado principalmente usando as definições de configuração de borda A/V, que podem ser configuradas no escopo do site ou de serviço (isto é, pode ser configurado para um servidor de borda de A/V individual).

Para retornar informações sobre as definições de configuração de borda de A/V usadas em sua organização, você deve usar o Shell de Gerenciamento do Lync Server e o cmdlet Get-CsAVEdgeConfiguration. Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsAVEdgeConfiguration).

As informações retornadas do cmdlet Get-CsAVEdgeConfiguration serão semelhantes a isto:

    Identity              : Global
    MaxTokenLifetime      : 08:00:00
    MaxBandwidthPerUserKb : 10000
    MaxBandwidthPerPortKb : 3000

## Retornando informações para todas as suas definições de configuração de borda de A/V

  - O seguinte comando retorna as informações sobre todas as configurações de borda da A/V Edge usados em sua organização:
    
        Get-CsAVEdgeConfiguration

## Retornando informações para definições de configuração de borda de A/V de escopo de site

  - Para retornar informações sobre um conjunto específico de definições de configuração de borda de A/V, especifique a Identidade desse conjunto ao executar o cmdlet Get-CsAVEdgeConfiguration. Por exemplo, este comando retorna informações somente para as configurações aplicadas ao site de Redmond:
    
        Get-CsAVEdgeConfiguration -Identity "site:Redmond"

## Retornando informações para as definições de configuração de borda de A/V escopo de serviços

  - E este comando retorna informações somente para as configurações aplicadas a um servidor de borda A/V específico:
    
        Get-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

## Consulte Também

#### Tarefas

[Criar ou Modificar um Conjunto de Configurações do Servidor de Borda A/V](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)  
[Excluir um Conjunto Existente de Configurações do Servidor de Borda A/V](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)  

#### Outros Recursos

[Servidores de Borda Áudio/Vídeo (A/V) no Lync Server 2013](lync-server-2013-audio-video-a-v-edge-servers.md)

