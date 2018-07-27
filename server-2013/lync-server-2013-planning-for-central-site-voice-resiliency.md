---
title: 'Lync Server 2013: Planejamento de resiliência de voz do site central'
TOCTitle: Planejamento de resiliência de voz do site central
ms:assetid: 52dd0c3e-cd3c-44cf-bef5-8c49ff5e4c7a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398347(v=OCS.15)
ms:contentKeyID: 49306713
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento de resiliência de voz do site central no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Cada vez mais, as empresas possuem vários sites espalhados por todo o mundo. Para qualquer solução de resiliência do Enterprise Voice, é crucial manter os serviços de emergência, o acesso à assistência técnica e a capacidade de realizar tarefas corporativas essenciais quando um site central está fora de serviço. Quando um site central torna-se indisponível, as seguintes condições devem ser atendidas:

  - O failover de voz deve ser fornecido.

  - Os usuários que normalmente se registram no Pool de Front-Ends no site central devem ser capazes de se registrarem com um Pool de Front-Ends. alternativo. Isso pode ser feito criando vários registros SRV de DNS, cada qual resolve para um Pool de diretores ou um Pool de Front-Ends em cada um dos seus sites centrais. Você pode ajustar a prioridade e os pesos dos registros SRV para que os usuários que são servidos pelo site central obtenham o Diretor e o Pool de Front-Ends correspondente antes daqueles em outros registros SRV.

  - As chamadas de usuários localizados em outros sites e para eles devem ser roteadas para a PSTN.

Este tópico descreve a solução recomendada para proteger a resiliência de voz do site central.

## Arquitetura e topologia

O planejamento para a resiliência de voz em um site central requer uma compreensão básica do papel central desempenhado pelo Registrador do Lync Server 2013 na habilitação do failover de voz. O Registrador do Lync Server é uma função de servidor que permite a autenticação e o registro de cliente e fornece os serviços de roteamento. Ele reside junto com outros componentes em um Servidor Standard Edition, Servidor Front-End, Diretor ou Aparelho de Filial Persistente. Um pool de registradores consiste em Serviços de Registrador sendo executados no Pool de Front-Ends e que residem no mesmo site. O Pool de Front-Ends deve ter balanceamento de carga. O balanceamento de carga DNS é recomendado, mas o balanceamento de carga de hardware é aceitável. Um cliente do Lync descobre o Pool de Front-Ends por meio do seguinte mecanismo de descoberta.

1.  Registro SRV de DNS

2.  Serviço Web de Descoberta Automática (novo no Lync Server 2013)

3.  Opção 120 do DHCP

Após o cliente do Lync conectar-se ao Pool de Front-Ends, ele é direcionado pelo balanceador de carga para um do Servidores Front-End no pool. Esse Servidor Front-End, um de cada vez, redireciona o cliente para um Registrador preferencial no pool.

Cada usuário habilitado para o Enterprise Voice é atribuído a um determinado pool de Registradores, que se torna o pool de Registradores principal do usuário. Em um determinado site, centenas ou milhares de usuários normalmente compartilham um único pool primário de Registradores. Para considerar o consumo de recursos do site central por qualquer usuário do site de filial que depende do site central para presença, conferência ou failover, recomendamos considerar cada usuário do site de filial como se o usuário fosse um usuário registrado no site central. Não existem limites atualmente para o número de usuários de sites de ramificação, incluindo usuários registrados com um Aparelho de Filial Persistente.

Para garantir a resiliência de voz em caso de falha do site central, o pool de Registradores primário deve ter um único pool de Registradores de backup designado localizado em outro site. O backup pode ser configurado usando as configurações de resiliência do Construtor de Topologias. Supondo que há um link WAN resistente entre dois sites, os usuários cujo pool de Registradores primário não está mais disponível são direcionados automaticamente ao pool de Registradores de backup.

As seguintes etapas descrevem o processo de descoberta e o registro de cliente:

1.  Um cliente descobre o Lync Server por meio de registros SRV do DNS. No Lync Server 2013, os registros SRV do DNS podem ser configurados para retornar mais de um FQDN para a consulta SRV do DNS. Por exemplo, se a empresa Contoso possui três sites centrais (América do Norte, Europa e Ásia-Pacífico) e um pool de Diretores em cada site central, os registros SRV do DNS podem apontar para os FQDNs do pool de Diretores em cada um dos três locais. Como o pool de Diretores em um dos locais está disponível, o cliente pode se conectar ao primeiro salto do Lync Server.
    
    > [!NOTE]  
    > Usar um Pool de diretores é opcional. Um Pool de Front-Ends pode ser usado em vez disso.

2.  O Pool de diretores informa o cliente do Lync sobre o pool de registradores primário e o pool de registradores de backup.

3.  O cliente do Lync tenta se conectar primeiro ao pool de registradores primário do usuário. Se o pool de registradores primário estiver disponível, o Registrador aceitará o registro. Se o pool de registradores primário não estiver disponível, o cliente do Lync tentará se conectar ao pool de registradores de backup. Se o pool de registradores de backup estiver disponível e tiver determinado que o pool de registradores primário do usuário não está disponível (detectando a falta de pulsação para um intervalo especificado de failover), o pool de registradores de backup aceitará o registro do usuário. Depois que o Registrador de backup detecta que o Registrador primário está novamente disponível, o pool de registradores de backup redirecionará os clientes do Lync failover para seu pool principal.

A figura a seguir mostra a topologia recomendada para garantir a resiliência do site central. Os dois sites são conectados por um link WAN resistente. Se o site central ficar indisponível, os usuários atribuídos a esse pool serão direcionados para o site de backup do registro.

**Topologia recomendada para a resiliência de voz do site central**

![Topologia para resiliência de voz do site central](images/Gg398347.19ea3e74-8a5c-488c-a34e-fc180ab9a50a(OCS.15).jpg "Topologia para resiliência de voz do site central")

## Requisitos e recomendações

