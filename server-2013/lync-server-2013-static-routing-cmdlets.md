---
title: Cmdlets de roteamento estático
TOCTitle: Cmdlets de roteamento estático
ms:assetid: 71d5e0cd-8412-4383-818a-95b851a4da4b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg416492(v=OCS.15)
ms:contentKeyID: 49307085
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets de roteamento estático

 

_**Tópico modificado em:** 2016-12-08_

Com as rotas estáticas, os administradores podem predeterminar as rotas de rede adotadas pelas mensagens SIP. Quando uma mensagem é recebida por um servidor, esse servidor verifica o endereço da mensagem e a encaminha para o servidor do próximo salto pré-configurado por um administrador. Se forem configuradas corretamente, as rotas estáticas ajudarão a garantir entregas de mensagens precisas e na hora certa, com uma sobrecarga mínima imposta aos servidores.

## Cmdlets de roteamento estático

A menos que seja instruído de outra forma pela equipe de suporte da Microsoft, as rotas estáticas configuradas para Microsoft Lync Server 2013 devem ser criadas usando o cmdlet [New-CsStaticRoute](new-csstaticroute.md). Depois que uma rota for criada, você poderá usar os cmdlets CsStaticRoutingConfiguration para adicionar essa rota a uma coleção de roteamento estática.

**Roteamento estático**

  -   
    [Get-CsSipResponseCodeTranslationRule](get-cssipresponsecodetranslationrule.md)

  -   
    [New-CsSipResponseCodeTranslationRule](new-cssipresponsecodetranslationrule.md)

  -   
    [Remove-CsSipResponseCodeTranslationRule](remove-cssipresponsecodetranslationrule.md)

  -   
    [Set-CsSipResponseCodeTranslationRule](set-cssipresponsecodetranslationrule.md)

  -   
    [New-CsStaticRoute](new-csstaticroute.md)

  -   
    [Get-CsStaticRoutingConfiguration](get-csstaticroutingconfiguration.md)

  -   
    [New-CsStaticRoutingConfiguration](new-csstaticroutingconfiguration.md)

  -   
    [Remove-CsStaticRoutingConfiguration](remove-csstaticroutingconfiguration.md)

  -   
    [Set-CsStaticRoutingConfiguration](set-csstaticroutingconfiguration.md)

  -   
    [New-CsSipProxyCustom](new-cssipproxycustom.md)

  -   
    [New-CsSipProxyRealm](new-cssipproxyrealm.md)

  -   
    [New-CsSipProxyTCP](new-cssipproxytcp.md)

  -   
    [New-CsSipProxyTLS](new-cssipproxytls.md)

  -   
    [New-CsSipProxyTransport](new-cssipproxytransport.md)

  -   
    [New-CsSipProxyUseDefault](new-cssipproxyusedefault.md)

  -   
    [New-CsSipProxyUseDefaultCert](new-cssipproxyusedefaultcert.md)

  -   
    [New-CsIssuedCertId](new-csissuedcertid.md)

## Consulte Também

#### Outros Recursos

[Blog do Lync Server PowerShell](http://go.microsoft.com/fwlink/?linkid=203150%26clcid=0x416)

