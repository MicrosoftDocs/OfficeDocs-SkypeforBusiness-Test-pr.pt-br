---
title: Configuração da Integridade no Lync Server 2013
TOCTitle: Configuração da Integridade no Lync Server 2013
ms:assetid: c00a8c8e-c2d2-4557-8c42-211c7cc96550
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205234(v=OCS.15)
ms:contentKeyID: 49307981
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração da Integridade no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Entre vários sites, artigos da Base de Conhecimento da Microsoft e ferramentas do Kit de recursos do Lync Server, os administradores que encontrarem problemas ao executar o Lync Server nunca estão longe para solucionarem o problema.

Obviamente não é possível garantir que você nunca encontrará problemas no Lync Server 2013, pois o Lync Server pode ser afetado por muitos itens, como falhas de rede e hardware, que o produto não pode controlar. Ao implementar o monitoramento de integridade, os administradores podem identificar problemas potenciais antes que se transformem em problemas reais. Por exemplo, os administradores pode usar o monitoramento do Lync Server para identificar tendências. Por exemplo, um aumento contínuo no número de conferências de áudio/vídeo pode indicar uma necessidade de adicionar mais capacidade antes do sistema ficar sobrecarregado.

De maneira semelhante, os administradores pode usar o System Center Operations Manager para ações como alertas em tempo real quando eventos especificados ocorrerem e executar transações sintéticas que testam proativamente o sistema. As transações sintéticas são usadas no Lync Server para se certificar de que os usuários sejam capazes de concluir tarefas comuns com sucesso, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na rede telefônica pública comutada (PSTN). Por exemplo, a execução periódica desses testes pode alertar você sobre problemas potenciais com usuários que se conectam ao Lync Server, além de proporcionar a oportunidade de corrigir o problema antes que a sua equipe de suporte receba muitas chamadas de usuários que não conseguem se conectar. Ao usar o System Center Operations Manager para executar essas transações sintéticas, os administradores podem monitorar rotineiramente a implantação do Lync Server continuamente por 24 horas todos os dias sem necessidade de mais ações além de responder alertas que podem ser alertas that podem ser emitidos.

> [!NOTE]  
> Para o Lync Server 2013, o Pacote de gerenciamento do System Center Operations Manager também pode detectar problemas &quot;externos&quot; que pode afetar adversamente o Lync Server. Por exemplo, os administradores podem ser notificados se o IIS (Serviços de Informações da Internet) ficar offline, se os recursos do sistema em um computador do Lync Server ficarem abaixo da quantidade estimada ou se um computador do Lync Server sofrer uma falha de hardware.

A configuração de integridade no Lync Server 2013 foi criada ao redor do System Center Operations Manager e do uso dos Pacotes de gerenciamento do Lync Server. Esses Pacotes de gerenciamento incluem um número de novos recursos e aprimoramentos, incluindo:

  - **Disponibilidade de cenário de qualquer local.** O Pacote de gerenciamento do Lync Server 2010 introduziu o conceito de monitoramento da disponibilidade de cenário do usuário final com transações sintéticas. No Lync Server 2013, esses agentes têm mais transações sintéticas e podem ser executadas de vários locais em uma empresa, de locais geográficos remotos fora da empresa, contra utilitários de filial e implantações do Lync Server 2010 para adicionar cobertura a implantações de Borda herdadas.

  - **Logs de transação sintéticos.** Quando uma transação sintética falhar, os administradores têm acesso a logs HTML para ajudar a determinar onde está a falha. Isso inclui entender que ação falhou, a latência de cada ação, a linha de comando usado para executar o teste e o erro encontrado.

  - **Maior cobertura de confiabilidade de chamada.** O Pacote de gerenciamento do Lync Server 2010 introduziu a confiabilidade de chamada alertando sobre a detecção de problemas de conectividade sérios que afetam chamadas de áudio dos usuários finais. Os Pacotes de gerenciamento do Lync Server 2013 adicionam cobertura a mensagens instantâneas (IM) de ponto a ponto e outros recursos de conferência básicos para maximizar a cobertura enquanto reduzem o ruído.

  - **Monitoramento de dependência.** Os cenários do Lync Server podem falhar devido a uma variedade de fatores externos como IIS offline, recursos de CPU e memória limitados e problemas de disco. Os novos pacotes de gerenciamento verificam várias dependências importantes para garantir que os administradores estejam cientes do impacto.

  - **Relatórios avançados.** Um conjunto de relatórios que ajuda os administradores a estimar a disponibilidade do cenários, planejar a capacidade e ver quais componentes têm mais problemas.

