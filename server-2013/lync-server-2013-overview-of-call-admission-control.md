---
title: 'Lync Server 2013: Visão geral do controle de admissão de chamada'
TOCTitle: Visão geral do controle de admissão de chamada
ms:assetid: 6fda0195-4c89-4dea-82e8-624f03e3d062
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398529(v=OCS.15)
ms:contentKeyID: 49307064
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral do controle de admissão de chamada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-22_

As comunicações em tempo real são sensíveis à perda de latência e pacotes que pode ocorrer em redes congestionadas. O CAC (serviço de controle de admissão de chamadas) determina, com base na largura de banda da rede disponível, se será permitido estabelecer sessões de comunicação em tempo real, como chamadas de voz ou vídeo. O design do CAC do Lync Server 2013 oferece quatro atributos principais:

  - é simples de implantar e gerenciar, sem a necessidade de equipamentos adicionais, como roteadores especialmente configurados.

  - Ele aborda casos críticos de uso de comunicações unificadas, como usuários móveis e vários pontos de presença. As políticas CAC são aplicadas de acordo com a localização do ponto de extremidade, não onde o usuário está hospedado.

  - Além de chamadas de voz, ele pode ser aplicado a outro tráfego, como chamadas de vídeo e sessões de conferência de áudio/vídeo.

  - Oferece a flexibilidade para permitir a representação de vários tipos de topologias de rede. Para obter exemplos, consulte [Componentes e topologias para CAC no Lync Server 2013](lync-server-2013-components-and-topologies-for-cac.md).

Se uma nova voz ou sessão de vídeo exceder os limites de largura de banda definidos em um link WAN, a sessão é bloqueada ou (somente para chamadas de telefone) redirecionada ao PSTN.

O CAC controla o tráfego em tempo real somente para voz e vídeo. Ele não controla o tráfego de dados.

Os administradores definem políticas CAC, que são aplicadas pelo Serviço de Política de Largura de Banda que é instalado com cada Pool de Front-Ends. As configurações do CAC são automaticamente propagadas a todos os Servidores Front-End do Lync Server em sua rede.

Para chamadas que falham devido a políticas CAC, a ordem de precedência para o redirecionamento de chamada é:

1.  Internet

2.  PSTN

3.  Caixa postal

A gravação de detalhes da chamada (CDR) captura as informações sobre chamadas que são reencaminhadas para o PSTN ou o correio de voz. O CDR não captura as informações sobre chamadas reencaminhadas para a Internet, porque a Internet é tratada como um caminho alternativo, em vez de uma opção secundária.

> [!NOTE]  
> Os depósitos de caixa postal não serão negados devido a restrições de largura de banda.

O Serviço de Política de Largura de Banda gera dois tipos de arquivos de log no formato de valores separados por vírgulas (CSV). O arquivo de log **falhas de verificação** captura as informações quando as solicitações de largura de banda são negadas. O arquivo de log **utilização do link** captura um instantâneo da topologia de rede e a utilização de largura de banda do link de WAN. Ambos arquivos de log podem ajudá-lo a ajustar as políticas CAC com base na utilização.

## Considerações sobre o Controle de Admissão de Chamada

O administrador seleciona a instalação do Serviço de Política de Largura de Banda no primeiro pool configurado no site central. Como há apenas um site central por região da rede, há apenas um Serviço de Política de Largura de Banda por região da rede, que gerencia a política de largura de banda para aquela região, os sites associados e os links para esses sites. O Serviço de Política de Largura de Banda é executado como parte do Servidores Front-End e, por isso, o pool conta com alta disponibilidade interna. O Serviço de Política de Largura de Banda em execução em cada Servidor Front-End é sincronizado a cada 15 segundos. Se o Pool de Front-Ends falhar, as políticas CAC não serão mais impostas para o site até que o Pool de Front-Ends e, consequentemente, o Serviço de Política de Largura de Banda entrem em operação novamente. Isso significa que todas as chamadas serão recebidas enquanto o Serviço de Política de Largura de Banda estiver inoperante. Portanto, ainda há a possibilidade de excesso de assinatura da largura de banda dos links durante esse período

