---
title: 'Lync Server 2013: Requisitos de infraestrutura do Active Directory'
TOCTitle: Requisitos de infraestrutura do Active Directory
ms:assetid: c2086f7b-662f-4179-ab99-2c0311ebd903
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412955(v=OCS.15)
ms:contentKeyID: 49308003
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de infraestrutura do Active Directory para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Antes de iniciar o processo de preparação do Serviços de Domínio Active Directory para o Lync Server 2013, certifique-se de que sua infraestrutura do Active Directory cumpre os seguintes requisitos:

  - Todos os controladores de domínio (que incluem todos os servidores de catálogo global) na floresta onde você implanta o Lync Server executam um dos sistemas operacionais abaixo:
    
      - Sistema operacional Windows Server 2012 R2
    
      - Sistema operacional Windows Server 2012
    
      - Sistema operacional Windows Server 2008 R2
    
      - Sistema operacional Windows Server 2008
    
      - Windows Server 2008 Enterprise 32 bits
    
      - Versões de 32 bits ou 64 bits do Sistema operacional Windows Server 2003 R2
    
      - Versões de 32 bits ou 64 bits do Sistema operacional Windows Server 2003

  - Todos os domínios em que você implantar o Lync Server são elevados para um nível de domínio funcional de Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, ou pelo menos Windows Server 2003.

  - A floresta na qual você implanta o Lync Server é elevada para um nível funcional de floresta do Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, ou pelo menos Windows Server 2003.
    
    > [!NOTE]  
    > Para alterar seu nível funcional de domínio de floresta ou domínio, consulte &quot;Aumentando os níveis funcionais do domínio e da floresta&quot; em <a href="http://go.microsoft.com/fwlink/?linkid=263775" class="uri">http://go.microsoft.com/fwlink/?linkid=263775</a>.

  - Um catálogo global é implantado em cada domínio no qual você implanta computadores ou usuários do Lync Server.

Lync Server 2013 suporta grupos universais nos sistemas operacionais Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2, Windows Server 2008, e Windows Server 2003. Os membros dos grupos universais podem incluir outros grupos e contas de qualquer domínio na árvore de domínio ou floresta e pode ser atribuído com permissões em qualquer domínio na árvore de domínio ou floresta. Suporte de grupo universal, combinado com a delegação do administrador, simplifica o gerenciamento de uma implantação do Lync Server. Por exemplo, não é necessário adicionar um domínio para outro para habilitar um administrador a gerenciar ambos.

