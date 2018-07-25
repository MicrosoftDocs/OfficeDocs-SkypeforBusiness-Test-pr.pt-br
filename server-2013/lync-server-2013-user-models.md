---
title: 'Lync Server 2013: Modelos de usuário'
TOCTitle: Modelos de usuário no Lync Server 2013
ms:assetid: c551371c-d740-4372-bada-f0d713ec0d33
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398811(v=OCS.15)
ms:contentKeyID: 49886401
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modelos de usuário no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os modelos de usuário descritos aqui oferecem a base para as medições de planejamento de capacidade e recomendações descritas no [Planejamento de capacidade para Lync Server 2013 usando modelos de usuário](lync-server-2013-capacity-planning-using-the-user-models.md).

## Modelos de usuário do Lync Server 2013

A tabela a seguir descreve o modelo do usuário para registro, contato, mensagem instantânea (IM) e presença para Lync Server 2013.

### Modelo de usuário de ambiente e registro

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Tamanho da implantação e distribuição</p></td>
<td><p>Modelamos uma grande implantação com três locais centrais, com um pool de Front-end por local.</p></td>
</tr>
<tr class="even">
<td><p>Porcentagem de usuários do Active Directory</p></td>
<td><p>Supomos que 70% de todos os usuários do Active Directory na organização estão habilitados para Lync Server. 80% desses usuários habilitados estão registrados no Lync Server diariamente (80% de simultaneidade). Os usuários simultâneos são a base para os números no restante desta seção.</p></td>
</tr>
<tr class="odd">
<td><p>Mudanças do Active Directory</p></td>
<td><p>Assumimos que 0,5% do total de usuários foram criados e habilitados para o Lync no Active Directory cada semana e que 0,5% do total de usuários são desabilitados do Active Directory e do Lync por semana. 5% dos usuários possuem pelo menos um atributo do Active Directory alterado cada semana.</p></td>
</tr>
<tr class="even">
<td><p>Grupos de distribuição do Active Directory</p></td>
<td><p>Supomos que o número de grupos de distribuição do Active Directory na organização seja igual a três vezes o número de todos os usuários no Active Directory. Os grupos de distribuição têm os seguintes tamanhos:</p>
<ul>
<li><p>64% têm de 2 a 30 usuários</p></li>
<li><p>13% têm de 31 a 50 usuários</p></li>
<li><p>10% têm de 51 a 100 usuários</p></li>
<li><p>13% têm de 101 a 500 usuários</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Usuários de VoIP (Voz sobre IP)</p></td>
<td><p>60% dos usuários do Lync Server estão habilitados para unified communications (UC) (isto é, seus números de telefone são pertencidos por Lync Server).</p></td>
</tr>
<tr class="even">
<td><p>Distribuição dos cliente registrados</p></td>
<td><p>65% dos clientes executam software do Lync 2013, incluindo Lync e Lync Phone Edition.</p>
<p>30% dos clientes executam software cliente de uma versão anterior do Lync.</p>
<p>5% dos clientes usam Lync Web App.</p>
<p>Se a mobilidade está habilitada, assumimos que 40% dos usuários utilizam simultaneamente mobilidade e outras opções de cliente registrado citadas anteriormente. Nesse caso, a taxa do o ponto de presença múltiplo de cliente (MPOP) é de 1:1.9. Se a mobilidade está desabilitada, a taxa MPOP é de 1:1.5.</p></td>
</tr>
<tr class="odd">
<td><p>Distribuição dos usuários remotos</p></td>
<td><p>70% os usuários se conectam internamente.</p>
<p>30% dos usuários se conectam por meio de um Servidor de Borda e um Diretor.</p></td>
</tr>
<tr class="even">
<td><p>Distribuição dos contatos</p></td>
<td><p>O número máximo de contatos de um usuário é 1.000. Menos de um 1% dos usuários tem 1.000 contatos. Menos de 25% dos usuários têm 100 ou mais contatos.</p>
<p>Média de 80 contatos para usuários com conectividade pública na nuvem. Desses usuários:</p>
<ul>
<li><p>50% dos contatos estão dentro da organização. 10% desses usuários são usuários remotos, se conectando de fora do firewall.</p></li>
<li><p>40% dos contatos são usuários públicos na nuvem (como usuários do AOL, Yahoo!, MSN ou Google Talk).</p></li>
<li><p>10% dos contatos são de parceiros federados.</p>

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>

