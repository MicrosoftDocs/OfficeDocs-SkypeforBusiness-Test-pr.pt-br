---
title: Excluir um Conjunto Existente de Configurações do Servidor de Borda A/V
TOCTitle: Excluir um Conjunto Existente de Configurações do Servidor de Borda A/V
ms:assetid: 668d3613-e464-4b68-967a-cfff90b9ce4b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688077(v=OCS.15)
ms:contentKeyID: 49886244
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir um Conjunto Existente de Configurações do Servidor de Borda A/V

 

_**Tópico modificado em:** 2012-11-01_

O Serviço de Borda A/V oferece uma maneira de seus usuários internos (conectados à sua rede organizacional) compartilharem áudio e vídeo com usuários externos (não conectados à sua rede organizacional). O Serviço de Borda A/V é gerenciado principalmente com o uso das configurações de Borda A/V, as quais podem ser definidas no escopo do site ou do serviço (ou seja, podem ser definidas para um Servidor de Borda A/V individual).

Quando você instala o Lync Server, um conjunto global de configurações de Borda A/V é criado para você. Esse conjunto global não pode ser excluído. No entanto, você pode usar o Shell de Gerenciamento do Lync Server e o cmdlet Remove-CsAVEdgeConfiguration para "redefinir" o conjunto global, ou seja, redefinir todas as propriedades do conjunto global para os valores padrão. Por exemplo, se você tiver definido a propriedade MaxTokenLifetime para 16 horas, ela será redefinida para seu valor padrão de oito horas.

No entanto, conjuntos de configurações personalizadas criados no escopo do site ou do serviço podem ser excluídos com o uso do cmdlet Remove-CsAVEdgeConfiguration. Se você excluir configurações de site, os Servidores de Borda A/V desse site serão gerenciados pelas configurações globais. Se excluir as configurações do escopo do serviço, o servidor será gerenciado pelas configurações do site (se houver) ou pelas configurações globais se não houver configurações de site disponíveis.

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Remove-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsAVEdgeConfiguration).

## Redefinindo o conjunto global

  - O comando a seguir redefine o conjunto global de configurações de Borda A/V:
    
        Remove-CsAVEdgeConfiguration -Identity "global"

## Removendo um conjunto do escopo do site

  - Este comando remove as configurações de Borda A/V aplicadas ao site de Redmond:
    
        Remove-CsAVEdgeConfiguration -Identity "site:Redmond"

## Removendo um conjunto do escopo do serviço

  - Este comando remove as configurações aplicadas ao Servidor de Borda A/V atl-edge-001.litwareinc.com:
    
        Remove-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com"

## Consulte Também

#### Tarefas

[Retornar Informações de Configuração do Servidor de Borda A/V](lync-server-2013-return-a-v-edge-server-configuration-information.md)  
[Criar ou Modificar um Conjunto de Configurações do Servidor de Borda A/V](lync-server-2013-create-or-modify-a-collection-of-a-v-edge-server-configuration-settings.md)  

#### Outros Recursos

[Servidores de Borda Áudio/Vídeo (A/V) no Lync Server 2013](lync-server-2013-audio-video-a-v-edge-servers.md)  
[Remove-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsAVEdgeConfiguration)

