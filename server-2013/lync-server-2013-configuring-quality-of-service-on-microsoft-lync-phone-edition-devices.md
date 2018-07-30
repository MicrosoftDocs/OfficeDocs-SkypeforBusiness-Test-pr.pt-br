---
title: Configurando a Qualidade de Serviço (QoS) nos Dispositivos Lync Phone Edition da Microsoft
TOCTitle: Configurando a Qualidade de Serviço (QoS) nos Dispositivos Lync Phone Edition da Microsoft
ms:assetid: a6eb2620-a512-4ab6-bdfd-eb76be43bbfe
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205137(v=OCS.15)
ms:contentKeyID: 49307710
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a Qualidade de Serviço (QoS) nos Dispositivos Lync Phone Edition da Microsoft

 

_**Tópico modificado em:** 2012-11-01_

Embora a qualidade de serviço (QoS) não seja ativada como padrão para iPhones, o QoS é ativado como padrão para dispositivos que executam o Lync Phone Edition. (Esses dispositivos são referidos comumente como UC ou telefones de Comunicações Unificadas). Para verificar isso, execute o seguinte comando do Windows PowerShell no Shell de Gerenciamento do Lync Server:

    Get-CsUCPhoneConfiguration

Se você não fizer nenhuma alteração em suas configurações de telefone UC, então você receberá informações de volta como essas:

    Identity             : Global
    CalendarPollInterval : 00:03:00
    EnforcePhoneLock     : True
    PhoneLockTimeout     : 00:10:00
    MinPhonePinLength    : 6
    SIPSecurityMode      : High
    VoiceDiffServTag     : 40
    Voice8021p           : 0
    LoggingLevel         : Off

Para fins de Qualidade de Serviço, apenas uma dessas propriedades é de interesse: VoiceDiffServTag. O VoiceDiffServTag representa o valor DSCP atribuído ao tráfego de voz que provém de um dispositivo Lync Phone Edition.

> [!NOTE]  
> O parâmetro Voice8021p não é mais suportado no Lync Server 2013. O parâmetro é ainda válido para compatibilidade reversa com o Microsoft Lync Server 2010; no entanto, não tem efeito em dispositivos usados com o Lync Server 2013.

Na maioria das redes, marcar pacotes do Lync Phone Edition com um VoiceDiffServTag de 40 não deve causar problemas. No entanto, 40 não é o valor geralmente usado para tráfego de áudio; em vez disso, o tráfego de áudio é quase sempre marcado com o código DSCP 46. Para manter a consistência em toda a rede, você pode alterar a propriedade VoiceDiffServTag dos seus telefones UC para 46.

Para fazer isso, você pode usar o Windows PowerShell ou o Painel de Controle do Lync Server. Para modificar o valor do VoiceDiffServTag usando o Windows PowerShell, execute o comando a seguir no Shell de Gerenciamento do Lync Server:

    Set-CsUCPhoneConfiguration -VoiceDiffServTag 46

O comando anterior redefine a coleção global das configurações do telefone UC. Observe, no entanto, que as configurações do telefone UC podem também ser atribuídas ao escopo do site. Para modificar as configurações do telefone UC no escopo do site, é necessário especificar a identidade do site. Por exemplo:

    Set-CsUCPhoneConfiguration -Identity "site:Redmond" -VoiceDiffServTag 46

Você pode também usar o seguinte comando para modificar simultaneamente suas configurações de telefone UC:

    Get-CsUCPhoneConfiguration | Set-CsUCPhoneConfiguration -VoiceDiffServTag 46

Se você preferir fazer essa alteração usando o Painel de Controle do Lync Server, então inicie o Painel de Controle e depois conclua o seguinte procedimento:

1.  Clique em **Clientes** e depois em **Configuração de Dispositivo**.

2.  Na guia **Configuração de Dispositivo**, clique duas vezes na coleção de configurações que deseja modificar (por exemplo, **Global**).

3.  Na caixa de diálogo **Editar Configuração de Dispositivo**, defina o valor da caixa **Qualidade de serviço (QoS) de voz** para **46** e depois clique em **Confirmar**.

Se você tiver várias coleções, será necessário repetir esse processo para cada coleção de configurações de telefone UC. O Painel de Controle do Lync Server não permitirá modificar simultaneamente várias coleções de configuração.

Se você tiver dispositivos que não são baseados no sistema operacional Windows (como iPhones), esses dispositivos em sua organização não serão afetados pela mudança da configuração do VoiceDiffServTag. Se desejar alterar os valores DSCP nesses dispositivos, será necessário consultar o manual de administração para cada um de seus tipos de dispositivos.

