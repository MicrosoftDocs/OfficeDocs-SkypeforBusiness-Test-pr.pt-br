---
title: 'Lync Server 2013: Configurar registros de Host DNS'
TOCTitle: Configurar registros de Host DNS
ms:assetid: 78a1afcf-41c8-4da5-8740-c6570c19078c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398593(v=OCS.15)
ms:contentKeyID: 49307184
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar registros de Host DNS para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

Para concluir com êxito este procedimento, você deve estar conectado no servidor ou domínio no mínimo como um membro do grupo de Administradores de Domínio ou membro do grupo DnsAdmins.

## Para configurar os registros de DNS Host A

1.  No servidor de Sistema de Nomes de Domínio (DNS), clique em **Iniciar** , em **Ferramentas Administrativas** e depois em **DNS** .

2.  Na árvore do console do seu domínio, expanda **Zonas de Consulta Direta** e clique com o botão direito do mouse no domínio em que o Lync Server 2013 será instalado.

3.  Clique em **Novo Host (A ou AAAA)** .

4.  Clique em **Nome** , digite o nome do host para o pool (o nome de domínio é considerado da zona na qual o registro está definido e não precisa ser inserida como parte do registro A).

5.  Clique em **Endereço IP** , digite o IP virtual (VIP) do balanceador de carga para o Pool de Front-Ends.
    
    > [!IMPORTANT]  
    > Nas implantações que usam um pool do Diretor, os registros do host (A) para URLs simples devem apontar para o VIP do balanceador de carga do Diretor.    
    > [!NOTE]  
    > Se você implantar apenas um servidor Enterprise Edition ou Diretor que esteja conectado à topologia sem um balanceador de carga, ou se você implantar um servidor Standard Edition, digite o endereço IP do servidor Enterprise Edition, o servidor Standard Edition ou o Diretor. Um balanceador de carga será necessário se você implantar mais de um servidor Enterprise Edition ou Diretor em um pool. Os balanceadores de carga não são usados com servidores Standard Edition.

6.  Clique em **Adicionar Host** e, depois, em **OK** .

7.  Para criar um registro A adicional, repita as etapas 4 e 5.

8.  Após criar todos os registros A necessários, clique em **Concluído** .

