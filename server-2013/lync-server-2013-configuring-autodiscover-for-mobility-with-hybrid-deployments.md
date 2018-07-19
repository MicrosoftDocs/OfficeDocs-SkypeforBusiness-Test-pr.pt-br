---
title: 'Lync Server 2013: Configurando Autodiscover para mobilidade com implantações híbridas'
TOCTitle: Configurando Autodiscover para mobilidade com implantações híbridas
ms:assetid: f838af79-d8b4-4122-b81c-7889573d143e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ215885(v=OCS.15)
ms:contentKeyID: 49308656
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Autodiscover no Lync Server 2013 para mobilidade com implantações híbridas

 

_**Tópico modificado em:** 2014-06-18_

Implantações híbridas são configurações que utilizam o serviço de nuvem do Microsoft Lync Online e a implantação local. neste tipo de configuração, o serviço de descoberta automática deve poder localizar a localização real do usuário, ou seja, a descoberta automática ajuda a localizar a conta do usuário e a localização do servidor que hospeda a conta do usuário, independente de esta na implantação local ou na implantação Skype for Business Online.

Por exemplo, se uma conta de usuário está hospedada em um servidor no Skype for Business Online, a tentativa de localizar o usuário acontecerá da seguinte forma, em processo conhecido como *detectabilidade* :

  - O usuário inicia uma tentativa de conexão com a implantação local, **contoso.com**.

  - A tentativa é enviada a lyncdiscover.contoso.com, o nome de DNS associado ao serviço de descoberta automática.

  - A descoberta automática refere-se ao pool registrador assumido em contoso.com na implantação local e fornece informações sobre o servidor que realmente está hospedado o usuário no Skype for Business Online. A descoberta automática envia ao usuário uma referência do serviço online de descoberta automática do **lync.com**.

  - O usuário inicia uma tentativa de conexão com o serviço online de descoberta automática do lync.com e pode localizar a conta do usuário e o servidor que o está hospedando.

Para permitir que os clientes móveis descubram a implantação em que o servidor que hospeda o usuário está localizado, é necessário configurar o serviço de descoberta automática com uma nova URL. Para configurar o serviço de descoberta automática, faça o seguinte:

## Configurando a descoberta automática para implantações híbridas

1.  Utilize Get-CsHostingProvider para recuperar o valor do atributo ProxyFQDN.

2.  A partir do Shell de Gerenciamento do Lync Server, digite
    
        Set-CsHostingProvider -Identity [identity] -AutodiscoverUrl https://webdir.online.lync.com/autodiscover/autodiscoverservice.svc/root
    
    Onde \[identidade\] é substituído pelo nome do domínio do espaço de endereço SIP compartilhado.

## Consulte Também

#### Outros Recursos

[Get-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsHostingProvider)  
[Set-CsHostingProvider](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsHostingProvider)

