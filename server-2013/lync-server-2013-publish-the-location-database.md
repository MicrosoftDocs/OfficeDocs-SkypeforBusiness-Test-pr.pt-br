---
title: Publicar o banco de dados de localização
TOCTitle: Publicar o banco de dados de localização
ms:assetid: dd032b5b-df0e-4017-ac46-e17570c1ab1e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398974(v=OCS.15)
ms:contentKeyID: 49308336
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Publicar o banco de dados de localização

 

_**Tópico modificado em:** 2012-10-30_

Os novos locais adicionados ao banco de dados de local não serão disponibilizados para o cliente até que sejam publicados.

Para obter detalhes, consulte o Shell de Gerenciamento do Lync Serverdocumentação para o seguinte cmdlet:

  - **Publish-CsLisConfiguration**

Se você usar gateways ELIN, também é necessário carregar os ELINs para o banco de dados ALI da transportadora PSTN. Sua transportadora PSTN pode exigir que você use um formato específico para os registros ELIN. Entre em contato com sua transportadora PSTN para obter detalhes. É possível exportar os registros do banco de dados do Serviço de Informações de Local e formatá-los conforme necessário.

## Para publicar o banco de dados local

  - Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

  - Execute o seguinte cmdlet para publicar o banco de dados local.
    
        Publish-CsLisConfiguration

