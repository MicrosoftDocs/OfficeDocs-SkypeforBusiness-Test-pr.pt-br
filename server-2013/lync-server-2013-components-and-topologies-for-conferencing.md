---
title: 'Lync Server 2013: Componentes e topologias para conferências'
TOCTitle: Componentes e topologias para conferências
ms:assetid: eb83052a-3360-4ba1-a6a0-6ee419942809
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399061(v=OCS.15)
ms:contentKeyID: 49308497
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes e topologias para conferências no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-04_

Ao selecionar conferência em Construtor de Topologias, ela é implantada como parte do Servidor Front-End ou Servidor Standard Edition. A conferência discada e o compartilhamento de PowerPoint requer componentes e configurações adicionais. As seções a seguir descrevem os componentes e topologias suportados para webconferência, conferência A/V e conferência discada.

## Componentes suportados

Os únicos componentes necessários para webconferência e conferência A/V são o Servidores Front-End ou o Servidores Standard Edition da sua organização. Para obter uma lista de requisitos de hardware e software do Servidores Front-End e do Servidores Standard Edition, consulte [Hardware suportado para Lync Server 2013](lync-server-2013-supported-hardware.md) e [Suporte a software e à infraestrutura de servidor no Lync Server 2013](lync-server-2013-server-software-and-infrastructure-support.md).

O Lync Server 2013 usa o Office Web Apps e o Servidor Office Web Apps para permitir o compartilhamento e renderização de apresentações do PowerPoint. Para obter mais informações sobre como instalar e configurar o Servidor Office Web Apps, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

Além dos requisitos de webconferência e conferência A/V, a conferência discada usa os seguintes componentes de Lync Server 2013:

  - **O serviço de aplicativo**    Serviço de aplicativos fornece uma plataforma para implantar, hospedar e gerenciar aplicativos de comunicações unificadas (UC). A conferência discada usa dois aplicativos de UC que requerem que o Serviço de aplicativos Atendedor de Conferência e o Anúncio de Conferência. Serviço de aplicativos estejam instalados e ativados por padrão em cada Servidor Front-End em um Pool de Front-Ends e em cada Servidor Standard Edition ao implantar uma carga de trabalho de conferência e selecionar a opção de conferência discadada.

  - **Aplicativo Atendedor de Conferência**    Aplicativo Atendedor de Conferência é um aplicativo de comunicações unificadas que aceita chamadas de redes de telefone públicas comutadas (PSTN), executa comandos e aceita chamadas de conferências A/V. O Aplicativo Atendedor de Conferência é instalado e ativado por padrão ao implantar uma carga de trabalho de conferência e selecionar a opção conferência discada.

  - **Aplicativo Comunicado de Conferência**    Aplicativo Comunicado de Conferência é um aplicativo de comunicações unificadas que reproduz tons e executa comandos aos participantes PSTN em determinadas ações, como quando os participantes entram ou saem de uma conferência, quando os participantes ativam e desativam o opção Mudo, quando alguém entra no lobby da conferência ou quando a conferência é bloqueada ou desbloqueada. Aplicativo Comunicado de Conferência também oferece suporte a comandos multifrequência de dois tons (DTMF) do teclado do telefone. Aplicativo Comunicado de Conferência é instalado e ativado automaticamente por padrão ao implantar uma carga de trabalho de Conferência e selecionar a opção conferência discada.

  - **Página Configurações de Conferência Discada**   O Página Configurações de Conferência Discada exibe os números de discagem da conferência com os idiomas disponíveis, informações atribuídas sobre a conferência (ou seja, para reuniões que não precisam ser agendadas) e controles DTMF durante a conferência, e oferece suporte ao gerenciamento do número de identificação pessoal (PIN) e informações atribuídas sobre a conferência. O Página Configurações de Conferência Discada é automaticamente instalado como parte do Serviços Web.

  - **Lync Server 2013, Servidor de Mediação e o gateway PSTN**   A conferência discada requer um Servidor de Mediação para traduzir os sinais (e mídias, em algumas configurações) entre o Lync Server 2013 e o gateway PSTN, e um gateway PSTN para traduzir os sinais e as mídias entre o Servidor de Mediação e o gateway PSTN. Para conferências discadas, você deve implantar pelo menos um Servidor de Mediação e um dos seguintes:
    
      - Gateway PSTN
    
      - PBX IP
    
      - Controlador de Borda de Sessão (SBC) (para um provedor de serviços de telefonia pela Internet ao qual você se conecta configurando um tronco SIP)
    
    > [!NOTE]  
    > Se você também está implantando o Enterprise Voice, o Servidor de Mediação e os gateways PSTN fazem parte da implantação do Enterprise Voice. Se você não está implantando o Enterprise Voice, é necessário implantar pelo menos um Servidor de Mediação e um gateway PSTN, IP-PBX ou SBC para conferências discadas.

  - **Armazenamento de arquivos**   O armazenamento de arquivos é usado para arquivos de áudio de nomes gravados. O Armazenamento de arquivos de áudio de nomes é um componente padrão de todas as implantações de Enterprise Edition ou Standard Edition.

  - **Armazenamento de usuários**   O armazenamento de usuários é usado para armazenar os PINs dos usuários do Lync Server 2013. Os PINs são marcados por hash. O Armazenamento de usuários é um componente padrão em todas as implantações do Enterprise Edition ou do Standard Edition.

  - **Painel de Controle do Lync Server**   Algumas configurações de discagem podem ser configuradas usando o Painel de Controle do Lync Server.

  - **Shell de Gerenciamento do Lync Server**   Todas as configurações de discagem podem ser configuradas usando os cmdlets do Shell de Gerenciamento do Lync Server. Os cmdlets do Shell de Gerenciamento do Lync Server estão disponíveis para implantar, configurar, executar, monitorar e resolver problemas do Aplicativo Atendedor de Conferência e do Aplicativo Comunicado de Conferência. Para obter mais informações sobre cmdlets específicos, consulte a documentação do Shell de Gerenciamento do Lync Server.

