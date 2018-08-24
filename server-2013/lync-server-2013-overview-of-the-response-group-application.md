---
title: 'Lync Server 2013: Visão geral do aplicativo Grupo de Resposta'
TOCTitle: Visão geral do aplicativo Grupo de Resposta
ms:assetid: 6cc333e7-4029-4372-86b2-016040c415fb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398513(v=OCS.15)
ms:contentKeyID: 49307026
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do aplicativo Grupo de Resposta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Quando um chamador chama um grupo de resposta, a chamada é roteada para um agente com base em um grupo de busca ou mas respostas do chamador para as perguntas de IVR (resposta de voz interativa). O Aplicativo Grupo de Resposta usa métodos de roteamento de grupo de resposta padrão para rotear a chamada para o próximo agente disponível. Os métodos de roteamento de chamada incluem serial, ocioso por mais tempo, paralelo, round robin, e encaminhamento de Atendente (ou seja, todos os agentes são chamados ao mesmo tempo a cada chamada de entrada, independentemente de sua presença atual). Se não houverem agentes disponíveis, a chamada será mantida em uma fila até que um agente esteja disponível. Enquanto está na fila, o chamador ouve música até um agente disponível aceitar a chamada. Se a fila estiver cheia ou se a chamada expirar enquanto estiver na fila, o chamador poderá ouvir uma mensagem e está desconectado ou transferido para um destino diferente. Quando um agente aceita a chamada, o chamador pode ou não ser capaz de ver a identidade do agente, dependendo de como o administrador configura o grupo de resposta. Os agentes podem ser formais, o que significa que eles devem entrar no grupo antes de aceitar chamadas encaminhadas para o grupo, ou informais, que significa que eles não precisam entrar no grupo para aceitar chamadas.

> [!NOTE]  
> Somente os usuários no local podem ser agentes. Se um agente muda para online, as chamadas do Grupo de Resposta não são roteadas para o agente.

> [!NOTE]  
> O Aplicativo Grupo de Resposta usa um serviço interno, chamado de Correspondência, para colocar chamadas na fila e encontrar agentes disponíveis. Cada computador que executa o Aplicativo Grupo de Respostaexecuta o serviço Correspondência, mas apenas um serviço Correspondência por pool do Lync Server está ativo no momento, os outros são passivos. Se o serviço Correspondência ativo ficar indisponível durante uma paralisação não planejada, um dos serviços Correspondência passivos ficará ativo. O Aplicativo Grupo de Resposta faz o melhor para garantir que o encaminhamento e enfileiramento de chamadas continue sem interrupções. No entanto, quando ocorre uma transição do serviço Correspondência, todas as chamadas em transferência no momento são perdidas. Por exemplo, se a transição for devido ao à interrupção do Servidor Front-End, as chamadas manipuladas no momento pelo serviço Correspondência ativo nesse Servidor Front-End também serão perdidas.

No Lync Server 2013, duas funções de gerenciamento estão disponíveis para gerenciar grupos de respostas: Gerente do Grupo de Resposta e Administrador do Grupo de Resposta. Os administradores do Grupo de Resposta podem gerenciar todos os aspectos de qualquer grupos de respostas. Os gerentes do Grupo de Resposta podem gerenciar apenas certos aspectos dos grupos de resposta que possuem. A nova função Gerente pode ajudar a reduzir os custos de administração, pois você pode delegar responsabilidades limitadas de grupos de respostas específicos a qualquer usuário habilitado para Enterprise Voice.

Para acomodar a nova função Gerente, o Lync Server 2013Aplicativo Grupo de Resposta introduz um **Tipo de Fluxo de Trabalho** Gerenciado ou Não gerenciado. A tabela a seguir descreve os grupos de respostas Gerenciado ou Não gerenciado.

### Grupos de respostas Gerenciado ou Não gerenciado

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipo de grupo de respostas</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Não gerenciado</p></td>
<td><ul><li><p>Os grupos de respostas não gerenciados não têm gerentes atribuídos. Somente o administrador do Grupo de Resposta pode configurar esses grupos de respostas.</p></li><li><p>Vários grupos de respostas não gerenciados podem compartilhar uma fila ou grupo de agentes.</p></li><li><p>Quando você migra grupos de respostas de uma versão anterior para o Lync Server 2013, o tipo é definido como Não gerenciado.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Gerenciado</p></td>
<td><ul><li><p>Os administradores do Grupo de Resposta podem configurar qualquer aspecto de grupos de respostas gerenciados.</p></li><li><p>Os gerentes do Grupo de Resposta não podem exibir nem modificar grupos de respostas que não sejam explicitamente atribuídos a eles.</p></li><li><p>Os gerentes do Grupo de Resposta podem definir apenas algumas configurações dos grupos de respostas explicitamente atribuídos a eles.</p></li><li><p>Os grupos de respostas gerenciados não podem compartilhas filas nem grupos de agentes com outros grupos de respostas, sejam gerenciados ou não gerenciados.</p></li></ul></td>
</tr>
</tbody>
</table>


A tabela a seguir descreve as ações que os gerentes do Grupo de Resposta podem ou não executar relativas aos grupos de respostas atribuídos a eles.

### Recursos do gerente do grupo de respostas

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Pode configurar:</th>
<th>Pode criar, excluir ou configurar:</th>
<th>Não pode:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ul><li><p>Agentes</p></li><li><p>Mensagem de boas-vindas</p></li><li><p>Nome do Grupo de Resposta</p></li><li><p>Descrição</p></li><li><p>Número de exibição</p></li><li><p>Horário comercial</p></li><li><p>Música de espera</p></li><li><p>Status (ativo/inativo)</p></li><li><p>Fluxos de trabalho de grupo de busca ou fluxos de trabalho de IVR (reposta interativa de voz)</p></li></ul></td>
<td><ul><li><p>Grupos de agentes</p></li><li><p>Filas</p></li><li><p>Conjuntos de feriados</p></li></ul></td>
<td><ul><li><p>Criar ou excluir qualquer tipo de fluxo de trabalho</p></li><li><p>Modificar configurações centrais do grupo de respostas, como: <strong>URI do SIP</strong> , <strong>Número de Telefone</strong> ou <strong>Tipo de Fluxo de Trabalho</strong> .</p></li></ul></td>
</tr>
</tbody>
</table>


Grupo de Resposta Os gerentes podem usar as ferramentas a seguir para gerenciar os grupos de respostas designados.

  - Painel de Controle do Lync Server
    
    > [!NOTE]  
    > Os gerentes do Grupo de Resposta podem gerenciar apenas configurações do Grupo de Resposta com esta ferramenta. Outras configurações do Lync Server não estão disponíveis aos gerentes.

  - Ferramenta de Configuração de Grupo de Resposta

  - Shell de Gerenciamento do Lync Server

O Grupo de Resposta também se adapta bem em ambientes de departamentos ou grupos de trabalho (para obter detalhes, consulte [Planejamento de capacidade para Grupo de Resposta no Lync Server 2013](lync-server-2013-capacity-planning-for-response-group.md)) e pode ser implantado em instalações de telefonia totalmente nova. Ele oferece suporte a chamadas de entrada da implantação do Enterprise Voice e da rede da operadora local. Os agentes podem usar o Lync 2013, Lync 2010, Lync 2010 Attendant ou Lync Phone Edition para atender a chamadas roteadas para eles.

O Aplicativo Grupo de Resposta é um componente do Enterprise Voice. Quando você implanta o Enterprise Voice, o Aplicativo Grupo de Resposta é instalado e ativado automaticamente.

