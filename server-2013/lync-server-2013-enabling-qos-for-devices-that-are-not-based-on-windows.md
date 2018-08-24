---
title: Habilitando QoS para dispositivos não baseado no Windows
TOCTitle: Habilitando QoS para dispositivos não baseado no Windows
ms:assetid: 26f793df-aef8-4028-9e3b-6c2c37ea61b9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204750(v=OCS.15)
ms:contentKeyID: 49306175
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitando QoS para dispositivos não baseado no Windows

 

_**Tópico modificado em:** 2012-11-01_

Ao instalar o Microsoft Lync Server 2013, a Qualidade do Serviço (QoS) não estará habilitado para qualquer dispositivo usado na organização que utiliza um sistema operacional diferente do Windows. É possível verificar isso executando o seguinte comando dentro do Shell de Gerenciamento do Lync Server 2013:

    Get-CsMediaConfiguration

Assumindo que você não realizou qualquer mudança em suas definições de configuração de mídia, você deve obter informação semelhante ao seguinte:

    Identity                          : Global
    EnableQoS                         : False
    EncryptionLevel                   : RequireEncryption
    EnableSiren                       : False
    MaxVideoRateAllowed               : VGA600K
    EnableG722StereoCodec             : True
    EnableH264Codec                   : True
    EnableAdaptiveBandwidthEstimation : True

Se a propriedade EnableQoS está definida para False (como no resultado anterior) isto significa que a Qualidade do Serviço não está habilitada para computadores e dispositivos que usam um sistema operacional diferente do Windows. O QoS está habilitado por padrão para dispositivos do Lync Phone Edition; no entanto, é possível desabilitar a Qualidade do Serviço para o Lync Phone Edition.

Para habilitar a Qualidade do Serviço no escopo global, execute o seguinte comando dentro do Shell de Gerenciamento do Lync Server:

    Set-CsMediaConfiguration -EnableQoS $True

O comando anterior habilita o QoS no escopo global; no entanto, é importante observar que as definições de configuração de mídia também podem ser aplicadas ao escopo local. Se você precisa habilitar a Qualidade do Serviço para um site, você deve incluir a Identidade das definições de configuração ao chamar o Set-CsMediaConfiguration. Por exemplo, este comando habilita o QoS para o site Redmond:

    Set-CsMediaConfiguration -Identity site:Redmond -EnableQoS $True

> [!NOTE]  
> Você não precisa habilitar o QoS no escopo local? Isto depende. As configurações atribuídas ao escopo local têm precedência sobre as configurações atribuídas para o escopo global. Suponha que você habilitou o QoS no escopo global, mas desabilitou no escopo local (para o local Redmond). Neste caso, a Qualidade do Serviço será desabilitada para o local Redmond. isto ocorre porque as configurações locais têm precedência. Para habilitar o QoS para o local Redmond, você precisará fazer isso usando as definições de configuração de mídia aplicada a este site.

Se você deseja habilitar simultaneamente o QoS para todas as suas definições de configuração de mídia (independente do escopo), execute este comando no Shell de Gerenciamento do Lync Server:

    Get-CsMediaConfiguration | Set-CsMediaConfiguration -EnableQoS $True

É possível desabilitar o QoS para dispositivos que usam um sistema operacional diferente do Windows, configurando o valor da propriedade EnableQoS para False. Por exemplo:

    Set-CsMediaConfiguration -Identity site:Redmond -EnableQoS $False

Isto oferece a habilidade de implementar o QoS em algumas partes da sua rede (por exemplo, no local Redmond) enquanto deixa a Qualidade do Serviço desabilitada em outras partes da sua rede.

O QoS pode ser habilitado e desabilitado somente usando o Shell de Gerenciamento do Lync Server. Estas opções não estão disponíveis no Painel de Controle do Lync Server.

