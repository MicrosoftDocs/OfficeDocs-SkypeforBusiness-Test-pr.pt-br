---
title: Instalando e configurando os nós do inspetor
TOCTitle: Instalando e configurando os nós do inspetor
ms:assetid: 61f6deea-e3ef-4468-9be8-a65705815ebb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204943(v=OCS.15)
ms:contentKeyID: 49306893
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando e configurando os nós do inspetor

 

_**Tópico modificado em:** 2015-03-09_

*Nós do inspetor* são computadores que periodicamente executam transações sintéticas do Lync Server. *Transações sintéticas* são cmdlets do Windows PowerShell que verificam se recursos básicos do usuário final, como a capacidade de entrar no sistema ou de trocar mensagens instantâneas, estão funcionando corretamente. Para o Lync Server 2013, o System Center Operations Manager pode executar as transações sintéticas que constam na tabela a seguir. A tabela mostra três tipos diferentes de transações sintéticas:

  - **Padrão**. São aquelas transações sintéticas que um nó do inspetor executa por padrão. Quando você criar um novo nó do inspetor, terá a opção de especificar quais transações sintéticas esse nó executará (essa é a finalidade do parâmetro Tests usado pelo cmdlet **New-CsWatcherNodeConfiguration**). Se você não usar o parâmetro Tests quando o nó do inspetor for criado, ele automaticamente executará todas as transações sintéticas padrão e não executará nenhuma das transações sintéticas não padrão. Isso significa, por exemplo, que o nó do inspetor será configurado para executar o teste Test-CsAddressBookService, mas não o teste Test-CsExumConnectivity.

  - **Não padrão**. Como o nome já diz, as transações sintéticas não padrão são testes que os nós do inspetor não executam por padrão. No entanto, o nó do inspetor pode ser habilitado para executar qualquer uma das transações sintéticas não padrão. Você pode fazer isso ao criar o nó do inspetor (usando o cmdlet **New-CsWatcherNodeConfiguration**) ou a qualquer momento após a criação. Muitas das transações sintéticas não padrão exigem etapas de configuração adicionais. Para obter detalhes, consulte [Instruções Especiais de Configuração para Transações Sintéticas](lync-server-2013-special-setup-instructions-for-synthetic-transactions.md).

  - **Estendidas**. Os testes estendidos são um tipo especial de transação sintética não padrão. Diferentemente das outras transações sintéticas, os testes estendidos podem ser executados várias vezes durante cada fase. Isso pode ser útil, por exemplo, para verificações de várias rotas de voz de PSTN (rede telefônica pública comutada) de um pool. Isso pode ser configurado com a simples adição de várias instâncias de um teste estendido a um nó do inspetor.

Para obter detalhes sobre o processo de adição de outras transações sintéticas a um nó do inspetor, consulte [Gerenciar nós inspetores](lync-server-2013-managing-watcher-nodes.md). Você pode usar o Shell de Gerenciamento do Lync Server para remover transações sintéticas de um nó do inspetor.

As transações sintéticas disponíveis para os nós do inspetor incluem as seguintes:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome do cmdlet (nome do teste)</th>
<th>Descrição</th>
<th>Tipo de transação sintética</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Test-CsAddressBookService (ABS)</p></td>
<td><p>Confirma se os usuários podem pesquisar outros usuários que não estão em sua lista de contatos.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsAddressBookWebQuery (ABWQ)</p></td>
<td><p>Confirma se os usuários podem pesquisar outros usuários que não estão em sua lista de contatos via HTTP.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsIM (IM)</p></td>
<td><p>Confirma se os usuários podem enviar mensagens instantâneas ponto a ponto.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsP2PAV (P2PAV)</p></td>
<td><p>Confirma se os usuários podem realizar chamadas de áudio ponto a ponto (apenas sinalização).</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsPresence (Presence)</p></td>
<td><p>Confirma se os usuários podem exibir a presença de outros usuários.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsRegistration (Registration)</p></td>
<td><p>Confirma se os usuários podem entrar no Lync.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsAudioConferencingProvider (ACP)</p></td>
<td><p>Não é usado com a versão local do Lync Server 2013</p></td>
<td><p>Estendida</p></td>
</tr>
<tr class="even">
<td><p>Test-CsPstnPeerToPeerCall (PSTN)</p></td>
<td><p>Confirma se os usuários podem realizar e receber chamadas de pessoas de fora da organização (números PSTN).</p></td>
<td><p>Não padrão, estendida</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsAVConference (AvConference)</p></td>
<td><p>Confirma se os usuários podem criar e participar de uma conferência de áudio/vídeo.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsAVEdgeConnectivity (AVEdgeConnectivity)</p></td>
<td><p>Confirma se os servidores de borda A/V podem aceitar conexões para chamadas ponto a ponto e chamadas em conferência.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsDataConference (DataConference)</p></td>
<td><p>Confirma se os usuários podem participar de uma conferência com colaboração de dados, uma reunião online que inclui atividades como quadros de comunicações e votações.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsExumConnectivity (ExumConnectivity)</p></td>
<td><p>Confirma se um usuário pode conectar-se ao Unificação de Mensagens (UM) do Exchange.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsGroupIM (GroupIM)</p></td>
<td><p>Confirma se os usuários podem enviar mensagens instantâneas em conferências e participar de conversas de mensagem instantânea com três ou mais pessoas.</p></td>
<td><p>Padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsGroupIM –TestJoinLauncher (JoinLauncher)</p></td>
<td><p>Confirma se os usuários podem criar reuniões agendadas e ingressar nelas através de um link de endereço Web.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsMCXP2PIM (MCXP2PIM)</p></td>
<td><p>Confirma se usuários de dispositivos móveis podem registrar-se e enviar mensagens instantâneas.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsPersistentChatMessage (PersistentChatMessage)</p></td>
<td><p>Confirma se os usuários podem trocar mensagens usando o serviço de Chat Persistente.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="odd">
<td><p>Test-CsUnifiedContactStore (UnifiedContactStore)</p></td>
<td><p>Confirma se os contatos de um usuário podem ser acessados por meio do repositório unificado de contatos. O repositório unificado de contatos permite que os usuários mantenham um único conjunto de contatos que pode ser acessado pelo Lync 2013, pelo Outlook e/ou pelo Outlook Web Access.</p></td>
<td><p>Não padrão</p></td>
</tr>
<tr class="even">
<td><p>Test-CsXmppIM (XmppIM)</p></td>
<td><p>Confirma se uma mensagem instantânea pode ser enviada através do gateway XMPP.</p></td>
<td><p>Não padrão</p></td>
</tr>
</tbody>
</table>


