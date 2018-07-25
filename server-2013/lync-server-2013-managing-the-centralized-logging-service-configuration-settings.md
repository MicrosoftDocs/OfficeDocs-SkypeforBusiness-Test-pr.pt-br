---
title: Gerenciando as configurações do serviço de registro em log centralizado usando PowerShell
TOCTitle: Gerenciando as configurações do serviço de registro em log centralizado usando PowerShell
ms:assetid: f455c3aa-0061-413d-bdfb-a3e78f82723d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721938(v=OCS.15)
ms:contentKeyID: 49886482
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando as configurações do serviço de registro em log centralizado usando PowerShell

 

_**Tópico modificado em:** 2012-11-01_

O Serviço de Log Centralizado é controlado e configurado por definições e parâmetros criados e usados pelo Controlador do Serviço de Log Centralizado (CLSController) para enviar comandos para o Agente Serviço de Log Centralizado (CLSAgent) do computador de um indivíduo. O agente processa os comandos enviados a ele e (no caso de um comando Iniciar) usa a configuração dos cenários, provedores, tamanho de log, duração de rastreamento e sinalizadores para começar a coletar logs de rastreamento de acordo com as informações de configuração fornecidas.


> [!IMPORTANT]  
> Nem todos os cmdlets do Windows PowerShell listados para o Serviço de Log Centralizado devem ser utilizados com implantações locais do Lync Server 2013. Embora possam parecer funcionar, os seguintes cmdlets não foram projetados para funcionar com implantações locais do Lync Server 2013:<ul><li><p><strong>Cmdlets CsClsRegion:</strong> <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsRegion">Get-CsClsRegion</a>, <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsRegion">Set-CsClsRegion</a>, <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsRegion">New-CsClsRegion</a> e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsRegion">Remove-CsClsRegion</a>.</p></li>
> 
> <li><p><strong>Cmdlets CsClsSearchTerm:</strong> <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsSearchTerm">Get-CsClsSearchTerm</a> e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsSearchTerm">Set-CsClsSearchTerm</a>.</p></li>
> 
> 
> <li><p><strong>Cmdlets CsClsSecurityGroup:</strong> <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsSecurityGroup">Get-CsClsSecurityGroup</a>, <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsSecurityGroup">Set-CsClsSecurityGroup</a>, <a href="https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsSecurityGroup">New-CsClsSecurityGroup</a> e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsSecurityGroup">Remove-CsClsSecurityGroup</a>.</p></li></ul>
> As configurações definidas nestes cmdlets não impedirão nem provocarão nenhum comportamento adverso, mas elas são projetadas para usar com o Microsoft Office 365 e não gerarão os resultados esperados em implantações locais. Isso não quer dizer que não há uso para esses cmdlets em implantações locais, mas sua utilização é um tópico mais avançado que não é abordado nesta documentação.


## Nesta seção

Os tópicos nesta seção definem as opções de configuração, parâmetros e configurações do Serviço de Log Centralizado. Informações sobre como configurar o Serviço de Log Centralizado, como recuperar as configurações, a criação de cenários, o gerenciamento de grupos de segurança do Serviço de Log Centralizado, pesquisar e mais estão contidos nos tópicos que seguem.

  - [Gerenciando a configuração do computador, local e de serviço de registro em log centralizado global](lync-server-2013-managing-computer-site-and-global-centralized-logging-service-configuration.md)

  - [Configurando provedores do serviço de registro em log centralizado](lync-server-2013-configuring-providers-for-centralized-logging-service.md)

  - [Configurando cenários para o serviço de registro em log centralizado](lync-server-2013-configuring-scenarios-for-the-centralized-logging-service.md)

## Consulte Também

#### Conceitos

[Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md)  
[Cmdlets de registro em log centralizado](https://docs.microsoft.com/en-us/powershell/module/skype/)

