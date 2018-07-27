---
title: 'Lync Server 2013: Configuração do Roteamento Baseado em Local para conferência'
TOCTitle: Configuração do Roteamento Baseado em Local para conferência
ms:assetid: d8c708cc-a1b1-48b1-808c-a64df15f7701
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362846(v=OCS.15)
ms:contentKeyID: 56270478
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração do Roteamento Baseado em Local para conferência no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O aplicativo de Configuração de Roteamento com Base no Local da Conferência depende da configuração no Roteamento com Base no Local do Lync Server 2013. As configurações principais são as seguintes:

  - O local de participantes ingressando em uma reunião é determinado com base em seus sites de rede. Um site de rede e sub-redes associadas deve ser definido no Lync Server de modo a impor o Roteamento com Base no Local.

  - Para impor o Roteamento com Base no Local de reuniões, os participantes do Lync devem ser habilitados para o Roteamento com Base no Local.

  - Para impor o Roteamento com Base no Local de extremidades PSTN ingressantes em reuniões, o tronco SIP usual para conexão a extremidades PSTN deve ser configurado para Roteamento com Base no Local.

Para saber mais sobre implantação e configuração de Roteamento com Base no Local do Lync Server 2013, consulte Configuração [Roteamento Baseado no Local](lync-server-2013-configuring-location-based-routing.md).

## Habilitando o aplicativo de Configuração de Roteamento com Base no Local da Conferência

O aplicativo de Configuração de Roteamento com Base no Local da Conferência está desabilitado por padrão. Antes de habilitar esse aplicativo, é preciso determinar os direitos de prioridade para assinatura deste. Para determinar essa prioridade, execute o seguinte cmdlet em Shell de Gerenciamento do Lync Server:

Get-CsServerApplication -Identity Service:Registrar:\<Pool FQDN\>

Nesse cmdlet, \<Pool FQDN\> se encontra o pool no qual o aplicativo de Configuração de Roteamento com Base no Local da Conferência será habilitado.

Esse cmdlet retornará uma lista de aplicativos hospedados pelo Lync Server e os valores de prioridade para cada um deles. O aplicativo de Configuração de Roteamento com Base no Local da Conferência precisa ser assinalado com um valor de prioridade maior que o aplicativo "UdcAgent", e menor que os aplicativos "DefaultRouting", "ExumRouting" e "OutboundRouting". É recomendado que o aplicativo de Configuração de Roteamento com Base no Local da Conferência seja assinalado como um valor de prioridade mais alto que o valor de prioridade do aplicativo "UdcAgent".

Por exemplo, se o aplicativo "UdcAgent" tiver uma prioridade valor "2", o aplicativo "DefaultRouting", uma prioridade valor "8", o aplicativo "ExumRouting", valor "9", e o aplicativo "OutboundRouting" , valor "10", então o aplicativo de Configuração de Roteamento com Base no Local da Conferência deve ser assinalado com um valor de prioridade valor "3". Isso ordenará a prioridade dos aplicativos da seguinte forma: Outros aplicativos (Prioridades: 0 a 1), "UdcAgent" (Prioridade: 2), aplicativo de Configuração de Roteamento com Base no Local da Conferência (Prioridade: 3), outros aplicativos (Prioridades: 4 a 8), "DefaultRouting" (Prioridade: 9), "ExumRouting" (Prioridade: 10) e "OutboundRouting" (Prioridade: 11).

Depois de encontrar os valores de prioridade corretos para o aplicativo de Configuração de Roteamento com Base no Local da Conferência, digite o seguinte cmdlet para cada pool de Front-End ou Servidor Standard Edition hospedando usuários habilitados para Roteamento com Base no Local:

New-CsServerApplication -Identity Service:Registrar:\<Pool FQDN\>/LBRouting -Priority \<Application Priority\> -Enabled $true -Critical $true -Uri http://www.microsoft.com/LCS/LBRouting

Por exemplo:

New-CsServerApplication -Identity Service:Registrar:LS2013CU2LBRPool.contoso.com/LBRouting -Priority 3 -Enabled $true -Critical $true -Uri http://www.microsoft.com/LCS/LBRouting

Depois de usar esse cmdlet, reinicie todos os servidores Front-End no pool de Servidores Standard Edition onde o aplicativo de Configuração de Roteamento com Base no Local da Conferência foi habilitado.

> [!IMPORTANT]  
> As condições do Roteamento com Base no Local da Conferência e transferências consultivas não serão impostas até que todos os Servidores Front-End nos pools aplicáveis ou do Standard Edition tenham sido reiniciados. Se você definir <strong>–Crítico</strong> para <strong>$true</strong> nos cmdlets anteriores, os serviços do Lync serão imediatamente reiniciados. Se você não desejar que os serviços sejam reiniciados imediatamente, defina <strong>–Crítico</strong> para <strong>$false</strong> neste momento, e depois use o <strong>Set-CsServerApplication</strong> para alterar <strong>-Crítico</strong> para <strong>$true</strong> posteriormente, depois de os serviços terem sido reiniciados.

Quando o aplicativo de Configuração de Roteamento com Base no Local da Conferência tiver sido habilitado com êxito, e todos os servidores Lync aplicáveis tiverem sido reiniciados, todas as conferências organizadas pelos usuários do Lync habilitados para Roteamento com Base no Local serão monitoradas para impedir desvios de tarifas de PSTN

