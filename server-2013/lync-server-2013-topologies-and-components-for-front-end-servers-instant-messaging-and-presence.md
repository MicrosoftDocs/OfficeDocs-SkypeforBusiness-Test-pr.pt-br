---
title: 'Lync Server 2013: Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença'
TOCTitle: Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença
ms:assetid: f08ce7a1-d14e-4a54-9771-a82c870658bf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412996(v=OCS.15)
ms:contentKeyID: 49308565
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologias e componentes para Servidores Front-End, serviço de mensagens instantâneas e presença no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Os únicos componentes necessários para mensagem instantânea (IM) e presença são:

  - Os servidores do front-end da sua organização ou servidores do Standard Edition. As capacidades de IM e presença estão sempre habilitadas nestes servidores.

  - Um balanceador de carga, se você tem um Enterprise EditionPool de Front-Ends. Para obter mais informações, consulte [Requisitos de balanceamento de carga para Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

## Planejando a implantação de pools de Front Ends

No Lync Server 2013, a arquitetura do Pool de Front-Ends mudou, e essas mudanças afetam a forma como você deve planejar e manter o seu Pools de Front-Ends.

Recomendamos que todos os seus Enterprise EditionPools de Front-Ends incluam pelo menos três Servidores de Front End. No Lync Server, a arquitetura dos Pools de Front-Ends usa um modelo de sistemas distribuídos, em que os dados de cada usuário são mantidos em três servidores de Front End no pool. Para obter mais informações sobre esta nova arquitetura, consulte [Alterações de topologia no Lync Server 2013](lync-server-2013-topology-changes.md).

Se você não deseja implantar três Enterprise EditionServidores Front-End e deseja ter recuperação de desastres, recomendamos usar o Lync ServerStandard Edition e criar dois pools com um relacionamento de backup emparelhado. Isso fornecerá uma solução para recuperação de desastres com apenas dois servidores. Para obter mais informações sobre recursos e topologias de recuperação de desastres e alta disponibilidade, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

## Planejando o gerenciamento de pool de Front Ends

Para Pools de Front-Ends, siga as diretrizes nesta seção.

## Garantindo que os pools sejam funcionais

Com o novo modelo distribuído para Pools de Front-Ends, alguns números de servidores do pool devem estar em execução para que o pool funcione. Há dois modos de perda para um pool

  - Perda de quórum no nível do grupo de roteamento, causada por servidores de réplica insuficientes para um grupo de roteamento em particular. Um grupo de roteamento é uma agregação de um conjunto de usuários hospedados no pool. Cada grupo de roteamento tem três réplicas no pool: uma primária e duas secundárias.

  - Perda de quórum no nível do pool, causada quando servidores sementes insuficientes estão em execução no pool.

## Perda de quórum no nível do grupo de roteamento

A primeira vez que você iniciar um novo Pool de Front-Ends, é essencial que 85% dos servidores estejam em operação, conforme exibido na tabela a seguir. Caso menos servidores estejam em operação, os serviços poderão ficar parados no estado inicial e o pool pode não iniciar.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Número total de servidores no pool</th>
<th>Número de servidores que devem estar em execução para que o pool seja iniciado na primeira vez</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>3</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>3</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p>5</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>5</p></td>
</tr>
<tr class="odd">
<td><p>8</p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p>9</p></td>
<td><p>7</p></td>
</tr>
<tr class="odd">
<td><p>10</p></td>
<td><p>8</p></td>
</tr>
<tr class="even">
<td><p>11</p></td>
<td><p>9</p></td>
</tr>
<tr class="odd">
<td><p>12</p></td>
<td><p>10</p></td>
</tr>
</tbody>
</table>


Cada vez subsequente que o pool for iniciado, 85% dos servidores devem ser iniciados (conforme exibido na tabela anterior). Caso não seja possível iniciar esse número de servidores (mas servidores suficientes podem ser iniciados para que não haja perda de quórum no nível do pool), é possível usar o cmdlet **Reset-CsPoolRegistrarState –ResetType QuorumLossRecovery** para permitir que o pool se recupere dessa perda de quórum no nível do grupo de roteamento e faça progresso. Para obter mais informações sobre como usar este cmdlet, consulte [Reset-CsPoolRegistrarState](https://docs.microsoft.com/en-us/powershell/module/skype/Reset-CsPoolRegistrarState).

> [!NOTE]  
> Como o Lync Server usa o banco de dados SQL primário como testemunha, se você desligar o banco de dados primário, alternar para a cópia Espelho e desligarServidores Front-End suficientes para que um número insuficiente esteja em operação de acordo com a tabela anterior, todo o pool será desligado. Para obter mais informações, consulte <a href="http://go.microsoft.com/fwlink/?linkid=393672">Testemunha de espelhamento de banco de dados</a>.

## Perda de quórum no nível do pool

Para que um Pool de Front-Ends funcione, ele não pode estar em perda de quórum no nível do pool. Se o número de servidores em execução estiver abaixo do nível funcional conforme exibido na tabela anterior, os servidores restantes no pool interromperão todos os serviços do Lync Server. Observe que os números na tabela a seguir assumem que os Servidores Back-end no pool estão em execução.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Número total de Servidores de Front End no pool</th>
<th>Número de servidores que devem estar em execução para o pool ser funcional</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>1</p></td>
</tr>
<tr class="even">
<td><p>3-4</p></td>
<td><p>Qualquer um dos 2</p></td>
</tr>
<tr class="odd">
<td><p>5-6</p></td>
<td><p>Qualquer um dos 3</p></td>
</tr>
<tr class="even">
<td><p>7</p></td>
<td><p>Qualquer um dos 4</p></td>
</tr>
<tr class="odd">
<td><p>8-9</p></td>
<td><p>Qualquer um dos 4 dos 7 primeiros servidores</p></td>
</tr>
<tr class="even">
<td><p>10-12</p></td>
<td><p>Qualquer um dos 5 dos 9 primeiros servidores</p></td>
</tr>
</tbody>
</table>


Na tabela anterior, os “primeiros servidores” são aqueles criados primeiro, cronologicamente, quando o pool foi iniciado pela primeira vez. Para determinar esses servidores, utilize o cmdlet **Get-CsComputer** com a opção **–PoolFqdn**. Esse cmdlet exibirá os servidores na ordem em que aparecem na topologia, e aqueles que aparecem no topo da lista são os primeiros servidores.

## Pool de Front-Ends com dois Servidores de Front End

Não recomendamos implantar um pool de Front Ends que contém apenas dois Servidores de Front End. Se você precisar implantar este tipo de pool, siga as seguintes orientações:

  - Se um dos dois Servidores de Front End ficar inativo, você deve ativá-lo assim que possível. Da mesma forma, se você precisar atualizar um dos dois servidores, ative-o assim que a atualização terminar.

  - Se por alguma razão você precisar desativar ambos os servidores ao mesmo tempo, realize o seguinte procedimento quando o tempo de inatividade do pool for concluído:
    
      - A prática recomendada é reiniciar os dois servidores front-end ao mesmo tempo.
    
      - Se os dois servidores não podem ser reiniciados ao mesmo tempo, você deve ativá-los na ordem contrária em que foram desativados.
    
      - Se você não puder ativá-los nesta ordem, use o seguinte cmdlet antes de ativar o pool:
        
            Reset-CsPoolRegistrarState -ResetType QuorumLossRecovery -PoolFQDN <FQDN>

## Etapas Adicionais para Garantir que os Pools sejam Funcionais

Observe alguns outros fatores para garantir que o Pools de Front-Ends permaneça funcional.

  - Ao migrar usuários para o pool pela primeira vez, certifique-se de que pelo menos três dos Servidores de Front End estão em execução.

  - Se você estabelecer um relacionamento de emparelhamento entre este e um outro pool para fins de recuperação de desastres, após estabelecer esse relacionamento você deve garantir que o pool tenha três Servidores de Front End em execução simultânea em algum momento para sincronizar adequadamente os dados com o pool de backup. Para obter mais informações sobre emparelhamento de pools e recursos de recuperação de desastres, consulte [Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

## Aprimorando a Confiabilidade de Atualizações de Pool

Quando há a necessidade de atualizar ou corrrigir os servidores em um Pool de Front-Ends, siga o fluxo de trabalho exibido em [Atualizar servidores Front End no Lync Server 2013](lync-server-2013-upgrade-or-update-front-end-servers.md), e as seguintes diretrizes:

  - Quando você move de um domínio de atualização para outro para obter atualizações (seguindo o fluxo de trabalho em [Atualizar servidores Front End no Lync Server 2013](lync-server-2013-upgrade-or-update-front-end-servers.md)), utilize o cmdlet **Get-CsPoolUpgradeReadinessState** e verifique se está no estado Pronto. Esperar 20 minutos entre cada domínio de atualização depois que alcançar o estado “Pronto” torna as atualizações mais confiáveis. Se ficar no estado **Não está Pronto** durante esses 20 minutos, reinicie o timer de 20 minutos. Além disso, você pode executar o cmdlet **Get-CsPoolFabricState** antes e depois de iniciar o intervalo de 20 minutos e se certificar de que não há alterações nos primários e secundários dos grupos de roteamento.

  - Não prossiga para o próximo domínio de atualização se qualquer um dos servidores no último domínio de atualização corrigido estiver parado ou não foi reiniciado. Isso também se aplica a qualquer servidor na atualização que não possa ser iniciado. Execute **Get-CsPoolFabricState** para se certificar de que todos os grupos de roteamento tenham um primário e pelo menos um secundário. Isso confirmará se todos os usuários têm serviço.

  - Se alguns usuários tiverem serviço e outros não, execute **Get-CsPoolFabricState** com a opção –Verbose para verificar grupos de roteamento que tenham réplicas ausentes. Não reinicie todo o pool como a primeira etapa de solução de problemas. Para obter mais informações sobre este cmdlet, consulte [Get-CsPoolFabricState](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsPoolFabricState).

  - Certifique-se de que todas as instâncias de janelas do Visualizador de Eventos ou Monitor de Desempenho estejam fechadas para instalações/desinstalações do Windows Fabric.

## Alterando a configuração de um Pool de Front Ends

Sempre que você adicionar ou remover Servidores de Front End de um pool, e depois publicar a nova topologia, siga essas orientações:

  - Após a publicação da nova topologia, você deve reiniciar cada Servidor Front-End no pool. Reinicie todos eles, um de cada vez.

  - Se todo o pool ficou desativado durante a alteração nas configurações, execute o seguinte cmdlet depois de publicar a nova topologia:
    
        Reset-CsPoolRegistrarState -PoolFQDN <PoolFQDN> -ResetType ServiceReset

Se um Servidor de Front End falhar e não puder ser substituído em alguns dias ou mais, remova o servidor da topologia. Adicione o novo Servidor de Front End à topologia quando estiver disponível novamente.

