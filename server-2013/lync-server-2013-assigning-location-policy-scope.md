---
title: 'Lync Server 2013: Atribuindo escopo da política de local'
TOCTitle: Atribuindo escopo da política de local
ms:assetid: e4c66517-c593-4253-b900-7b4dd8bddf2f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205360(v=OCS.15)
ms:contentKeyID: 49308415
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atribuindo escopo da política de local no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-06_

Como com outras políticas do Lync Server, as políticas de local podem ser atribuídas em vários níveis de escopo: global, de site e de usuário. No entanto, o escopo das políticas de local a nível de usuário se comporta um pouco diferente do que outras políticas do Lync Server. Não apenas as políticas de local por usuário podem ser aplicadas aos objetos de ponto de extremidade (como os objetos de contato de Telefone de Área Comum e Usuários), elas também podem ser aplicadas aos sites de rede do Lync Server. Os sites de rede são agrupamentos de subredes de cliente associadas com um local geográfico (mas não necessariamente deve ser todas as subredes em um site central ou site de filial). Qualquer cliente conectado às subredes de um site de rede obtém automaticamente a política de local atribuída a este site de rede. Em casos onde uma política de local a nível de usuário é atribuída ao usuário e a um site de rede, a política de local baseada em site de rede substitui qualquer configuração de política por usuário.

Cada site de rede possui uma política de rede atribuída e cada política possuirá diferentes valores de Usos PSTN, URIs de notificação e URIs de conferência atribuídos.

> [!NOTE]  
> O motivo para esta política especial se comportar desta forma é porque quando um usuário hospedado em um pool em um site de escritório visita outro site e precisa fazer uma chamada de emergência, as configurações de roteamento de chamada E9-1-1 adequadas para este site de rede serão aplicadas não importando qual pool ou site o usuário está atribuído.
