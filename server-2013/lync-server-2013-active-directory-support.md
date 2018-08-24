---
title: 'Lync Server 2013: Suporte a Active Directory'
TOCTitle: Suporte a Active Directory
ms:assetid: 28ed9ac4-586d-4803-ad45-99c4fa793f54
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425756(v=OCS.15)
ms:contentKeyID: 49306200
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

As topologias locais do Serviços de Domínio Active Directory suportadas pelo Lync Server 2013 são as seguintes:

  - Floresta única com domínio único

  - Floresta única com uma única árvore e vários domínios

  - Floresta única com várias árvores e namespaces não contíguos

  - Várias florestas em uma topologia de floresta central

  - Várias florestas em uma topologia de floresta de recursos

> [!NOTE]  
> O Lync Server 2013 não oferece suporte a domínios de rótulo único. Por exemplo, uma floresta com um domínio raiz chamado <strong>contoso.local</strong> é suportado, mas um domínio raiz de rótulo único chamado <strong>local</strong> não é suportado. Para obter detalhes, consulte o artigo 300684 da Base de Dados de Conhecimento da Microsoft, &quot;Informações sobre a configuração do Windows para domínios com nomes DNS de rótulo único&quot;, em <a href="http://go.microsoft.com/fwlink/p/?linkid=143752">http://go.microsoft.com/fwlink/p/?linkId=143752</a>.

> [!NOTE]  
> O Lync Server 2013 não suporta renomeação de domínios. Se você precisar renomear um domínio onde o Lync Server estiver implantado, você precisará primeiro desinstalar o Lync Server, em seguida renomear o domínio, e por fim reinstalar o Lync Server.

Para obter detalhes sobre as topologias suportadas e requisitos para implantações locais, consulte [Requisitos, suporte e topologia de Serviços de Domínio Active Directory no Lync Server 2013](lync-server-2013-active-directory-domain-services-requirements-support-and-topologies.md) na documentação de Planejamento.

