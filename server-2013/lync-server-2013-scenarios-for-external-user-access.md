---
title: 'Lync Server 2013: Cenários de acesso de usuário externo'
TOCTitle: Cenários de acesso de usuário externo
ms:assetid: 25697446-b045-4d12-9b1c-47f694b4f224
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425727(v=OCS.15)
ms:contentKeyID: 49306153
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cenários de acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Conceder acesso ao usuário externo para o Lync Server 2013 exige a implantação de pelo menos um Servidor de Borda e um proxy inverso em sua rede de perímetro. Opcionalmente, você pode implantar um Diretor ou Pool de diretores na sua rede interna.

Se você precisar de mais capacidade do que um único Servidor de Borda pode oferecer ou se precisa de maior disponibilidade para sua implantação do Servidor de Borda, é possível configurar o balanceamento de carga ou implantar vários Servidores de Borda em um pool de carga balanceada. Se sua organização possui vários centros de dados, é possível ter implantações do Servidor de Borda ou Pool de borda em mais de um local. No entanto, apenas uma das implantações do Servidor de Borda podem ser designadas como uma rota de federação.

Esta seção define os cenários para implantações do Servidor de Borda e mapeia as seções de planejamento para possíveis cenários. Por exemplo, se sua implantação exige alta disponibilidade, a federação com contatos XMPP e mobilidade Lync, você deve selecionar as entradas correspondentes na tabela a seguir que poderia satisfazer estes requisitos e usar as seções de planejamento referenciadas para definir sua implantação, conforme ilustrado no seguinte gráfico.

**Processo de seleção do cenário de implantação do Servidor de Borda**

![Fluxograma de implantação de exemplo](images/Gg425727.007100b5-6923-4909-bfd7-897d8867205f(OCS.15).jpg "Fluxograma de implantação de exemplo")

Usando este processo, é possível planejar e documentar a configuração de todos os recursos em potencial que você pretende implantar para seus usuários. No entanto, é possível adicionar serviços de federação e mobilidade após ter implantado o Servidor de Borda e confirmar a operação correta antes de adicionar outros recursos. O processo de adicionar recursos a uma implantação do Servidor de Borda existente é abordada na seção Implantação. Para obter detalhes sobre a implantação, consulte [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) Ao incluir planejamento para estes recursos durante o processo de planejamento inicial, é possível preparar para os requisitos de DNS, firewall e certificado para recursos adicionados, que permite adquirir certificados e configurar os requisitos DNS e porta/protocolo antecipadamente.


> [!TIP]
> Se você estiver planejando instalar o Servidores de Borda e o proxy inverso e adicionar recursos posteriormente (por exemplo, federação e mobilidade), determine quais certificados você precisará para todos os serviços após a implantação. Planejamento e aquisição de certificados para todos os recursos antecipadamente, implantado inicialmente ou não, evita que você precise solicitar novos certificados para satisfazer os requisitos de federação (isto é, no Servidores de Borda) ou o proxy inverso (isto é, serviços de mobilidade).



> [!NOTE]  
> Todos os serviços de borda são executados em cada Servidor de Borda. Os serviços não podem ser divididos entre dois Servidores de Borda diferentes. Se você implantar um Pool de borda para escalabilidade, todos os serviços de borda são implantados em cada Servidor de Borda no pool. Federação XMPP, Office Communications Server e federação Lync Server, conectividade de IM público e mobilidade do cliente são serviços adicionais que podem ser implantados após implantar seu primeiro Servidor de Borda ou Pool de borda. Serviços de mobilidade é o recurso que usa proxy inverso. A instalação de serviços de mobilidade não adicionará recursos para seu Servidores de Borda, mas exigirá a reconfiguração do seu proxy inverso. A coluna <strong>objetivo de instalação</strong> que lista estes recursos oferece diretrizes de planejamento na coluna associada em <strong>Seção ou seções de planejamento do Servidor de Borda</strong> para o planejamento simultâneo destes recursos para ser implantado quando o Servidores de Borda é instalado e configurado.

