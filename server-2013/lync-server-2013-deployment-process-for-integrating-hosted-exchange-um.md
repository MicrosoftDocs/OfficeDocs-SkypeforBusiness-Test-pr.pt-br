---
title: 'Lync Server 2013: Processo de implantação para integrar o Exchange UM hospedado'
TOCTitle: Processo de implantação para integrar o Exchange UM hospedado
ms:assetid: dbec9c38-7f66-419d-b8c3-c61380052cac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398968(v=OCS.15)
ms:contentKeyID: 49308312
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação para integrar o Exchange UM hospedado ao Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Um planejamento efetivo para integrar o Lync Server 2013 ao serviço de UM (Unificação de Mensagens) do Exchange hospedado requer que os seguintes procedimentos sejam levados em consideração:

  - Pré-requisitos para a integração do Lync Server 2013 com a UM do Exchange hospedada

  - Etapas necessárias durante o processo de integração

## Pré-requisitos de implantação para a integração com UM do Exchange hospedada

Antes de começar o processo de integração, você já deve ter implantado o Lync Server 2013 (como mínimo, um pool de front-end ou um servidor do Standard Edition), um Servidor de Borda e o Lync 2013 ou clientes do Lync 2010.

## Processo de integração

A tabela a seguir fornece uma visão geral do processo de integração da UM do Exchange hospedada. Para obter detalhes sobre as etapas de implantação, consulte [Fornecendo caixa postal a usuários do Lync Server 2013 no Exchange UM hospedado](lync-server-2013-providing-lync-server-users-voice-mail-on-hosted-exchange-um.md) na documentação Implantação.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Direitos e permissões</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Configuração do Servidor de Borda.</p></td>
<td><ol>
<li><p>Configure o Servidor de Borda para federação.</p></li>
<li><p>Replique manualmente os dados para o Servidor de Borda.</p></li>
<li><p>Configure um provedor de hospedagem no Servidor de Borda.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configure-the-edge-server-for-integration-with-hosted-exchange-um.md">Configurar Servidor de Borda para integração com o Exchange UM hospedado</a></p></td>
</tr>
<tr class="even">
<td><p>Configure a política de caixa postal hospedada.</p></td>
<td><ol>
<li><p>Modifique a política global de caixa postal hospedada ou crie uma nova política de caixa postal hospedada com escopo de Site ou Por usuário.</p></li>
<li><p>Para políticas com o escopo Por usuário, atribua a política aos usuários ou grupos.</p></li>
</ol></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-manage-hosted-voice-mail-policies.md">Gerenciar políticas de caixa postal hospedada no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Habilite os usuários para caixa postal hospedada</p></td>
<td><ul>
<li><p>Configure contas de usuário para usuário cujas caixas postais estão em um serviço do Exchange hospedado.</p></li>
</ul></td>
<td><p>RTCUniversalUserAdmins</p></td>
<td><p><a href="lync-server-2013-enable-users-for-hosted-voice-mail.md">Habilitar usuários para correio de voz hospedado no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure objetos de contato hospedados.</p></td>
<td><ol>
<li><p>Crie objetos de contato Atendedor Automático para UM do Exchange hospedada.</p></li>
<li><p>Crie objetos de contato Acesso do Assinante para UM do Exchange hospedada.</p></li>
</ol></td>
<td><p>RTCUniversalUserAdmins</p>

> [!NOTE]  
> Para criar, modificar ou remover objetos de contato, o usuário que executa o cmdlet New-CsExUmContact, Set-CsExUmContact ou Remove-CsExUmContact precisa ter a permissão correta para a unidade organizacional Active Directory na qual os novos objetos de contato são armazenados. Essa permissão pode ser atribuída por meio da execução do cmdlet Grant-CsOUPermission. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.

</td>
<td><p><a href="lync-server-2013-create-contact-objects-for-hosted-exchange-um.md">Criar objetos de contato para Exchange UM hospedado no Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>

