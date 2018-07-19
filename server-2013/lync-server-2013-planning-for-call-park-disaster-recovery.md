---
title: 'Lync Server 2013: Planejamento para recuperação de desastre de Estacionamento de Chamada'
TOCTitle: Planejamento para recuperação de desastre de Estacionamento de Chamada
ms:assetid: f7cf3958-177b-4340-a864-35a6f44d6d88
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205395(v=OCS.15)
ms:contentKeyID: 49308647
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para recuperação de desastre de Estacionamento de Chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-30_

Esta seção descreve algumas formas de preparar o Aplicativo de Estacionamento de Chamada para recuperação de desastres e algumas considerações para o processo de recuperação de desastres.

## Preparando a recuperação de desastres do Estacionamento de Chamada

Considere o seguinte ao preparar e realizar os procedimentos de recuperação de desastres:

  - Planeje a recuperação de desastres ao realizar o planejamento de capacidade. Para a capacidade de recuperação de dasestres, cada pool em pools emparelhados deve ser capaz de lidar com as cargas de trabalho dos serviços do Estacionamento de Chamada. Para obter mais informações sobre o planejamento de capacidade do Estacionamento de Chamada, consulte [Planejamento de capacidade para Estacionamento de Chamada no Lync Server 2013](lync-server-2013-capacity-planning-for-call-park.md).

  - Durante a recuperação de desastres, os usuários que foram redirecionados para o pool de backup como parte do processo de failover usam o serviço Estacionamento de Chamada executado no pool de backup. Portanto, o suporte ao Estacionamento de Chamada durante a recuperação de desastres requer que o Aplicativo de Estacionamento de Chamada esteja implantado e habilitado no pool primário e no pool de backup.

  - Cada pool deve ter um intervalo válido de números de órbita para ser utilizado pelos usuários hospedados no pool a fim de estacionar chamadas.

  - Sempre mantenha uma cópia de backup separada de qualquer música em espera personalizada que fora carregada no Estacionamento de Chamada. Esses arquivos não passam por backup como parte do processo de recuperação de desastres do Lync Server 2013 e serão perdidos se os arquivos carregados no pool forem danificados, corrompidos ou apagados.

## Considerações de recuperação de desastres do Estacionamento de Chamada

É possível definir apenas um conjunto de configurações do Aplicativo de Estacionamento de Chamada e um arquivo de áudio de música em espera personalizada por pool. Essas configurações incluem o tempo limite máximo, a música em espera, o número máximo de tentativas de recebimento de chamadas e o tempo limite de URI. Para exibir essas configurações, execute o cmdlet **Get-CsCpsConfiguration**. Para obter detalhes sobre o cmdlet **Get-CsCpsConfiguration**, consulte [Get-CsCpsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCpsConfiguration).

Durante a recuperação de desastres, o Estacionamento de Chamada usa o Aplicativo de Estacionamento de Chamada no pool de backup, portanto, as configuração no pool principal não passam por backup. Se o pool principal não puder ser recuperado e você implantar um novo pool para substituí-lo, as configurações do pool principal serão perdidas e você precisará configurar novamente as configurações do Estacionamento de Chamada e qualquer arquivo de áudio de música em espera personalizada no novo pool.

Se você implantar um novo pool com um nome de domínio totalmente qualificado (FQDN) diferente para substituir o pool principal, você precisará reatribuir todos os intervalos de órbita do Estacionamento de Chamada associados ao pool principal ao FQDN do novo pool. Para rearibuir os intervalos de órbita ao novo pool, você pode usar o Painel de Controle do Lync Server ou o cmdlet **Set-CsCallParkOrbit**. Para obter detalhes sobre o cmdlet **Set-CsCallParkOrbit**, consulte [Set-CsCallParkOrbit](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCallParkOrbit).

