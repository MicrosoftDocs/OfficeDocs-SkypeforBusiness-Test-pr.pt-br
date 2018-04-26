---
title: Redefinir controle de admissão de chamada
TOCTitle: Redefinir controle de admissão de chamada
ms:assetid: 5873f56c-f3d6-4d73-beea-c9f37d5077f6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688064(v=OCS.15)
ms:contentKeyID: 49886228
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Redefinir controle de admissão de chamada

 

_**Tópico modificado em:** 2012-10-11_

Se um Lync Server 2010Pool de Front-Ends estiver hospedando um CAC (controle de admissão de chamadas), você deve mover a hospedagem do CAC para um pool do Lync Server 2013 antes de poder remover o Lync Server 2010Pool de Front-Ends.

## Para redefinir o CAC

1.  Abrir o Construtor de Topologias.

2.  Clique com o botão direito no nó do site e, em seguida, clique em **Editar propriedades** .

3.  Em **Configuração de Controle de Admissão de Chamadas** , certifique-se de que a opção **Habilitar controle de admissão de chamadas** está selecionada.

4.  Em **Pool de Front-Ends para executar Controle de Admissão de Chamadas (CAC)** , selecione o pool do Lync Server 2013 no qual o CAC está hospedado e, em seguida, clique em **OK** .

5.  Publique a topologia.

