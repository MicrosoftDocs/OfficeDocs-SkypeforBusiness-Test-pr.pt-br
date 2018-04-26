---
title: Migrar dispositivos analógicos
TOCTitle: Migrar dispositivos analógicos
ms:assetid: ad072916-87ed-4d44-8289-aab87da86250
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721846(v=OCS.15)
ms:contentKeyID: 49886356
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Migrar dispositivos analógicos

 

_**Tópico modificado em:** 2012-10-16_

O Lync Server fornece suporte para dispositivos analógicos. Especificamente, os dispositivos analógicos suportados são fones de áudio e faxes analógicos. Você pode configurar os gateways qualificados para suportar o uso de dispositivos analógicos no seu ambiente do Lync Server. Depois de migrar do Lync Server 2010 para o Lync Server 2013, é necessário migrar os objetos de contato associados nos dispositivos analógicos. Use o Shell de Gerenciamento do Lync Server para recuperar todos os objetos de contato associados aos dispositivos analógicos do Lync Server 2010 e, em seguida, mova esses objetos para o pool do Lync Server 2013.

## Para migrar dispositivos analógicos

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Na linha de comando, digite:
    
        Get-CsAnalogDevice -Filter {RegistrarPool -eq "pool01.contoso.net"} | Move-CsAnalogDevice -Target pool02.contoso.net

3.  Verifique se todos os objetos de contato foram movidos para o pool do Lync Server 2013. Na linha de comando, digite:
    
        Get-CsAnalogDevice -Filter {RegistrarPool -eq "pool02.contoso.net"}

4.  Verifique se todos os objetos de contato estão associados ao pool do Lync Server 2013.

