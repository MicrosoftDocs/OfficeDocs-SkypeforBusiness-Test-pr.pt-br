---
title: Metodologia de qualidade de chamada do Lync no Lync Server 2013
TOCTitle: 'Pôster: Metodologia de qualidade de chamada do Lync'
ms:assetid: a069f4e5-4f80-4f0f-8657-2e07276b6b41
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn593600(v=OCS.15)
ms:contentKeyID: 61084813
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Metodologia de qualidade de chamada do Lync no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este artigo acompanha o pôster [Metodologia de qualidade de chamada do Lync](http://go.microsoft.com/fwlink/?linkid=391841), que você pode baixar do Centro de Download.

![Pôster descrevendo o processo CQM](images/Dn594589.d239e04a-1c3b-4f0e-93af-88b85198615a(OCS.15).jpg "Pôster descrevendo o processo CQM")

Use esse pôster para aprender sobre a CQM, a Metodologia de Qualidade de Chamada do Lync 2013 e 2010 que o ajuda a localizar e eliminar problemas que afetam a qualidade da chamada e a experiência do usuário de implementações do Lync que incluem recursos do Enterprise Voice. A Metodologia de Qualidade de Chamada é uma nova estrutura de solução de problemas e gerenciamento de serviços que enfatiza melhor os esforços para aprimorar os serviços do Enterprise Voice no Lync. Neste artigo, você saberá mais sobre a CQM, os tipos de servidores e soluções monitorados e o que fazer com os dados de telemetria coletados.

Em caso de dúvidas sobre como usar a CQM, envie suas perguntas para cqmfeedback@microsoft.com.

O pôster explica as seguintes áreas:

  - O que é a CQM do Lync?

  - Priorize: Execute consultas de tendências

  - PCD

  - Gerenciado/não gerenciado

  - O caminho do servidor

  - O caminho final

  - O caminho para os pontos de extremidade

  - Gerenciamento de serviço

  - Regras do jogo de tabuleiro

## O que é a CQM do Lync?

A Metodologia de Qualidade de Chamada é uma nova estrutura de solução de problemas e gerenciamento de serviço que enfatiza melhor os esforços para aprimorar os serviços do Enterprise Voice no Lync. Quando você usa a CQM, menos esforço é necessário para assegurar a qualidade da chamada e a satisfação do usuário de serviços do Enterprise Voice. A CQM é explicada com mais detalhes no [Guia de Rede do Lync Server](http://go.microsoft.com/fwlink/p/?linkid=390677). Este artigo e o pôster são resumos desse conteúdo.

A CQM divide a solução de problemas do sistema em três caminhos. São eles: o caminho para o servidor, que examina os servidores e os links entre eles, o caminho para os pontos de extremidade, que examina os dispositivos de usuário e a mídia usados para a realização de chamadas e o caminho final, que aborda a integração de chamadas de rede telefônica comutada tradicional.

Cada um desses caminhos é dividido em vários segmentos relacionados a uma área ou tópico específico e, em cada segmento, são feitas definições sobre o que é um nível de qualidade aceitável, ações são executadas para atingir esse nível de qualidade e um plano de gerenciamento de serviço é colocado em vigor para manter esse nível de qualidade antes de passarmos para o próximo tópico.

O pôster apresenta a CQM do Lync como um jogo de tabuleiro para três jogadores, sendo que cada um seguirá por um desses três caminhos. As cartas inclusas no download são usadas para simular impedimentos para a qualidade de chamada que devem ser superados. Dicas e sugestões sobre os destinos e como atingi-los estão incluídas ao longo dos três caminhos, bem como diretrizes de priorização de qual caminho seguir primeiro em aplicações reais (no jogo, os três caminhos são abordados em paralelo).

Como a CQM funciona nas versões anteriores do Lync? A CQM é nova no Lync 2013, mas é possível adaptá-la para uso com o Lync 2010. A CQM pode funcionar em um certo grau com o Microsoft Office Communicator, mas isso não foi testado e não há suporte para tal.

Em caso de dúvidas sobre como usar a CQM, envie suas perguntas para cqmfeedback@microsoft.com.

## Priorize: Execute consultas de tendências

A primeira etapa na CQM é executar cada uma das consultas de tendências por duas semanas e depois analisar os resultados. Priorize a ação corretiva pelo maior colaborador de fluxo, a mais alta taxa de fluxo fraco e as áreas gerenciadas (aquelas controladas por você).  Se as consultas de Unidade de controle multiponto de áudio/vídeo (AV MCU) ou Mediação apresentarem resultados ruins, comece no caminho vermelho ou de servidor. Se as consultas conectadas ou não conectadas apresentarem resultados ruins, comece no caminho azul ou final. Se as consultas de VPN ou externas apresentarem resultados fracos, comece no caminho verde ou para os pontos finais.

Depois que você escolher um caminho com o qual começar, defina uma meta para cada área (Declarar), trabalhe para alcançar essa meta (Atingir) e depois implemente procedimentos para preservar a meta (Manter). Também é possível usar esse pôster como um jogo para entender os princípios por trás da CQM.

## PCD

A ferramenta PreCall Diagnostics (PCD) o ajudará a identificar e diagnosticar problemas na sua rede de perímetro (o banco de dados de QoE não coleta informações na sua borda ou rede de perímetro) e também para solucionar problemas de conexão no caminho final. A ferramenta está disponível como um aplicativo moderno do Windows 8 ou um aplicativo de desktop do Windows em http://apps.microsoft.com/windows/en-us/app/lync-2013-precall-diagnostics/9607fe33-2b51-403d-9615-c23f248e7c88.

## Gerenciado/não gerenciado

A implantação do Lync Server e a infraestrutura de rede geralmente podem ser divididas em espaços gerenciados e não gerenciados. O espaço gerenciado inclui toda a sua rede interna conectada e infraestrutura de servidor. O espaço não gerenciado é a infraestrutura sem fio e a rede externa.

Fazer essa distinção aumenta a clareza dos seus dados e ajuda sua organização a enfatizar cargas de trabalho que terão um impacto mensurável na qualidade de voz e vídeo do usuário. Os usuários terão uma expectativa de qualidade diferente se a chamada for feita na infraestrutura que você possui (gerenciada) em comparação com a infraestrutura que está parcialmente sob o controle de alguma outra entidade (não gerenciada). Isso não significa que os usuários sem fio só podem contar com seus próprios recursos para obter experiências excelentes com o Lync Server.

A melhora da qualidade de voz no espaço não gerenciado requer que você tenha alta qualidade no espaço gerenciado. Se a opção sem fio (Wi-Fi) será considerada espaço gerenciado ou não gerenciado depende da organização. As técnicas para obter um ambiente saudável são diferentes nos dois espaços, bem como as soluções.

## O caminho do servidor

O segmento 1 do caminho do servidor aborda os servidores reais na implementação do Lync. Colete dados de KHI referentes ao próprio servidor e sua função na implementação e analise o resultado. Se for necessário agir, corrija os problemas encontrados. Mais detalhes sobre esse tópico são apresentados no artigo sobre [Key Health Indicators no Lync Server 2013](lync-server-2013-poster-key-health-indicators.md) que acompanha o pôster de KHI.

O segmento seguinte aborda fluxos de mídia entre o servidor AV MCU e o servidor de mediação. Comece determinando suas metas de limites de fluxo fraco. Fluxos fracos geralmente são PacketLossRate \> .01 ou PacketLossRateMax \> .05. Outra meta desejável é PoorStreamsRatio \< 2%. Em seguida, use consultas detalhadas para localizar pares de servidores AVMCU e de mediação com fluxos fracos, investigue a causa de fluxos fracos, examine o equipamento de rede nos caminhos de fluxo fraco, corrija os fluxos fracos e defina a configuração ideal para o equipamento de rede. Para manter sua realização, implemente processos e ferramentas para gerenciar a mudança de configuração e relatar novas áreas de problemas.

Em seguida, examine os fluxos de mídia entre o servidor de Mediação e o gateway de PSTN (Rede Telefônica Pública Comutada). Comece determinando suas metas para limites de fluxo fracos. Os fluxos fracos geralmente são PacketLossRate \> .01 ou PacketLossRateMax \> .05. Outra meta desejável é PoorStreamsRatio \< 2%. Em seguida, use consultas detalhadas para localizar pares de servidor de Mediação e gateway com fluxos fracos, investigue a causa de fluxos fracos, examine o equipamento de rede nos caminhos de fluxo fraco, corrija os fluxos fracos e defina a configuração ideal para o equipamento de rede. Para manter sua realização, implemente processos e ferramentas para gerenciar a mudança de configuração e relatar novas áreas de problemas.

Por fim, examine as métricas de integridade do seu gateway PSTN. Identifique as estatísticas que indicam integridade e defina metas em relação a elas. Nenhuma diretriz específica é fornecida aqui, pois muitos gateways podem ser usados. Após o estabelecimento das metas, corrija conforme necessário para atingir a meta; no processo, provavelmente você definirá uma configuração ideal para o gateway. Para manter sua realização, implemente processos e ferramentas para gerenciar a mudança de configuração e relatar novas áreas de problemas. As atualizações de firmware e software podem alterar sua configuração ou levá-lo a alterar a definição da configuração ideal, portanto, aborde essas atividades com cuidado.

## O caminho final

Dos dois caminhos de conexão com a rede possíveis para os clientes, espera-se que a opção com fio ofereça a qualidade mais alta e esse deve ser seu foco inicial no caso de problemas finais. Use a consulta de CQM com fio (LastMile\_0\_Wired) e os dados de proporção de fluxos fracos fornecido por ela. Nós sugerimos a definição de uma meta de PoorStreamsRatio \< 5% para locais com \> 300 fluxos). Para atingir suas metas, corrija as sub-redes na ordem da pior para a melhor e implemente QoS.

Depois que você otimizar a qualidade das suas conexões com fio, será mais fácil melhorar a qualidade sem fio porque a infraestrutura sem fio fica sobre o núcleo com fio em cada local. Os fluxos sem fio fracos em um local com boa qualidade com fio devem ser atribuídos a componentes sem fio específicos. A consulta de CQM sem fio (LastMile\_1\_Wireless) opera em um intervalo de datas e retornará todos os fluxos sem fio internos no seu ambiente de clientes Lync para ou de servidores de conferência ou de mediação. Nós sugerimos a definição de uma meta de PoorStreamsRatio \< 5% para locais com \> 300 fluxos). Para atingir suas metas, corrija sub-redes na ordem da pior para a melhor e implemente QoS.

