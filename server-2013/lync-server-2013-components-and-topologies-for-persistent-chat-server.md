---
title: 'Lync Server 2013: Componentes e topologias para Servidor de Chat Persistente'
TOCTitle: Componentes e topologias para Servidor de Chat Persistente
ms:assetid: 6a0a14a0-baad-44e9-b26e-4d192c0a0e70
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398500(v=OCS.15)
ms:contentKeyID: 49307005
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologias para Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-05_

O Servidor de Chat Persistente oferece suporte a configurações com um único servidor e com vários servidores. O Servidor de Chat Persistente também pode ser executado em um Servidor Standard Edition do Lync Server 2013. Essas configurações consistem nos componentes e topologias do Servidor de Chat Persistente a seguir.

## Componentes do Servidor de Chat Persistente

A instalação da versão mais recente do Servidor de Chat Persistente requer os seguintes componentes:

  - Um ou mais computadores que executam o Servidor de Chat Persistente e fornecem os seguintes serviços:
    
      - Serviço de Chat Persistente
    
      - Serviço de conformidade, que é ativado quando a conformidade é habilitada
    
    > [!IMPORTANT]  
    > No Lync Server 2013, os Serviços Web do Chat Persistente para Carregamento/Download de Arquivos foram colocados no Servidor Front-End do Lync Server 2013.<br />    Os Serviços Web do Chat Persistente para Gerenciamento de Salas de Chat também foram colocados no Servidor Front-End do Lync Server 2013.

  - O(s) servidor(es) (mais de um servidor se o espelhamento for usado) que hospeda(m) o banco de dados Back-End do SQL Server para hospedagem do banco de dados de conteúdo do Chat Persistente em que o conteúdo das salas de chat, as salas e as categorias são armazenados.
    
    > [!NOTE]  
    > O banco de dados Back-End armazena os dados de histórico do chat, incluindo informações sobre as categorias e as salas do Chat Persistente criadas.

  - Se a conformidade estiver habilitada, o(s) servidor(es) (mais de um servidor se o espelhamento for usado) que hospeda(m) o banco de dados Back-End do SQL Server para hospedagem do banco de dados de conformidade do Chat Persistente em que os eventos de conformidade e conteúdo de chat para fins de conformidade são armazenados.

Para administrar o Servidor de Chat Persistente de um computador separado (como um console administrativo), use o Painel de Controle do Lync Server no computador. Em seguida, esse computador deve ser implantado em um domínio do Serviços de Domínio Active Directory com pelo menos um servidor de catálogo global na raiz da floresta.

Para obter detalhes sobre os requisitos de hardware e software do Servidor de Chat Persistente, consulte [Requisitos técnicos do Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-technical-requirements-for-persistent-chat-server.md), [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) e [Suporte a software e à infraestrutura de servidor no Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md) na documentação de suporte.

## Colocação com suporte

O Lync Server 2013 oferece suporte a diversos cenários de colocação, permitindo a flexibilidade de economizar com custos de hardware executando vários componentes em um único servidor (se você tiver uma organização pequena) ou de executar componentes individuais em servidores diferentes (se você tiver uma organização maior que precise de escalabilidade e desempenho). Você certamente deve considerar os fatores de escalabilidade antes de decidir se colocará os componentes.

O serviço de conformidade do Chat Persistente (se a conformidade estiver habilitada) será colocado no Servidor Front-End do Lync Server 2013.

O Servidor de Chat Persistente pode ser implantado no Servidor Standard Edition. O Servidor Back-End do Servidor de Chat Persistente e o banco de dados de conformidade do Chat Persistente podem ser colocados no Servidor Standard Edition no Servidor Back-End do SQL Server Express local. Para obter detalhes sobre os componentes que podem ser colocados nele, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md) na documentação de suporte.

Para o Enterprise Edition do Lync Server 2013, os Servidores de Chat Persistente não podem ser colocados no Servidor Enterprise Edition. O banco de dados do SQL Server do Servidor de Chat Persistente pode ser colocado no banco de dados do Servidor Back-End de um Pool de Front-Ends do Enterprise Edition. O banco de dados do SQL Server da conformidade do Chat Persistente também pode ser colocado no banco de dados do Servidor Back-End de um pool de Enterprise Edition.

> [!IMPORTANT]  
> O servidor que hospeda o banco de dados do Chat Persistente pode hospedar outros bancos de dados. No entanto, ao considerar a colocação do banco de dados do Chat Persistente em outros bancos de dados, lembre-se de que, se você for armazenar mensagens de muitos usuários, o espaço em disco exigido pelo banco de dados do Chat Persistente poderá aumentar muito. Por esse motivo, recomendamos colocar o banco de dados do Chat Persistente no banco de dados Back-End.

