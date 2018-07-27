---
title: 'Lync Server 2013: Criar ou modificar um grupo de agente'
TOCTitle: Criar ou modificar um grupo de agente
ms:assetid: f1461fff-51c1-4f4b-9311-8cba02c333fc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205370(v=OCS.15)
ms:contentKeyID: 49308576
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um grupo de agente no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-07_

Use um dos procedimentos a seguir para criar ou modificar um grupo de agentes.

> [!NOTE]  
> Um Administrador—por exemplo, CsVoiceAdministrator—deve habilitar os usuários para Enterprise Voice e Lync Server antes de poderem ser designados a grupos de agentes. Se você é um dos Gerentes de Grupo de Resposta designados para um fluxo de trabalho gerenciado, você pode criar grupos de agentes e usá-los nos fluxos de trabalho que gerencia.

> [!IMPORTANT]  
> Quando você atribui usuários como agentes de grupo de resposta, informe-os de que, se eles tiverem o modo Privacidade habilitado, precisarão pesquisar por contatos &quot;RGS Presence Watcher&quot; e adicioná-los à sua lista Contatos. Agentes que tem o modo Privacidade habilitado, mas não tem &quot;RGS Presence Watcher&quot; em sua lista de Contatos, não podem receber chamadas no grupo de resposta. Agentes que não têm o modo Privacidade habilitado não são afetados.

## Usar Painel de Controle do Lync Server para criar ou modificar um grupo de agentes

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.
    
    > [!NOTE]  
    > Se você é um dos Gerentes de Grupo de Resposta delegados para um fluxo de trabalho gerenciado, você pode criar grupos e os usar nos fluxos de trabalho que você gerencia.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Grupos de resposta** e depois em **Grupo**.

4.  Na página **Grupo**, execute um dos seguintes procedimentos:
    
      - Para criar um novo grupo de agentes, clique em **Novo**. No campo de pesquisa **Selecionar um serviço**, digite todo ou parte do nome do serviço **ApplicationServer** para o qual você deseja adicionar o grupo. Na lista resultante de serviços, clique no serviço desejado e em **OK**.
    
      - Para modificar um grupo de agentes existente, digite todo ou parte do nome do grupo de agentes no campo de pesquisa. Na lista de resultados, clique no grupo desejado, clique em **Editar** e depois, clique em **Exibir Detalhes**.

5.  Em **Nome**, digite o nome que identifica o grupo de agentes.

6.  Em **Descrição**, digite uma descrição para o grupo.

7.  Na **Política de participação**, selecione uma das seguintes opções para configurar o comportamento de logon para o grupo:
    
      - Selecione **Informal** para especificar que os agentes no grupo não precisam entrar e sair do grupo. Os agentes entram automaticamente no grupo quando entram no Lync Server 2013.
    
      - Selecione **Formal** para especificar que os agentes no grupo precisam entrar e sair do grupo. Quando você seleciona essa opção, os agentes clicam em um item de menu no Lync para abrir o Internet Explorer e exibir um console de página da web para entrar e sair do grupo.

8.  Em **Tempo de alerta (segundos)**, especifique a duração em segundos do toque para um agente antes de oferecer a chamada para o próximo agente disponível (o padrão é de 20 segundos).
    
    > [!IMPORTANT]  
    > A configuração Tempo de alerta do agente não pode ultrapassar 180 segundos. Caso contrário, o aplicativo do cliente rejeitará a chamada devido ao fato de o timer de transação SIP atingir seu tempo máximo de espera.

9.  No **Método de roteamento**, selecione o método para roteamento de chamadas a agentes no grupo da seguinte maneira:
    
      - Para oferecer uma nova chamada primeiro ao agente que ficou mais tempo ocioso (teve uma presença de **Disponível** ou **Inativo** no Lync Server por mais tempo), clique em **Ocioso por mais tempo**.
    
      - Para oferecer uma nova chamada para todos os operadores disponíveis ao mesmo tempo, clique em **Em paralelo**. A chamada é enviada ao primeiro operador que a aceitar.
    
      - Para oferecer uma nova chamada a cada operador um após o outro, clique em **Round robin**.
    
      - Para sempre oferecer uma nova chamada aos operadores na ordem em que estão na lista **Operadores**, clique em **Em série**.
    
      - Para oferecer uma nova chamada a todos os agentes conectados ao Lync Server 2013 e ao Aplicativo Grupo de Resposta ao mesmo tempo, independentemente de sua presença atual, clique em **Attendant**. Usuários do Lync 2010 Attendant configurados como agentes podem ver todas as chamadas que estão aguardando e responder às chamadas em espera em qualquer ordem. A chamada é enviada ao primeiro agente que a aceita, e os outros usuários do Lync 2010 Attendant não veem mais a chamada.

