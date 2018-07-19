---
title: 'Lync Server 2013: Preparando seu ambiente para VDI'
TOCTitle: Preparando seu ambiente para VDI
ms:assetid: a3ec2e13-1a73-4b1c-a54a-8db7d4cd50f9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205154(v=OCS.15)
ms:contentKeyID: 49307674
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando seu ambiente no Lync Server 2013 para VDI

 

_**Tópico modificado em:** 2013-02-22_

Para preparar o ambiente para o plug-in VDI do Lync, o administrador deve executar o seguinte procedimento.

1.  No Lync Server 2013, certifique-se de que o EnableMediaRedirection está definido como TRUE para todos os usuários VDI. Para obter detalhes, consulte os tópicos da Ajuda para o cmdlet [New-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClientPolicy) e o cmdlet [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy).

2.  No computador do data center, instale o cliente do Lync 2013 em todas as máquinas virtuais.

3.  Nos computadores locais, instale o plug-in VDI do Lync.

