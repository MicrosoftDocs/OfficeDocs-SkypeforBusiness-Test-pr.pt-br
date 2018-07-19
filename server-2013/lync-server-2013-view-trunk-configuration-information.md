---
title: Visualizar Informações de Configuração do Tronco no Lync Server 2013
TOCTitle: Visualizar Informações de Configuração do Tronco no Lync Server 2013
ms:assetid: ebe10e14-08c2-4797-9254-9ed89516d5cd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721927(v=OCS.15)
ms:contentKeyID: 49886469
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visualizar Informações de Configuração do Tronco no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-22_

As configurações do tronco SIP definem o relacionamento e as capacidades entre um Servidor de Mediação e o gateway das redes de telefone públicas comutadas (PSTN), uma central privada (PBX) ou um Controlador de Borda de Sessão (SBC) no provedor de serviço. Essas configurações realizam atividades como especificar:

  - Se o desvio de mídia deve ser ativado nos troncos.

  - As condições em que os pacotes do protocolo de controle de transporte em tempo real (RTCP) são enviados.

  - Se é necessário criptografia de protocolo de transporte seguro em tempo real (SRTP) em cada tronco.

Ao instalar o Microsoft Lync Server 2013, uma coleção global de configurações do tronco SIP são criadas para você. Além disso, os administradores pode criar coleções de configurações personalizadas no escopo do site ou no escopo do serviço (somente para o serviço de gateway PSTN).

## Exibindo Informações de Configuração do Troco SIP Usando o Painel de Controle do Lync Server

1.  Em Painel de Controle do Lync Server, clique em **Roteamento de voz** e depois clique em **Configuração do tronco**.

2.  Na guia **Configuração do tronco**, você verá uma lista de todas as suas coleções de configuração de tronco; para cada coleção você verá os valores de propriedade **Nome**, **Escopo**, **Estado** e **Desvio de mídia**, juntamente com o número de **utilizações de PSTN**, **Regras para chamar números** e **Regras de números chamados** associados com a coleção. Para exibir informações adicionais sobre um coleção de configurações de tronco, clique na coleção de interesse, clique em **Editar** e depois clique em **Exibir detalhes**. Observe que você pode exibir informações detalhadas somente de uma coleção de configurações de tronco por vez.

## Exibindo Informações de Configurações do Tronco SIP Usando os Cmdlets do Lync Server PowerShell

As configurações do tronco SIP também podem ser exibidas usando o Lync Server PowerShell e o cmdlet Get-CsTrunkConfiguration. Esse cmdlet pode ser executado do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Exibindo as Informações de Configuração do Tronco SIP

  - Para exibir informações sobre todas as suas configurações de tronco SIP, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsTrunkConfiguration
    
    Isso retornará informações parecidas com:
    
        Identity                                  : Global
        OutboundTranslationRulesList              : {}
        SipResponseCodeTranslationRulesList       : {}
        OutboundCallingNumberTranslationRulesList : {}
        PstnUsages                                : {}
        Description                               :
        ConcentratedTopology                      : True
        EnableBypass                              : False
        EnableMobileTrunkSupport                  : False
        EnableReferSupport                        : True
        EnableSessionTimer                        : False
        EnableSignalBoost                         : False
        MaxEarlyDialogs                           : 20
        RemovePlusFromUri                         : False
        RTCPActiveCalls                           : True
        RTCPCallsOnHold                           : True
        SRTPMode                                  : Required
        EnablePIDFLOSupport                       : False
        EnableRTPLatching                         : False
        EnableOnlineVoice                         : False
        ForwardCallHistory                        : False
        Enable3pccRefer                           : False
        ForwardPAI                                : False
        EnableFastFailoverTimer                   : True

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Get-CsTrunkConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsTrunkConfiguration).