Os Pacotes de gerenciamento também incluem vários recursos para ajudar a detectar e diagnosticar fornecem visibilidade em tempo real da integridade da sua implantação do Lync Server. Esses recursos estão listados na seguinte tabela.

### Recursos do pacote de gerenciamento

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Recurso</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Transações sintéticas</p></td>
<td><p>Os cmdlets do Windows PowerShell que podem ser executados de vários locais para garantir que os cenários do usuário final como conectar, presença, IM e conferência estarão disponíveis para usuários finais.</p></td>
</tr>
<tr class="even">
<td><p>Alertas de confiabilidade de chamada</p></td>
<td><p>Consultas de banco de dados para CDR (Registros de detalhes de chamada). Esses registros são gravados pelo Servidores Front-End para refletir se os usuários finais conseguiram se conectar a uma chamada ou por que uma chamada foi encerrada. Essas consultas resultam em alertas que indicam quando uma ampla variedade de usuários finais estão passando por problemas de conectividade de chamadas ponto a ponto ou a funcionalidade de conferência básica.</p></td>
</tr>
<tr class="odd">
<td><p>Alertas de qualidade de mídia</p></td>
<td><p>As consultas de banco de dados que visualizam os relatórios de Qualidade da Experiência (QoE) publicados por clientes ao fim de cada chamada. Essas consultas resultam em alertas que identificam cenários nos quais os usuários provavelmente observaram qualidade de mídia ruim durante chamadas e conferências. Os dados aproveitam métricas-chave como latência e perda de pacote, métricas que contribuem diretamente para a qualidade da chamada.</p></td>
</tr>
<tr class="even">
<td><p>Integridade do componente</p></td>
<td><p>Componentes individuais do servidor geram alertas usando logs de eventos e contadores de desempenho. Esses alertas indicam condições de falha que podem ter um impacto crítico em um ou mais cenários do usuário final. Esses alertas também podem indicar várias outras condições de falha, incluindo serviços que não estão funcionando, alta taxa de falhas, alta latência de mensagens ou problemas de conectividade.</p></td>
</tr>
<tr class="odd">
<td><p>Integridade da dependência</p></td>
<td><p>As falha podem ocorrer por vários motivos externos. Os pacotes de gerenciamento agora monitoram e coletam dados para algumas das dependência externas críticas que podem indicar vários problemas, incluindo a disponibilidade IIS, o uso da CPU e da memória por servidores e processos, além de métricas de disco.</p></td>
</tr>
</tbody>
</table>


Os alertas emitidos pelo sistema foram classificados em três categorias gerais:

  - **Alertas de alta prioridade.** Esses alertas indicam condições que resultaram em falhas no serviço para grandes grupos de usuários. Por exemplo, uma falha de componente em uma única máquina não é um alerta de alta prioridade porque o Lync Server 2013 tem recursos de alta disponibilidade integrados. Em vez disso, os alertas de alta prioridade representam problemas sérios o suficiente para “tirar o sono dos administradores”. As falha detectadas por transações sintéticas e serviços offline (por exemplo, conferências de áudio/vídeo) são qualificadas como alertas de alta prioridade.

  - **Alertas de prioridade média.**. Esses alertas indicam condições que afetam um subconjunto de usuários ou indicam a degradação da qualidade da chamada. Isso inclui problemas como falhas de componentes, latência no estabelecimento da chamada ou qualidade de áudio degradada em uma chamada. Os alertas nesta categoria são têm monitoração de estado e indicam o status atual do problema. Por exemplo, considere que o tempo de estabelecimento de chamada excede o limite de alerta. Se o tempo de estabelecimento de chamada retornar ao normal, esses alertas serão resolvidos automaticamente no System Center Operations Manager. A expectativa para esses alertas é de que um administrador os notará no mesmo dia útil.

  - **Outros alertas.** São alertas de componentes que podem afetar um usuário específico ou um subconjunto de usuários. Por exemplo, talvez o serviço de Catálogo de endereços não consiga analisar a entrada do Active Directory de determinado usuário. A expectativa para esses alertas é que que os administradores os solucionarão quando tiverem tempo disponível.

## Nesta seção

  - [Configurando o Lync Server para Trabalhar com System Center Operations Manager](lync-server-2013-configuring-lync-server-to-work-with-system-center-operations-manager.md)

  - [Usando Registro em Log Sofisticado para Transações Sintéticas](lync-server-2013-using-rich-logging-for-synthetic-transactions.md)

  - [Usando Microsoft SQL Server 2008 R2 como seu banco de dados de System Center Operations Manager](lync-server-2013-using-microsoft-sql-server-2008-r2-as-your-system-center-operations-manager-database.md)