10. Em **Agentes**, especifique como você deseja criar sua lista de agentes:
    
      - Para usar uma lista de agentes personalizada, clique em **Definir um grupo personalizado de agentes** e execute um dos seguintes procedimentos:
        
          - Para adicionar um usuário ao grupo de agentes, clique em **Selecionar**, depois no campo de pesquisa **Selecionar Agentes**, digite todo ou parte do nome do usuário que você quer adicionar ao grupo e clique em **Localizar**. Na lista de agentes resultante, clique no usuário que você quer adicionar e clique em **OK**.
        
          - Para remover um usuário do grupo de agentes, na lista de agentes, clique no usuário que deseja remover e clique em **Remover**.
        
          - Para alterar a ordem em que os agentes são oferecidos às chamadas nos grupos usando rodízio ou encaminhamento em série, na lista de agentes, clique em um usuário e depois clique em seta para cima ou na seta para baixo.
    
      - Para usar uma lista de distribuição do Microsoft Exchange Server como grupo de agentes, clique em **Usar uma lista de distribuição de email existente** e em **Endereço da lista de distribuição**, digite o endereço de email da lista de distribuição (por exemplo, NetworkSupport@contoso.com).
        
        Se você usar uma lista de distribuição por email, estará sujeito às seguintes restrições:
        
          - Você não pode selecionar várias listas de distribuição para o grupo de operadores. Cada grupo oferece suporte a apenas uma lista de distribuição.
        
          - Se a lista de distribuição contiver uma ou mais listas de distribuição, os membros das listas aninhadas não serão adicionados à lista de operadores.
        
          - Se os roteamentos em série e round robin forem selecionados, o servidor oferecerá uma chamada de entrada ao agente apropriado de acordo com o método de roteamento e com a ordem na qual os agentes estão listados na lista de distribuição.
        
          - Se a lista de distribuição contiver usuários, para os quais o Lync Server 2010 estiver habilitado, porém o Enterprise Voice não estiver habilitado, eles serão adicionados ao grupo de agentes como agentes não funcionais. Garanta que todos os membros da lista de distribuição tenham o Enterprise Voice habilitado em suas contas de usuário.
        
        > [!IMPORTANT]  
        > Se você usar uma lista de distribuição de email, associações ou listas ocultas poderão ficar visíveis ao administrador ou usuários do Grupo de Resposta.        
        Associações ou listas ocultas podem se tornar visíveis da seguinte maneira:
        
          - Se uma lista de distribuição tiver sido configurada de modo que a associação fique oculta e o administrador do Grupo de Resposta atribua a lista de distribuição à lista de agentes, os usuários podem chamar o grupo para descobrir quem são os membros.
        
          - Se uma lista de distribuição tiver sido configurada de modo que fique oculta na Lista de Endereços Global do Exchange, o administrador do Grupo de Resposta poderá ver a lista de distribuição e atribui-la à lista de agentes se o processo do Grupo de Resposta tiver os direitos e permissões de usuário apropriados, mesmo se o administrador não tiver os direitos e permissões de usuário apropriados.

11. Clique em **Confirmar**.

## Usar Windows PowerShell para criar ou modificar um grupo de agentes

1.  Faça logon como um membro do grupo RTCUniversalServerAdmins ou como um membro de uma das funções administrativas predefinidas que oferecem suporte ao Grupo de Resposta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Use **New-CsRgsAgentGroup** para criar um novo grupo de agentes. Use **Set-CsRgsAgentGroup** para modificar um grupo de agentes existente. Na linha de comando, execute:
    
        New-CsRgsAgentGroup -Name "<agent group name>" -Parent $serviceId [-Description "<agent group description>"] -[AgentAlertTime <# seconds until call is routed to next agent>] [-ParticipationPolicy <Formal | Informal>] [-RoutingMethod <method for routing calls>] [-AgentsByUri("<first agent's SIP address>","<second agent's SIP address>")];
    
    Por exemplo:
    
        New-CsRgsAgentGroup -Name "Help Desk" -Parent "service:ApplicationServer:atl-cs-001.contoso.com"  -Description "Contoso Help Desk" -AgentAlertTime 20 -ParticipationPolicy Formal -RoutingMethod RoundRobin -AgentsByUri("sip:mindy@contoso.com","sip:bob@contoso.com")
    
    > [!IMPORTANT]  
    > A configuração Tempo de alerta do agente não pode ultrapassar 180 segundos. Caso contrário, o aplicativo do cliente rejeitará a chamada devido ao fato de o timer de transação SIP atingir seu tempo máximo de espera.

4.  Confirme a criação do novo grupo. Execute:
    
        Get-CsRgsAgentGroup -Name "Help Desk"

## Consulte Também

#### Tarefas

[Excluir um grupo de agentes](lync-server-2013-delete-an-agent-group.md)  

#### Outros Recursos

[Gerenciar grupos de agentes dos grupos de resposta](lync-server-2013-managing-response-group-agent-groups.md)  
[Get-CsService](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsService)  
[New-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsRgsAgentGroup)  
[Set-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsRgsAgentGroup)  
[Get-CsRgsAgentGroup](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsRgsAgentGroup)