</li>
</ul>
<p>Média de 50 contatos para usuários sem conectividade pública na nuvem. Desses usuários:</p>
<ul>
<li><p>80% dos contatos estão dentro da organização. 10% desses usuários são usuários remotos, se conectando de fora do firewall.</p></li>
<li><p>20% dos contatos são de parceiros federados.</p>
<p>Cada usuário possui 1 grupo de distribuição em sua lista de contatos. Para testar o desempenho, assumimos que os grupos de distribuição são sempre expandidos.</p></li>
</ul>
<p>25% dos contatos do usuário utilizam XMPP.</p></td>
</tr>
<tr class="odd">
<td><p>Tempo de sessão</p></td>
<td><p>A sessão média de logon do usuário dura 12 horas. Todos os usuários fazem logon em até 120 minutos após o início da sessão.</p></td>
</tr>
</tbody>
</table>


### Modelo de usuário de IM e presença

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Sessões de IM ponto a ponto</p></td>
<td><p>Cada usuário tem em média seis sessões de IM ponto a ponto por dia.</p>
<p>10 mensagens instantâneas por sessão.</p>
<p>Cada mensagem é correspondida com duas mensagens de INFO SIP e 2 mensagens SIP 200 OK (para os indicadores de status como “&lt;Name&gt; está digitando”)</p></td>
</tr>
<tr class="even">
<td><p>Sondagem de presença</p></td>
<td><p>Em geral, supomos o pool de presença com uma média de 60 pools por usuário, por hora. Para cada usuário, suponha uma média de:</p>
<ul>
<li><p>Um pool por dia de presença de usuários na guia organização do usuário (mas não na Lista de contatos). O número médio de não contatos na guia organização do usuário é de 15 usuários. Dois cartões de visita visualizando operações por dia.</p></li>
<li><p>Um pool de presença sempre que o usuário clica em outro usuário para começar uma conversa, estimativa de uma vez por hora.</p></li>
<li><p>Seis pesquisas do usuário por hora. Cada vez que uma pesquisa é realizada, um pool de lote é enviado para todos na lista de resultados da pesquisa. Suponha que o tamanho médio dos resultados da pesquisa é 20. Se os resultados da pesquisa permanecem na tela, o pool de lote é atualizado a cada 5 minutos; assumimos que haverá duas atualizações por hora.</p></li>
<li><p>Quando o usuário abre ou visualiza um email no Outlook, um pool de presença de usuários nos campos Para: e Cc: do email, com estimativa de cinco emails por hora e quatro usuários por email.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Assinaturas de presença</p></td>
<td><p>Quando um usuário adiciona outro como contato, o primeiro usuário está se <em>inscrevendo</em> em cinco categorias de informação sobre o segundo usuário. As atualizações dessas categorias de informação são automaticamente enviadas ao primeiro usuário.</p>
<p>Para cada cliente, uma única solicitação de inscrição em lote é enviada para obter o estado de presença em uma média de 40 contatos, com 40 diálogos adicionais para obter presença de contatos federados.</p>
<p>A presença de membros de um grupo de distribuição expandido é encontrada através de inscrições de presença persistente, não pool, e é modelada como 1 expansão por usuário para cada 2 horas.</p>
<p><em>Descrições curtas</em> ocorrem quando um usuário faz o login, há uma inscrição de lote para todos os contatos do usuário e o usuário faz o logoff logo. Assumimos 6 inscrições curtas por usuário, por hora, onde cada inscrição dura 10 minutos.</p></td>
</tr>
<tr class="even">
<td><p>Publicação de Presença</p></td>
<td><p>O estado de presença é publicado em uma média de 4 publicações por usuário, por hora, com um máximo de 6 por usuário, por hora.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Tamanho do Documento de Presença</p></td>
<td><p>O tamanho médio de um documento de presença completo é assumido como 4K, com um máximo de 25K.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir descreve o modelo de usuário para uso do catálogo de endereços.

