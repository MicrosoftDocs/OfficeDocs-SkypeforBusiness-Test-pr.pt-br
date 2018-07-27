---
title: Lista de verificação da implantação do controle de admissão de chamadas para Lync Server 2013
TOCTitle: Lista de verificação da implantação do controle de admissão de chamadas para Lync Server 2013
ms:assetid: d56a525f-3da5-4ac0-a311-0c5efd98c9df
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398928(v=OCS.15)
ms:contentKeyID: 49308231
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação da implantação do controle de admissão de chamadas para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-22_

Consulte a lista de verificação para confirmar se você concluiu todas as tarefas de configuração necessárias para a implantação do controle de admissão de chamadas.

  - Se um ou mais Servidores de Borda for implantado, cada endereço IP de interface externa precisa ser adicionado à lista de subredes nas configurações de rede, com uma bitmask de 32. Associe também essa sub-rede (endereço IP) ao ID do site de rede para o local geográfico onde o serviço Borda A/V está implantado.
    
    > [!NOTE]  
    > Os Servidores de Borda não são necessários para implementar o CAC.

  - Certifique-se de que CAC está habilitado, através do Painel de Controle do Lync Server ou executando o cmdlet conforme especificado no [Habilitar o controle de admissão de chamadas no Lync Server 2013](lync-server-2013-enable-call-admission-control.md).

  - Certifique-se de que o CAC está habilitado em todos os sites centrais. Isto pode ser realizado através do Construtor de Topologias. Se um aviso é gerado ao publicar, *não* ignore-o.

  - Certifique-se de que todas as subredes gerenciadas na rede empresarial estão definidas nas configurações de rede. Também é essencial que toda subrede esteja associada a um site de rede, conforme explicado em [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md).

  - Certifique-se de que a subrede ou os endereços IP de todos os Servidores de Front-End, Aparelhos de Filial Persistentes (SBAs), Servidores de Conferência de Áudio/Vídeo (se estiverem em um pool separado) e Servidores de Mediação estejam definidos nas configurações de rede.

