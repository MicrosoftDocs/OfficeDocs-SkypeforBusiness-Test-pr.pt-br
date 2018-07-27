---
title: 'Lync Server 2013: Definir um Servidor de Mediação no Construtor de Topologia'
TOCTitle: Definir um Servidor de Mediação no Construtor de Topologia
ms:assetid: 59d8f5ba-5064-4ea5-b4bf-2b9736e0fedd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398391(v=OCS.15)
ms:contentKeyID: 49306801
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir um Servidor de Mediação no Construtor de Topologia no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-25_

Siga as etapas deste tópico para usar o Construtor de Topologias para definir um Servidor de Mediação autônomo ou um pool colocado com um Pool de Front-Ends em um local no qual o Enterprise Voice ainda não tenha sido implantado.

Você pode definir uma topologia usando uma conta que seja membro do grupo Administradores.

## Definir o Servidor de Mediação colocado em um Pool de Front-Ends

Siga as etapas deste tópico para usar o Construtor de Topologias para definir um Servidor de Mediação colocado em um Pool de Front-Ends em um local no qual o Enterprise Voice ainda não tenha sido implantado.

## Para adicionar um Servidor de Mediação a um Pool de Front-Ends

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Em Construtor de Topologias, na árvore de console, expanda o nome do site para o qual você deseja definir um Pool de Front-Ends.

3.  Na árvore do console, clique com o botão direito do mouse no tipo de Pool de Front-Ends desejado e clique em **Novo Pool de Front-Ends..** .

4.  Navegue pelo assistente **Definir Novo Pool de Front-Ends** até chegar à página **Selecionar funções de servidor colocadas** .

5.  Em **Selecionar funções de servidor colocadas** , marque a opção **Colocar Servidor de Mediação**.
    
    > [!NOTE]  
    > <ul>    
> <li><p>Se o tipo de Pool de Front-Ends que você selecionou for o Enterprise Edition, o componente do Servidor de Mediação será instalado em todos os Servidores Front-End desse Pool de Front-Ends.</p></li>    
> 
> <li><p>O <strong>Pool do próximo salto</strong> usado pelo Servidor de Mediação será o Pool de Front-Ends no qual o Servidor de Mediação será colocado.</p></li>    
> 
> 
> <li><p>O <strong>Pool de Borda</strong> usado pelo Servidor de Mediação será o mesmo Pool de borda associado ao Pool de Front-Ends no qual o Servidor de Mediação é colocado.</p></li>    </ul>


6.  Clique em **Tornar Padrão** para usar esse Pool de Front-Ends para encaminhar as chamadas de Microsoft Office Communications Server 2007 R2 para o PSTN.

7.  Clique em **Concluir** quando tiver terminado de associar um ou mais pares ao Pool de Front-Ends.
    
    > [!NOTE]  
    > Antes de prosseguir para a próxima etapa do processo de implantação do Enterprise Voice, verifique se o pool de Servidor de Mediação (ou seja, o Pool de Front-Ends com o componente do Servidor de Mediação colocado) está usando os FQDNs que você especificou.

8.  Em seguida, siga os procedimentos em [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md) na documentação do Guia de Implantação para adicionar o Servidor de Mediação à sua topologia antes de prosseguir para a próxima etapa de modificação das portas de escuta do Servidor de Mediação, se necessário. Você deve publicar sua topologia sempre que usar o Construtor de Topologias para definir ou modificá-la.

## Definir o Servidor de Mediação autônomo

Siga as etapas deste tópico para usar o Construtor de Topologias para definir um Servidor de Mediação autônomo ou um pool em um site no qual o Enterprise Voice ainda não tenha sido implantado.

Se você já implantou o Servidor de Mediação colocado nos Pools de Front-Ends desse site, pode pular esta seção e a [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md) e ir para a [Configurando troncos no Lync Server 2013](lync-server-2013-configuring-trunks.md).

> [!NOTE]  
> Esta seção pressupõe que você tenha configurado pelo menos um Pool de Front-Ends, conforme descrito em <a href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013</a> e em <a href="lync-server-2013-publish-the-topology.md">Publicar a topologia no Lync Server 2013</a> na documentação do Guia de Implantação.

## Para adicionar um Servidor de Mediação

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Em Construtor de Topologias, na árvore de console, expanda o nome do site para o qual você deseja definir um Servidor de Mediação.