O Serviço de Política de Largura de Banda fornece alta disponibilidade em um Pool de Front-Ends; porém, ele não fornece redundância em Pools de Front-Ends. O Serviço de Política de Largura de Banda não pode realizar failover de um Pool de Front-Ends para outro. Quando o serviço do Pool de Front-Ends é recuperado, o Serviço de Política de Largura de Banda é retomado e pode impor as verificações de política de largura de banda novamente.

## Considerações de Rede

Embora a restrição de largura de banda para áudio e vídeo é imposta pelo Serviço de Política de Largura de Banda em Lync Server 2013, essa restrição não é imposta no roteador de rede (camada 2 e 3). O CAC do Lync Server 2010 não pode impedir que um aplicativo de dados, por exemplo, consuma a largura de banda de rede inteira em um link WAN, incluindo a largura de banda que está reservada para áudio e vídeo por sua política CAC. Para proteger a largura de banda necessária na rede, você pode implantar um protocolo de Qualidade de Serviço (QoS), como os Serviços Diferenciados (DiffServ). Portanto, uma prática recomendada é coordenar as políticas de largura de banda do CAC definidas com quaisquer configurações de QoS que você possa implantar.

## Mídia e Sinalização de Caminhos através de VPN

Se a sua empresa oferece suporte à mídia através de VPN, verifique se tanto o fluxo de mídia e o fluxo de sinalização vão através de VPN ou ambos são roteados pela internet. Por padrão, a mídia e os fluxos de sinalização passam pelo encapsulamento VPN.

## Controle de Admissão de Chamada de Usuários Externos

O controle de admissão de chamada não será aplicado aos usuários remotos onde o tráfego de rede flui através da Internet. Como o tráfego de mídia atravessa a Internet, que não não é gerenciada por Lync Server, o CAC não pode ser aplicado. Serão realizadas verificações de CAC, no entanto, na parte da chamada que flui através da rede corporativa.

## Controle de Admissão de Chamada das Conexões PSTN

O controle de admissão de chamada é aplicável no Servidor de Mediação, independentemente de estar conectado a um IP/PBX, um gateway PSTN ou um tronco SIP. Como o Servidor de Mediação é um agente de usuário consecutivo (B2BUA), ele encerra a mídia. Ele tem dois lados de conexão: um lado conectado ao Lync Server e um lado do gateway, que é conectado a IP/PBXs, gateways PSTN ou troncos SIP. Para obter detalhes sobre as conexões PSTN, consulte [Planejamento de conectividade de PSTN no Lync Server 2013](lync-server-2013-planning-for-pstn-connectivity.md).

O CAC pode ser aplicado em ambos os lados do Servidor de Mediação, a menos que o bypass de mídia esteja ativado. Se o bypass de mídia estiver ativado, o tráfego de mídia não atravessa o Servidor de Mediação, mas flui diretamente entre o cliente do Lync e o gateway. Nesse caso, o CAC não é necessário. Para obter detalhes, consulte [Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md).

A figura a seguir ilustra como o CAC é aplicado em conexões PSTN, com e sem o bypass de mídia habilitado.

**Aplicação de controle de admissão de chamada em conexões para o PSTN**

![Imposição da conexão de bypass de mídia do CAC de voz](images/Gg398529.4d66d529-0912-4de1-abec-266f54272eb3(OCS.15).jpg "Imposição da conexão de bypass de mídia do CAC de voz")

## Compatibilidade de Controle de Admissão de Chamada com Versões Anteriores do Office Communications Server

O controle de admissão de chamada pode ser ativado somente em pontos de extremidade que estão habilitados para o Lync Server 2010 e posterior.

O controle de admissão de chamada não pode ser ativado em pontos de extremidade executando o Office Communicator 2007 R2 ou anterior.

**Aplicativo do CAC em diferentes versões do Lync Server**

![Diagrama de Comparação da versão do CAC de voz](images/Gg398529.fdbfee7e-15fc-445b-949d-8d61e61ac350(OCS.15).jpg "Diagrama de Comparação da versão do CAC de voz")

