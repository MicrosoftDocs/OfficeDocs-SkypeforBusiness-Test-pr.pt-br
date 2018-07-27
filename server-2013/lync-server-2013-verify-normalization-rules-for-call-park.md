---
title: 'Lync Server 2013: Verificar regras de normalização para Estacionamento de Chamadas'
TOCTitle: Verificar regras de normalização para Estacionamento de Chamadas
ms:assetid: deaa170f-041e-45cb-8eab-f02931ab541e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398981(v=OCS.15)
ms:contentKeyID: 49308352
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar regras de normalização para Estacionamento de Chamadas no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-11_

As órbitas do Estacionamento de Chamada não devem ser normalizadas. Verifique seus planos de discagem para garantir que seus números de órbita não estão normalizados. Você deve criar uma regra de normalização adicional para evitar que sua órbitas sejam normalizadas, seguindo o procedimento em [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md) para definir uma nova regra de normalização, para que o **Padrão de correspondência** identifique o intervalo de órbita e o **Padrão de conversão** é **$1**. Por exemplo, se seu intervalo de órbita do Estacionamento de Chamada é 7000 - 7999, o **Padrão de correspondência** é **^(7\\d{3})$** e o **Padrão de conversão** é **$1**.

> [!IMPORTANT]  
> Certifique-se de que a regra de normalização padrão em seu plano de discagem não contém o <strong>^(\d*)</strong>. Caso contrário, sua regra de normalização do Estacionamento de Chamada nunca será executada.

## Consulte Também

#### Tarefas

[Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md)

