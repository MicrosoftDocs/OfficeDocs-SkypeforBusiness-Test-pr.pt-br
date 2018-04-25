---
title: Verificar se a replicação de usuário foi concluída
TOCTitle: Verificar se a replicação de usuário foi concluída
ms:assetid: 119e9896-45e5-4f8b-af43-7b09360ada0b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204680(v=OCS.15)
ms:contentKeyID: 49305928
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar se a replicação de usuário foi concluída

 

_**Tópico modificado em:** 2012-09-17_

Ao executar o cmdlet **Move-CsUser** , você pode encontrar falhas porque informações do usuário entre o Active Directory Domain Services (AD DS) e os bancos de dados do Lync Server 2013 não estão sincronizadas, porque a replicação inicial está incompleta. O tempo que leva para conclusão bensucedida da sincronização inicial do serviço do Lync Server 2013 User Replicator depende do número de controladores de domínio hospedados na floresta do Active Directory que hospeda o pool do Lync Server 2013. O processo de sincronização inicial do serviço do Lync Server 2013 User Replicator ocorre quando o servidor de front end do Lync Server 2013 é iniciado pela primeira vez. Depois disso, a sincronização se baseia no intervalo do User Replicator. Conclua as etapas a seguir para verificar se a replicação do usuário foi concluída antes de executar o cmdlet **Move-CsUser** .

## Para verificar se a replicação de usuário foi concluída

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Clique no menu **Iniciar** e em **Executar** .

3.  Insira **eventvwr.exe** e clique em **OK** .

4.  No Visualizador de Eventos, clique em **Logs de Aplicativos e Serviços** para expandir e selecione Lync Server.

5.  No painel **Ações** , clique em **Filtrar Log Atual** .

6.  Na lista **Fontes de evento** , clique em **Replicador de Usuário do LS** .

7.  Em **\<Todas as identificações de evento\>** insira **30024** e clique em **OK** .

8.  Na lista de eventos filtrados, na guia **Geral** , procure uma entrada que declare que a replicação de usuário foi concluída com êxito.

