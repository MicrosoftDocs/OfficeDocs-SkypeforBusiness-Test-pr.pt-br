---
title: Processo de migração
TOCTitle: Processo de migração
ms:assetid: b2bd9c76-2f4b-4d14-a5c4-157bbff75de0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205181(v=OCS.15)
ms:contentKeyID: 49307834
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de migração

 

_**Tópico modificado em:** 2012-09-24_

O procedimento de migração com suporte e recomendado para o Lync Server 2013 é a migração lado a lado. Este tópico descreve porque você deve usar a migração lado a lado e também inclui informações sobre coexistência.

## Migração lado a lado

Em praticamente cada migração, você deve usar o caminho de migração lado a lado. Na migração lado a lado, você pode implantar um novo servidor com o Lync Server 2013 juntamente com um servidor correspondente que esteja executando o Office Communications Server 2007 R2 e depois transferir operações para o novo servidor. Se for necessário reverter para o Office Communications Server 2007 R2, somente é necessário deslocar as operações de volta aos servidores originais. Lembre-se de que nessa situação, quaisquer novas reuniões agendadas com os clientes atualizados não funcionarão e também seria necessário fazer o downgrade dos clientes.

## Teste de coexistência

Depois de implantar o Lync Server 2013 em paralelo ao Office Communications Server 2007 R2, a topologia representa um estado de teste de coexistência do Lync Server 2013 e do Office Communications Server 2007 R2. Neste estado, é importante testar e verificar se os serviços foram inicializados, se cada site pode ser administrador e se os clientes pode se comunicar com usuários atuais e herdados. Antes da migração de todos os usuários, é importante entender o estado de cada implantação e verificar se cada implantação está pronta e funcionando corretamente. Normalmente, a fase de testes de coexistência existe pelo teste piloto do Lync Server 2013. Os usuários antigos são movidos para o Lync Server 2013 por um período de tempo, para garantir que aplicativos compatibilidade, recursos e funções estão funcionando adequadamente. Depois do teste piloto, os usuários e os aplicativos são movidos para a versão de produção do Lync Server 2013 e os pools herdados e os aplicativos do Office Communications Server 2007 R2 são desativados.

