---
title: 'Lync Server 2013: Planejamento de capacidade usando modelos de usuário'
TOCTitle: Planejamento de capacidade usando modelos de usuário
ms:assetid: 902ab23e-94d6-482a-9d6e-c0b28dc3e03d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615015(v=OCS.15)
ms:contentKeyID: 49886310
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de capacidade para Lync Server 2013 usando modelos de usuário

 

_**Tópico modificado em:** 2016-12-08_

Esta seção oferece orientação sobre quantos servidores serão necessários em um local para o número de usuários desse local, sendo que a utilização é semelhante à descrita em [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md). A tabela a seguir resume essas recomendações.

## Plataforma de hardware testada

Todos os resultados de desempenho e recomendações de implantação desta seção são baseados em testes de desempenho em servidores que executam o hardware descrito na tabela a seguir. Recomendamos usar hardware similar. Se você usar hardware menos poderoso, poderá enfrentar problemas de funcionalidade ou desempenho ruim. Observe que essas recomendações de hardware são mais altas que das versões anteriores do Lync Server.

### Hardware usado em testes de desempenho

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente de hardware</th>
<th>Recomendado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Processador duplo de 64 bits, núcleo hexagonal, 2.26 gigahertz (GHz) ou superior</p>
<p>Processadores Intel Itanium não são suportados para funções de servidor Lync Server.</p></td>
</tr>
<tr class="even">
<td><p>Memória</p></td>
<td><p>32 gigabytes (GB)</p></td>
</tr>
<tr class="odd">
<td><p>Disco</p></td>
<td><ul><li><p>8 ou mais discos rígidos de 10.000-RPM com pelo menos 72 GB de espaço livre em disco.</p>
<p>Dois dos discos devem usar RAID 1 e seis devem usar RAID 10.</p>
<p>- OU -</p></li><li><p>Drivers de estado sólido (SSDs) que oferecem desempenho semelhante a 8 drivers de disco mecânico de 10.000-RPM.</p></li></ul></td>
</tr>
<tr class="even">
<td><p>Rede</p></td>
<td><ul><li><p>1 adaptador de rede de porta dupla, 1 Gbps ou superior (2 recomendados, que exige agrupamento com um único endereço MAC e um único endereço IP)</p></li></ul></td>
</tr>
</tbody>
</table>


## Resumo de Resultados

A tabela a seguir resume essas recomendações.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Função de servidor</th>
<th>Número máximo de usuários suportados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Pool de Front-Ends com doze Servidores Front-End e um Servidor Back-End ou um par espelhado de Servidores Back-End.</p></td>
<td><p>80.000 usuários únicos, mais 50% de pontos múltiplos de presença (MPOP) representando instâncias não móveis, mais 40% de usuários ativados para mobilidade de um total de 152.000 pontos de extremidade.</p></td>
</tr>
<tr class="even">
<td><p>Conferência A/V</p></td>
<td><p>O serviço de conferência A/V fornecido por um Pool de Front-Ends suporta as conferências do pool, supondo um tamanho máximo de conferência de 250 usuários e apenas uma conferência deste tamanho sendo executada ao mesmo tempo.</p>
<div class="alert">
> [!NOTE]  
> Além disso, você pode suportar grandes conferências de 250 a 1000 usuários implantando um Pool de Front-Ends separado com dois Servidores Front-End para hospedar as grandes conferências. Para obter detalhes, consulte <a href="lync-server-2013-supporting-large-meetings.md">Suporte a Reuniões Grandes usando Lync Server 2013</a>.
</div></td>
</tr>
<tr class="odd">
<td><p>Um Servidor de Borda</p></td>
<td><p>12.000 usuários remotos simultâneos</p></td>
</tr>
<tr class="even">
<td><p>Um Diretor</p></td>
<td><p>12.000 usuários remotos simultâneos</p></td>
</tr>
<tr class="odd">
<td><p>Monitoring Server e Servidor de Arquivamento</p></td>
<td><p>No Lync Server 2013, os serviços de front end de monitoramento e arquivamento são agora executados em cada Servidor Front-End, em vez de nas funções de servidor separadas.</p>
<p>O monitoramento e arquivamento ainda exigem seus próprios armazenamentos de banco de dados. Se você também executar o Exchange 2013, é possível manter seus dados de arquivamento no Exchange, em vez de em banco de dados SQL dedicados.</p></td>
</tr>
<tr class="even">
<td><p>Um Servidor de Mediação</p></td>
<td><p>Um Servidor de Mediação colocado com Servidor Front-End é executado em cada Servidor Front-End em um pool, e deve fornecer capacidade suficiente para os usuários no pool. Para Servidor de Mediação autônomo, consulte a seção “ Servidor de Mediação” posteriormente neste tópico.</p></td>
</tr>
<tr class="odd">
<td><p>Um servidor do Standard Edition</p></td>
<td><p>Recomendamos que se você usar os servidores do Standard Edition para hospedar usuários, sempre use dois servidores, pareados usando as recomendações do <a href="lync-server-2013-planning-for-high-availability-and-disaster-recovery.md">Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013</a>. Cara servidor no par pode hospedar até 2.500 usuários e, se um servidor falhar, o servidor restante poderá dar suporte a 5.000 usuários em um cenário de falha.</p>
<p>Se sua implantação inclui um quantidade de tráfego significativa de áudio ou vídeo, o desempenho do servidor pode ser prejudicado com mais de 2.500 usuários por servidor. Neste caso, você deve considerar adicionar mais servidores do Standard Edition ou movê-los para o Lync ServerEnterprise Edition.</p></td>
</tr>
</tbody>
</table>


