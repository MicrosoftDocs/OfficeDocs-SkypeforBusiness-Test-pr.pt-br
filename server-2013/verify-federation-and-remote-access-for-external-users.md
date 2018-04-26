---
title: Verificar federação e acesso remoto de usuários externos
TOCTitle: Verificar federação e acesso remoto de usuários externos
ms:assetid: a383fefb-c428-4462-93fd-15ba540fa867
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688163(v=OCS.15)
ms:contentKeyID: 49886342
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar federação e acesso remoto de usuários externos

 

_**Tópico modificado em:** 2012-09-18_

Após passar a rota de federação para o Lync Server 2013  Servidor de Borda, você deve realizar alguns testes funcionais para verificar que a federação funciona conforme esperado. Os testes de acesso do usuários externo devem incluir qualquer tipo de usuário externo suportado pela sua organização, incluindo qualquer um ou todos os seguintes.

## Teste a conectividade de usuários externos e do acesso externo

  - Os usuários de pelo menos um domínio federado, um usuário interno em Lync Server 2013 e um usuário Lync Server 2010. Teste as mensagens instantâneas (IM), presença, áudio/vídeo (A / V) e o compartilhamento de área de trabalho.

  - Usuários de cada provedor de serviços de IM públicos, aos quais sua empresa oferece suporte, (e para os quais o provisionamento foi realizado) que se comunicam com um usuário no Lync Server 2013 e no Lync Server 2010.

  - Verifique se usuários anônimos podem participar de conferências.

  - Um usuário hospedado no Lync Server 2010 usando acesso de usuário remoto (que faz login no Lync Server 2010 de fora da intranet, mas sem VPN) com um usuário no Lync Server 2013 e no Lync Server 2010. Teste IM, presença, A/V e compartilhamento de desktop.

  - Um usuário hospedado no Lync Server 2013 usando acesso de usuário remoto (que faz login no Lync Server 2013 de fora da intranet, mas sem VPN) com um usuário no Lync Server 2013 e no Lync Server 2010. Teste IM, presença, A/V e compartilhamento de desktop.

