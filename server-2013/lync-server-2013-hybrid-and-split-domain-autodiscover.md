---
title: Domínio híbrido e divido – descoberta automática
TOCTitle: Domínio híbrido e divido – descoberta automática
ms:assetid: c855bcc5-b656-4d2d-92d6-f016f2797d3a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945652(v=OCS.15)
ms:contentKeyID: 52057710
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Domínio híbrido e divido – descoberta automática

 

_**Tópico modificado em:** 2013-02-14_

Um espaço de endereço SIP compartilhado, também conhecido como implantação de *domínio dividido* ou implantação *híbrida*, é uma configuração na qual os usuários são implantados em uma implantação local e um ambiente online. O resultado desejado é ter um usuário, independentemente de onde seu servidor doméstico esteja localizado (local ou online), para fazer logon na implantação e ser redirecionado ao local de seu servidor doméstico. Para conseguir isso, o recurso de Descoberta automática do Lync Server 2013 é usado para redirecionar o usuário online para a topologia online. Isso é realizado configurando o URL de Descoberta automática usando o Shell de Gerenciamento do Lync Server e os cmdlets **Get-CsHostingProvider** e **Set-CsHostingProvider**.

## Mobilidade para a Implantação de domínio dividido

Será necessário coletar e registrar os seguintes atributos implantados:

  - No Shell de Gerenciamento do Lync Server, digite
    
        Get-CsHostingProvider

  - Nos resultados, encontre o provedor online com o atributo **ProxyFQDN**. Por exemplo, sipfed.online.lync.com.

  - Registre o valor do ProxyFQDN.

  - Habilitar federação no Painel de Controle do Lync Server local, permitindo a federação com o provedor online.

  - Habilite a federação para o provedor online. Por padrão, todos os usuários online são habilitados para federação de domínio e podem se comunicar com todos os domínios.

  - Se você for definir domínios bloqueados e permitidos, determine os domínios que permitirá ou bloqueará explicitamente.

  - Para federação online, é necessário planejar exceções de firewall, certificados e registros de host DNS (A ou AAAA, se estiver usando IPv6). Além disso, é necessário configurar as políticas de federação. Para obter detalhes, consulte [Planejamento para Federação do Servidor Lync Server e Office Communications](lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md).

