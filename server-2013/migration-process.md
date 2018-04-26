---
title: Processo de migração
TOCTitle: Processo de migração
ms:assetid: 13d71f4b-9d5e-4ea3-9e93-29fdad7ac68f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204696(v=OCS.15)
ms:contentKeyID: 49305961
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de migração

 

_**Tópico modificado em:** 2012-09-17_

O procedimento de migração recomendado e com suporte para o Lync Server 2013 é a migração lado a lado. Este tópico descreve porquê você deve usar a migração lado a lado e também inclui informações sobre testes de coexistência.

## Migração lado a lado

Em praticamente cada migração, você deve usar o caminho de migração lado a lado. Em uma migração lado a lado, implante um novo servidor com o Lync Server 2013 ao lado de um servidor correspondente que esteja executando o Lync Server 2010 e transfira operações para o novo servidor. Se for necessário reverter para o Lync Server 2010, somente é necessário deslocar as operações de volta aos servidores originais. Lembre-se de que nessa situação, quaisquer novas reuniões agendadas com os clientes atualizados não funcionarão e também seria necessário fazer o downgrade dos clientes.

## Teste de coexistência

Depois de implantar o Lync Server 2013 em paralelo com o Lync Server 2010, a implantação representa um estado de teste de coexistência do Lync Server 2013 e do Lync Server 2010. Durante este estado, é importante testar e garantir que os serviços estejam iniciados, que cada site possa ser administrado e que os clientes possam se comunicar com usuários atuais e herdados. Antes da migração de todos os usuários, é muito importante entender o estado de cada implantação e garantir que cada uma delas esteja funcional e funcionando adequadamente. Normalmente, a fase de teste de coexistência existe por todo o teste piloto do Lync Server 2013. Os usuários antigos são movidos para o Lync Server 2013 por um período de tempo, para garantir que a compatibilidade de aplicativos, recursos e funções estejam funcionando adequadamente. Depois do teste piloto, usuários e aplicativos são movidos para a versão de produção do Lync Server 2013 e os pools e aplicativos herdados do Lync Server 2010 são desativados.

