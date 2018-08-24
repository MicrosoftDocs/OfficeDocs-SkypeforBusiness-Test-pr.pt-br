---
title: Configurar um aplicativo SNMP no Lync Server 2013
TOCTitle: Configurar um aplicativo SNMP no Lync Server 2013
ms:assetid: c4b4a736-3b2e-45b9-a965-19d22161ad57
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412972(v=OCS.15)
ms:contentKeyID: 49308042
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar um aplicativo SNMP no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-03_

O Lync Server 2013 inclui uma interface de serviço da Web padrão que você pode usar para conectar o Serviço de Informações de Local aos aplicativos SNMP que correspondem endereços MAC com informação de porta e opção.

Se um aplicativo SNMP estiver instalado e o Serviço de Informações de Local falha para encontrar uma correspondência no banco de dados de localização, o Serviço de Informações de Local consulta automaticamente o aplicativo usando o endereço MAC oferecido pelo cliente. O Serviço de Informações de Local usa a informação de porta e opção retornada pelo aplicativo SNMP para consultar o banco de dados de localização novamente.

Para obter detalhes, consulte [Set-CsWebServiceConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsWebServiceConfiguration).

> [!NOTE]  
> Endereços MAC não estão disponíveis em computadores executando o Windows 8.

## Para configurar a URL do aplicativo SNMP

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o seguinte cmdlet para configurar a URL do aplicativo SNMP.
    
        Set-CsWebServiceConfiguration -MACResolverUrl "<SNMP application url>"