## Servidor Front-End

> [!NOTE]  
> Pools alongados não são suportados pela função desse servidor.

Em um Pool de Front-Ends, você deve ter um Servidor Front-End para cada 6.600 usuários hospedados no pool, supondo que o hyper-threading esteja ativado em todos os servidores no pool, e que o hardware do servidor atenda às recomendações em [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md). O número máximo de usuários em um Pool de Front-Ends é 80.000. Se houver mais de 80.000 usuários em um site, é possível implantar mais de um Pool de Front-Ends.

Ao contar o número de usuários em um Pool de Front-Ends, inclua os usuários hospedados em Aparelhos de Filial Persistente e Servidores de Filial Persistente em filiais associadas a este Pool de Front-Ends.

Quando um servidor ativo está indisponível, suas conexões são transferidas automaticamente para outros serviços no pool. Por exemplo, se você tiver 30.000 usuários e cinco Servidores Front-End, se um dos servidores estiver indisponível, as conexões de 6.000 usuários precisam ser transferidas aos outros quatro servidores. Os quatro servidores restantes terão 7.500 usuários cada, o que é um número maior que o recomendado.

Se em vez disso, você iniciou com seis Servidores Front-End para seus 30.000 usuários e em seguida um se tornou indisponível, um total de 5.000 usuários será movido para os cinco servidores restantes. Cada um desses cinco servidores hospedará 6.000 usuários, que é o âmbito recomendado.

O número máximo de usuários em um Pool de Front-Ends é 80.000. O número máximo de Servidores Front-End em um pool é 12.

Para um Pool de Front-Ends com 80.000 usuários, doze Servidores Front-End são suficientes para o desempenho, em implantações comuns que seguem os [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md). As implantações projetadas para suportar failover de recuperação de desastres supõem que um máximo de 40.000 usuários possam ser hospedados em cada um dos Pools de Front-Ends pareados, no qual cada pool tem Servidores Front-End suficientes para acomodar os usuários em ambos os pools, caso um pool tenha que ser transferido para o outro.

