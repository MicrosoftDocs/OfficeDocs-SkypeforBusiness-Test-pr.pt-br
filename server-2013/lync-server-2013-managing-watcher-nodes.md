---
title: Gerenciar nós inspetores
TOCTitle: Gerenciar nós inspetores
ms:assetid: 66deaf49-a71f-4a6e-ada0-ea8b688ee921
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688078(v=OCS.15)
ms:contentKeyID: 49886245
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar nós inspetores

 

_**Tópico modificado em:** 2012-10-20_

Além de modificar as transações sintéticas que são executadas em um nó do inspetor, os administradores também podem usar o cmdlet **Set-CsWatcherNodeConfiguration** para realizar duas outras tarefas importantes: habilitar e desabilitar o nó do inspetor e configurá-lo para usar URLs internas ou externas durante a execução de testes.

Por padrão, os nós do inspetor são projetados para executar periodicamente todas as transações sintéticas habilitadas. Porém, eventualmente, pode ser necessário suspender essas transações. Por exemplo, se o nó do inspetor estiver temporariamente desconectado da rede, não há motivo para executar as transações sintéticas. Sem conectividade de rede, essas transações certamente falharão. Se você desejar desabilitar o nó do inspetor temporariamente, execute um comando semelhante ao seguinte no Shell de Gerenciamento do Lync Server:

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $False

Esse comando desabilitará a execução das transações sintéticas no nó do inspetor atl-watcher- 001.litwareinc.com. Para retomar a execução das transações sintéticas, defina a propriedade Enabled novamente como True ($True):

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -Enabled $True

> [!NOTE]  
> A propriedade Enabled pode ser usada para habilitar e desabilitar os nós do inspetor. Se você desejar excluir permanentemente um nó do inspetor, use o cmdlet <strong>Remove-CsWatcherNodeConfiguration</strong>:<br />Remove-CsWatcherNodeConfiguration –Identity &quot;atl-watcher-001.litwareinc.com&quot;<br />Esse comando remove todas as configurações de nó do inspetor do computador especificado, o que impede que o computador execute transações sintéticas automaticamente. No entanto, o comando não desinstala os arquivos de agente do System Center nem os arquivos de sistema do Lync Server 2013.

Por padrão, os nós do inspetor usam as URLs externas de uma organização durante a realização de seus testes. No entanto, também é possível configurá-los para usar as URLs internas da organização. Isso permite que os administradores verifiquem o acesso a URLs pelos usuários localizados dentro da rede de perímetro. Para configurar um nó do inspetor para usar as URLs internas em vez das externas, defina a propriedade UseInternalWebUrls como True ($True):

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $True

Se você redefinir essa propriedade para o valor padrão False ($False), o inspetor usará as URLs externas:

    Set-CsWatcherNodeConfiguration -Identity "atl-watcher-001.litwareinc.com" -UseInternalWebUrls $False

