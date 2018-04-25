---
title: 'Lync Server 2013: Tarefas semanais'
TOCTitle: Tarefas semanais
ms:assetid: d564839b-b49d-4c5d-b67e-dc5abb0f6980
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn722432(v=OCS.15)
ms:contentKeyID: 62281971
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tarefas semanais no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

As tarefas semanais são geralmente relacionadas à coleta e à análise de logs e relatórios.

## Arquivar logs de eventos

Se os logs de eventos não estiverem configurados para substituir eventos, conforme necessário, eles deverão ser arquivados e excluídos regularmente .

Sua organização deverá definir políticas e procedimentos para o arquivamento de logs.

## Criar relatórios

Crie relatórios de status para auxiliar no planejamento da capacidade, nas revisões de SLA e na análise de desempenho. Use dados diários do log de eventos e o Monitor do Sistema para criar relatórios sobre uso do disco, da memória e da CPU. Use System Center Operations Manager para gerar relatórios de tempo de atividade e disponibilidade.

Sua organização deverá definir políticas e procedimentos para os relatórios de status.

## Relatórios de incidentes

Execute uma auditoria semanal dos relatórios de incidentes da sua organização que estejam relacionados ao Lync Server. Essa auditoria deve incluir o seguinte:

  - Os principais incidentes gerados, resolvidos e pendentes.

  - Soluções para os incidentes não resolvidos.

  - Relatórios de atualização para incluir novos tíquetes de problemas.

  - Atualização de um repositório de documentos para guias de solução de problemas e post-mortems sobre interrupções.

Como o sistema de acompanhamento de incidentes de sua organização é uma escolha independente do Lync Server, instruções ou ponteiros específicos não estão disponíveis. Consulte a documentação do sistema escolhido pela sua organização.

## Verificar logs e desempenho do IIS

