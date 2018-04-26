---
title: 'Lync Server 2013: Configurar planos de discagem para conferência discada'
TOCTitle: Configurar planos de discagem para conferência discada
ms:assetid: a3e0958e-384f-43e5-b4c9-686b6ecac7ed
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412768(v=OCS.15)
ms:contentKeyID: 49307673
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar planos de discagem para conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-25_

Quando você implanta a conferência discada, precisa criar ou modificar um ou mais planos de discagem para o roteamento de números de telefone de acesso de discagem. Verifique se pelo menos uma regra de normalização em cada plano de discagem converte ramais telefônicos em números de telefone completos no formato E.164. Os usuários da conferência discada ingressam em conferências como usuários corporativos autenticados, digitando seu PIN (número de identificação pessoal) e seu número de telefone. Você precisa de uma regra de normalização para converter ramais em números de telefone completos, de forma que os usuários possam ser autenticados ao inserir somente um ramal telefônico.

Para configurar planos de discagem para conferência discada, execute o seguinte procedimento:

  - Independente de implantar o Enterprise Voice, modifique o plano de discagem global para adicionar uma região de conferência discada e para garantir que uma regra de normalização converta seus números de acesso discado de modo preciso. Para instruções detalhadas, consulte [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md).

  - Se você não implantou o Enterprise Voice, crie planos de discagem para todos os seus números de acesso de conferência discada. Certifique-se de incluir uma região de conferência discada. Para instruções detalhadas, consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md).

  - Se você implantou o Enterprise Voice, modifique os planos de discagem do Enterprise Voice conforme o necessário para incluir regiões e usar regras de normalização apropriadas para números de acesso de discagem. Para instruções detalhadas, consulte [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md). Você também pode criar planos de discagem dedicados, usados somente para números de acesso de discagem. Para instruções detalhadas, consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md).

Para detalhes sobre como planejar regiões, consulte [Exigências da conferência discada no Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md) na documentação de Planejamento.

## Nesta seção

  - [Exibir informações do plano de discagem no Lync Server 2013](lync-server-2013-view-dial-plan-information.md)

  - [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)

  - [Modificar um plano de discagem no Lync Server 2013](lync-server-2013-modify-a-dial-plan.md)

  - [Definindo regras de normalização no Lync Server 2013](lync-server-2013-defining-normalization-rules.md)

