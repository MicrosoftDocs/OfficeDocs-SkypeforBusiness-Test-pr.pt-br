---
title: Balanceamento de carga DNS no Lync Server 2013
TOCTitle: Balanceamento de carga DNS no Lync Server 2013
ms:assetid: 7ed0ed20-33ad-4253-926d-21d392590ae7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398634(v=OCS.15)
ms:contentKeyID: 49307249
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Balanceamento de carga DNS no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server apresenta o balanceamento de carga DNS, uma solução de software que pode reduzir muito a sobrecarga administrativa para o balanceamento de carga na sua rede. O balanceamento de carga DNS equilibra o tráfego de rede exclusivo do Lync Server, como o tráfego SIP e o tráfego de mídia.

Se implantar o balanceamento de carga DNS, a sobrecarga da administração da sua organização para os balanceadores de carga de hardware será bastante reduzida. Além disso, a solução complexa de problemas relacionados à configuração incorreta de balanceadores de carga de tráfego SIP será eliminada. Você também pode impedir as conexões de servidor para que seja possível assumir servidores offline. O balanceamento de carga DNS também garante que os problemas de balanceador de carga de hardware não afetem elementos do tráfego SIP, como o roteamento básico de chamada.

Se você usar o balanceamento de carga DNS, também poderá adquirir os balanceadores de carga de hardware de custo mais baixo do que se usasse os balanceadores de carga de hardware para todos os tipos de tráfego. Você deve usar balanceadores de carga que passaram pelo teste de qualificação de interoperabilidade com o Lync Server. Para obter detalhes sobre testes de interoperabilidade do balanceador de carga, consulte "Parceiros de balanceador de carga do Lync Server 2010" em <http://go.microsoft.com/fwlink/?linkid=202452>.

O balanceamento de carga DNS é suportado para pools de Front-Ends, pools de Servidor de Borda, pools do Diretor e pools autônomos do Servidor de Mediação.

## Balanceamento de carga DNS em pools do Diretor e pools de Front-End

Você pode usar o balanceamento de carga DNS para o tráfego SIP em pools de Front-End e pools do Diretor. Com o balanceamento de carga DNS implantado, você precisará usar também os balanceadores de carga de hardware para esses pools, mas somente para tráfego HTTPS de cliente-servidor. O balanceador de carga de hardware é usado para tráfego HTTPS de clientes nas portas 443 e 80.

Embora você ainda precisará de balanceadores de carga de hardware para estes pools, sua configuração e administração será principalmente para o tráfego HTTPS, aos quais os administradores dos balanceadores de carga de hardware estão acostumados.

## Balanceamento de carga DNS e suporte aos clientes e servidores mais antigos

O balanceamento de carga DNS oferece suporte a failover automático apenas para servidores executando o Lync Server 2013 ou Lync Server 2010 e clientes do Lync 2013 e Lync 2010. Versões anteriores de clientes e o Office Communications Server ainda podem se conectar a pools de balanceamento de carga DNS, mas se não podem fazer uma conexão com o primeiro servidor para o qual o balanceamento de carga DNS os refere, não conseguem fazer failover para outro servidor no pool.

Além disso, se você estiver usando o UM do Exchange, apenas o Exchange 2010 SP1 ou o pacote de serviços mais recente possui o suporte interno para o balanceamento de carga DNS do Lync Server. Se você usar uma versão anterior do Exchange, não terá recursos de failover para esses cenários UM do Exchange:

  - Reproduzindo a caixa postal do Enterprise no telefone

  - Transferindo chamadas de um Atendedor Automático UM do Exchange

Todos os outros cenários UM do Exchange funcionarão corretamente.

## A implantação do balanceamento de carga DNS em pools do Diretor e pools de Front-End

A implantação do balanceamento DNS de carga nos pools de Front-Ends e pools do Diretor requer a execução de algumas etapas extras com os registros DNS e FQDNs.

  - Um pool que usa o balanceamento de carga DNS deve ter dois FQDNs: o pool FQDN normal usado pelo balanceamento de carga DNS (como pool01.contoso.com) e resolve para os IPs físicos dos servidores no pool e outro FQDN para os serviços Web do pool (como web01.contoso.com), que resolve para o endereço IP virtual do pool.
    
    Em Construtor de Topologias, se você deseja implantar um pool, para criar o FQDN extra para os serviços Web do pool você deve marcar a caixa de seleção **Substituir o FQDN do pool de Serviços Web interno** e digitar o FQDN na página **Especificar as URLs dos Serviços Web para este pool**.

  - Para suportar o FQDN usado pelo balanceamento de carga DNS, você deve provisionar o DNS para resolver o FQDN do pool (como pool01.contoso.com) para os endereços IP de todos os servidores no pool (por exemplo, 192.168.1.1, 192.168.1.2 e assim por diante). Você deve incluir somente os endereços IP dos servidores que estão atualmente implantados.
    

    > [!WARNING]
    > Se você tiver mais de um Pool de Front-Ends ou Servidor Front-End, os serviços FQDN de Web externo devem ser exclusivos. Por exemplo, se você definir os serviços FQDN de Web externo de um Servidor Front-End como <STRONG>pool01.contoso.com</STRONG>, você não pode usar <STRONG>pool01.contoso.com</STRONG> para outro Pool de Front-Ends ou Servidor Front-End. Se você também estiver implantando Diretores, os serviços FQDN de Web externo definidos por qualquer Diretor ou Pool de diretores devem ser exclusivos de qualquer outro Diretor ou Pool de diretores, além de qualquer Pool de Front-Ends ou Servidor Front-End. Se você decidir ultrapassar os serviços de web internos com um FQDN autodefinido, cada FQDN deve ser exclusivo a partir de qualquer outro Pool de Front-Ends, Diretor ou um Pool de diretores.



