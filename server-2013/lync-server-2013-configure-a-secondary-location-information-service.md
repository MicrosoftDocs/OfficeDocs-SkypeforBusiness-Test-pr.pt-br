---
title: "config. um serviço de informações de localização secundário no Lync Server 2013"
TOCTitle: "config. um serviço de informações de localização secundário no Lync Server 2013"
ms:assetid: 083ffbc6-7c18-4141-85f9-8825b62c3d10
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398138(v=OCS.15)
ms:contentKeyID: 49305798
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar um serviço de informações de localização secundário no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-30_

Lync Server 2013 oferece uma interface de serviço web que você pode usar para apontar o Serviço de Informações de Local Servidor de Informações de Local para um banco de dados de Fonte de Localização Secundária (SLS). A interface de serviço web que faz a conexão ao banco de dados SLS deve estar em conformidade com o Serviço de Informações de Local Servidor de Informações de Local WSDL. Se tanto o banco de dados de Localização quanto o banco de dados de Localização Secundário forem configurados, o Serviço de Informações de Local Servidor de Informações de Local primeiro consultará o banco de dados de Localização e, se nenhuma correspondência for encontrada, usará um proxy para a Solicitação de Local do cliente para o banco de dados SLS. Se o local existir no SLS, o Serviço de Informações de LocalServidor de Informações de Local usará um proxy para o local retornar ao cliente.

Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server para o cmdlet a seguir:

  - **Set-CsWebServiceConfiguration**

## Para configurar o banco de dados de localização secundária

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet a seguir para configurar o URL para a localização do banco de dados de localização secundária.
    
        Set-CsWebServiceConfiguration -SecondaryLocationSourceURL "<web service url>"