## O caminho para os pontos de extremidade

Comece as consultas ao caminho para os pontos de extremidade com os fones de ouvido e outros dispositivos que sabidamente produzem qualidade aceitável quando usados com o Lync. Nós sugerimos uma meta de AvgSendListen MOS \> 3.6 para implementações com mais de 100 fluxos.) Atinja a meta identificando dispositivos problemáticos e corrija-os ou troque-os.

Em seguida, examine o dispositivo ou computador que processa o áudio para chamadas de usuário final. Uma métrica de qualidade de meta sugerida é AudioMic GlitchRate \> 1. Conforme você identificar as configurações de sistema ideais para os sistemas de usuários, defina uma configuração ideal de computador que inclua versões de driver.

Agora, examine o caminho de rede que um fluxo de áudio segue de um sistema de ponto de extremidade do Lync, que pode causar qualidade de áudio ruim. Se o áudio percorrer uma conexão de VPN, talvez você observe problemas de latência. Se um cliente do Lync interno não puder estabelecer um fluxo de mídia direto com outro cliente do Lync interno para uma chamada com dois participantes ou ponto a ponto, seu fallback será realizado para um caminho que retransmite por meio de um servidor Lync Edge, novamente, levando a problemas de latência, bem como um aumento do potencial de perda e tremulação. Nós sugerimos que você defina uma métrica de qualidade de 0% de Mídia sobre VPN. Durante a correção para atingir a meta definida, identifique as sub-redes com problema e investigue as regras de firewall, os modeladores de pacote e outras configurações de equipamento de rede relevantes.

