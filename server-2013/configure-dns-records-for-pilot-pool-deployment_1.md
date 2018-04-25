---
title: Configurar registros de DNS para implantação de pool piloto
TOCTitle: Configurar registros de DNS para implantação de pool piloto
ms:assetid: 5c7a6e10-e1e9-4479-9bf9-d4a3e2e09ff0
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688072(v=OCS.15)
ms:contentKeyID: 49886235
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar registros de DNS para implantação de pool piloto

 

_**Tópico modificado em:** 2012-09-24_

Antes de implantar o pool piloto do Lync Server 2013, você deve atualizar as entradas do Host DNS A do pool piloto. Para concluir com êxito esse procedimento, você deve estar conectado ao servidor ou domínio no mínimo como um membro do grupo Administradores do Domínio ou um membro do grupo DnsAdmins.

**Para configurar os registros de DNS Host A**

1.  No servidor de Sistema de Nomes de Domínio (DNS), clique em **Iniciar**, em **Ferramentas Administrativas** e depois em **DNS**.

2.  Na árvore do console do seu domínio, expanda **Zonas de Consulta Direta** e clique com o botão direito do mouse no domínio em que o Lync Server 2013 será instalado.

3.  Clique em **Novo Host (A ou AAAA)**.

4.  Clique em **Nome**, digite o nome do host para o pool (o nome de domínio é considerado da zona na qual o registro está definido e não precisa ser inserida como parte do registro A).

5.  Clique em **Endereço IP**, digite o endereço IP do Pool de Front-Ends.

6.  Clique em **Adicionar Host** e, depois, em **OK**.

7.  Quando tiver terminado, clique em **Concluído**.

