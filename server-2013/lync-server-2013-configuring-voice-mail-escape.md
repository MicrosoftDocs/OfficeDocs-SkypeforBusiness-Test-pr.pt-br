---
title: Configurando escape da caixa postal no Lync Server 2013
TOCTitle: Configurando escape da caixa postal no Lync Server 2013
ms:assetid: a1d19e6c-82ff-4768-8ae5-da981368ce40
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688157(v=OCS.15)
ms:contentKeyID: 49886338
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando escape da caixa postal no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

Quando um usuário configura ligação simultânea para um celular, um chamador geralmente é roteado para a caixa postal pessoal do usuário, caso o celular esteja desligado, sem bateria ou fora de área. Com o Microsoft Lync Server 2013, os usuários podem optar por ter suas chamadas de trabalho roteadas para seu sistema de caixa postal corporativa. Especificamente, um timer pode ser configurado e, se a chamada for atendida pela caixa postal da operadora dentro do intervalo de tempo definido, o Lync Server 2013 desconectará do sistema de caixa postal da operadora (e da caixa postal pessoal do usuário), enquanto os pontos de extremidade restantes do usuário no sistema corporativo continuarão a tocar. Desta maneira, o chamador será roteado automaticamente para a caixa postal corporativa do usuário.

Essa configuração é realizada usando o cmdlet do Shell de Gerenciamento do Lync Server, Set-CsVoicePolicy, no nível de política de voz, com os seguintes parâmetros.

## Configurar escape de caixa postal

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Especifique os parâmetros a seguir para **Set-CsVoicePolicy**:
    
      - **EnableVoicemailEscapeTimer** - Ativa ou desativa o timer de escape
    
      - **PSTNVoicemailEscapeTimer** - Especifica o valor do tempo limite em milissegundos. O valor padrão é 1500 milissegundos e o valor pode ir de 0 a 8000 milissegundos.

## Exemplo

    Set-CsVoicePolicy UserVoicePolicy -EnableVoiceMailEscapeTimer $true - PSTNVoicemailEscapeTimer 2000
    
    Set-CsVoicePolicy -Identity site:SitePolicy -EnableVoiceMailEscapeTimer $true -PSTNVoicemailEscapeTimer 1500

## Consulte Também

#### Outros Recursos

[Configurando políticas de voz e registros de uso de PSTN para autorizar recursos e privilégios de chamada no Lync Server 2013](lync-server-2013-configuring-voice-policies-and-pstn-usage-records-to-authorize-calling-features-and-privileges.md)

