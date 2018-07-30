---
title: 'Lync Server 2013: Planejamento para recuperação de desastre de grupos de resposta'
TOCTitle: Planejamento para recuperação de desastre de grupos de resposta
ms:assetid: 14e0f5dc-77cd-42cd-a9c9-4d0da38fb1cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204699(v=OCS.15)
ms:contentKeyID: 49305972
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para recuperação de desastre de grupos de resposta no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Essa seção descreve algumas maneiras de preparar respostas de grupo para recuperação de desastres e fornece uma visão geral do processo de recuperação de desastres.

## Preparando-se para a recuperação de desastres do Grupo de Resposta

Lembre-se, ao se preparar para e executar procedimentos de recuperação de desastres, das coisas a seguir.

> [!NOTE]  
> Em um ambiente de coexistência, apenas os grupos de resposta do Lync Server 2013 são suportados para os procedimentos de recuperação de desastres descritos neste documento.

  - Planeje para recuperação de desastres ao fazer seu planejamento de capacidade. Para capacidade de recuperação de desastres, cada pool em um pool pareado deve ser capaz de lidar com as cargas de trabalho de todos os grupos de resposta em ambos os pools. Para detalhes sobre planejamento de capacidade do Grupo de Resposta, consulte [Planejamento de capacidade para Grupo de Resposta no Lync Server 2013](lync-server-2013-capacity-planning-for-response-group.md).

  - Faça cópias de backup regularmente de todas as configurações de grupo de resposta em todos os Pools de Front-Ends onde você implantou o Aplicativo Grupo de Resposta, usando o procedimento de exportação descrito neste documento. Para detalhes, consulte [Procedimento de recuperação de desastre do grupo de resposta no Lync Server 2013](lync-server-2013-response-group-disaster-recovery-procedures.md). Mantenha as cópias de backup em um local seguro.

  - Mantenha uma cópia separada de backup de todos os arquivos de áudio originais que você usou para o Aplicativo Grupo de Resposta, incluindo quaisquer gravações e arquivos de música de espera. Mantenha os arquivos de backup em um local seguro.

  - Para recuperação de desastre do Lync Server 2013, todas as definições do Grupo de Resposta devem ter nomes exclusivos por toda a sua implantação. Esse requisito se aplica a fluxos de trabalho, filas, grupos de agente, conjuntos de feriados e horários comerciais. Você deve verificar se este requisito é atendido quando os pools primário e de backup ainda estão ativos, e antes de precisar iniciar qualquer procedimento de failover. Caso encontre conflitos de nome ao importar dados de grupo de resposta ao pool de backup, a importação falha. Para completar o procedimento de importação e failover, você deve solucionar os conflitos de nome, renomeando o objeto de grupo de resposta no pool de backup, ou usando o cmdlet **Import-CsRgsConfiguration** com o parâmetro -ResolveNameConflicts para solucionar automaticamente o conflito anexando um número de identificação exclusivo ao objeto de grupo de resposta.

  - No geral, recomendamos que você execute backups diários, mas caso possua um volume alto de alterações, você pode querer programar backups mais frequentes. a quantidade de informações que você pode perder em caso de desastre depende da frequência de seus backups, como também da frequência e volume de alterações.

  - É possível importar grupos de resposta a um pool de backup antes que ocorra uma operação de failover ou desastre. Adiantar importações de grupos de resposta reduz o tempo de inatividade, pois o Serviço Grupo de Resposta do Lync Server pode ser restaurado no pool de backup assim que as chamadas de backup são encaminhadas para o pool de backup.
    
    > [!NOTE]  
    > O Aplicativo Grupo de Resposta não pode contatar quaisquer agentes hospedados em um pool inativo até que o failover seja concluído. Durante este tempo, o Aplicativo Grupo de Resposta processa chamadas como se estes agentes estivessem indisponíveis.

## Processo de Recuperação de Desastre de Grupo de Resposta

No caso de um desastre, você pode recuperar grupos de resposta usando qualquer uma das seguintes abordagens de recuperação:

  - Failover para um pool de backup e então failback para o pool original.

  - Failover para um pool de backup, criar um novo pool com um FQDN (nome de domínio totalmente qualificado) diferente e então importar os grupos de resposta ao novo pool.

