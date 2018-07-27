---
title: 'Lync Server 2013: Componentes obrigatórios para acesso de usuário externo'
TOCTitle: Componentes obrigatórios para acesso de usuário externo
ms:assetid: 2d0f9817-14e7-4109-95dc-62420e3c29e2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425779(v=OCS.15)
ms:contentKeyID: 49306240
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes obrigatórios para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A maioria dos componentes de Borda é implantada em uma rede de perímetro, Os seguintes componentes criam a topologia de borda da rede de perímetro. Exceto onde observado, os componentes fazem parte do [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md) e estão na rede de perímetro. Os componentes de Borda incluem o seguinte:

  - Servidores de Borda

  - Proxies reversos

  - Firewalls

  - Diretores (opcional e logicamente localizado na rede interna)

  - Balanceamento de carga para Topologias de Borda Dimensionadas (balanceamento de carga DNS ou um balanceador de carga de hardware)
    
    > [!IMPORTANT]  
    > O uso do balanceamento de carga de DNS em uma interface e do balanceamento de carga de hardware na outra não é suportado. É preciso usar o balanceamento de carga de hardware ou de DNS nas duas interfaces.

## Servidores de Borda

O Servidores de Borda envia e recebe o tráfego de rede para os serviços oferecidos pela implantação interna por usuários externos. O Servidor de Borda executa os seguintes serviços:

  - **Serviço de Borda de Acesso**   O Serviço de Borda de Acesso fornece um ponto de conexão único e confiável para o tráfego de saída e de entrada do protocolo SIP.

  - **Serviço de Borda de Webconferência**   O Serviço de Borda de Webconferência permite que os usuários externos ingressem em reuniões hospedadas em sua implantação interna do Lync Server 2013.

  - **Serviço de Borda A/V**   O Serviço de Borda A/V disponibiliza o compartilhamento de áudio, vídeo e aplicativo e a transferência de arquivos para usuários externos. Os usuários podem adicionar áudio e vídeo às reuniões que incluem participantes externos e podem se comunicar usando áudio e vídeo diretamente com um usuário externo em sessões ponto a ponto. O Serviço de Borda A/V também fornece suporte para compartilhamento de área de trabalho e transferência de arquivo.

  - **XMPP Proxy service**   The XMPP Proxy service accepts and sends extensible messaging and presence protocol (XMPP) messages to and from configured XMPP Federated partners.

Os usuários externos autorizados podem acessar o Servidores de Borda para poder conectar sua implantação do Lync Server 2013 interno, mas o Servidores de Borda não oferece um meio de qualquer outro acesso para rede interna.

> [!NOTE]  
> Os servidores de borda são implantados para fornecer conexões para clientes Lync habilitados e outros servidores de Borda da Microsoft (como em cenários de federação). Eles não são criados para permitir conexões de outros tipos de servidor ou cliente de ponto de extremidade. O servidor de Gateway XMPP pode ser implantado para permitir conexões com parceiros XMPP configurados. O servidor de Borda e o Gateway XMPP podem oferecer suporte a apenas conexões de ponto de extremidade desses tipos de federação e cliente.

## Proxy reverso

O proxy reverso é necessário para o seguinte:

  - Permitir que os usuários se conectem às reuniões ou conferências discadas usando URLs simples

  - Permitir que os usuários externos baixem o conteúdo da reunião

  - Habilitar os usuários externos a expandir grupos de distribuição

  - Permitir que o usuário obtenha um certificado baseado no usuário para autenticação com base no certificado cliente

  - Permitir que os usuários remotos baixem arquivos do Servidor de Catálogo de Endereço ou enviem consultas ao serviço Address Book Web Query

  - Permitir que os usuários remotos obtenham atualizações para softwares clientes ou de dispositivo

  - Para habilitar dispositivos móveis para descobrir automaticamente o Servidores Front-End oferecendo serviços de mobilidade

  - Permitir notificações por push para dispositivos móveis dos serviços de notificação por push do Office 365 ou da Apple

For additional information related to reverse proxies and the requirements that reverse proxies must meet, see the details in [Requisitos de configuração do proxy reverso no Lync Server 2013](lync-server-2013-configuration-requirements-for-reverse-proxy.md).

> [!NOTE]  
> Usuários externos não precisam de uma conexão de rede virtual privada (VPN) com sua organização para participar de comunicações utilizando o Lync Server 2013. Se você implementou a tecnologia VPN em sua organização e os usuários utilizam a VPN para Lync, o tráfego de mídia (como conferência de vídeo) pode ser afetado de forma adversa. Considere oferecer um meio para que o tráfego de mídia conecte-se ao serviço de Borda AV diretamente e ignore a VPN. Para obter detalhes, consulte o artigo do Blog NextHop, “Enabling Lync Media to Bypass a VPN Tunnel,” em <a href="http://go.microsoft.com/fwlink/p/?linkid=256532">http://go.microsoft.com/fwlink/p/?LinkId=256532</a>.

## Firewall

É possível implantar sua topologia de borda com apenas um firewall externo ou com firewalls internos e externos. As arquiteturas de cenário incluem dois firewalls. O uso de dois firewalls é a abordagem recomendada, pois garante o roteamento estrito de uma borda de rede para a outra e protege sua implantação interna atrás de dois níveis de firewall.

## Diretor

Um Diretor é uma função do servidor opcional separada no Lync Server 2013 que não hospeda contas do usuário ou oferece presença ou serviços de conferência. Serve como um servidor de salto interno no qual um Servidor de Borda roteia o tráfego SIP de entrada destinado para servidores internos. O Diretor pré-autentica as solicitações de entrada e redireciona-os para o pool inicial do usuário ou servidor. Ao pré-autenticar no Diretor, é possível derrubar solicitações das contas do usuário que são desconhecidas para a implantação.

Um Diretor ajuda a isolar os servidores do Standard Edition e Servidores de Front-End nos pools de Front-End do Enterprise Edition de tráfego malicioso como ataques de negação de serviço (DoS). Se a rede está congestionada com tráfego externo inválido como um ataque, o tráfego termina no Diretor. Para obter detalhes sobre o uso do Diretores, consulte [Cenários para o Diretor no Lync Server 2013](lync-server-2013-scenarios-for-the-director.md).

## Consulte Também

#### Conceitos

[Requisitos do balanceador de carga do hardware para Lync Server 2013](lync-server-2013-hardware-load-balancer-requirements.md)