3.  Na árvore do console, clique com o botão direito do mouse no nó **Pools de mediação** e clique em **Pool do servidor de mediação**.

4.  Em **Definir Novo Pool de Mediação** , digite o FQDN (nome de domínio totalmente qualificado) do Servidor de Mediação.

5.  Em seguida, siga um destes procedimentos:
    
      - Se você desejar implantar vários Servidor de Mediação no pool para fornecer alta disponibilidade, selecione **Pool de vários computadores** .
        
        > [!NOTE]  
        > Você deve implantar o balanceamento de carga DNS para oferecer suporte a pools de Servidor de Mediação com vários Servidor de Mediação. Para obter detalhes, consulte a seção &quot;Usando o balanceamento de carga DNS em pools de Servidor de Mediação&quot; de <a href="lync-server-2013-dns-load-balancing.md">Balanceamento de carga DNS no Lync Server 2013</a> na documentação de planejamento.    
      - Se você desejar implantar somente um Servidor de Mediação do pool porque não precisa alta disponibilidade, selecione **Pool de Computador Único** . Ignore a etapa seguinte.

6.  Se você selecionou **Pool de Vários Computadores** na etapa anterior, no item **Definir os computadores neste pool** , clique em **FQDN do Computador** , digite o FQDN de cada servidor no pool e clique em **Adicionar** . Repita essa etapa para todos os outros Servidor de Mediação que você deseja adicionar ao pool. Quando tiver definido todos os computadores no pool, clique em **Avançar** .

7.  Na página **Selecionar o próximo salto** , clique em **Pool de próximo salto** , clique no FQDN do pool de front-ends que usará o Servidor de Mediação e clique em **Avançar** .

8.  Na página **Selecionar um Servidor de Borda** , execute um destes procedimentos:
    
      - Se você desejar fornecer a conectividade PSTN a usuários externos habilitados para o Enterprise Voice, em **Selecionar Pool de Borda usado por este Servidor de Mediação** , clique no FQDN do pool de Servidor de Borda que usará esse pool de Servidor de Mediação para fornecer conectividade PSTN aos usuários externos e clique em **Avançar** .
    
      - Se você não pretende habilitar usuários externos para o Enterprise Voice ou se não deseja fornecer conectividade PSTN aos usuários quando eles estiverem fora da rede interna, clique em **Avançar** .

9.  Em seguida, siga os procedimentos em [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md) na documentação de Implantação para adicionar o Servidor de Mediação à topologia. Você deve publicar a sua topologia sempre que usar o Construtor de Topologias para criar ou modificar a topologia de modo que os dados possam ser usados para instalar os arquivos nos servidores que estejam executando o Lync Server. Prossiga para as próximas etapas para modificar as portas de escuta do Servidor de Mediação, se necessário.

## Definir as portas de escuta do Servidor de Mediação

Siga as etapas deste tópico para usar o Construtor de Topologias para definir as portas de escuta a partir das quais um Servidor de Mediação ou um pool aceitará conexões de entrada de um par de gateway.

## Para modificar as portas de escuta do Servidor de Mediação

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  No Construtor de Topologias, na árvore do console, expanda o nó **Pools de mediação** e clique com o botão direito do mouse no Servidor de Mediação criado anteriormente.

3.  Por padrão, as portas de escuta SIP no Servidor de Mediação são 5070 para o tráfego TLS do Lync Server e 5067 para o tráfego TLS de pares (gateways, PBXs ou SBCs). A porta TCP é desabilitada por padrão. Você deve habilitar a porta TCP se tiver gateways que não oferecem suporte a TLS.

4.  Especifique o intervalo desejado de portas de escuta TLS ou TCP a partir das quais o Servidor de Mediação aceitará conexões de entrada de gateways PSTN.
    
    > [!NOTE]  
    > Não é necessário inserir um intervalo de portas TCP se a opção <strong>Habilitar porta TCP</strong> não estiver marcada. Essa configuração é opcional.

Em seguida, execute o procedimento em [Definir um gateway no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-a-gateway-in-topology-builder.md) e instale os arquivos em cada Servidor de Mediação do pool seguindo os procedimentos em [Instalar os arquivos para o Servidor de Mediação no Lync Server 2013](lync-server-2013-install-the-files-for-mediation-server.md).