Realize uma revisão semanal dos logs e do desempenho do IIS (Serviços de Informações da Internet). Para obter mais informações sobre como monitorar os logs e o desempenho do IIS, consulte [Visão Geral do Log de Eventos do Windows Server 2003 Internet Information Services (IIS)](http://go.microsoft.com/fwlink/?linkid=36077). A revisão deve incluir o seguinte:

  - Contadores do Cache do Serviço da Web para monitorar o cache do serviço WWW.

  - Contadores de Active Server Pages (ASPs) para monitorar os aplicativos executados como ASPs.

Para obter mais informações sobre como monitorar os logs e o desempenho do IIS, consulte [Visão Geral do Log de Eventos do Windows Server 2003 Internet Information Services (IIS)](http://go.microsoft.com/fwlink/?linkid=36077).

## Gerar relatórios de banco de dados

**Para gerar relatórios sobre o Banco de Dados SQL**

1.  Abra o Lync Server 2013.

2.  Na árvore de console, expanda o nó de floresta, expanda **Pools Enterprise** e clique no pool para o qual deseja gerar um relatório de banco de dados.

3.  No painel de detalhes, clique na guia **Banco de Dados**.

4.  Na guia **Banco de Dados**, faça o seguinte:
    
    1.  Para exibir o nome do banco de dados, expanda **Configurações Gerais** e exiba o nome do banco de dados.
    
    2.  Para recuperar as estatísticas atuais de resumo do usuário para o pool, expanda **Relatórios de Resumo do Usuário**, clique em **Ir** e exiba os resultados.
    
    3.  Para recuperar os dados atuais por usuário para um único usuário do pool, expanda **Relatórios por Usuário**, digite o URI SIP do usuário, clique em **Ir** e exiba os resultados.

Para recuperar as estatísticas atuais de resumo de conferência para o pool, expanda **Relatórios de Resumo de Conferência**, clique em **Ir** e exiba os resultados.

## Verificar a segurança e as atualizações do Lync Server

Identifique qualquer novo service pack, hotfix ou atualização. Se for apropriado, teste isso em um laboratório de teste e use os procedimentos de controle de alterações para providenciar a implantação nos servidores de produção. Além disso, as atualizações do componente Lync Server agora estão disponíveis como parte da atualização do Windowsl. Todas as atualizações do componente Lync Server devem ser atualizadas simultaneamente em todos os servidores que executam o Lync Server para o qual as atualizações são aplicáveis.

## Executar o Analisador de Práticas Recomendadas do Lync Server 2013

A Ferramenta Analisador de Práticas Recomendadas do Lync Server 2013 é uma ferramenta de diagnóstico que coleta informações de configuração e determina se a configuração está definida de acordo com as práticas recomendadas da Microsoft. A documentação dessa ferramenta está disponível em [Analisador de Práticas Recomendadas do Lync Server 2013](lync-server-2013-lync-server-best-practices-analyzer.md) e [Executar o Best Practices Analyzer](https://technet.microsoft.com/pt-br/library/gg398652\(v=ocs.15\)).

A ferramenta compara os dados de configuração de sua implantação com um conjunto de regras predefinidas para o Lync Server e relata possíveis problemas. Para cada problema relatado, a ferramenta fornece a configuração atual no ambiente do Lync Server e a configuração recomendada.

Com o acesso de rede correto, a ferramenta pode examinar seu AD DS e os servidores que executam o Lync Server 2013 para fazer o seguinte:

  - Realizar verificações de integridade de maneira proativa, examinando se a configuração está definida de acordo com as práticas recomendadas

  - Gerar uma lista de problemas, como parâmetros de configuração de qualidade inferior ou opções sem suporte ou não recomendadas

  - Julgar a integridade geral de um sistema

  - Ajudar a solucionar problemas específicos

  - Solicitar que você baixe atualizações se elas estiverem disponíveis

  - Fornecer documentação online e local sobre os problemas relatados e incluir dicas de solução de problemas

  - Gerar informações de configuração que possam ser capturadas para revisão posterior

Assegurar que o RTCBPA.msi esteja instalado em todos os servidores Lync Server 2013 e gerar um Relatório de Verificação de Integridade semanal. Observe os resultados e corrija, se necessário.

## Examinar os indicadores de desempenho de SLA

Verifique os principais dados de desempenho da semana anterior. Examine o desempenho em relação aos requisitos do SLA. Identifique tendências e itens que não atenderam aos objetivos.

## Examinar os relatórios do Pacote de Gerenciamento do System Center Operations Manager e de qualidade de experiência

Obtenha e examine os relatórios do Pacote de Gerenciamento do Lync Server 2013 e de Qualidade de Experiência.

## Gerando e exibindo relatórios de banco de dados para pools enterprise

**Para gerar relatórios de pools**

1.  Abra o Lync Server 2013.

2.  Na árvore do console, expanda o nó de floresta, expanda **Pools Enterprise** e clique no pool para o qual você deseja gerar um relatório de banco de dados.

3.  No painel de detalhes, clique na guia **Banco de Dados**.

4.  Na guia **Banco de Dados**, faça o seguinte:
    
    1.  Para exibir o nome do banco de dados, expanda **Configurações Gerais** e exiba o nome do banco de dados.
    
    2.  Para recuperar as estatísticas atuais de resumo do usuário para o pool, expanda **Relatórios de Resumo do Usuário**, clique em **Ir** e exiba os resultados.
    
    3.  Para recuperar os dados atuais por usuário para um único usuário do pool, expanda **Relatórios por Usuário**, digite o URI SIP do usuário, clique em **Ir** e exiba os resultados.

Para recuperar as estatísticas atuais de resumo de conferência para o pool, expanda **Relatórios de Resumo de Conferência**, clique em **Ir** e exiba os resultados.

Para cada Pool Enterprise, os administradores poderão usar a guia **Banco de Dados** para exibir o nome do banco de dados e recuperar e exibir relatórios do banco de dados.

### Relatórios de Bancos de Dados e Descrições

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Seção</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Relatórios de Resumo do Usuário</p></td>
<td><p>Dbanalyze /v /report:diag [/sqlserver:value]</p>
<p>Essa seção exibe informações de agregação sobre os usuários de um pool, como o número de usuários habilitados, o número médio de contatos por usuário e o número de usuários para recursos específicos.</p>
<p>Durante o uso desses relatórios, estas informações poderão ser úteis:</p>
<ul>
<li><p>Um usuário habilitado é um usuário que está habilitado para o Lync Server 2013 usando o Snap-in Usuários e Computadores do Active Directory.</p></li>
<li><p>Um usuário ativo é um usuário que fez logon ou se registrou.</p></li>
<li><p>Os relatórios de resumo também oferecem um conjunto de informações estatísticas sobre os contatos. Essas estatísticas somente são válidas para a população de usuários que fizeram logon pelo menos uma vez e que têm, no mínimo, um contato. Consequentemente, você normalmente não verá um número mínimo de contatos igual a 0. Devido a esse comportamento, se um usuário não tiver contatos (mas estiver ativo, ou seja, tiver se registrado), você poderá ver: &lt;vazio&gt; para alguns campos estatísticos.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Relatórios por Usuário</p></td>
<td><p>Dbanalyze /v /report:disk [/sqlserver:value]</p>
<p>Diferentemente dos relatórios de resumo, que são calculados em relação a uma população de usuários, esses relatórios são sobre um usuário específico.</p></td>
</tr>
<tr class="odd">
<td><p>Relatórios de Resumo de Conferência</p></td>
<td><p>Dbanalyze /v /report:conf [/sqlserver:value]</p>
<p>Essa seção exibe informações de agregação sobre as estatísticas de resumo de conferência para o pool, como o número de conferências ativas e o número total de participantes.</p></td>
</tr>
<tr class="even">
<td><p>Relatórios de Resumo do Usuário</p></td>
<td><p>Dbanalyze /v /report:diag [/sqlserver:value]</p>
<p>Essa seção exibe informações de agregação sobre os usuários de um pool, como o número de usuários habilitados, o número médio de contatos por usuário e o número de usuários para recursos específicos.</p>
<p>Durante o uso desses relatórios, estas informações poderão ser úteis:</p>
<ul>
<li><p>Um usuário habilitado é um usuário que está habilitado para o Lync Server 2013 usando o Snap-in Usuários e Computadores do Active Directory.</p></li>
<li><p>Um usuário ativo é um usuário que fez logon ou se registrou.</p></li>
<li><p>Os relatórios de resumo também oferecem um conjunto de informações estatísticas sobre os contatos. Essas estatísticas somente são válidas para a população de usuários que fizeram logon pelo menos uma vez e que têm, no mínimo, um contato. Consequentemente, você normalmente não verá um número mínimo de contatos igual a 0. Devido a esse comportamento, se um usuário não tiver contatos (mas estiver ativo, ou seja, tiver se registrado), você poderá ver: &lt;vazio&gt; para alguns campos estatísticos.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Relatórios por Usuário</p></td>
<td><p>Dbanalyze /v /report:disk [/sqlserver:value]</p>
<p>Diferentemente dos relatórios de resumo, que são calculados em relação a uma população de usuários, esses relatórios são sobre um usuário específico.</p></td>
</tr>
<tr class="even">
<td><p>Relatórios de Resumo de Conferência</p></td>
<td><p>Dbanalyze /v /report:conf [/sqlserver:value]</p>
<p>Essa seção exibe informações de agregação sobre as estatísticas de resumo de conferência para o pool, como o número de conferências ativas e o número total de participantes.</p></td>
</tr>
</tbody>
</table>


## Executando o Analisador de Utilização de Largura de Banda

O Analisador de Utilização de Largura de Banda é uma ferramenta que cria relatórios sobre várias exibições de consumo de largura de banda pelos pontos de extremidade de UC nos links WAN da rede corporativa. Esses relatórios podem ser usados para compreender o padrão atual de consumo da largura de banda e auxiliar no planejamento da capacidade da largura de banda. Ele também itera na capacidade da largura de banda atribuída a diversos links.

Essa ferramenta faz o seguinte:

  - Gera relatórios específicos para uso de áudio na rede

  - Ajuda com um planejamento de capacidade mais eficaz e iteração na capacidade da largura de banda atribuída a diversos links

O Analisador de Utilização de Largura de Banda pode gerar plotagens gráficas dos relatórios de uso e capacidade da largura de banda. São elas:

  - Todos os links WAN da rede corporativa

  - Filtradas por links WAN selecionados que foram escolhidos

  - Filtradas por links WAN que excederam a capacidade do link

  - Filtradas por links WAN que subutilizaram a largura de banda provisionada

  - Filtrar por links WAN que estavam atingindo níveis críticos (uso da largura de banda maior que 90% da capacidade de largura de banda do link WAN)

  - Filtradas por tipo de link WAN — links de sites da rede, links interregionais e links dentro de um site

  - Filtradas pela região da rede

A documentação dessa ferramenta está disponível em [Documentação das Ferramentas do Resource Kit do Lync Server 2013](https://technet.microsoft.com/pt-br/library/jj945604\(v=ocs.15\)).

## Consulte Também

#### Outros Recursos

[Lista de verificação semanal de tarefas](lync-server-2013-operations-checklists.md)

