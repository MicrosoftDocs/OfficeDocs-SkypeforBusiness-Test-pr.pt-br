---
title: Remover uma entrada de host autorizada
TOCTitle: Remover uma entrada de host autorizada
ms:assetid: 56a04140-347e-4eef-bede-0e858534f71e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204902(v=OCS.15)
ms:contentKeyID: 49306758
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remover uma entrada de host autorizada

 

_**Tópico modificado em:** 2012-09-26_

Este tópico descreve como remover uma entrada de host herdada (conhecida como uma *entrada de aplicativo confiável* no Lync Server 2013). Você deve remover entradas de host autorizadas existentes para quaisquer gateways SIP/CSTA na sua implantação do Office Communications Server 2007 R2 ao migrar seu controle de chamada remota para uma implantação do Lync Server 2013. Você deve utilizar ferramentas administrativas incluídas no Office Communications Server 2007 R2 para remover as entradas de host autorizadas existentes.

## Para remover uma entrada de host autorizada em uma implantação do Office Communications Server 2007 R2

1.  Abra o console administrativo do Office Communications Server 2007 R2.

2.  Expanda a árvore e clique com o botão direito no pool no qual o host autorizado foi criado.

3.  Clique em **Propriedades** e clique em **Propriedades do Front-End** .

4.  Clique na guia **Autorização do Host** .

5.  Selecione um servidor e clique em **Remover** .

6.  Em **Propriedades** , clique em **OK** .

