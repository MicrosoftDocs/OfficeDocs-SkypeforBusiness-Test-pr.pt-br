---
title: 'Lync Server 2013: Implantando um servidor ou aparelho de filial persistente - Tarefas do site central'
TOCTitle: Implantando um servidor ou aparelho de filial persistente - Tarefas do site central
ms:assetid: 0f631a36-fc2e-41cd-8a0d-f27e84f4a89e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398189(v=OCS.15)
ms:contentKeyID: 49305899
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando um servidor ou aparelho de filial persistente com o Lync Server 2013 - Tarefas do site central

 

_**Tópico modificado em:** 2012-10-18_

Conclua as tarefas seguintes no local central. Se estiver implantando um Servidor de Filial Persistente, ignore a primeira tarefa.

> [!IMPORTANT]  
> Antes de realizar as tarefas desta seção, as condições a seguir devem estar em vigor:<ul><li><p>O Lync Server deve ser instalado no site central.</p></li><li><p>Um técnico de instalação do site de filial deve ser adicionado ao grupo RTCUniversalSBATechnicians.</p></li></ul>
> Além disso, recomendamos que você faça o seguinte:<ul><li><p>Implantar um servidor DHCP no site de filial para permitir que os cliente obtenham os endereços IP.</p></li><li><p>Como alternativa para implantar um servidor DHCP em cada site de filial, habilite o DHCP do Lync Server no Aparelho de Filial Persistente ou Servidor de Filial Persistente utilizando o cmdlet Shell de Gerenciamento do Lync Server<strong>Set-CsRegistrarConfiguration –EnableDHCPServer $true</strong>. Para obter detalhes, consulte a seção “Requisitos de Hardware e Software” do <a href="lync-server-2013-branch-site-resiliency-requirements.md">Requisitos de resiliência do site da filial para Lync Server 2013</a> na documentação de Planejamento.</p></li></ul>

## Nesta seção

  - [Adicionar um Aplicativo de Filial Persistente ao Active Directory no Lync Server 2013](lync-server-2013-add-a-survivable-branch-appliance-to-active-directory.md)

  - [Adicionar sites de filial a sua topologia no Lync Server 2013](lync-server-2013-add-branch-sites-to-your-topology.md)

  - [Definir um Servidor ou Aparelho de Filial Persistente no Lync Server 2013](lync-server-2013-define-a-survivable-branch-appliance-or-server.md)

