---
title: 'Lync Server 2013: Configurar número de acesso da conferência discada'
TOCTitle: Configurar número de acesso da conferência discada
ms:assetid: d8a18030-f318-43dd-834d-70e5014b5e8a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398952(v=OCS.15)
ms:contentKeyID: 49308279
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar número de acesso da conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2011-07-17_

Ao implantar uma conferência discada, você precisa configurar números de telefone que os usuários poderão discar da PSTN para participar da parte de áudio das conferências. Esses números de acesso de discagem aparecem nos convites de reunião e na página Configurações de Conferência Discada.

Antes de criar números de acesso discado, primeiro você precisa planejar as regiões de conferência discada e, em seguida, configurar os planos de discagem nas regiões. Para obter detalhes sobre as regiões, consulte [Exigências da conferência discada no Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md) na documentação Planejamento. Para obter detalhes sobre como configurar os planos de discagem para conferência discada, consulte [Configurar planos de discagem para conferência discada no Lync Server 2013](lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md).

> [!NOTE]  
> Não é possível usar um novo número de acesso discado até que a replicação dos Serviços de Domínio do Active Directory (AD DS) desse número de acesso seja concluída. A replicação pode demorar algumas horas para ser concluída.

> [!NOTE]  
> Após a criação dos números de acesso discado, é possível modificar o nome de exibição dos objetos de contato do Active Directory de modo que os usuários possam identificar com mais facilidade o número de acesso correto. Use o cmdlet <strong>Set-CsDialInConferencingAccessNumber</strong> para modificar o nome de exibição. Não modifique os objetos do Active Directory manualmente. Para obter detalhes sobre como modificar um número de acesso, consulte a documentação do Shell de Gerenciamento do Lync Server para o cmdlet <strong>Set-CsDialInConferencingAccessNumber</strong>.

## Nesta seção

[Criar ou modificar um número de acesso de conferência discada no Lync Server 2013](lync-server-2013-create-or-modify-a-dial-in-conferencing-access-number.md)

## Consulte Também

#### Conceitos

[Exigências da conferência discada no Lync Server 2013](lync-server-2013-dial-in-conferencing-requirements.md)  

#### Outros Recursos

[Configurar planos de discagem para conferência discada no Lync Server 2013](lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md)