## Identificando e mapeando suas metas de implantação


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Objetivo de instalação</th>
<th>Documentação de planejamento do Servidor de Borda</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Você decidiu que um único servidor é suficiente para serviços de Borda em sua infraestrutura. Você também pretende usar endereços IP privados para interfaces externas do servidor de Borda com NAT para a Internet.</p>
<p>Use esta seção de planejamento se estiver implantando um único Servidor de Borda em seu perímetro. Você implantará um Servidor de Borda com endereço IP privado atribuído ao Servidor de Borda e usará o NAT para oferecer endereços IP públicos para usuários externos na Internet.</p></td>
<td><p><a href="lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md">Única borda consolidada com endereços IP privados e NAT no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Você decidiu que um único servidor é suficiente para serviços de Borda em sua infraestrutura. Você também pretende usar endereços IP públicos para interfaces externas do servidor de Borda para a Internet.</p>
<p>Use esta seção de planejamento se estiver implantando um único Servidor de Borda em seu perímetro. Você implantará um Servidor de Borda com endereços IP públicos atribuídos ao Servidor de Borda. Ao invés do NAT, você usará o roteamento neste cenário. O endereço IP público atual do Servidor de Borda são disponibilizados para conexões externas do usuário.</p></td>
<td><p><a href="lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md">Única borda consolidada com endereços IP públicos no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Você decidiu que alta disponibilidade dos serviços de Borda é importante para seus usuários e irá implantar dois ou mais Servidores de Borda neste pool. Você também pretende usar endereços IP privados para as interfaces externas do Servidor de Borda com NAT para a Internet.</p>
<p>Use esta seção de planejamento se estiver implantando um pool do Servidores de Borda em seu perímetro. Você implantará o Servidores de Borda com os endereços IP privados atribuídos ao Servidor de Borda, usando balanceamento de carga DNS para distribuir comunicação no pool. Você usará NAT para oferecer endereços IP públicos para usuários externos na Internet.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md">Borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Você decidiu que alta disponibilidade dos serviços de Borda é importante para seu usuário e irá implantar dois ou mais Servidores de Borda neste pool. Você também pretende usar endereços IP públicos para as interfaces externas do Servidor de Borda na Internet.</p>
<p>Use esta seção de planejamento se estiver implantando um pool do Servidores de Borda em seu perímetro. Você implantará o Servidores de Borda com endereços IP públicos atribuídos ao Servidor de Borda, usando balanceamento de carga DNS para distribuir comunicação entre o pool. Ao invés do NAT, você usará o roteamento para oferecer endereços IP públicos para usuários externos na Internet.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md">Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Você decidiu que alta disponibilidade dos serviços de Borda é importante para seus usuários e implantará dois ou mais Servidores de Borda neste pool usando um balanceador de carga de hardware.</p>
<p>Use esta seção de planejamento se estiver implantando um pool de Servidores de Borda em seu perímetro. Você implantará o Servidores de Borda com endereços IP públicos atribuídos ao Servidor de Borda, usando balanceadores de carga de hardware para distribuir comunicações entre o pool. Ao invés do NAT, você usará o roteamento para oferecer endereços IP públicos para usuários externos na Internet.</p></td>
<td><p><a href="lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md">Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Os cenários de federação permite planejar o recurso que irá estender os tipos de parceiros que os usuários podem se comunicar.</p><ul><li><p>Federação Lync Server</p></li><li><p>Federação Office Communications Server</p></li><li><p>Conectividade a redes públicas de mensagens instantâneas</p></li><li><p>Federação XMPP</p></li></ul></td>
<td><p>Planejamento para cenários de federação</p><ul><li><p><a href="lync-server-2013-planning-for-lync-server-and-office-communications-server-federation.md">Planejamento para Federação do Servidor Lync Server e Office Communications</a></p></li><li><p><a href="lync-server-2013-planning-for-public-instant-messaging-connectivity.md">Planejamento para conectividade para redes públicas de mensagens instantâneas no Lync Server 2013</a></p></li><li><p><a href="lync-server-2013-planning-for-extensible-messaging-and-presence-protocol-xmpp-federation.md">Planejamento para Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP) no Lync Server 2013</a></p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Serviços de mobilidade são oferecidos através do proxy inverso. Os serviços que permitem a mobilidade para usuários externos são implantados no Servidor Front-End ou Pool de Front-Ends. Você cria ou modifica regras de publicação existentes no proxy inverso para habilitar os serviços de mobilidade para seus usuários externos.</p></td>
<td><p><a href="lync-server-2013-planning-for-mobility.md">Planejamento para mobilidade no Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>



> [!TIP]
> Nas seguintes seções Cenários existem arquiteturas de referência, DNS de exemplo, definições de porta/protocolo e requisitos de certificado. Também inclui diagramas para seu DNS, definições de porta/protocolo e necessidades de certificado. Os diagramas oferecerão um modelo para você preencher e distribuir para outras equipes (por exemplo, a Equipe de Rede da sua organização, Equipe de Infraestrutura de Chave Pública e Equipe de Implantação do Servidor). O objetivo do diagrama é melhorar a comunicação e garantir o sucesso ao comunicar os elementos de configuração obrigatórios do Servidor de Borda para pessoas que irão realizar o trabalho de configuração. Recomendamos que você use os diagramas e as arquiteturas de referência associados para planejar sua implantação.