Os pacotes IP podem usar TCP ou UDP. O TCP é ideal para fluxos de dados. O UDP não tem conexão e é mais eficiente para mídia, pois os mecanismos de recuperação de TCP não podem abordar a perda em mídia de tempo real. O Lync sempre prefere UDP, mas reverterá para o TCP se uma sessão UDP não puder ser estabelecida. As sessões de mídia sobre TCP apresentarão qualidade mais fraca do que sobre UDP. Nós recomendamos uma definição de qualidade de 0% de conexões sobre TCP. Durante a correção para atingir a meta definida, identifique sub-redes com problemas e investigue as regras de firewall, modeladores de pacote e outras configurações de equipamentos de rede relevantes.

## Gerenciamento de serviço

O gerenciamento de serviço está no estado final da CQM e o destino de todos os três caminhos. Para manter altos níveis de qualidade da chamada, monitore estas áreas:

1.  **Usuários** - As atividades de correção devem mostrar um aumento mensurável na satisfação do usuário. Você pode medir isso por meio de tíquetes de problemas ou outros mecanismos de feedback. Também é possível publicar métricas de qualidade.

2.  **Processo** - defina processos diários, semanais e mensais para operacionalizar a CQM. O monitoramento do ritmo começa em uma frequência mais alta durante a correção (diária) e passa para uma frequência mais baixa (mensal) conforme você estabiliza.

