---
title: Configurando um nó inspetor para participar do System Center Discovery
TOCTitle: Configurando um nó inspetor para participar do System Center Discovery
ms:assetid: 15c5dcfd-603b-47ea-af1b-8714c2ec08af
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204704(v=OCS.15)
ms:contentKeyID: 49305988
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando um nó inspetor para participar do System Center Discovery

 

_**Tópico modificado em:** 2012-10-22_

Para assegurar que seu nó do inspetor participa do processo de descoberta para o System Center Operations Manager, você deve concluir o procedimento a seguir, em um computador onde o console do System Center Operations Manager tenha sido instalado:

1.  Na guia **Administração**, clique em **Gerenciado por Agente**.

2.  Clique com o botão direito no nome do computador do nó do inspetor, e então clique em **Propriedades**. Na caixa de diálogo **Propriedades**, na guia **Segurança**, selecione **Permitir que este agente aja como um proxy e descubra objetos gerenciados em outros computadores**, e então clique em **OK**.

Após configurar o nó de observador para agir como um proxy, reinicie o computador do nó do inspetor. Depois que o computador tenha reiniciado, verifique que não estão sendo registrados eventos de erro no log de evento do Operations Manager nesse computador. Depois que o computador tenha ficado por volta de 15 minutos funcionando, use o console do Operations Manager para verificar se seus computadores do Lync Server estão listados sob a categoria **Lync**.