Durante a fase de failover da recuperação de desastre, os grupos de resposta são hospedados em vários pools: no pool primário (que está indisponível) e no pool de backup. Os grupos de resposta em ambos os pools possuem o mesmo nome e proprietário (o pool primário), mas pais diferentes.

Ao recuperar criando um novo pool com um FQDN diferente, você deve atribuir ao novo pool a propriedade dos grupos de resposta, ao importá-los. A propriedade dos grupos de resposta permanece com o pool original a menos que, ou até que, você explicitamente reatribua a propriedade usando o parâmetro -OverwriteOwner com o cmdlet **Import-CsRgsConfiguration**.

> [!NOTE]  
> Você também precisa usar o parâmetro -OverwriteOwner caso tenha reconstruído o pool durante a recuperação (isso é, o banco de dados do Grupo de Resposta está vazio), independentemente de usar o mesmo FQDN. Você não precisa usar o parâmetro -OverwriteOwner caso não tenha reconstruído o pool, mas é permitido que use este parâmetro a qualquer momento em que você importar grupos de resposta de volta ao pool primário.

Você pode definir apenas um conjunto de definições de configuração do Grupo de Resposta no nível de aplicativo por pool. Estas definições incluem a configuração de música de espera padrão, o arquivo de áudio música de espera padrão, o período de carência de retorno de toque e a configuração de contexto de chamada. Para visualizar essas definições de configuração, execute o cmdlet **Get-CsRgsConfiguration**. Para detalhes sobre o cmdlet **Get-CsRgsConfiguration**, consulte [Get-CsRgsConfiguration](https://docs.microsoft.com/powershell/module/skype/Get-CsRgsConfiguration).

Você pode transferir estas configurações do nível de aplicativo de um pool para outro utilizando o cmdlet **Import-CsRgsConfiguration** com o parâmetro –ReplaceExistingSettings, mas fazer isso substitui as definições no pool de destino.

> [!IMPORTANT]  
> Essa limitação sobre a transferência de definições para outro pool é verdadeira apenas para as definições de nível de aplicativo e o arquivo de música de espera padrão. Ela não se aplica a grupos de agentes, filas, fluxos de trabalho, horários comerciais e conjuntos de feriados.

Caso não queira substituir as definições de nível de aplicativo no pool de backup durante um desastre e o pool primário não possa ser recuperado, as definições de nível de aplicativo do pool primário serão perdidas. Caso precise criar um novo pool para substituir o pool primário durante a recuperação, seja com o mesmo FQDN ou com um diferente, você não pode recuperar as definições de nível de aplicativo originais. Neste caso, você precisa configurar o novo pool com essas definições e incluir o arquivo de áudio de música de espera.

Caso decida usar o cmdlet **Import-CsRgsConfiguration** para transferir definições de nível de aplicativo do pool primário ao pool de backup durante um desastre, você então pode transferir as definições do pool de backup ao novo pool durante a recuperação, do mesmo modo que você as transferia do pool primário ao pool de backup.

A tabela a seguir é uma visão geral das etapas envolvidas na recuperação de grupos de resposta.

Para detalhes sobre executar estas etapas, consulte [Procedimento de recuperação de desastre do grupo de resposta no Lync Server 2013](lync-server-2013-response-group-disaster-recovery-procedures.md).

### Etapas de Recuperação de Desastre de Grupo de Resposta

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Grupos e funções necessários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Antes da interrupção</p></td>
<td><p>Execute, rotineiramente, o cmdlet <strong>Export-CsRgsConfiguration</strong> para criar backups de todas as configurações de Grupo de Resposta em todos os Pools de Front-Ends onde o Aplicativo Grupo de Resposta está implantado.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="even">
<td><p>Durante a interrupção</p></td>
<td><p>Execute o cmdlet <strong>Import-CsRgsConfiguration</strong> para importar a configuração do Serviço Grupo de Resposta do Lync Server de backup do pool primário ao pool de backup.</p>
<div class="alert">
> [!NOTE]  
> Use o parâmetro -ReplaceExistingSettings caso queira substituir definições do Grupo de Resposta de nível de aplicativo no pool de backup pelas definições do pool primário. Se você não transferir as definições de nível de aplicativo do pool primário ao pool de backup, e o pool primário não possa ser recuperado, você perderá as definições do pool primário.
</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="odd">
<td><p>Após importar</p></td>
<td><p>Execute os cmdlets do Grupo de Resposta com o parâmetro -ShowAll (para exibir todos os grupos de resposta), ou com o parâmetro -Owner (para exibir apenas os grupos de resposta importados) para verificar se todas as configurações de grupo de resposta foram importadas ao pool de backup.</p>
<div class="alert">
> [!IMPORTANT]  
> Caso não use nenhum dos parâmetros -ShowAll ou -Owner, os grupos de resposta que você importou ao pool de backup não serão listados nos resultados retornados pelos cmdlets.
</div>
<p>Execute os cmdlets a seguir:</p><ul><li><p><strong>Get-CsRgsWorkflow</strong></p></li><li><p><strong>Get-CsRgsQueue</strong></p></li><li><p><strong>Get-CsRgsAgentGroup</strong></p></li><li><p><strong>Get-CsRgsHoursOfBusiness</strong></p></li><li><p><strong>Get-CsRgsHolidaySet</strong></p></li></ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="even">
<td><p>Após o failover</p></td>
<td><ul><li><p>Realize uma chamada de teste a um grupo de resposta que foi importado ao pool de backup e verifique se a chamada é atendida corretamente.</p></li><li><p>Todos os operadores formais devem entrar novamente em seus grupos formais no pool de backup.</p></li><li><p>Gerencie alterações de configuração:</p>
<p>Grupos de resposta no pool de backup, sejam importados ao pool de backup, ou de propriedade do pool de backup, podem ser modificados normalmente durante a interrupção.</p>
<div class="alert">
> [!IMPORTANT]  
> Você deve usar o Shell de Gerenciamento do Lync Server para gerenciar grupos de resposta que você importou ao pool de backup. Você não pode usar o Painel de Controle do Lync Server para gerenciar os grupos de resposta enquanto eles estão no pool de backup.
</div></li></ul></td>
<td><p>N/D</p></td>
</tr>
<tr class="odd">
<td><p>Após recuperação, antes de failback</p></td>
<td><p>Execute o cmdlet <strong>Export-CsRgsConfiguration</strong> especificando o parâmetro -Source como o pool de backup, e o parâmetro -Owner como o pool primário para exportar os grupos de resposta de propriedade do pool primário, a partir do pool de backup.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
<tr class="even">
<td><p>Após failback</p></td>
<td><ul><li><p>Execute o cmdlet <strong>Import-CsRgsConfiguration</strong> para importar os grupos de resposta de volta ao pool primário.</p>
<div class="alert">
> [!NOTE]  
> Caso o pool primário não possa ser recuperado e você implante um novo pool para substituí-lo, use o parâmetro -ReplaceExistingSettings para transferir as definições de nível de aplicativo do pool de backup ao novo pool. Caso não transfira as configurações do pool de backup, o novo pool usará as configurações padrão.
</div></li><li><p>Execute os cmdlets a seguir com o parâmetro -ShowAll (para exibir todos os grupos de resposta) ou o parâmetro -Owner (para exibir apenas grupos de resposta importados) para verificar se todas as configurações de grupo de resposta foram importados com sucesso de volta ao pool primário:</p><ul><li><p><strong>Get-CsRgsWorkflow</strong></p></li><li><p><strong>Get-CsRgsQueue</strong></p></li><li><p><strong>Get-CsRgsAgentGroup</strong></p></li><li><p><strong>Get-CsRgsHoursOfBusiness</strong></p></li><li><p><strong>Get-CsRgsHolidaySet</strong></p></li></ul></li><li><p>Realize uma chamada de teste a um grupo de resposta que foi importado de volta ao pool primário e verifique se a chamada é atendida corretamente.</p></li><li><p>Execute, opcionalmente, o cmdlet <strong>Export-CsRgsConfiguration</strong> no pool de backup com o parâmetro -RemoveExportedConfiguration para remover os grupos de resposta pertencentes ao pool primário, a partir do pool de backup.</p></li></ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsResponseGroupAdministrator</p></td>
</tr>
</tbody>
</table>

