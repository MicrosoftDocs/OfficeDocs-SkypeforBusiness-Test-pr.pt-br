---
title: Práticas recomendadas para sua infraestrutura principal do Lync Server 2013
TOCTitle: Práticas recomendadas para sua infraestrutura principal do Lync Server 2013
ms:assetid: 44aff88d-536c-4613-a81e-5398c9c6a648
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn518328(v=OCS.15)
ms:contentKeyID: 60505934
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Práticas recomendadas para sua infraestrutura principal do Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Provavelmente, você já executou as etapas para projetar a tolerância a falhas no seu sistema, usando práticas como assegurar a redundância de hardware, proteger contra falta de energia, instalar rotineiramente atualizações de segurança e medidas antivírus e atividade do Monitoring Server. Essas práticas beneficiam não só a sua infraestrutura do Microsoft Lync Server 2013, como também toda a sua rede. Se você não tiver implementado essas práticas, recomendamos que faça isso antes de implantar o Lync Server 2013.

Para ajudar a proteger os servidores na sua implantação do Lync Server 2013 contra danos acidentais ou propositais que podem causar tempo de inatividade, tome estas precauções:

  - Mantenha os servidores atualizados com atualizações de segurança. A assinatura do Microsoft Security Notification Service ajuda a assegurar que você receba notificações imediatas de versões de boletim de segurança de qualquer produto Microsoft. Para assinar, acesse o site Microsoft Technical Security Notifications em [http://go.microsoft.com/fwlink/p/?LinkId=145202](http://go.microsoft.com/fwlink/p/?linkid=145202).

  - Verifique se os direitos de acesso estão configurados corretamente.

  - Mantenha os servidores em um ambiente físico que impeça o acesso não autorizado. Verifique se o software antivírus adequado está instalado em todos os servidores. Mantenha o software atualizado com os arquivos de assinatura de vírus mais recentes. Use o recurso de atualização automática do seu aplicativo antivírus para manter as assinaturas de vírus atuais.

  - Nós recomendamos que você desabilite os serviços do sistema operacional Windows Server que não forem necessários nos computadores em que o Lync Server 2013 for instalado.

  - Criptografe os sistemas operacionais e as unidades de disco em que os dados estiverem armazenados com um sistema de criptografia de volume completo, a menos que você possa garantir o controle constante e completo dos servidores, o isolamento típico total e o descomissionamento apropriado e seguro de unidades de disco substituídas ou com falha.

  - Desabilite todas as portas de DMA (Acesso Remoto Direto à Memória) externas do servido, a menos que você possa garantir o controle muito rigoroso sobre o acesso físico aos servidores. Ataques baseados em DMA, que podem ser iniciados de modo razoavelmente fácil, podem expor informações confidenciais, como chaves de criptografia privada.

