---
title: Criar ou Modificar um Conjunto de Configurações do Servidor de Borda A/V
TOCTitle: Criar ou Modificar um Conjunto de Configurações do Servidor de Borda A/V
ms:assetid: 43899518-59c6-4be4-8892-d6f6207bfaab
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688039(v=OCS.15)
ms:contentKeyID: 49886196
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou Modificar um Conjunto de Configurações do Servidor de Borda A/V

 

_**Tópico modificado em:** 2012-11-01_

O serviço de Borda A/V fornece uma forma para seus usuários internos (usuários que não estão logados na sua rede organizacional) a compartilhar áudio e vídeo com usuários externos (usuários que não estão logados na sua rede organizacional). O serviço de Borda A/V é primariamente gerenciado utilizando definições de configuração de Borda A/V, configuração que pode ser definida no escopo do local ou no escopo do serviço (isto é, pode ser configurado para um serviço de Borda A/V individual.

Ao instalar o Lync Server, uma coleção global de definições de configuração de Borda A/V é criada para você. Além disso, você pode utilizar o Shell de Gerenciamento do Lync Server e o cmdlet New-CsAVEdgeConfiguration para criar novas configurações no escopo do local ou no escopo do serviço (isto é, para um servidor de Borda A/V individual). Se você criar novas configurações, tenha em mente que:

  - As configurações definidas no escopo de serviço (isto é, em um servidor individual) tem prioridade sobre qualquer outra coisa.

  - As configurações definidas no escopo do local têm prioridade sobre configurações definidas no escopo global. Entretanto, as configurações de escopo de serviço também irão substituir configurações de escopo de local.

  - As configurações no escopo global serão utilizadas apenas se não houver configurações definidas no serviço no servidor individual e se não houver configurações locais para o site onde o servidor está localizado.

Qualquer configuração pode ser modificada utilizando o cmdlet Set-CsAVEdgeConfiguration. Para mais informações, consulte os tópicos de ajuda para [New-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAVEdgeConfiguration) e o cmdlet [Set-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsAVEdgeConfiguration).

## Criando uma nova definição de configuração de Borda A/V no escopo do local

  - O comando a seguir criar uma nova coleção de definições de configuração de Borda A/V para o site Redmond:
    
        New-CsAVEdgeConfiguration -Identity "site:Redmond"

## Criando uma definição de configuração de Borda A/V personalizada no escopo do local

  - Por não haver parâmetros adicionais incluídos, essas novas configurações utilizarão os valores padrão para o serviço de Borda A/V. De forma alternativa, você pode adicionar parâmetros e valores de parâmetros para criar uma coleção personalizada. Por exemplo, este comando define a propriedade MaxTokenLifetime para 4 horas (04 horas : 00 minutos : 00 segundos):
    
        New-CsAVEdgeConfiguration -Identity "site:Redmond" -MaxTokenLifetime "04:00:00"

## Criando uma definição de configuração de Borda A/V personalizada no escopo de serviço

  - Este comando cria um conjunto similar aplicado ao servidor de Borda A/V atl-edge-001.litwareinc.com:
    
        New-CsAVEdgeConfiguration -Identity "service:EdgeServer:atl-edge-001.litwareinc.com" -MaxTokenLifetime "04:00:00"

## Modificando definições de configuração de Borda A/V existentes

  - Neste exemplo, o cmdlet Set-CsAVEdgeConfiguration é utilizado para alterar o tempo de vida máximo do token para o site Redmond para 12 horas:
    
        Set-CsAVEdgeConfiguration -Identity "site:Redmond" -MaxTokenLifetime "12:00:00"

## Consulte Também

#### Tarefas

[Retornar Informações de Configuração do Servidor de Borda A/V](lync-server-2013-return-a-v-edge-server-configuration-information.md)  
[Excluir um Conjunto Existente de Configurações do Servidor de Borda A/V](lync-server-2013-delete-an-existing-collection-of-a-v-edge-server-configuration-settings.md)  

#### Outros Recursos

[Servidores de Borda Áudio/Vídeo (A/V) no Lync Server 2013](lync-server-2013-audio-video-a-v-edge-servers.md)  
[New-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsAVEdgeConfiguration)  
[Set-CsAVEdgeConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsAVEdgeConfiguration)

