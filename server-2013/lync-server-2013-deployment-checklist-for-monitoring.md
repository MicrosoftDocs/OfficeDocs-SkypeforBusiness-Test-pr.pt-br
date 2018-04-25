---
title: 'Lync Server 2013: Lista de verificação de implantação para monitoramento'
TOCTitle: Lista de verificação de implantação para monitoramento
ms:assetid: 4e798370-277c-4391-84b4-13a972b45ca6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204874(v=OCS.15)
ms:contentKeyID: 49886199
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação de implantação para monitoramento no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Apesar de o monitoramento já estar instalado e ativado em cada servidor Front End, ainda há várias etapas que você deve realizar antes de poder recolher os dados de monitoramento do Microsoft Lync Server 2013. Essas etapas são descritas na seguinte lista de verificação:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Fase</p></td>
<td><p>Etapas</p></td>
<td><p>Associação de grupo e função</p></td>
<td><p>Documentação</p></td>
</tr>
<tr class="even">
<td><p><strong>Instalar os pré-requisitos de hardware e software</strong></p></td>
<td><p>Instale uma versão do Microsoft SQL Server suportada no computador que atuará como armazenamento de dados backend do monitoramento.</p></td>
<td><p>Usuário do domínio que também é membro do grupo local de administradores.</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Hardware suportado para Lync Server 2013</a> no guia do Modo de suporte</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Suporte a software e à infraestrutura de servidor no Lync Server 2013</a> no guia de Modo de suporte</p></td>
</tr>
<tr class="odd">
<td><p><strong>Criar a topologia interna apropriada para dar suporte ao monitoramento</strong></p></td>
<td><p>Use o Construtor de Topologia Lync Server 2013 para adicionar o banco de dados de monitoramento à topologia e, em seguida, publique a topologia atualizada.</p></td>
<td><p>Para definir uma topologia, um usuário que seja membro do grupo local de usuários.</p>
<p>Para publicar a topologia, um usuário que seja membro do grupo de administradores de domínio e do grupo RTCUniversalServerAdmins.</p></td>
<td><p><a href="lync-server-2013-associating-a-monitoring-store-with-a-front-end-pool.md">Associando um Repositório de Monitoramento ao Pool de Front End</a> no guia de Implantação</p></td>
</tr>
<tr class="even">
<td><p><strong>Habilitar a configuração de monitoramento apropriada</strong></p></td>
<td><p>Habilitar registro de detalhes das chamadas (CDR) e/ou o monitoramento da Qualidade da Experiência (QoE) no escopo global e/ou do site.</p></td>
<td><p>Um usuário que seja membro do grupo RTCUniversalServerAdmins ou que tenha sido atribuído a uma função RBAC que fornece acesso aos cmdlets CsCdrConfiguration e CsQoEConfiguration .</p></td>
<td><p><a href="lync-server-2013-configuring-call-detail-recording-and-quality-of-experience-settings.md">Configurando registro de detalhes de chamada e definições de qualidade de experiência</a> no guia de Operações</p></td>
</tr>
</tbody>
</table>

