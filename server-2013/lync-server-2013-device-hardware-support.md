---
title: 'Lync Server 2013: Suporte a hardware de dispositivo'
TOCTitle: Suporte a hardware de dispositivo
ms:assetid: ba07ca91-32b4-49cf-801c-47a2d1d96e18
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412908(v=OCS.15)
ms:contentKeyID: 49307927
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a hardware de dispositivo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Configurações de hardware específicas devem ser feitas antes de você implantar telefones IP e dispositivos analógicos.

Telefones IP executando o Lync Phone Edition oferecem suporte a LLDP-MED (Link Layer Discovery Protocol-Media Endpoint Discovery) e PoE (Power over Ethernet). Para aproveitar o LLDP-MED, o comutador deve suportar IEEE802.1AB e ANSI/TIA-1057. Para aproveitar o PoE, o comutador deve oferecer suporte a PoE802.3AF ou 802.3at.

Para habilitar o LLDP-MED, o administrador precisa habilitar o LLDP usando a janela do console do comutador e definir a política de rede do LLDP-MED com a ID de VLAN de voz correta.

Além disso, se sua implantação incluir dispositivos analógicos, é necessário configurar o gateway analógico para usar o Lync Server e o gateway precisa ser um dos seguintes:

  - Um adaptador de telefone analógico (ATA)

  - Um gateway analógico PSTN

  - Um Aparelho de Filial Persistente que inclua um gateway PSTN analógico

  - Um Aparelho de Filial Persistente que inclui um gateway PSTN que se comunica com um ATA

Para aprender como configurar um gateway analógico, consulte "Planejando a implantação de dispositivos analógicos" em [http://go.microsoft.com/fwlink/p/?LinkId=268537](http://go.microsoft.com/fwlink/p/?linkid=268537) na Biblioteca TechNet do Lync Server 2010. (Os dispositivos analógicos funcionam no Lync Server 2013 da mesma maneira que no Lync Server 2010.)

> [!IMPORTANT]  
> É possível configurar o comutador para o Enhanced 9-1-1 (E9-1-1), se o comutador suportar isso.
