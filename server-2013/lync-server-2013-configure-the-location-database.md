---
title: Configurar o banco de dados de localização no Lync Server 2013
TOCTitle: Configurar o banco de dados de localização no Lync Server 2013
ms:assetid: 8544be31-6958-47ef-b926-fdc80d56191c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398679(v=OCS.15)
ms:contentKeyID: 49307329
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o banco de dados de localização no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-17_

Para que os clientes possam detectar automaticamente seu local na rede, primeiro configure o banco de dados de localização. Se você não configurar o banco de dados de localização e o **Local obrigatório** na política de local for definido como **Sim** ou **Aviso de isenção de responsabilidade**, o sistema solicitará que o usuário insira um local manualmente.

Para configurar o banco de dados local, você executará as seguintes tarefas:

1.  Preencha o banco de dados com um mapeamento dos locais para os elementos de rede. Se usar um gateway com número de identificação local de emergência, será necessário inclui o ELIN no campo \<CompanyName\>.

2.  Valide os endereços em relação ao MSAG (catálogo de endereços principal) mantido pelo provedor de serviços de emergência.

3.  Publicar o banco de dados atualizado.

> [!NOTE]  
> Como alternativa, você pode definir um banco de dados de origem do local secundário, que pode ser usado em vez do banco de dados local. Para obter detalhes, consulte <a href="lync-server-2013-configure-a-secondary-location-information-service.md">Configurar um serviço de informações de localização secundário no Lync Server 2013</a>.

## Nesta seção

  - [Preencher o banco de dados de localização](lync-server-2013-populate-the-location-database.md)

  - [Validar endereços](lync-server-2013-validate-addresses.md)

  - [Publicar o banco de dados de localização](lync-server-2013-publish-the-location-database.md)

