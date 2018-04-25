---
title: Verificar se a replicação de usuário foi concluída
TOCTitle: Verificar se a replicação de usuário foi concluída
ms:assetid: 199dc9de-b555-468f-a42a-9e92ea6c9053
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204712(v=OCS.15)
ms:contentKeyID: 49306030
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar se a replicação de usuário foi concluída

 

_**Tópico modificado em:** 2012-09-28_

Ao executar o cmdlet **Move-CsLegacyUser** , você pode experimentar uma falha devido às informações de usuário entre o AD DS (Serviços de Domínio Active Directory) e os bancos de dados do Lync Server 2013 estarem fora de sincronia pois a replicação inicial está incompleta. O tempo necessário para a conclusão com êxito da sincronização inicial do serviço de Replicador do Usuário do Lync Server 2013 depende do número de controladores de domínio que estão hospedados na floresta do Active Directory que hospeda o pool do Lync Server 2013. O processo de sincronização inicial do serviço de Replicador de Usuário do Lync Server 2013 ocorre quando o servidor Front-End do Lync Server 2013 é iniciado pela primeira vez. Depois disso, a sincronização se baseia no intervalo do Replicador de Usuário. Complete os passos a seguir para verificar que a replicação de usuário foi concluída antes de executar o cmdlet **Move-CsLegacyUser** .

## Para verificar que a replicação de usuário foi concluída

1.  A partir do servidor Front-End do Lync Server 2013, clique no menu **Iniciar** , e então clique em **Executar** .

2.  Insira **eventvwr.exe** e clique em **OK** .

3.  No Visualizador de Eventos, clique em **Logs de Aplicativos e Serviços** para expandi-lo e selecione Lync Server.

4.  No painel **Ações** , clique em **Filtrar Log Atual** .

5.  Na lista **Fontes de evento** , clique em **Replicador de Usuário do LS** .

6.  Em **\<Todas as identificações de evento\>** insira **30024** e clique em **OK** .

7.  Na lista de eventos filtrados, na guia **Geral** , procure uma entrada que declare que a replicação de usuário foi concluída com êxito.