Se você colocar o banco de dados do Chat Persistente no banco de dados Back-End, poderá usar uma única instância do SQL Server para todos os bancos de dados ou poderá usar uma instância separada do SQL Server para cada banco de dados, com a seguinte limitação:

  - Cada instância do SQL Server pode conter somente um único banco de dados Back-End e um único banco e dados do Chat Persistente.

Para obter detalhes sobre a colocação de todas as funções de servidor e bancos de dados, consulte [Colocação em conjunto de servidor suportado no Lync Server 2013](lync-server-2013-supported-server-collocation.md) na documentação de suporte.

## Topologias do Servidor de Chat Persistente

O Servidor de Chat Persistente oferece suporte às seguintes topologias:

  - Servidor Front-End do Servidor de Chat Persistente de único servidor do Lync Server 2013 Enterprise Edition

  - Servidor Front-End do Servidor de Chat Persistente de vários servidores do Lync Server 2013 Enterprise Edition

  - Lync Server 2013Servidor Standard Edition usando o SQL Server Express

  - Lync Server 2013Servidor Standard Edition e Servidor de Chat Persistente em um servidor separado usando o Servidor Standard Edition como servidor de próximo salto.

Você pode adicionar o Servidor de Chat Persistente à sua implantação do Lync Server 2013 usando o Construtor de Topologias. Você pode adicionar um Pool de Servidor de Chat Persistente de um único servidor ou de vários servidores à sua topologia.

> [!IMPORTANT]  
> Depois que você criar um Pool de Servidor de Chat Persistente com um único servidor usando o Construtor de Topologias, não poderá adicionar mais servidores ao pool.

## Topologia de servidor único

A configuração mínima e a implantação mais simples do Servidor de Chat Persistente é a topologia de Servidor Front-End do Servidor de Chat Persistente único. Essa implantação requer um único servidor que executa o Servidor de Chat Persistente (que opcionalmente executa o serviço de conformidade, se a conformidade estiver habilitada), um servidor que hospeda o banco de dados do SQL Server e, se a conformidade for necessária, o banco de dados do SQL Server para armazenar os dados de conformidade.

> [!IMPORTANT]  
> Você não pode adicionar mais servidores a um Pool de Servidor de Chat Persistente que começou como uma implantação de um único servidor no Construtor de Topologias. Recomendamos usar a topologia de pool de vários servidores, mesmo se você for usar um único servidor, para que possa adicionar mais servidores no futuro se for necessário.

A figura a seguir mostra todos os componentes obrigatórios e opcionais de uma topologia de um Servidor Front-End do Servidor de Chat Persistente único com conformidade.

**Servidor de Chat Persistente único**

![Topologia de servidor único com serviço de Conformidade](images/Gg615006.9168fa52-61e0-4d17-a14d-45fd32e81456(OCS.15).jpg "Topologia de servidor único com serviço de Conformidade")

## Topologia de vários servidores

Para fornecer maior capacidade e confiabilidade, você pode implantar uma topologia com vários servidores, conforme descrito em [Planejando o Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-planning-for-persistent-chat-server.md). A topologia de vários servidores pode incluir até quatro computadores ativos executando o Servidor de Chat Persistente (configurações de alta disponibilidade e recuperação de desastres permitem até oito, mas somente quatro podem estar ativos e os quatro outros ficam em espera). Cada servidor pode oferecer suporte a até 20 mil usuários simultâneos gerando um total de 80 mil usuários simultâneos conectados a um Pool de Servidor de Chat Persistente com quatro servidores. Uma topologia de vários servidores é o mesmo que uma topologia de um único servidor, com exceção de que vários servidores hospedam o Servidor de Chat Persistente e a escalabilidade é maior. Vários computadores executando o Servidor de Chat Persistente devem estar no mesmo domínio do Serviços de Domínio Active Directory que o Lync Server e o serviço de conformidade.

A figura a seguir mostra todos os componentes de uma topologia de vários servidores com vários computadores executando o Servidor de Chat Persistente, o serviço de conformidade opcional e um banco de dados de conformidade separado.

**Vários Servidores de Chat Persistente**

![Topologia de múltiplos servidores](images/Gg615006.19aea898-28df-4d9b-903c-f72ef062d919(OCS.15).jpg "Topologia de múltiplos servidores")

As topologias de vários servidores fornecem a funcionalidade de pool de servidores. Em um pool de servidores, os serviços do Chat Persistente se comunicam e compartilham dados. Por exemplo, o histórico de chat originalmente registrado em um serviço de Chat Persistente fica disponível em qualquer serviço de Chat Persistente no sistema. Um arquivo carregado por meio de um serviço de Chat Persistente pode ser acessado por qualquer serviço de Chat Persistente. Os usuários podem estar conectados a diferentes Servidores Front-End de Servidor de Chat Persistente e podem conversar e se comunicar uns com os outros.

A porta padrão TCP 8011 conecta um servidor a um pool de servidores e é usada pelo serviço de Chat Persistente para intercomunicação ou para fins administrativos.