## Balanceamento de carga DNS em pools de servidor de borda

Você pode implantar o balanceamento de carga DNS em pools de servidor de borda. Se você fizer isso, deve estar ciente de algumas considerações.

Usar o balanceamento de carga DNS nos servidores de borda provoca uma perda da capacidade de failover nos seguintes cenários:

  - Federação com organizações que executam versões anteriores do Office Communications Server liberado antes de Lync Server 2010.

  - Troca de mensagens instantâneas com usuários de serviços públicos de mensagens instantâneas (IM), AOLand Yahoo\!, além de provedores e servidores com base em XMPP, como o Google Talk.
    
    > [!IMPORTANT]  
    > <ul>    
> 
> <li><p>O Google Talk atualmente é o único parceiro XMPP.</p></li>    
> 
> 
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para Conectividade a Redes Públicas de Mensagens Instantâneas do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada uma data de descontinuação para o AOL e o Yahoo! em junho de 2013. Para ver detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>    </ul>


Esses cenários funcionarão desde que todos os servidores de borda no pool estejam funcionando. Se um servidor de borda estiver disponível, as solicitações enviadas para esses cenários falharão, em vez de rotear para outro servidor de borda.

Se estiver utilizando o UM do Exchange, você deve utilizar um pacote mínimo do Exchange 2013 para obter suporte com relação ao balanceamento de carga do Lync Server DNS no Edge. Se você utilizar uma versão mais antiga do Exchange, seus usuários remotos não terão recursos de failover para esses cenários UM do Exchange:

  - Reproduzindo a caixa postal do Enterprise no telefone

  - Transferindo chamadas de um Atendedor Automático UM do Exchange

Todos os outros cenários UM do Exchange funcionarão corretamente.

A interface de Borda interna e externa devem usar o mesmo tipo de balanceamento de carga. Não é possível usar o balanceamento de carga DNS na interface de Borda e o balanceamento de carga de hardware na outra interface de Borda.

## Implantando o Balanceamento de Carga DNS em Pools de Servidor de Borda

Para implantar o balanceamento de carga DNS na interface externa do seu pool de Servidor de Borda, são necessárias as seguintes entradas DNS:

  - Para o serviço de Borda de Acesso, você precisa de uma entrada para cada servidor no pool. Cada entrada deve resolver o FQDN do serviço de Borda de Acesso (por exemplo, sip.contoso.com) para o endereço IP do serviço de Borda de Acesso em um dos Servidores de Borda no pool.

  - Para o serviço de Borda de Conferência Web, você precisa de uma entrada para cada servidor no pool. Cada entrada deve resolver o FQDN do serviço de Borda de Conferência Web (por exemplo, webconf.contoso.com) para o endereço IP do serviço de Borda de Conferência Web em um dos Servidores de Borda no pool.

  - Para o serviço de Borda de A/V, você precisa de uma entrada para cada servidor no pool. Cada entrada deve resolver o FQDN do serviço de Borda de A/V (por exemplo, av.contoso.com) para o endereço IP do serviço de Borda de A/V em um dos Servidores de Borda no pool.

Para implantar o balanceamento de carga DNS na interface interna do pool de Servidor de Borda, você deve adicionar um registro DNS A, que resolve o FQDN interno do pool do Servidor de Borda para o endereço IP de cada servidor do pool.

## Usando o balanceamento de carga DNS em pools do servidor de mediação

Você pode usar um balanceamento de carga DNS em pools do Servidor de Mediação autônomos. Todo o tráfego SIP e de mídia é balanceado pelo balanceamento de carga DNS.

Para implantar o balanceamento de carga DNS em um pool do Servidor de Mediação, vcê deve provisionar o DNS para resolver o FQDN do pool (por exemplo, mediationpool1.contoso.com) para os endereços IP de todos os servidores no pool (por exemplo, 192.168.1.1, 192.168.1.2 e assim por diante).

## Bloquer o Tráfego a um Servidor com Balanceamento de Carga DNS

Se você usar um balanceamento de carga DNS e precisar bloquear o tráfego para um computador específico, não é suficiente apenas remover as entradas do endereço IP do Pool FQDN. Você deve remover a entrada DNS do computador.

Observe que, para tráfego entre servidores, Lync Server 2013 usa balanceamento de carga por topologia. Os servidores lêem a topologia publicada no Repositório de Gerenciamento Central para obter os FQDNs dos servidores na topologia e distribuir automaticamente o tráfego entre os servidores. Para bloquear um servidor de receber tráfego entre servidores, você deve remover o servidor da topologia.

