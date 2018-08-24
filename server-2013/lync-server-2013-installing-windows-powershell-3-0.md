---
title: 'Lync Server 2013: Instalando Windows PowerShell 3.0'
TOCTitle: Instalando Windows PowerShell 3.0
ms:assetid: d87bf21e-0a43-41cb-8fdc-626cedec8538
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205328(v=OCS.15)
ms:contentKeyID: 49308285
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando Windows PowerShell 3.0 para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para implantar o Lync Server 2013 com êxito, será necessário ter o Windows PowerShell 3.0 em todos os computadores que façam parte da Lync Server topologia.

Para os sistemas que executam o Windows Server 2012 ou o Windows Server 2012 R2, não será necessário fazer nada aqui, e você poderá passar para o estágio seguinte da implantação, porque o PowerShell 3.0 está incluído nos sistemas operacionais.

> [!IMPORTANT]  
> Mas, para os sistemas que executam o Windows Server 2008 R2 SP1, será necessário instalar o PowerShell 3.0 como pré-requisito antes da instalação Lync Server 2013, ou eles não funcionarão. Para instalar o PowerShell 3.0, consulte o <a href="http://go.microsoft.com/fwlink/p/?linkid=329800">Windows Management Framework 3.0</a>. Este é um link direto para a página de download do PowerShell 3.0, juntamente com as informações relacionadas à instalação com êxito.

Após a instalação, ou quando você desejar apenas verificar e se certificar antes de continuar com a implantação do Lync Server, confirme se o PowerShell 3.0 que está no servidor é bastante direto se você fizer isso:

1.  No servidor que você deseja verificar, escolha **Iniciar**, clique em **Todos os Programas**, **Acessórios**, **Windows PowerShell**, e em **Windows PowerShell**.

2.  No console do Windows PowerShell, digite o seguinte comando no prompt de comando e pressione ENTER:
    
        Get-Host | Select-Object Version

3.  Se o Windows PowerShell 3.0 tiver sido instalado, você verá um resultado semelhante ao seguinte:
    
        Version
        -------
        3.0