## Topologias suportadas

No Lync Server 2013, o servidor que executa os serviços de conferência é sempre colocado com os Servidores Front-End ou com os Servidores Standard Edition. Durante a implantação inicial, Construtor de Topologias permite optar por incluir a realização de conferências na sua topologia. Você também pode usar o Construtor de Topologias para adicionar conferências a uma implantação existente. Para obter mais informações, consulte [Definindo e configurando a topologia no Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md).

## Topologias de conferência discada

É possível implantar a conferência discada nas seguintes topologias e configurações:

  - Lync Server 2013Standard Edition

  - Lync Server 2013Enterprise Edition

  - Com ou sem o Enterprise Voice

É possível implantar o Serviço de aplicativos, o Aplicativo Atendedor de Conferência e o Aplicativo Comunicado de Conferência em um local central, mas não no local da filial.

> [!NOTE]  
> Se você implantar a conferência discada, deverá implantá-la em cada pool que você implantar a Conferência do Lync Server 2013. Não é necessário atribuir números de acesso em cada pool, mas é necessário implantar o recurso de conferência discada em cada pool. Essa solicitação suporta o recurso de nome registrado quando um usuário faz uma chamada para um número de acesso de um pool para ingressar em uma conferência do Lync Server 2013 em um pool diferente.

## Topologias suportadas para Lync Server 2013 e Office Web Apps

Lync Server 2013 fornece as formas a seguir de configurar o Servidor Office Web Apps. Dependendo das suas necessidades, você pode:

  - **Instalar o Lync Server 2013 e o Servidor Office Web Apps no local, atrás do firewall da sua organização, e na mesma área de rede.** Com esta topologia, o acesso externo ao Servidor Office Web Apps será fornecido pelo servidor de proxy reverso. O Lync Server 2013 e o Servidor Office Web Apps (ou um farm Servidor Office Web Apps) são instalados no local, atrás do firewall da sua empresa. De preferência, você deve instalar o Servidor Office Web Apps na mesma área de rede do Lync Server.
    
    Clientes externos do Lync podem se conectar ao Lync Server 2013 e ao Servidor Office Web Apps usando um servidor de proxy reverso, que é um servidor que faz solicitações da Internet e as encaminha para a rede interna. (Os clientes internos não precisam usar o servidor de proxy reverso porque podem se conectar diretamente ao Servidor Office Web Apps.) Esta topologia funciona melhor se você deseja usar um farm dedicado do Servidor Office Web Apps que somente é usado pelo Lync Server 2013.

  - **Usando um Servidor Office Web Apps implantado externamente**
    
    Nesta topologia, Lync Server 2013 é implantado no local e usa um Servidor Office Web Apps que é implantado fora da área de rede do Lync Server. Isso pode ocorrer quando o Servidor Office Web Apps é compartilhado por vários aplicativos na corporação e é implantado em um rede que requer o Lync Server para usar a interface externa do Servidor Office Web Apps, e vice-versa.
    
    Não é necessário instalar um servidor de proxy reverso. Em vez disso, todas as solicitações do Servidor Office Web Apps para Lync Server 2013 são encaminhadas pelo Servidor de Borda. Os seus clientes internos e externos do Lync se conectam ao Servidor Office Web Apps usando a URL externa.
    
    Se o Servidor Office Web Apps for implantado fora do seu firewall interno, selecione a opção **Office Web Apps Server está implantado em uma rede externa (ou seja, de perímetro/Internet)** em Construtor de Topologias. Para obter mais informações, consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

Independente da topologia selecionada, é fundamental que as portas de firewall certas estejam abertas. É necessário garantir que os nomes de DNS, endereços IP e portas não estejam bloqueados por firewalls no Servidor Office Web Apps, no balanceador de carga ou no Lync Server.

> [!NOTE]  
> Outra opção para fornecer acesso externo ao Servidor Office Web Apps é implantar o servidor em uma rede de perímetro. Se você optar por fazer isso, tenha em mente que a instalação do Servidor Office Web Apps requer que o computador servidor seja membro do seu domínio Active Directory. A menos que sua política de rede permita computadores na rede de perímetro como membros do domínio Active Directory, é recomendado não instalar Servidor Office Web Apps na rede de perímetro. Em vez disso, você deve instalar o Servidor Office Web Apps na rede interna e fornecer acesso ao usuário externo através do servidor de proxy reverso.
