---
title: "Lync Server 2013: Definir e config. uma topologia no Construtor de Topologia"
TOCTitle: Definir e configurar uma topologia no Construtor de Topologia
ms:assetid: 99231ff5-1c21-432b-ad65-8675fcd484f9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398788(v=OCS.15)
ms:contentKeyID: 49307557
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir e configurar uma topologia no Construtor de Topologia para Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Executar o Construtor de Topologias para definir uma nova topologia ou para modificar uma topologia existente não requer a associação em um grupo de administradores local ou grupo de domínio privilegiado. O Construtor de Topologias o guiará pelas etapas necessárias para definir sua topologia para um pool de Front End no Enterprise Edition ou um Standard Edition, com base em seus requisitos de configuração.

Você deve usar o Construtor de Topologias para concluir e publicar a topologia antes de instalar o Lync Server 2013 nos servidores. O procedimento a seguir inclui as etapas necessárias para definir uma nova topologia.

## Para definir uma topologia

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  No Construtor de Topologias, selecione **Nova Topologia** . Você será solicitado a informar uma localização e nome de arquivo para salvar a topologia. Dê à topologia um nome significativo e aceite a extensão padrão .tbxml. Clique em **OK** .

3.  Navegue até a localização onde deseja salvar o arquivo XML da nova topologia, insira um nome para o arquivo e clique em **Salvar** .

4.  Na página **Definir o domínio primário** , insira o nome do domínio SIP primário para a sua organização e clique em **Avançar** .

5.  Na página **Especificar domínios com suporte adicionais** , insira os nomes de domínios adicionais, se houver e clique em **Avançar** .

6.  Na página **Definir o primeiro site** , insira um nome e uma descrição para o primeiro site e clique em **Avançar** .

7.  Na página **Especificar detalhes do site** , insira as informações de localização para o site e clique em **Avançar** .

8.  Na página **Nova topologia definida com êxito**, certifique-se de que a caixa de seleção **Abrir o Assistente de Novo Front End quando este assistente for fechado** esteja marcada, e clique em **Concluir**.

Depois de ter definido e salvado a topologia, use o Assistente de Novo Front End para definir um pool de Front End ou um Servidor Standard Edition para seu site. Para obter detalhes, consulte [Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013](lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md).