Não é necessário instalar nós do inspetor para usar o System Center Operations Manager. Se você não instalar esses nós, ainda poderá obter alertas em tempo real de componentes do Lync Server 2013 quando ocorrer um problema (o Pacote de Gerenciamento de Componentes e Usuários não usa nós do inspetor). No entanto, os nós do inspetor serão necessários se você desejar monitorar cenários completos usando o pacote de Gerenciamento de Monitoramento Ativo.

> [!NOTE]  
> Os administradores também podem executar transações sintéticas manualmente, sem a necessidade de usar ou instalar o Operations Manager. Para obter detalhes sobre os diversos cmdlets Test-Cs, consulte o <a href="https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps">Índice de cmdlets do Lync Server 2013</a>.

Dependendo do porte de sua implantação, as transações sintéticas podem consumir uma grande quantidade de memória e tempo de processamento do computador. Por esse motivo, é recomendável usar um computador dedicado como nó do inspetor. Por exemplo, você não deve configurar um Servidor Front-End para atuar como um nó do inspetor. Os nós do inspetor devem atender aos mesmos requisitos de hardware básicos de qualquer outro computador que desempenha alguma função em seu Lync Server.

> [!NOTE]  
> Um nó do inspetor do Microsoft Lync Server 2010 herdado não pode ser colocado na mesma máquina em que há um nó do inspetor do Lync Server 2013. Isso ocorre porque os arquivos de sistema básicos do Lync Server 2010 e do Lync Server 2013 não podem estar instalados no mesmo computador.<br />No entanto, os nós do inspetor do Lync Server 2013 podem monitorar simultaneamente o Lync Server 2013 e o Lync Server 2010. As duas versões do produto oferecem suporte a transações sintéticas padrão.

Os nós do inspetor do Lync Server 2013 podem ser implantados dentro ou fora de uma empresa para ajudar a verificar:

   A conectividade com pools para usuários internos da empresa.

   A conectividade através de redes de perímetro para usuários remotos que trabalham fora da empresa.

   A conectividade com dispositivos de filiais.

   A conectividade com o Lync Server 2010 dentro da empresa e através de redes de perímetro.

Diferentes opções de autenticação estão disponíveis para dentro e fora da empresa a fim de simplificar a administração. Para obter detalhes, consulte [Configurando um nó inspetor para executar transações sintéticas](lync-server-2013-configuring-a-watcher-node-to-run-synthetic-transactions.md).

Para configurar um computador para atuar como um nó do inspetor, execute as etapas a seguir após ter instalado o System Center Operations Manager e importado os pacotes de gerenciamento do Lync Server 2013.

Antes de instalar os arquivos básicos do Lync Server 2013 e os arquivos de agente do System Center, você também deve verificar se o computador do nó do inspetor atende a todos os pré-requisitos para a instalação do Lync Server 2013. Além disso, o computador do nó do inspetor também deve ter os seguintes itens instalados:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente de hardware</th>
<th>Requisitos mínimos</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Um dos seguintes:</p><ul><li><p>Processador de 64 bits, quad-core, 2,33 GHz ou superior</p></li><li><p>Processador de 2 vias e 64 bits, dual-core, 2,33 GHz ou superior</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Memória</p></td>
<td><p>8 GB</p></td>
</tr>
<tr class="odd">
<td><p>Rede operando sistema</p></td>
<td><ul><li><p>1 adaptador de rede 1 Gbps</p></li><li><p>Windows Server 2008 R2, Windows Server 2012 ou</p>
<p>Windows Server 2012 R2</p></li></ul></td>
</tr>
</tbody>
</table>


  - A versão completa do .NET Framework 4.5.

  - Windows Identity Foundation.

  - Windows PowerShell 3.0.

Depois que todos esses pré-requisitos forem atendidos, você poderá configurar o nó do inspetor executando as seguintes etapas:

  - Instale os arquivos básicos do Lync Server 2013 no computador do nó do inspetor.

  - Instale o agente do System Center Operations Manager no computador do nó do inspetor.

  - Execute o arquivo executável Watchernode.msi.

  - Use os cmdlets **CsWatcherNodeConfiguration** para configurar os usuários de teste a serem empregados pelo nó do inspetor.

