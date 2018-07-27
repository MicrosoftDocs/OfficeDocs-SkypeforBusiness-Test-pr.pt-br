---
title: 'Lync Server 2013: Colocação em conjunto de servidor suportado para componentes de borda'
TOCTitle: Colocação em conjunto de servidor suportado para componentes de borda
ms:assetid: 435c4dd8-36af-4b71-9b88-3ffcf0fc5c65
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425934(v=OCS.15)
ms:contentKeyID: 49306537
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Colocação em conjunto de servidor suportado para componentes de borda no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

O serviço de Borda de Acesso, o serviço de Borda de Webconferência, o serviço de Borda A/V e o serviço de Proxy XMPP são colocados no Servidores de Borda. Os servidores fornecem funções necessárias para o acesso de usuário externo e devem ser implantados como servidores dedicados:

  - Servidor de Borda

  - Diretor (opcional)

  - Proxy reverso

> [!IMPORTANT]  
> O proxy reverso não precisa ser dedicado apenas a serviço Lync Server 2013. Por exemplo, você pode fornecer serviços para publicar os serviços da Web Lync Server e, concomitantemente, fornecer um site da Web publicado para outro site da Web que não possua rolamento nenhum em Lync Server. Se você já tiver um servidor proxy reverso na rede de perímetro para dar suporte a outros serviços, poderá usá-lo para o Lync Server 2013.
