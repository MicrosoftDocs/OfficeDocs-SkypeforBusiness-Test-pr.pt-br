---
title: Implementar clientes do Lync Server 2013
TOCTitle: Implementar clientes do Lync Server 2013
ms:assetid: 508e5dfa-588b-4289-81ce-2043c2d79e04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204883(v=OCS.15)
ms:contentKeyID: 49306690
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implementar clientes do Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

Após migrar os usuários para o Lync Server 2013, faça o seguinte:

1.  Utilize o Filtro da Versão do Cliente no novo servidor do Lync Server 2013 para permitir que somente os clientes com as atualizações mais recentes instaladas entrem.

2.  Se necessário, defina as configurações de Política de Grupo que são exigidas para a inicialização do cliente. Para obter detalhes, consulte [Configurando políticas de bootstrap de cliente no Lync Server 2013](lync-server-2013-configuring-client-bootstrapping-policies.md) na Documentação de implantação. A definição dessas configurações somente é necessária se você quiser alterar as políticas de inicialização do cliente existentes ou se você quiser definir novas políticas de inicialização do cliente. Se você não planeja configurar as políticas de inicialização do cliente ou quiser que as políticas de inicialização do cliente herdadas permaneçam em vigor, nenhuma ação é necessária.

3.  Configure outras políticas de usuário e do cliente para usuários ou grupos de usuários específicos utilizando o Painel de Controle do Lync Server 2013, Shell de Gerenciamento do Lync Server 2013 ou ambos. Para obter detalhes, consulte [Configurações Novas e Modificadas para Lync 2013](lync-server-2013-new-and-changed-settings-for-lync-2013.md) na Documentação de planejamento.

4.  Implante a versão mais recente dos cliente do Lync Server 2013 com as atualizações cumulativas mais recentes. Para obter detalhes, consulte [Implantando clientes e dispositivos no Lync Server 2013](lync-server-2013-deploying-clients-and-devices.md) na Documentação de implantação.

5.  (Opcional) Se a sua organização exigir o modo de privacidade de presença avançado do Lync Server 2013, após concluir a migração, defina uma Regra de política da versão do usuário para impedir que versões anteriores do cliente entrem. Em seguida, habilite o modo de privacidade de presença avançado.
    
    > [!IMPORTANT]  
    > Não habilite o modo de privacidade de presença avançado do Lync 2013 até que cada usuário em um determinado pool do servidor tenha as versões mais recentes do cliente instaladas.