Os seguintes requisitos e recomendações para a implementação de resiliência de voz do site central são apropriados para a maioria das organizações:

  - Os sites nos quais residem os pools de Registradores primário e de backup devem estar conectados por um link WAN resistente.

  - Cada site central deve conter um pool de Registradores que consiste em um ou mais Registradores.

  - Cada pool de Registradores deve ser o balanceamento de carga usando o balanceamento de carga DNS ou o balanceamento de carga de hardware. Para obter informações mais detalhadas sobre a configuração de seu balanceamento de carga, consulte [Requisitos de balanceamento de carga para Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

  - Cada usuário deve ser atribuído a um pool de Registradores primário usando o cmdlet Shell de Gerenciamento do Lync Server**set-CsUser** ou o Painel de Controle do Lync Server.

  - O pool de Registradores primário deve ter um único pool de Registrador de backup localizado em um site central diferente.

  - O pool de Registradores primário deve ser configurado para failover para o pool de Registradores de backup. Por padrão, o Registrador primário é definido para fazer failover para o pool de Registradores backup após um intervalo de 300 segundos. Você pode alterar esse intervalo usando o Construtor de Topologias do Lync Server 2013.

  - Configure uma rota de failover, como descrito no tópico [Configurando uma rota de failover no Lync Server 2013](lync-server-2013-configuring-a-failover-route.md) na documentação de Planejamento. Ao configurar a rota, especifique um gateway que está localizado em um site diferente do gateway especificado na rota primária.

  - Se o site central continha o servidor de gerenciamento primário e o site pode ficar inoperante por um longo período, você precisa reinstalar suas ferramentas de gerenciamento no local de backup; caso contrário, você não poderá alterar nenhuma configuração de gerenciamento.

## Dependências

O Lync Serverdepende dos seguintes componentes de software e infraestrutura para garantir a resiliência de voz:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Componente</strong></p></td>
<td><p><strong>Funcional</strong></p></td>
</tr>
<tr class="even">
<td><p>DNS</p></td>
<td><p>Resolvendo registros SRV e registros A para conectividade de servidor-servidor e servidor-cliente</p></td>
</tr>
<tr class="odd">
<td><p>Exchange e Serviços Web do Exchange (EWS)</p></td>
<td><p>Armazenamento de contatos; dados do calendário</p></td>
</tr>
<tr class="even">
<td><p>Unificação de Mensagens do Exchange e Serviços Web do Exchange</p></td>
<td><p>Logs de chamada, lista de caixas postais, caixa postal</p></td>
</tr>
<tr class="odd">
<td><p>Opções 120 de DHCP</p></td>
<td><p>Se o servidor DNS não estiver disponível, o cliente tentará usar a Opção 120 de DHCP para descobrir o Registrador. Para que isso funcione, um servidor DHCP deve ser configurado ou o DHCP do Lync Server 2013 deve ser ativado. Para obter detalhes, consulte os Requisitos de hardware e software para resiliência de site de filial na seção <a href="lync-server-2013-branch-site-resiliency-requirements.md">Requisitos de resiliência do site da filial para Lync Server 2013</a>.</p></td>
</tr>
</tbody>
</table>


## Recursos de voz persistente

Se os requisitos e recomendações anteriores foram implementadas, os seguintes recursos de voz serão fornecidos pelo pool de Registradores de backup:

  - Chamadas PSTN em saída

  - Chamadas PSTN de entrada, se o provedor oferecer suporte à capacidade de fazer failover para um site de backup

  - Chamadas corporativas entre usuários em ambos, o mesmo site e entre dois sites diferentes

  - Manipulação básica de chamadas, incluindo espera, recuperação e transferência de chamadas

  - Mensagens instantâneas entre duas pessoas e compartilhamento de áudio e vídeo entre usuários no mesmo site

  - Encaminhamento de chamadas, toque simultâneo dos pontos de extremidade, delegação de chamada e serviços de chamada de equipe, mas somente se as duas partes da delegação de chamadas ou todos os membros da equipe estiverem configurados no mesmo site.

  - Os clientes e telefones existentes continuam funcionando.

  - Gravação de detalhes da chamada (CDR)

  - Autenticação e autorização

Dependendo de como são configurados, os seguintes recursos de voz podem ou não funcionar quando um site central primário está fora de serviço:

  - Depósito e recuperação de caixa postal
    
    Se você desejar disponibilizar o UM do Exchange quando o site central primário estiver fora de serviço, deverá fazer o seguinte:
    
      - Altere os registros SRV do DNS para que os servidores do UM do Exchange no site central apontem para os servidores de backup do UM do Exchange em outro site.
    
      - Configure o plano de discagem do UM do Exchange de cada usuário para incluir os servidores do UM do Exchange no site central e no site do backup, mas designe os servidores do UM do Exchange de backup como desabilitados. Se o site primário ficar indisponível, o administrador do Exchange terá que marcar os servidores do UM do Exchange no site de backup como habilitados.
    
    Se nenhuma das soluções anteriores for possível, o UM do Exchange não estará disponível caso o evento do site central se torne indisponível.

  - Conferência de todos os tipos
    
    Um usuário que realizou failover para um site de backup pode ingressar em uma conferência que é criada ou hospedada por um organizador cujo pool está disponível, mas não pode criar ou hospedar uma conferência no seu próprio pool primário, que não está mais disponível. Da mesma forma, outros usuários não podem ingressar em conferências hospedadas no pool primário do usuário afetado.

Os seguintes recursos de voz não funcionam quando um site central primário está fora de serviço:

  - Atendedor Automático de Conferência

  - Roteamento baseado em DND e presença

  - Atualização de configurações de encaminhamento de chamadas

  - Serviço do Grupo de Resposta e Estacionamento de Chamada

  - Provisionamento de novos telefones e clientes

  - Pesquisa na Web do Catálogo de Endereços

## Consulte Também

#### Outros Recursos

[Planejamento de resiliência de voz no site da filial no Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md)