3.  **Ferramentas** - identifique ferramentas para medir e corrigir. Talvez você ache útil automatizar a execução de consultas CQM para oferecer suporte aos processos. A correção pode exigir mais ferramentas, por exemplo, para impor configurações padronizadas em elementos de rede ou solução de problemas de rede em fluxos fracos.

## Regras do jogo de tabuleiro

Use este pôster como uma referência a uma implementação de CQM ou como um jogo para praticar os conceitos. Para jogar, você precisará de um dado e das cartas fornecidas. Uma versão baixável das cartas está disponível para impressão em papel Avery 5871 padrão.

O jogo é para 3 jogadores. Há três caminhos que os jogadores podem usar para atingir a qualidade desejada e alcançar o estado de Gerenciamento de Serviço do centro: servidor, ponto de extremidade e final. Cada caminho tem paradas onde você declara metas de qualidade, atinge objetivos e mantém um aspecto do sistema. Coloque os cartões na área indicada acima e desenhe 5 cartões. Examine os cartões que você desenhou e coloque-os no segmento relevante do tabuleiro. Cada jogador se move pelos cartões em seu caminho passo a passo, declarando metas de qualidade, atingindo essas metas e mantendo os níveis de serviço. O jogo é concluído quando todos os jogadores chegam ao estado de Gerenciamento de Serviço do centro. Regras mais detalhadas são fornecidas com o download de cartões do jogo.

Para **declarar** uma meta de qualidade, examine os parâmetros aplicáveis a essa meta e declare em voz alta o que você vai aceitar ou não. Nós recomendamos os pontos iniciais, mas você deve tomar a decisão final. A exceção são os dados de KHI, em que os padrões estabelecidos pela Microsoft devem ser usados. Observe o pôster de KHI fornecido.

Para **atingir** metas no jogo, use os cartões fornecidos no lugar de dados de KHI e consultas de sistema. Se, no início do jogo, você não desenhou um cartão em relação a um determinado aspecto, continue depois dele. Se houver um cartão relevante, jogue o dado. Se jogou e obteve um número abaixo do indicado no cartão, você foi bem-sucedido. Se o número for o indicado no cartão ou estiver acima dele, pegue outro cartão. Se o cartão indicar que dois ou mais jogadores precisam jogar o dado, eles deverão fazer isso.

Para **manter** o jogo, declare em voz alta o plano de gerenciamento de serviço em relação a esse aspecto do ambiente do Lync.

## Consulte Também

#### Outros Recursos

[Guia de Rede do Lync Server](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[Key Health Indicators: A base para a manutenção de Lync Servers íntegros](http://go.microsoft.com/fwlink/?linkid=391838)  
[Metodologia de qualidade de chamada do Lync](http://go.microsoft.com/fwlink/?linkid=391841)

