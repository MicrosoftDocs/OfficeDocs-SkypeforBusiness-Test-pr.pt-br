---
title: 'Lync Server 2013: Topologia e componentes para mobilidade'
TOCTitle: Topologia e componentes para mobilidade
ms:assetid: be3cae7a-095d-4785-91ba-6fac99eba92a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690037(v=OCS.15)
ms:contentKeyID: 49307953
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologia e componentes para mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-17_

    The information in this topic pertains to Cumulative Updates for Lync Server 2013: February 2013.

Para suportar aplicativos móveis Lync em dispositivos móveis, o Lync Server 2013 oferece três serviços: Serviço de Mobilidade do Mcx Lync Server 2013, Serviço de Descoberta Automática do Lync Server 2013, e Serviços de Notificação por Push do Lync Server 2013. As atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013 adicionaram um serviço complementar, porém avançado, para os Clientes móveis do Lync 2013—suporte à mobilidade pelo uso do Unified Communications Web API, ou UCWA. Esta seção descreve brevemente esses componentes e identifica as topologias do Lync Server 2013 que dão suporte à mobilidade.

> [!NOTE]  
> Os serviços de mobilidade também estão disponíveis em implantações híbridas. Não é necessário implantar serviços para suportar a mobilidade se os seus usuários estão hospedados online. Você não precisa definir uma configuração para o Serviço de Descoberta Automática a fim de permitir que usuários móveis encontrem sua identidade online.

> [!IMPORTANT]  
> Caso esteja planejando qualquer conectividade de usuário externo (por exemplo, federação, acesso de usuário externo ou recursos de mobilidade), você deve usar o Servidores de Borda com Servidor Standard Edition e o Servidor Front-End ou Pool de Front-Ends. A Servidor Standard Edition e a Servidor Front-End ou o Pool de Front-Ends não têm os componentes necessários para permitir que usuários externos acessem sua implantação interna ou para que a implantação interna se comunique com seus usuários externos. Para todos os cenários que incluem usuários que colaboram ou se comunicam com usuário internos, incluindo a mobilidade, você deve implantar pelo menos uma Servidor de Borda e um proxy reverso.<br />A <em>notificação por push</em> usa um tipo de federação para serviços do Lync Online, que hospeda a PNCH (Push Notification Clearing House). A notificação por push se refere aos alertas sonoros, alertas na tela (texto) e selos que são enviados por aplicativos para o Apple iPhone, o iPad e o Windows Phone, quando o dispositivo móvel está inativo. A PNCH recebe notificações por push do Lync Server. Quando a PNCH recebe uma notificação de uma mensagem, o PNCH encaminha uma notificação para clientes móveis pelos Apple Push Notification Services ou pelo Push Notification Service do Lync Server 2013, com base no cliente móvel para o qual a mensagem se destina. A PNCH é um serviço necessário para esses cliente móveis. Para federar ao Lync Online, a PNCH usa a Servidores de Borda, além de certificados para garantir a confidencialidade e a autenticação, políticas e registros de sistema de nome de domínio (DNS) configurados corretamente. os clientes Lync Mobile com base no Nokia Symbian e em Android não usam PNCH. Para obter detalhes sobre como planejar e implantar o Servidores de Borda, consulte <a href="lync-server-2013-planning-for-external-user-access.md">Planejamento para acesso de usuário externo no Lync Server 2013</a> e <a href="lync-server-2013-deploying-external-user-access.md">Implantação de acesso do usuário externo no Lync Server 2013</a>.<br />Os clientes móveis de dispositivos Apple Lync 2013 introduzidos pelas atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013 não utilizam mais notificação por push nem push notification clearing house (PNCH). Os clientes móveis Lync 2013 com Windows Phone ainda utilizam notificação por push e PNCH.

## Componentes de mobilidade

