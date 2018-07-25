---
title: Lista de verificação de implantação para conferência A/V
TOCTitle: Lista de verificação de implantação para conferência A/V
ms:assetid: 6d47426f-6559-407b-9ac1-2453f0b7a2a2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ619183(v=OCS.15)
ms:contentKeyID: 49307034
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação de implantação para conferência A/V

 

_**Tópico modificado em:** 2015-03-09_

Assim como a implantação de outros componentes do Lync Server 2013, a implantação da conferência A/V requer o uso do Construtor de Topologias para criar e publicar uma topologia que incorpore conferências.

## Sequência de implantação

Você pode implantar conferências ao mesmo tempo em que implanta a topologia inicial ou após implantar pelo menos um Pool de Front-Ends ou Servidor Standard Edition

## Processo de implantação de conferências

A tabela a seguir fornece uma visão geral das etapas necessárias para implantar conferências em uma topologia existente.


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
<th>Associações a grupos e funções</th>
<th>Documentação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Instalar pré-requisitos de hardware e software</strong></p></td>
<td><p>A conferência é executada em Servidores Front-End de um Pool de Front-Ends e Servidores Standard Edition. Não há requisitos adicionais de hardware e software além daqueles para instalar esses servidores.</p>


> [!NOTE]  
> Lync Server 2013 usa Office Web Apps e o Servidor Office Web Apps para manipular o compartilhamento e a renderização de apresentações de PowerPoint. Para obter detalhes sobre a instalação e configuração do Servidor Office Web Apps, consulte <a href="lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md">Configurando a integração com servidor de Office Web Apps e Lync Server 2013</a>.

</td>
<td><p>Usuário do domínio que é membro do grupo local de Administradores</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Hardware suportado para Lync Server 2013</a> na documentação Suporte</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Suporte a software e à infraestrutura de servidor no Lync Server 2013</a> na documentação Suporte</p>
<p><a href="lync-server-2013-determining-your-system-requirements.md">Determinando seus requisitos de sistema para Lync Server 2013</a> na documentação Planejamento.</p>
<p><a href="lync-server-2013-technical-requirements-for-archiving.md">Requisitos técnicos de Arquivamento no Lync Server 2013</a> na documentação Planejamento.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p><strong>Crie a topologia interna apropriada para dar suporte a conferências</strong></p></td>
<td><p>Execute o Construtor de Topologias para adicionar conferências à topologia e publicar essa topologia.</p></td>
<td><p>Para definir a topologia, uma conta que é membro do grupo local de Usuários</p>
<p>Para publicar a topologia, uma conta que é membro do grupo de Admins. do Domínio e do grupo do RTCUniversalServerAdmins, e que tem permissões de controle total (ler/escrever/modificar) sobre o compartilhamento do arquivo a ser usado para o repositório de arquivamento do Lync Server 2013 (de forma que o Construtor de Topologias possa configurar os DACLs requeridos)</p></td>
<td><p><a href="lync-server-2013-define-and-configure-a-topology-in-topology-builder.md">Definir e configurar uma topologia no Construtor de Topologia para Lync Server 2013</a> na documentação Implantação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Configurar políticas e suporte de conferências</strong></p></td>
<td><p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para definir configurações de conferências.</p></td>
<td><p>Grupo RTCUniversalServerAdmins (somente Windows PowerShell) ou atribua usuários à função [] ou CSAdministrator</p></td>
<td><p><a href="lync-server-2013-conferencing-policies.md">Políticas de conferência no Lync Server 2013</a> na documentação Operações.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Outros Recursos

[Visão geral de conferência no Lync Server 2013](lync-server-2013-overview-of-conferencing.md)  
[Definindo seus requisitos para conferência no Lync Server 2013](lync-server-2013-defining-your-requirements-for-conferencing.md)