### Modelo de usuário para uso do catálogo de endereços

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Modo de pesquisa do Catálogo de endereços</th>
<th>Uso</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Consulta da web do Catálogo de endereços somente (todas as consultas realizadas pelo serviço Consulta da web do Catálogo de endereços)</p></td>
<td><p>Quatro consultas de prefixo por usuário, por dia.</p>
<p>60 consultas de pesquisa exatas por usuário, por dia. 40% delas são em lote, com uma média de 20 contatos por consulta. Os outros 60% das consultas servem para um único contato.</p>
<p>25 consultas de foto por usuário, por dia. 24 para uma única foto, o restante é uma consulta em lote com uma média de 20 contatos.</p>
<p>Uma consulta de pesquisa de organização por usuário, por dia.</p></td>
</tr>
<tr class="even">
<td><p>Modo misto, arquivo do catálogo de endereços e consultas da web usadas. Esse é o modo padrão.</p></td>
<td><p>Somente dois tipos de consulta vão para a rede, as consultas de pesquisa de foto e organizacional total.</p>
<p>25 consultas de foto por usuário, por dia. 24 para uma única foto, o restante é uma consulta em lote com uma média de 20 contatos.</p>
<p>Uma consulta de pesquisa de organização por usuário, por dia.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir descreve o modelo de conferência.

### Modelo de conferência

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Reuniões agendadas versus reuniões do tipo &quot;Reunir Agora&quot;</p></td>
<td><p>60% agendadas, 40% não agendadas.</p>
<p>Das reuniões programadas, assumimos que 80% são conferências atribuídas, que são ocorrências de conferências recorrentes; 10% são reuniões abertas uma vez; 8% são reuniões anônimas únicas, e 2% são reuniões fechadas uma vez.</p></td>
</tr>
<tr class="even">
<td><p>Distribuição de cliente de conferência</p></td>
<td><p>Para reuniões agendadas:</p>
<ul>
<li><p>65% dos usuários de conferência utilizam Lync 2013.</p></li>
<li><p>5% dos usuários de conferência utilizam Microsoft Lync Web App.</p></li>
<li><p>30% dos usuários de conferência utilizam clientes anteriores, incluindo Microsoft Lync 2010, Office Communicator 2007 R2, Office Communicator 2007 e Microsoft Office Communicator Web Access (versão 2007).</p></li>
</ul>
<p>Para reuniões não agendadas:</p>
<ul>
<li><p>70% dos usuários de conferência utilizam Lync 2013.</p></li>
<li><p>30% dos usuários de conferência utilizam clientes anteriores, incluindo Microsoft Lync 2010, Office Communicator 2007 R2, Office Communicator 2007 e Microsoft Office Communicator Web Access (versão 2007).</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Simultaneidade de reunião</p></td>
<td><p>5% dos usuários estarão em conferências durante as horas de trabalho. Dessa forma, em um pool de 80.000 usuários, 4.000 usuários poderão estar em conferências a qualquer momento.</p></td>
</tr>
<tr class="even">
<td><p>Distribuição do áudio de reunião</p></td>
<td><p>40% de combinação entre conferência de áudio VoIP e discada, com uma proporção de 3:1 de usuários VoIP para usuários discados.</p>
<p>35% somente de áudio VoIP.</p>
<p>15% somente de áudio de conferência discada.</p>
<p>10% sem áudio (conferências somente de IM, com uma média de cinco mensagens enviadas por usuário).</p></td>
</tr>
<tr class="odd">
<td><p>Combinação de mídias para conferências</p></td>
<td><p>75% das conferências são conferências da Web, com áudio mais alguma outra modalidade de colaboração.</p>
<p>Para essas conferências, os outros métodos de colaboração são os seguintes:</p>

