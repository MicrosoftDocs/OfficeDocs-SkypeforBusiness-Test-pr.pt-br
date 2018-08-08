---
title: "Configurando o computador com Lync Server p/ participar da System Center Discovery"
TOCTitle: "Configurando o computador com Lync Server p/ participar da System Center Discovery"
ms:assetid: 2f9c9cb0-3120-4571-9cd2-657c2123fe21
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204776(v=OCS.15)
ms:contentKeyID: 49306271
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando o computador com Lync Server para participar da System Center Discovery

 

_**Tópico modificado em:** 2012-10-20_

Para certificar-se de que seu novo agente do Lync Server participa do processo de descoberta do System Center Operations Manager, você deve concluir o seguinte procedimento em cada computador onde o console do System Center Operations Manager foi instalado:

1.  Na guia **Administração**, clique em **Agente Gerenciado**.

2.  Clique com o botão direito no nome do computador e clique em **Propriedades**. Na caixa de diálogo **Propriedades**, na guia **Segurança**, selecione **Permitir que este agente haja como um proxy e descubra objetos gerenciados em outros computadores** e clique em **OK**.

Após concluir a etapa 2, reinicie o serviço do Agente de Integridade. (Reiniciar o serviço "forçará" a descoberta da nova máquina. Se você não reiniciar o serviço, pode levar até 4 horas antes que uma nova máquina seja descoberta no Gerenciador de Operações do Centro do Sistema.) Após o serviço ter sido reiniciado, verifique se nenhum evento de erro foi registrado no log de eventos do Gerenciador de Operações neste computador.

