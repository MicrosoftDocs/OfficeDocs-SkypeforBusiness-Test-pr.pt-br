---
title: 'Lync Server 2013: Planejamento de capacidade para Servidor de Chat Persistente'
TOCTitle: Planejamento de capacidade para Servidor de Chat Persistente
ms:assetid: 7a850cd5-c789-4795-a8ff-083be21ae784
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615006(v=OCS.15)
ms:contentKeyID: 49307206
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de capacidade para Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Servidor de Chat Persistente pode executar chats com vários usuários em tempo real, que podem persistir para recuperação e pesquisa futuras. Ao contrário das mensagens instantâneas (IM) salvas na caixa de correio do usuário quando o histórico de conversas é configurado, uma sessão de Servidor de Chat Persistente fica aberta por mais tempo e o conteúdo é salvo em um servidor, juntamente com mensagens, arquivos, URLs e outros dados que fazem parte da conversa em andamento.

O planejamento de capacidade é uma parte importante da preparação para implantar Servidor de Chat Persistente. Este tópico fornece detalhes sobre as topologias suportadas Servidor de Chat Persistente e tabelas de planejamento de capacidade que você pode usar para determinar a melhor configuração para a sua implantação. Ele também descreve como gerenciar melhor Servidor de Chat Persistente as implantações que exigem maior capacidade em horários de pico.