> [!NOTE]  
> Esses números somam mais de 100%, pois uma conferência pode ter vários métodos de colaboração.

<ul>
<li><p>50% adiciona compartilhamento de aplicativos. Assumimos que um usuário envia dados a um pico de 1,1 MB por segundo.</p></li>
<li><p>50% adicionam mensagem instantânea (com média de 2 mensagens por usuário).</p></li>
<li><p>20% de colaboração de dados adicionados, incluindo PowerPoint ou quadro de anotações. Nestes, uma média de 2 arquivos 2 PowerPoint apresentados por conferência, com um tamanho de arquivo médio do PowerPoint de 10 MB (sem vídeo integrado) ou 30 MB (com vídeo integrado). Média de 20 anotações por quadro de anotações.</p></li>
<li><p>20% de vídeo adicionado. Destes usuários, 70% estão em conferências habilitadas para vídeo multivisualização, onde cada usuário recebe 2-3 fluxos de vídeo.</p></li>
<li><p>15% notas compartilhadas adicionadas.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Distribuição dos participantes da reunião</p></td>
<td><p>50% de usuários internos autenticados.</p>
<p>25% de usuários de acesso remoto autenticados.</p>
<p>15% de usuários anônimos.</p>
<p>10% de usuários federados.</p></td>
</tr>
<tr class="odd">
<td><p>Distribuição de ingresso na reunião</p></td>
<td><p>Os usuários são simulados como participação da reunião dentro dos primeiros 5 minutos.</p></td>
</tr>
</tbody>
</table>


Em pools de Front-End regulares, o Lync Server 2013 possui um tamanho de reunião suportado máximo de 250 usuários. Cada pool pode hospedar uma reunião de 250 usuários por vez. Enquanto esta grande reunião está ocorrendo, o pool também pode hospedar outras conferências menores. Além disso, é possível suportar reuniões de até 1000 usuários configurando um pool exclusivo para hospedar estas reuniões. Para obter detalhes, consulte [Suporte a reuniões grandes no Lync Server 2013](lync-server-2013-support-for-large-meetings.md).

Conferências foram simuladas como a seguir:

  - 85% das conferências tinham quatro participantes.

  - 10% das conferências tinham seis participantes.

  - 5% das conferências tinham 11 participantes.

  - Uma grande conferência de 250 usuários.

A tabela a seguir fornece detalhes sobre o modelo de usuário para conferências envolvendo usuários discados.

### Modelo de usuário de conferência discada

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Autenticado/anônimo</p></td>
<td><p>70% de chamadores participaram como anônimos e foram solicitados por um nome de registro. 30% participaram como usuários autenticados.</p></td>
</tr>
<tr class="even">
<td><p>Duração da chamada e música em espera</p></td>
<td><p>A duração média da chamada sem música em espera: 50 segundos.</p>
<p>50% dos usuários de chamada recebida ouvem música em espera, durante uma média de 5 minutos.</p></td>
</tr>
<tr class="odd">
<td><p>DTMF (Dual-tone multifrequency)</p></td>
<td><p>15% das conferências somente discadas têm líderes de telefone. 10% das conferências mistas que incluem usuários discados também têm líderes de telefone.</p>
<p>20% dos líderes de telefone usam 2 comandos DTMF por conferência.</p></td>
</tr>
<tr class="even">
<td><p>Idiomas do anúncio</p></td>
<td><p>As simulações usam Inglês como o idioma de anúncio.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir fornece detalhes sobre o modelo de usuário para lobbies de conferência.

