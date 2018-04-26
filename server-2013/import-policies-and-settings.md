---
title: Importar políticas e configurações
TOCTitle: Importar políticas e configurações
ms:assetid: b25decee-2ee5-4836-b370-454411d39252
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205178(v=OCS.15)
ms:contentKeyID: 49307854
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Importar políticas e configurações

 

_**Tópico modificado em:** 2012-09-28_

After you merge your Office Communications Server 2007 R2 topology information with your Lync Server 2013 pilot pool, you need to run a Lync Server 2013 Management Shell cmdlet to migrate your Office Communications Server 2007 R2 policies and configuration settings to your Lync Server 2013 pilot pool.

The **Import-CsLegacyConfiguration** cmdlet imports policies, voice routes, dial plans, Communicator Web Access URLs, and dial-in access numbers to Lync Server 2013.

## Para migrar as configurações e políticas

1.  On the Lync Server 2013 Front End server, start the Shell de Gerenciamento do Lync Server.

2.  Na linha de comando, digite o seguinte:
    
        Import-CsLegacyConfiguration
    
    After the policies are imported, use the procedure that follows to see the imported policies in the Painel de Controle do Lync Server .

## Para ver as políticas importadas

1.  Open Lync Server 2013 Control Panel.

2.  Clique em **Roteamento de Voz** e veja as políticas importadas.

3.  Clique em **Conferência** e veja as políticas importadas.

4.  Click **Federation and External Access** and view the imported policies.

5.  Clique em **Monitoramento e Arquivamento** e veja as políticas importadas.

