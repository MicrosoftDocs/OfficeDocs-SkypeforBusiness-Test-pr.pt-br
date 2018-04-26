---
title: 'Lync Server 2013: Compreendendo os requisitos de firewall para Servidor SQL'
TOCTitle: Compreendendo os requisitos de firewall para Servidor SQL
ms:assetid: 31d7df2c-589f-465e-be74-cf6767db190d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425818(v=OCS.15)
ms:contentKeyID: 49306303
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Compreendendo os requisitos de firewall para Servidor SQL com Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para a implantação do Standard Edition, exceções de firewall são criadas automaticamente durante a instalação do Lync Server 2013. No entanto, para implantações do Enterprise Edition é preciso configurar as exceções de firewall manualmente no Servidor Back-End do SQL Server. O protocolo TCP/IP permite o uso de determinada porta uma vez para um certo endereço IP. Isso significa que, para o servidor baseado no SQL Server, é possível atribuir a instância de banco de dados padrão à porta TCP padrão 1433. Para qualquer outra instância, é preciso usar o SQL Server Configuration Manager a fim de atribuir portas exclusivas e não usadas. Este tópico aborda:

  - Requisitos para uma exceção de firewall ao usar a instância padrão

  - Requisitos para uma exceção de firewall para o serviço SQL Server Browser

  - Requisitos para portas de escuta estática ao usar instâncias nomeadas

## Requisitos para uma exceção de firewall ao usar a instância padrão

Se você estiver usando a instância padrão do SQL Server para qualquer banco de dados ao implantar o Lync Server 2013, os seguintes requisitos de regra de firewall serão utilizados para ajudar a garantir a comunicação do pool de Front-Ends com a instância padrão do SQL Server.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo</th>
<th>Porta</th>
<th>Direção</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP</p></td>
<td><p>1433</p></td>
<td><p>Entrada para SQL Server</p></td>
</tr>
</tbody>
</table>


## Requisitos para uma exceção de firewall para o serviço SQL Server Browser

O serviço SQL Server Browser localizará as instâncias do banco de dados e comunicará a porta que a instância (nomeada ou padrão) está configurada para usar.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo</th>
<th>Porta</th>
<th>Direção</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>UDP</p></td>
<td><p>1434</p></td>
<td><p>entrada</p></td>
</tr>
</tbody>
</table>


## Requisitos para portas de escuta estáticas ao usar instâncias nomeadas

Ao usar instâncias nomeadas na configuração do SQL Server para bancos de dados que dão suporte ao Lync Server 2013, é preciso configurar portas estáticas usando o SQL Server Configuration Manager. Depois que as portas estáticas forem atribuídas a cada instância nomeada, crie exceções para cada porta estática no firewall.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Protocolo</th>
<th>Porta</th>
<th>Direção</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP</p></td>
<td><p>Definido estaticamente</p></td>
<td><p>entrada</p></td>
</tr>
</tbody>
</table>


## Documentação do SQL Server

A documentação do Microsoft SQL Server 2012 fornece orientações detalhadas sobre como configurar o acesso de firewall para banco de dados. Para obter detalhes sobre o Microsoft SQL Server 2012, consulte “Configurar o Firewall do Windows para permitir acesso ao SQL Server” em [http://go.microsoft.com/fwlink/p/?linkId=218031](http://go.microsoft.com/fwlink/p/?linkid=218031).