Os serviços que suportam a mobilidade são:

  - **Lync Server 2013 Unified Communications Web API (UCWA)**   Oferece serviços para comunicação em tempo real com clientes móveis e clientes Web no Lync Server 2013. Quando você implanta as atualizações cumulativas de fevereiro de 2013 no Lync Server 2013 ao Servidor Front-End e Diretor, a instalação cria um diretório virtual nos serviços Web internos e externos (Ucwa). Um componente Web que faz parte do diretório virtual UCWA aceita chamadas de clientes habilitados para uso do UCWA. Os aplicativos do cliente se comunicam por uma interface REST para presença, contatos, mensagens instantâneas, VoIP, videoconferência e colaboração. O UCWA utiliza um canal baseado em P-GET para enviar eventos, como uma chamada em entrada, mensagem instantânea em entrada, ou uma mensagem para o aplicativo do cliente.
    
    > [!NOTE]  
    > <em>REST</em> ou transferência de estado representacional é um estilo arquitetural de software para sistemas distribuídos que foi amplamente adotado em diversas formas e é muito adequado às exigências dos serviços Web em geral.

  - **Lync Server 2013 Serviço de Mobilidade (Mcx)**   Este serviço oferece suporte à funcionalidade Lync, como mensagens instantâneas (IM), presença e contatos, em dispositivos móveis. O Serviço de Mobilidade foi instalado em todo Servidor Front-End cada pool que deverá suportar a funcionalidade Lync nos dispositivos móveis. Quando você instala o Lync Server 2013, um novo diretório virtual (Mcx) é criado tanto no site interno como no externo em seu Servidores Front-End.
    
    > [!IMPORTANT]  
    > O Lync Server 2013, com as atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013, suporta tanto o Mobility service introduzido na atualização cumulativa de novembro de 2011 para o Lync Server 2010, comumente chamado de Mcx, quanto o componente Web UCWA. A combinação desses dois serviços de mobilidade oferece interoperabilidade e utilização por usuários com clientes móveis Lync 2010 Mobile e Lync 2013 em Lync Server 2013.

  - **Lync Server 2013 Serviço de Descoberta Automática**   Este serviço identifica a localização do usuário e permite que dispositivos móveis e outros clientes do Lync localizem recursos—como URLs internos e externos para Lync Server 2013 Serviços da Webs, e o URL para Mcx ou UCWA—independentemente do local da rede. A descoberta automática usa nomes de host inseridos no código (lyncdiscoverinternal para usuários na rede e lyncdiscover para usuário fora da rede) e o domínio SIP do usuário. Oferece suporte a conexões de cliente que utilizem HTTP ou HTTPS.
    
    O serviço de Descoberta Automática é instalado em todo Servidor Front-End e em todo Diretor em cada pool que deve suportar funcionalidade Lync em dispositivos móveis. Quando você instala o Serviço de Descoberta Automática, um novo diretório virtual (Descoberta Automática) é criado abaixo dos sites interno e externo em ambos os Servidores Front-End e Diretores.
    
    > [!NOTE]  
    > O serviço de Descoberta Automática está listado aqui porque permanece sendo um componente crítico ao fornecer serviços a clientes móveis. A função da Descoberta Automática em Lync Server 2013 expandiu-se para oferecer serviços para todos os clientes. Para detalhes sobre o planejamento para o serviço de Descoberta Automática, consulte <a href="lync-server-2013-planning-for-autodiscover.md">Planejando para a descoberta automática</a>.

  - **Serviço de Notificação por Push**   Este é um serviço de nuvem que está localizado no data centerLync Online. Quando o aplicativo móvel do Lync em um dispositivo suportado pelo Apple iOS ou Windows Phone está inativo, não é possível responder a novos eventos, como um convite para novas mensagens instantâneas (IM), uma mensagem instantânea perdida, uma chamada perdida, ou caixa postal, pois esses dispositivos não oferecem suporte a aplicativos móveis em execução em segundo plano. Nesses casos, uma notificação de novo evento—chamada de *notificação por push*—é enviada ao dispositivo móvel. O Serviço de mobilidade envia a notificação para o Serviço de notificação por push com base em nuvem, que envia a notificação para o Apple Push Notification Service (APNS) (para dispositivos Apple iOS suportados) ou para o Microsoft Push Notification Service (MPNS) (para Windows Phone), que a envia então para o dispositivo móvel. Em seguida, o usuário pode responder à notificação com o dispositivo móvel para ativar o aplicativo.
    
    O Lync 2010 Mobile em dispositivos Apple e Windows Phone utilizam notificações por push. O cliente móvel Lync 2013 para dispositivos Apple introduzido nas atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013 não utiliza mais notificação por push nem push notification clearing house (PNCH).

O diagrama abaixo ilustra como o Serviço de notificação por push se encaixa em uma topologia do Lync Server 2013 que utilize clientes móveis Lync 2013 e UCWA.

![UCWA de serviços de notificação por push](images/Hh690037.166d60fd-ff71-4ffe-9f66-3c8bbde0b5ae(OCS.15).jpg "UCWA de serviços de notificação por push")

Introduzido na atualização cumulativa de novembro de 2011 para o Lync Server 2010, o serviço Mcx oferece serviços para clientes Lync 2010 Mobile. O diagrama a seguir ilustra o Push Notification Service com aplicação em uma topologia utilizando Mcx e clientes Lync 2010 Mobile.

![MCX de serviços de notificação por push](images/Hh690037.3081634e-60e7-4348-b24e-bbbf05a90f5f(OCS.15).jpg "MCX de serviços de notificação por push")

## Topologias suportadas

A instalação das atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013 adiciona os componentes Web do UCWA para suportar mobilidade para recursos de clientes móveis Lync 2013 nas topologias a seguir:

  - Lync Server 2013  Standard Edition

  - Lync Server 2013 Enterprise Edition

O Servidor de Borda pode ser um Lync Server 2010 Servidor de Borda.

Uma implantação de Lync Server 2013 sem as atualizações cumulativas de fevereiro de 2013 para o Lync Server 2013 utilizarão o Mcx Mobility Service e poderão oferecer serviços somente para Lync 2010 Mobile.

> [!IMPORTANT]  
> O Mobility Service é suportado no Servidores Front-End que é colocado com a função Servidor de Mediação com duas interfaces de rede, mas você precisa realizar as etapas apropriadas para configurar as interfaces. Você precisa atribuir os endereços IP à interface específica que se comunicará como o Servidor de Mediação, e o IP de interface de rede que se comunicará como o Servidor Front-End. Você pode fazer isso no Construtor de Topologias selecionando o IP correto para cada serviço, em vez de utilizar a opção padrão <strong>Usar todos os endereços IP configurados</strong>.

## Consulte Também

#### Outros Recursos

[Planejamento para acesso de usuário externo no Lync Server 2013](lync-server-2013-planning-for-external-user-access.md)  
[Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md)  
[Planejando para a descoberta automática](lync-server-2013-planning-for-autodiscover.md)

