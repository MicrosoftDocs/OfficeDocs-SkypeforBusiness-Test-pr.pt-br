---
title: Configurar registros de DNS para implantação de pool piloto
TOCTitle: Configurar registros de DNS para implantação de pool piloto
ms:assetid: eb421bad-4bf1-4837-a077-7795094692d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721921(v=OCS.15)
ms:contentKeyID: 49886462
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar registros de DNS para implantação de pool piloto

 

_**Tópico modificado em:** 2012-09-29_

Antes de implantar o pool piloto Lync Server 2013, você deve atualizar as entradas de DNS Host A do pool piloto. Para realizar este procedimento com sucesso, é necessário fazer login no servidor ou domínio como membro do grupo Admins. de Domínio ou do grupo DnsAdmins.

**Para configurar os registros de DNS Host A**

1.  No servidor de Sistema de Nomes de Domínio (DNS), clique em **Iniciar** , em **Ferramentas Administrativas** e depois em **DNS** .

2.  Na árvore do console do seu domínio, expanda **Zonas de Consulta Direta** e clique com o botão direito do mouse no domínio em que o Lync Server 2013 será instalado.

3.  Clique em **Novo Host (A ou AAAA)** .

4.  Clique em **Nome** , digite o nome de host do pool Lync Server 2013 (o nome de domínio é presumido de acordo com a zona em que o registro está definido e não precisa ser informado como parte do registro A).

5.  Clique em **Endereço IP** , digite o endereço IP do Pool de Front-Ends.

6.  Clique em **Adicionar Host** e, depois, em **OK** .

7.  Quando tiver terminado, clique em **Concluído** .

