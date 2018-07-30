---
title: Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server
TOCTitle: Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server
ms:assetid: 8b9b2bad-a4b3-42e1-85a7-04022e9442ad
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205063(v=OCS.15)
ms:contentKeyID: 49307382
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Políticas para Arquivamento quando Usando Integração do Exchange Server

 

_**Tópico modificado em:** 2012-10-09_

Se as caixas de correio dos usuários hospedados em Exchange 2013 sofrerem bloqueio in-loco, as políticas de bloqueio in-loco do Exchange controlarão o arquivoamento para esses usuários. Se você usar a integração do Microsoft Exchange em sua implementação, as políticas do Exchange 2013 substituirão as políticas de arquivamento do Lync Server para os usuários hospedados em Exchange 2013. Para obter informações sobre como configurar políticas de arquivamento do Exchange, consulte a documentação do Exchange 2013. Para obter detalhes sobre como configurar as políticas de uso dos usuários hospedados no Lync Server 2013, consulte [Configurando Políticas de Usuário para Arquivamento no Lync Server](lync-server-2013-setting-up-user-policies-for-archiving-in-lync-server.md) na documentação de implantação. Para obter detalhes sobre o funcionamento das políticas, consulte [Como o arquivamento funciona no Lync Server 2013](lync-server-2013-how-archiving-works.md) na documentação de planejamento, implantação e operações.

> [!NOTE]  
> Se você implantar Exchange 2013 e Lync Server 2013 na mesma floresta, suas políticas de bloqueio in-loco do Exchange 2013 controlarão o arquivamento. Se você implantar Exchange 2013 e Lync Server 2013 em florestas separadas, consulte &quot;Implantando Lync Server e Microsoft Exchange em florestas diferentes&quot; em <a href="lync-server-2013-deployment-checklist-for-archiving.md">Lista de verificação da implantação para Arquivamento no Lync Server 2013</a>.