O número de usuários suportados com bom desempenho por um Pool de Front-Ends específico pode diferir desses números pelos seguintes motivos:

  - O hardware dos seus Servidores Front-End não está de acordo com as recomendações em [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

  - A utilização da sua organização difere de forma significativa dos modelos de usuário, bem como possui um volume consideravelmente maior de tráfego de conferências.

> [!IMPORTANT]  
> No Lync Server 2013, os bancos de dados de presença são agora hospedados nos Servidores Front-End, ao contrário do Lync Server 2010, onde eram hospedados no Servidor Back-End. Isso significa que o desempenho e capacidade de disco em seus Servidores Front-End não deve ser comprometida das recomendações listas anteriormente nesta seção e nas <a href="lync-server-2013-server-hardware-platforms.md">Plataformas de hardware de servidor para Lync Server 2013</a>, independentemente do número de usuários hospedados por seus Servidores Front-End.

A tabela a seguir exibe a largura de banda média para IM e presença, considerado o modelo de usuário conforme definido em [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md).


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Largura de banda média por usuário</th>
<th>Requisitos de largura de banda por Servidor Front-End com 6.600 usuários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1,3 Kpbs</p></td>
<td><p>13 Mbps</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Para aprimorar o desempenho de mídia da Conferência A/V colocada e a funcionalidade do Servidor de Mediação em seus Servidores Front-End, você deve permitir receive-side scaling (RSS) nos adaptadores de rede em seus Servidores Front-End. O RSS permite que pacotes de entrada sejam manipulados em paralelo por vários processadores no servidor. Para obter mais detalhes, consulte &quot;Receive-Side Scaling Enhancements in Windows Server 2008&quot; (aprimoramentos no dimensionamento do lado receptor no Windows Server 2008&quot; em <a href="http://go.microsoft.com/fwlink/?linkid=268731" class="uri">http://go.microsoft.com/fwlink/?linkid=268731</a>. Para obter detalhes sobre como ativar RSS, consulte a documentação do seu adaptador de rede.

## Máximos de Conferência

Dado o modelo de usuário em que 5% dos usuários em um pool podem estar em uma conferência em qualquer momento, um pool de 80.000 usuários poderia ter cerca de 4.000 usuários em conferências de uma só vez. Espera-se que essas conferências sejam uma mistura de mídias (algumas somente IM, algumas IM com áudio, algumas áudio/vídeo, por exemplo) e de número de participantes. Não existe um limite rígido para o número real de conferências permitidas e o uso real determina o desempenho real. Por exemplo, se sua organização tem muito mais conferências de modo misto do que as supostas no modelo de usuário, pode ser necessário implantar mais Servidores Front End ou Servidores de Conferência A/V do que as recomendações neste documento. Para detalhes sobre as suposições no modelo de usuário, consulte Servidores Front-End. Além disso, se o número médio de conferências hospedadas for conhecido, você pode usar as tabelas em [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md) para estimar suas necessidades de servidor.

O tamanho máximo suportado de conferências hospedadas por um Lync Server 2013Pool de Front-Ends regular, que também hospeda usuários é 250 participantes. Enquanto esta conferência de 250 usuários está acontecendo, o pool ainda suporta outras conferências, de forma que 5% dos usuários do pool estão em conferências simultâneas. Por exemplo, em um pool de doze Servidores Front-End e 80.000 usuários, enquanto a conferência de 250 usuários está acontecendo, o Lync Server suporta outros 3.750 usuários participando de conferências menores.

Independente do número de usuários hospedados no Pool de Front-Ends ou servidor Standard Edition, o Lync Server suporta um mínimo de 125 outros usuários participando de conferências menores no mesmo pool ou servidor que está hospedando uma conferência de 250 usuários.

Para permitir conferências entre 250 e 1.000 usuários, você pode definir um Pool de Front-Ends separado, só para hospedar essas conferências. Esse Pool de Front-Ends não hospedará nenhum usuário. Para obter detalhes, consulte [Suporte a Reuniões Grandes usando Lync Server 2013](lync-server-2013-supporting-large-meetings.md).

Se sua organização tem muito mais conferências de modo misto do que as supostas no modelo de usuário, pode ser necessário implantar mais Servidores Front-End que as recomendações neste documento (até um limite de 12 FEs). Para obter detalhes sobre as suposições no modelo do usuário, consulte [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md).

## Servidor de Borda

> [!NOTE]  
> Pools alongados não são suportados pela função desse servidor.

Você deve implantar um Servidor de Borda para cada 12.000 usuários que acessarão um site simultaneamente. São recomendados no mínimo dois Servidores de Borda para alta disponibilidade. Essas recomendações supõem que o hardware para o seus Servidores de Borda cumpre as recomendações em [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

Ao contar o número de usuários para os Servidores de Borda, inclua os usuários hospedados em Aparelhos de Filial Persistente e Servidores de Filial Persistente em filiais associadas a um Pool de Front-Ends neste local.

> [!NOTE]  
> Para aprimorar o desempenho do serviço de Borda de Conferência A/V em seus Servidores de Borda, você deve habilitar o receive-side scaling (RSS) nos adaptadores de rede em seus Servidores de Borda. O RSS permite que pacotes recebidos sejam manipulados em paralelo por vários processadores no servidor. Para detalhes, consulte <a href="http://go.microsoft.com/fwlink/?linkid=206013" class="uri">http://go.microsoft.com/fwlink/?linkid=206013</a>. Para informações sobre como habilitar o RSS, consulte a documentação do seu adaptador de rede.

## Diretor

> [!NOTE]  
> Pools alongados não são suportados pela função desse servidor.

Se implantar a função de servidor Diretor, recomendamos que você implante um Diretor para cada 12.000 usuários remotos que acessarão um site ao mesmo tempo. São recomendados no mínimo dois Diretores para alta disponibilidade. Essas recomendações supõem que o hardware para seus Servidores de Borda atende as recomendações em [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

Ao contar o número de usuários para os Diretores, inclua os usuários hospedados em Aparelhos de Filial Persistente e Servidores de Filial Persistente em filiais associadas a um Pool de Front-Ends neste local.

## Servidor de Mediação

> [!NOTE]  
> Pools alongados não são suportados pela função desse servidor.

Se você colocar o Servidor de Mediação com Servidor Front-End, o Servidor de Mediação será executado em cada Servidor Front-End no pool, e deverá fornecer capacidade suficiente para os usuários no pool.

Se você implantar um pool de Servidor de Mediação autônomo, a quantidade de Servidor de Mediação a implantar depende de vários fatores, incluindo o hardware usado para Servidor de Mediação, o número de usuários de VoIP que você tem, o número de pontos de gateway que cada Pool do servidor de mediação controla, o tráfego de pico desses gateways, e a porcentagem de chamadas com mídia que contorna o Servidor de Mediação.

As tabelas a seguir fornecem orientações sobre quantas chamadas simultâneas um Servidor de Mediação pode tratar, supondo que o hardware dos Servidor de Mediação atenda os requisitos em [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) e que o hyper-threading esteja ativado. Para obter detalhes sobre a escalabilidade do Servidor de Mediação, consulte [Estimando uso e tráfego de voz para Lync Server 2013](lync-server-2013-estimating-voice-usage-and-traffic.md) e [Orientações de implantação para Servidor de Mediação no Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md).

Todas as tabelas a seguir supõem a utilização resumida em [Modelos de usuário no Lync Server 2013](lync-server-2013-user-models.md).

### Capacidade do Servidor de Mediação autônomo: 70% de usuários internos, 30% de usuários externos com capacidade de chamada sem desvio (transcodificação de mídia executada pelo Servidor de Mediação)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware de servidor</th>
<th>Número máximo de chamadas</th>
<th>Número máximo de linhas T1</th>
<th>Número máximo de linhas E1</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Processador duplo, hex-core, CPU de 2,26 GHz hyper-threaded, <strong>com hyper-threading desabilitado</strong>, com 32 GB de memória e uma placa de adaptador de rede dual-port.</p></td>
<td><p>1100</p></td>
<td><p>46</p></td>
<td><p>35</p></td>
</tr>
<tr class="even">
<td><p>Processador duplo, hex-core, CPU de 2,26 GHz hyper-threaded, com 32 GB de memória e uma placa de adaptador de rede dual-port.</p></td>
<td><p>1500</p></td>
<td><p>63</p></td>
<td><p>47</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Embora servidores com 32 GB de memória tenham sido usados para testes de desempenho, servidores com 16 GB de memória são suportados para um Servidor de Mediação autônomo e são suficientes para fornecer o desempenho mostrado nesta tabela.

### Servidor de Mediação Capacidade ( Servidor de Mediação Colocado com Servidor Front-End) 70% de usuários internos, 30% de usuários externos, capacidade de chamadas sem contorno (processamento de mídia executado por Servidor de Mediação)

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Hardware de servidor</th>
<th>Número máximo de chamadas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Processador duplo, hex-core, CPU de 2,26 GHz hyper-threaded com hyper-threading e 2 placas de adaptador de rede de 1GB.</p></td>
<td><p>150</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Este número é muito menor que os números para o Servidor de Mediação autônomo, pois o Servidor Front-End precisa lidar com outros recursos e funções dos 6.600 usuários hospedados nele, além da transcodificação necessária para chamadas de voz.

> [!NOTE]  
> Para melhorar o desempenho do Servidor de Mediação, você precisa ativar o receive-side scaling (RSS) nos adaptadores de rede em seus Servidor de Mediação. O RSS permite que pacotes de entrada sejam manipulados em paralelo por vários processadores no servidor. Para obter mais detalhes, consulte &quot;Receive-Side Scaling Enhancements in Windows Server 2008&quot; (aprimoramentos no dimensionamento do lado receptor no Windows Server 2008&quot; em <a href="http://go.microsoft.com/fwlink/?linkid=268731" class="uri">http://go.microsoft.com/fwlink/?linkid=268731</a>. Para obter detalhes sobre como ativar RSS, consulte a documentação do seu adaptador de rede.

## Servidor Back-End

No Lync Server 2013, os banco de dados de presença estão localizados nos Servidores Front-End, em vez do Servidor Back-End. Isso resultou em um requisito muito mais simples para cada Servidor Back-End no Lync Server 2013, equivalente aos requisitos de hardware para o Servidor Front-End. Compare isso com o Lync Server 2010, onde o Servidor Back-End era necessário ser um servidor de grau muito maior com 25 discos. No entanto, a carga de trabalho dos Servidores Back-End é ainda tal que você não deve falhar em atender as recomendações de hardware listadas anteriormente nesta seção e em [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

Para fornecer alta disponibilidade ao seu Servidor Back-End, recomendamos implantar espelhamento de servidor. Para obter mais informações, consulte [Alta disponibilidade do Servidor Back-End no Lync Server 2013](lync-server-2013-back-end-server-high-availability.md).

## Monitoring Server e Servidor de Arquivamento

No Lync Server 2013, se você implantar monitoramento ou arquivamento, a funcionalidade de front end desses serviços é executada nos Servidores Front-End, em vez de em funções de servidor separadas. O monitoramento e arquivamento ainda usam, cada um deles, seu próprio armazenamento de banco de dados, separado do armazenamento de back end. Como alternativa, se você tiver Exchange 2013 implantado, você pode armazenar dados de arquivamento de mensagens instantâneas no Exchange, em vez de em um armazenamento SQL dedicado.

A tabela a seguir indica aproximadamente quanto armazenamento de banco de dados é exigido por usuário, por dia, para os dados de monitoramento e arquivamento.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p></p></td>
<td><p><strong>CDR (Monitoramento)</strong></p></td>
<td><p><strong>QoE (Monitoramento)</strong></p></td>
<td><p><strong>Arquivamento</strong></p></td>
</tr>
<tr class="even">
<td><p>Espaço em disco exigido por usuário, por dia</p></td>
<td><p>49 KB</p></td>
<td><p>28 KB</p></td>
<td><p>57 KB</p></td>
</tr>
</tbody>
</table>


A Microsoft usou o hardware na tabela a seguir do servidor de banco de dados para monitoramento e arquivamento durante seus testes de desempenho. O teste coletou dados de dois Pools de Front-Ends, cada qual contendo 80.000 usuários.

### Hardware usado nos testes de desempenho de monitoramento e arquivamento

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Componente de hardware</th>
<th>Recomendado</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>CPU</p></td>
<td><p>Processador duplo de 64 bits, núcleo hexagonal, 2.26 gigahertz (GHz) ou superior</p></td>
</tr>
<tr class="even">
<td><p>Memória</p></td>
<td><p>4 gigabytes (GB)</p></td>
</tr>
<tr class="odd">
<td><p>Disco</p></td>
<td><p>25 unidades de disco rígido de 10.000-RPM com 300 GB em cada unidade, com a seguinte configuração</p>
<h3 id="section-3"> </h3>
<div>
<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Unidade</strong></p></td>
<td><p><strong>Configuração RAID</strong></p></td>
<td><p><strong>Número de discos</strong></p></td>
</tr>
<tr class="even">
<td><p>CDR, QoE e arquivos de banco de dados de arquivamento, em uma única unidade</p></td>
<td><p>1+0</p></td>
<td><p>16</p></td>
</tr>
<tr class="odd">
<td><p>Arquivo de log do banco de dados de CDR</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="even">
<td><p>Arquivo de log do banco de dados de QoE</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
<tr class="odd">
<td><p>Arquivo de log do banco de dados de arquivamento</p></td>
<td><p>1</p></td>
<td><p>2</p></td>
</tr>
</tbody>
</table>

</div></td>
</tr>
<tr class="even">
<td><p>Rede</p></td>
<td><ul><li><p>1 adaptador de rede de porta dupla, 1 Gbps ou superior (2 recomendados, que exige agrupamento com um único endereço MAC e um único endereço IP)</p></li></ul></td>
</tr>
</tbody>
</table>


## Nesta seção

  - [Estimando uso e tráfego de voz para Lync Server 2013](lync-server-2013-estimating-voice-usage-and-traffic.md)

  - [Orientações de implantação para Servidor de Mediação no Lync Server 2013](lync-server-2013-deployment-guidelines-for-mediation-server.md)