Para baixar o Servidor de Chat Persistente, consulte "Servidor de Chat Persistente do Microsoft Lync Server 13" em [http://go.microsoft.com/fwlink/p/?linkId=209539](http://go.microsoft.com/fwlink/p/?linkid=209539).

Para obter detalhes de instalação do Servidor de Chat Persistente, consulte [Instalando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-installing-persistent-chat-server.md) e [Configurando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-configuring-persistent-chat-server.md) na documentação de implantação.

As ferramentas de suporte, como o Lync Server Planning Tool, podem ajudá-lo ainda mais no planejamento de capacidade. Para obter detalhes sobre a Planning Tool, consulte [Iniciando o processo de planejamento para Lync Server 2013](lync-server-2013-beginning-the-planning-process.md) na documentação de planejamento.

## Topologias do Servidor de Chat Persistente com suporte

Você pode implantar o Servidor de Chat Persistente em pools de servidor único ou vários servidores, e com topologia de pool único ou vários pools.

Também oferecemos suporte ao Servidor de Chat Persistente no Servidor Standard Edition para novas implantações do Lync Server 2013. Porém, o desempenho e dimensionamento serão afetados, e como não há uma opção de alta disponibilidade para essa nova implantação, esperamos que você a use principalmente para fins de prova de conceito, avaliação, etc.

> [!NOTE]  
> Para obter detalhes adicionais sobre as duas topologias, consulte <a href="lync-server-2013-planning-for-persistent-chat-server.md">Planejando o Servidor de Chat Persistente no Lync Server 2013</a> nesta documentação definida e <a href="lync-server-2013-deploying-persistent-chat-server.md">Implantando Servidor de Chat Persistente no Lync Server 2013</a> na documentação de implantação.

## Topologia de servidor único

A configuração mínima e a implantação mais simples do Servidor de Chat Persistente é a topologia de Servidor Front-End do Servidor de Chat Persistente único. Essa implantação requer um único servidor que executa o Servidor de Chat Persistente (que opcionalmente executa o serviço de conformidade, se a conformidade estiver habilitada), um servidor que hospeda o banco de dados do SQL Server e, se a conformidade for necessária, o banco de dados do SQL Server para armazenar os dados de conformidade.

> [!IMPORTANT]  
> Você não pode adicionar outros servidores a um Pool de Servidor de Chat Persistente iniciado como uma implantação de servidor único no Construtor de Topologias. Recomendamos usar a topologia de pool de vários servidores, mesmo que você utilize um único servidor, de modo que seja possível adicionar mais servidores posteriormente, se necessário.

A figura a seguir mostra todos os componentes obrigatórios e opcionais de uma topologia de um Servidor Front-End do Servidor de Chat Persistente único com conformidade.

**Servidor de Chat Persistente único**

![Topologia de servidor único com serviço de Conformidade](images/Gg615006.9168fa52-61e0-4d17-a14d-45fd32e81456(OCS.15).jpg "Topologia de servidor único com serviço de Conformidade")

## Topologia de vários servidores

Para fornecer maior capacidade e confiabilidade, você pode implantar uma topologia com vários servidores, conforme descrito em [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md). A topologia de vários servidores pode incluir até quatro computadores ativos executando o Servidor de Chat Persistente (configurações de alta disponibilidade e recuperação de desastres permitem até oito, mas somente quatro podem estar ativos e os quatro outros ficam em espera). Cada servidor pode oferecer suporte a até 20 mil usuários simultâneos gerando um total de 80 mil usuários simultâneos conectados a um Pool de Servidor de Chat Persistente com quatro servidores. Uma topologia de vários servidores é o mesmo que uma topologia de um único servidor, com exceção de que vários servidores hospedam o Servidor de Chat Persistente e a escalabilidade é maior. Vários computadores executando o Servidor de Chat Persistente devem estar no mesmo domínio do Serviços de Domínio Active Directory que o Lync Server e o serviço de conformidade.

A figura a seguir mostra todos os componentes de uma topologia de vários servidores com vários computadores executando o Servidor de Chat Persistente, o serviço de conformidade opcional e um banco de dados de conformidade separado.

**Vários Servidores de Chat Persistente**

![Topologia de múltiplos servidores](images/Gg615006.19aea898-28df-4d9b-903c-f72ef062d919(OCS.15).jpg "Topologia de múltiplos servidores")

Em uma implantação do Servidor de Chat Persistente com quatro servidores, em que 80.000 usuários podem conectar e usar o Chat Persistente simultaneamente, a carga é distribuída igualmente em 20.000 usuários por servidor. Se um servidor ficar indisponível, os usuários conectados ao servidor perderão acesso ao Servidor de Chat Persistente. Os usuários desconectados serão transferidos automaticamente aos servidores restantes até a restauração do servidor indisponível. Dependendo da quantidade de tráfego do Chat Persistente na rede, essa transferência poderá demorar alguns minutos ou mais. Como cada um dos servidores restantes pode estar hospedando até 30.000 usuários, recomendamos a restauração rápida do servidor indisponível para evitar problemas de desempenho. Caso contrário, você poderá disponibilizar outro Servidor de Chat Persistente usando o Construtor de Topologias ou o cmdlet do Windows PowerShell, **set-CsPersistentChatActiveServer**.

## Planejamento de capacidade do Servidor de Chat Persistente

As tabelas a seguir podem ajudá-lo no planejamento de capacidade do Servidor de Chat Persistente. Elas mostram como a alteração de diversas configurações do Servidor de Chat Persistente influenciam os recursos de capacidade.

## Planejando a capacidade máxima do Servidor de Chat Persistente

Use a seguinte tabela de exemplo para determinar o número de usuários que você será capaz de suportar.

### Exemplo de capacidade máxima do Pool de Servidor de Chat Persistente

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Instâncias de serviço de Chat Persistente ativas</p></td>
<td><p><em>4</em></p></td>
</tr>
<tr class="even">
<td><p>Instâncias de serviço do Chat Persistente</p></td>
<td><p><em>8 (4 must be inactive; only a maximum of 4 can be active)</em></p></td>
</tr>
<tr class="odd">
<td><p>Usuários ativos conectados</p></td>
<td><p><em>80,000</em></p></td>
</tr>
<tr class="even">
<td><p>Total de usuários provisionados</p></td>
<td><p>150.000</p></td>
</tr>
<tr class="odd">
<td><p>Número de pontos de extremidade</p></td>
<td><p>120.000</p></td>
</tr>
</tbody>
</table>


No exemplo anterior, o plano é oferecer suporte ao máximo de usuários permitidos pelo Servidor de Chat Persistente: quatro servidores/instâncias do serviço de Chat Persistente (pode haver mais quatro servidores passivos executando o Servidor de Chat Persistente para alta disponibilidade e recuperação de desastres) e 20.000 usuários por servidor, para um total de 80.000 usuários ativos.

## Planejamento de capacidade para gerenciamento de acesso da sala de Chat Persistente

A tabela de exemplo a seguir pode ajudá-lo a planejar o gerenciamento de acesso da sala de Chat Persistente em um Pool de Servidor de Chat Persistente.

### Gerenciando o exemplo de acesso da sala de chat

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Salas de chat pequenas</th>
<th>Salas de chat médias</th>
<th>Salas de chat grandes</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tamanho das salas de chat (número de usuários conectados)</p></td>
<td><p>30 por sala</p></td>
<td><p>150 por sala</p></td>
<td><p>16.000 por sala</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Salas de chat</p></td>
<td><p>32.000</p></td>
<td><p>1.067</p></td>
<td><p>10</p></td>
<td><p>33.077</p></td>
</tr>
<tr class="odd">
<td><p>% de salas que são auditórios</p></td>
<td><p>1%</p></td>
<td><p>1%</p></td>
<td><p>50%</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>% de salas abertas</p></td>
<td><p>3%</p></td>
<td><p>3%</p></td>
<td><p>50%</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Salas abertas (para associação explícita)</p></td>
<td><p>960</p></td>
<td><p>32</p></td>
<td><p>5</p></td>
<td><p>997</p></td>
</tr>
<tr class="even">
<td><p>Salas não abertas (salas normais com associação explícita)</p></td>
<td><p>31.040</p></td>
<td><p>1,035</p></td>
<td><p>5</p></td>
<td><p>32.080</p></td>
</tr>
<tr class="odd">
<td><p>Salas de auditório (ingresso de apresentadores adicionais)</p></td>
<td><p>0</p></td>
<td><p>32</p></td>
<td><p>5</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Salas gerenciadas pro associação direta</p></td>
<td><p>50%</p></td>
<td><p>10%</p></td>
<td><p>0%</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Salas gerenciadas por grupos de usuários</p></td>
<td><p>50%</p></td>
<td><p>90%</p></td>
<td><p>100%</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Grupos de usuários na lista de associação de cada sala de chat para salas abertas (sem especificação explícita)</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p>0</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Usuários na lista de associação de cada sala de chat para salas não abertas</p></td>
<td><p>30</p></td>
<td><p>150</p></td>
<td><p>16.000</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Grupos de usuários na lista de associação de cada sala de chat para salas não abertas</p></td>
<td><p>3</p></td>
<td><p>5</p></td>
<td><p>10</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Usuários e grupos de usuários na lista de gerentes de cada sala de chat (para salas abertas e não abertas)</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Usuários e grupos de usuários na lista de apresentadores de cada sala de chat (para salas abertas e não abertas)</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Entidades de associação com base em usuário em todas as salas não abertas</p></td>
<td><p>465.600</p></td>
<td><p>15.520</p></td>
<td><p>-</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Entidades de associação com base em grupo usuários em todas as salas não abertas</p></td>
<td><p>46.560</p></td>
<td><p>4656</p></td>
<td><p>50</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Entidades de usuários e grupos de usuários em todas as salas de chat de auditório</p></td>
<td><p>0</p></td>
<td><p>192</p></td>
<td><p>50</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Entidades de gerente com base em usuários e grupos de usuários em todas as listas de gerentes das salas de chat</p></td>
<td><p>192.000</p></td>
<td><p>6.400</p></td>
<td><p>60</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Usuários ativos por sala de chat</p></td>
<td><p><em>30</em></p></td>
<td><p><em>150</em></p></td>
<td><p><em>16,000</em></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Salas de chat por usuário</p></td>
<td><p><em>12</em></p></td>
<td><p><em>2</em></p></td>
<td><p><em>2</em></p></td>
<td><p><em>16</em></p></td>
</tr>
<tr class="odd">
<td><p>Grupos de usuário na lista de membros de cada sala de chat</p></td>
<td><p><em>10</em></p></td>
<td><p><em>10</em></p></td>
<td><p><em>15</em></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Salas gerenciadas por grupos de usuários</p></td>
<td><p><em>50%</em></p></td>
<td><p><em>50%</em></p></td>
<td><p><em>50%</em></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Entidades de participação baseadas em grupos de usuário em todas as salas de chat</p></td>
<td><p>155.200</p></td>
<td><p>5173</p></td>
<td><p>68</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Entidades de participação baseadas em usuários em todas as salas de chat</p></td>
<td><p>465.600</p></td>
<td><p>77.600</p></td>
<td><p>72.000</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Usuários e grupos de usuários no gerenciador de cada sala de chat, apresentador e listas de escopo</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p>6</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Usuários e grupos de usuários em todas as listas de escopo, gerentes e apresentadores das salas de chat</p></td>
<td><p>192.000</p></td>
<td><p>6400</p></td>
<td><p>60</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Entradas de controle de acesso</p></td>
<td><p>704.160</p></td>
<td><p>26.768</p></td>
<td><p>160</p></td>
<td><p>731.088</p></td>
</tr>
<tr class="even">
<td><p>Entradas de controle de máximo acesso</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>2.000.000</p></td>
</tr>
</tbody>
</table>


No exemplo anterior, quando você implanta os Servidores de Chat Persistente de acordo com a diretrizes recomendadas, podem lidar com até 80.000 usuários ativos em um pool de quatro servidores com a conformidade ativada.

Este exemplo mostra como salas de chat são categorizadas como pequenas (30 usuários ativos a qualquer momento), médias (150 usuários ativos) e grandes (16.000 usuários ativos). O número de salas de chat de um determinado tamanho é calculado com base no número total de:

  - Usuários ativos no sistema

  - Usuários ativos em salas de chat de determinado tamanho

  - Salas de chat de um tamanho determinado onde ingressa um único usuário

Para cada sala de chat, a tabela de planejamento de capacidade anterior especifica o número de entradas de controle de acesso que estão associados com a sala de chat, incluindo entradas que são atribuídos diretamente para a sala de chat. Você pode controlar o acesso a salas de chat individuais usando listas de controle de acesso (ACLs). Você também pode controlar o acesso no nível de categoria. Em uma ACL, uma entrada de controle de acesso individual pode ser um grupo de usuários (por exemplo, um grupo de segurança, uma lista de distribuição) ou um único usuário. Você pode definir as entradas de controle de acesso aos membros, aos apresentadores e aos gerentes de sala de chat.

> [!IMPORTANT]  
> No planejamento da estratégia de gerenciamento de salas de chat, tenha em mente que o número total de entradas de controle de acesso permitido é 2 milhões. Se as entradas de controle de acesso calculado excederem 2 milhões, o desempenho do servidor pode degradar significativamente. Para evitar esse problema, sempre que possível, verifique se as entradas de controle de acesso são grupos de usuários em vez de usuários individuais.

## Planejamento de capacidade para gerenciar o acesso de sala de chat por convite

Você pode usar a tabela a seguir de planejamento de capacidade para compreender o número de convites que o Servidor de Chat Persistentecria e armazena no banco de dados do Chat Persistente quando configurado para enviar convites. Você gerencia convites na categoria usando a página **Configurações de Categoria da Sala de Chat** no Painel de Controle do Lync Server ou usando o cmdlet do Windows PowerShell, **set-csPersistentChatCategory**. Você pode gerenciar convites em uma sala de chat ( em linha com o que a categoria permite) usando a página **Gerenciamento de Salas** aberta no cliente do Lync ou usando um cmdlet do Windows PowerShell, **set-csPersistentChatRoom**.

Os dados de exemplo na tabela a seguir pressupõem que, na página de **configurações de sala de chat** para 50% de todas as salas de chat, a opção de **convites** está definida como **Sim** .

> [!IMPORTANT]  
> Se o valor calculado para o número de convites gerado pelo servidor exceder 1 milhão, o desempenho do servidor pode degradar significativamente. Para evitar esse problema, verifique se você minimizou o número de salas de chat que estão configurados para enviar convites ou restrinja o número de usuários que podem ingressar em salas de chat que foram configuradas para enviar convites.

### Acesso à sala de chat por amostra de convite

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Salas de chat pequenas</th>
<th>Salas de chat médias</th>
<th>Salas de chat grandes</th>
<th>Total</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuários que podem acessar a sala de chat</p></td>
<td><p>30 por sala</p></td>
<td><p>150 por sala</p></td>
<td><p>16.000 por sala</p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Porcentagem de salas com convites</p></td>
<td><p>50%</p></td>
<td><p>50%</p></td>
<td><p>50%</p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Salas de chat configuradas para enviar convites</p></td>
<td><p><em>16,000</em></p></td>
<td><p><em>533</em></p></td>
<td><p><em>5</em></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Usuários que podem acessar a sala de chat</p></td>
<td><p><em>60</em></p></td>
<td><p><em>225</em></p></td>
<td><p><em>16,000</em></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Convites gerados pelo Servidor de Chat Persistente</p></td>
<td><p>960.000</p></td>
<td><p>120.000</p></td>
<td><p>80.000</p></td>
<td><p>1.160.000</p></td>
</tr>
<tr class="even">
<td><p>Número de convites máximo permitido</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p>2.000.000</p></td>
</tr>
<tr class="odd">
<td><p>Modelo 1 - Iniciar com o número esperado de mensagens por sala/dia</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Taxa de chat por sala (por dia)</p></td>
<td><p>50</p></td>
<td><p>500</p></td>
<td><p>100</p></td>
<td><p>650</p></td>
</tr>
<tr class="odd">
<td><p>Taxa de chat (por segundo) em todas as salas</p></td>
<td><p>55,56</p></td>
<td><p>18,52</p></td>
<td><p>0,03</p></td>
<td><p>74</p></td>
</tr>
<tr class="even">
<td><p>Modelo 2 - Iniciar com um número de mensagens publicadas por usuário/dia</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Taxa de chat por usuário/dia</p></td>
<td><p>15</p></td>
<td><p>5</p></td>
<td><p>0,1</p></td>
<td><p>20</p></td>
</tr>
<tr class="even">
<td><p>Taxa de chat por sala (por dia)</p></td>
<td><p>38</p></td>
<td><p>375</p></td>
<td><p>800</p></td>
<td><p>1.213</p></td>
</tr>
<tr class="odd">
<td><p>Taxa de chat (por segundo) em todas as salas</p></td>
<td><p>41,67</p></td>
<td><p>13,89</p></td>
<td><p>0,28</p></td>
<td><p>56</p></td>
</tr>
</tbody>
</table>


## Modelo do usuário de desempenho do Servidor de Chat Persistente

A tabela a seguir descreve o modelo de usuário para Servidor de Chat Persistente. Ele fornece a base para a requisitos de planejamento de capacidade e representa uma organização típica com 80.000 usuários simultâneos em quatro servidores.

### Modelo do usuário de desempenho do Servidor de Chat Persistente

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Número de usuários ativos conectados</p></td>
<td><p>80.000</p></td>
</tr>
<tr class="even">
<td><p>Número de instâncias do serviço de Servidor de Chat Persistente</p></td>
<td><p>4</p></td>
</tr>
<tr class="odd">
<td><p>Tamanho de salas de chat pequenas</p></td>
<td><p>30 usuários</p></td>
</tr>
<tr class="even">
<td><p>Tamanho médio de salas de chat</p></td>
<td><p>150 usuários</p></td>
</tr>
<tr class="odd">
<td><p>Tamanho grande de salas de chat</p></td>
<td><p>16.000 usuários</p></td>
</tr>
<tr class="even">
<td><p>Número total de salas de chat</p></td>
<td><p>33.077</p></td>
</tr>
<tr class="odd">
<td><p>Número de salas de chat pequenas</p></td>
<td><p>32.000</p></td>
</tr>
<tr class="even">
<td><p>Número de salas de chat médias</p></td>
<td><p>1.067</p></td>
</tr>
<tr class="odd">
<td><p>Número de salas de chat grandes</p></td>
<td><p>10</p></td>
</tr>
<tr class="even">
<td><p>Número total de salas de chat por usuário</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Número de salas de chat pequenas por usuário</p></td>
<td><p>12</p></td>
</tr>
<tr class="even">
<td><p>Número de salas de chat médias por usuário</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>Número de salas de chat grandes por usuário</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>Número de salas com ingresso por usuário</p></td>
<td><p>24</p></td>
</tr>
<tr class="odd">
<td><p>Taxa de pico de associação</p></td>
<td><p>10/segundo</p></td>
</tr>
<tr class="even">
<td><p>Taxa de chat total</p></td>
<td><p>24/segundo</p></td>
</tr>
<tr class="odd">
<td><p>Taxa de chat para pequenas salas de chat</p></td>
<td><p>22,22/segundo</p></td>
</tr>
<tr class="even">
<td><p>Taxa de chat para salas de chat médias</p></td>
<td><p>1,67/segundo</p></td>
</tr>
<tr class="odd">
<td><p>Taxa de chat para salas de chat grandes</p></td>
<td><p>Aprox. 0,15/segundo</p></td>
</tr>
<tr class="even">
<td><p>Porcentagem de salas de chat configuradas para convites</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Porcentagem de participação direta em</p></td>
<td><p>50%</p></td>
</tr>
<tr class="even">
<td><p>Porcentagem de membros em grupo</p></td>
<td><p>50%</p></td>
</tr>
<tr class="odd">
<td><p>Número médio de afiliações ancestrais no Serviços de Domínio Active Directory</p></td>
<td><p>100 - 200</p></td>
</tr>
<tr class="even">
<td><p>Número de contatos inscritos por usuário</p></td>
<td><p>80</p></td>
</tr>
<tr class="odd">
<td><p>Número médio de pontos de extremidade por usuário</p></td>
<td><p>1,5</p></td>
</tr>
<tr class="even">
<td><p>Número médio de salas de chat visíveis por ponto de extremidade</p></td>
<td><p>1,5</p></td>
</tr>
<tr class="odd">
<td><p>Número médio de salas de chat visíveis por usuário</p></td>
<td><p>2,25 (50% para uma sala e 50% para duas salas); até seis salas abertas, uma por monitor</p></td>
</tr>
<tr class="even">
<td><p>Número de participantes sondados por intervalo</p></td>
<td><p>25 por sala de chat visível</p></td>
</tr>
<tr class="odd">
<td><p>Duração do intervalo de sondagem</p></td>
<td><p>5 minutos</p></td>
</tr>
<tr class="even">
<td><p>Número de participantes sondados por segundo</p></td>
<td><p>15.000</p></td>
</tr>
<tr class="odd">
<td><p>Número de alterações de presença por hora por usuário</p></td>
<td><p>6</p></td>
</tr>
<tr class="even">
<td><p>Número de alterações de presença por segundo</p></td>
<td><p>133,33</p></td>
</tr>
</tbody>
</table>

