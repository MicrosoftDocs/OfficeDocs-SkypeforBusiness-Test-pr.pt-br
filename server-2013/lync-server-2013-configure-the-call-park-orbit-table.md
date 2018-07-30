---
title: 'Lync Server 2013: Configurar a tabela de órbita de Estacionamento de Chamadas'
TOCTitle: Configurar a tabela de órbita de Estacionamento de Chamadas
ms:assetid: e5cc0c19-7b2c-48e7-a21d-cfb23c842f0f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399020(v=OCS.15)
ms:contentKeyID: 49308416
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar a tabela de órbita de Estacionamento de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-10_

O Estacionamento de Chamada Para que os usuários possam estacionar e recuperar as chamadas, você deve configurar a tabela de órbitas do Estacionamento de Chamada. É necessário especificar os intervalos dos números de ramal (órbitas) que a sua organização reservará para estacionar as chamadas e definir a rota desses intervalos especificando qual pool de Estacionamento de Chamada processará cada intervalo. Ao definir os intervalos de órbita, a meta é ter órbitas suficientes a ponto de que nenhuma seja reutilizada muito rápido, mas não tantas órbitas a ponto de limitar o número de ramais disponíveis para os usuários de outros serviços. É possível criar vários intervalos de órbitas de Estacionamento de Chamada para cada pool do Lync Server onde o Aplicativo de Estacionamento de Chamada é implantado. Cada intervalo de órbita do Estacionamento de Chamada deve ter um nome exclusivo globalmente e um conjunto de extensões exclusivo.

> [!IMPORTANT]  
> Normalmente, um intervalo de órbitas engloba 100 órbitas ou menos. Cada intervalo pode ser muito maior, contanto que seja menor do que o máximo de 10.000 órbitas por intervalo e tenha menos de 50.000 órbitas por pool. Se o intervalo for muito pequeno, as órbitas serão reutilizadas mais rapidamente.

Use blocos de extensões virtuais (extensões sem um usuário ou telefone atribuído a elas) para intervalos de órbita.

> [!NOTE]  
> A atribuição do número DID como números de órbita na tabela de órbita do Estacionamento de Chamada não é suportada.

## Nesta seção

[Criar ou modificar o intervalo de órbita de Estacionamento de Chamadas no Lync Server 2013](lync-server-2013-create-or-modify-a-call-park-orbit-range.md)