### Modelo de usuário de lobby de conferência

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Número de usuários no lobby</p></td>
<td><p>5% dos usuários discados passam pelo lobby e 25% dos outros usuários passam pelo lobby</p></td>
</tr>
<tr class="even">
<td><p>Admissão a partir do lobby</p></td>
<td><p>Em simulações, todos os usuários foram admitidos pelo apresentador antes do tempo limite do cliente.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir descreve o modelo de usuário para outras sessões ponto a ponto.

### Modelo de usuário de sessões ponto a ponto

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Compartilhamento de aplicativos</p></td>
<td><p>Cada usuário participa de 5 sessões de compartilhamento de aplicativo ponto a ponto por mês, uma média de 0,25 sessões por dia.</p></td>
</tr>
<tr class="even">
<td><p>Transferência de arquivos</p></td>
<td><p>Cada usuário participa de uma sessão de transferência de arquivo ponto a ponto por mês (como parte de uma sessão de IM), para uma média de 0,05 sessões por dia. O tamanho de arquivo médio da sessão transferido é de 1 MB.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir descreve o modelo de usuário para políticas.

### Políticas de Modelo do Usuário

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Categoria</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Políticas de Arquiamento, Presença e Conferência</p></td>
<td><p>Assumimos que há uma política global, 10 políticas de conferência de marcação, 4 políticas de Arquivamento e 10 políticas de presença de tag.</p></td>
</tr>
<tr class="even">
<td><p>Política de voz</p></td>
<td><p>Assumimos que há uma política global e 2 políticas de tag por local. 100% dos locais possuem uma política local e 30% dos usuários possuem uma política por usuário atribuída. Assumimos um plano de discagem por local e duas rotas por local.</p></td>
</tr>
</tbody>
</table>


## Horário de pico

Para sessões ponto a ponto, a carga durante o pico é calculada usando tentativas de chamada no horário de pico (BHCA). Esse termo do setor de voz supõe que 50% de todas as chamadas para esse dia serão completadas em 20% do tempo. Isso é calculado usando a seguinte fórmula:

`BHCA=(total calls * 0.5) / 1.6`

O teste de desempenho simulou o horário de pico executando sessões VoIP e outras sessões ponto a ponto com uma carga de hora de pico durante pelo menos 1,6 hora por dia.

A carga de pico de conferência supõe que 75% de todas as conferências para um dia de oito horas ocorre em 4 horários de pico. Esses horários de pico têm 1,5 vezes a carga média de conferência.

## Enterprise Voice para chamadas PSTN

As seguintes previsões aplicam-se às chamadas do Enterprise Voice:

  - 50% dos usuários são habilitados para Enterprise Voice e 60% destes usuários são habilitados para chamada PSTN.

  - Cada um destes usuários habilitados para chamada PSTN faz 4 chamadas PSTN durante a hora ocupada. Cada duração de chamada é de 3 minutos.

  - 65% destas chamadas de voz PSTN usam bypass de mídia.

## Mobilidade

40% dos usuários registrados são assumidos como habilitados para Mobilidade. Para cada usuário que possui habilidade habilitado, assumimos que a atividade do cliente móvel é aditivo àquelas de outras instâncias MPOP deste usuário, com exceção das interações de conferência, para as quais o cliente de mobilidade é apenas outro tipo de cliente que pode ser usado para participar de conferências.

## Chat Persistente

Assumimos que 25% dos usuários registrados sejam envolvidos em sessões de chat Persistente, com as seguintes características:

  - Uma média de 1,5 salas de bate-papo por usuário

  - Cada sala de bate-papo resulta em 12 solicitações de pool por hora, indicando uma média de 10 usuários cada

## Grupo de Resposta e Estacionamento de Chamadas

Assumimos que 0,15% dos usuários registrados pertencem aos grupos de resposta. Assumimos que 0,02% dos usuários registrados possuem chamadas estacionadas em um determinado ponto do tempo.

