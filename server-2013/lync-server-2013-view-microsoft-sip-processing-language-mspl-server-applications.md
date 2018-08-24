---
title: "Lync Server 2013: Exibir app de servidor do Idioma de Proc. SIP da Microsoft"
TOCTitle: Exibir aplicativos de servidor do Idioma de Processamento SIP da Microsoft
ms:assetid: b7df1323-b6bd-4925-8fe6-5241c91fe51b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182575(v=OCS.15)
ms:contentKeyID: 49307898
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir aplicativos de servidor do Idioma de Processamento SIP da Microsoft (MSPL) no Lync Server 2013

 

_**Tópico modificado em:** 2014-09-26_

Um aplicativo servidor MSPL (Microsoft SIP Processing Language) é um aplicativo somente script que usa a linguagem de scripts em vez da API do Microsoft Lync 2010. O MSPL fornece um controle mais granular sobre os comportamentos de filtragem e proxy, além de um recurso para expedir mensagens específicas para aplicativos SIP baseados em transações. O MSPL é usado especificamente para filtragem e roteamento de mensagens SIP. Os aplicativos MSPL são executados no mesmo processo que o módulo UserServices, enquanto um programa baseado na API do Lync 2010 é executado em um processo separado.

É possível usar a página **Aplicativo de Servidor** no grupo **Topologia** do Painel de Controle do Lync Server para ver uma lista dos aplicativos de servidor do MSPL executados em Servidores Front-End em seu ambiente do Lync Server 2013. A lista mostra os scripts disponíveis para cada pool, além de mostrar se estão habilitados ou se são críticos. Os scripts são executados na ordem em que estão listados.

Esses scripts incluem o seguinte:

  - O ClientVersionFilter fornece ao administrador uma maneira de especificar a versão dos clientes suportada por um pool. O filtro de versão do cliente verifica a versão do cliente e pode impedir o cliente de entrar no serviço ou apresentar uma mensagem que indica se ele ou ela está usando um cliente que não é suportado. O filtro de versão do cliente também pode ser configurado para exibir para o usuário uma mensagem contendo a URL da versão mais recente do cliente que pode ser baixada.

  - O TranslationService converte um número discado por um usuário em um número E.164, de acordo com as regras de normalização definidas pelo administrador. Para obter mais detalhes, consulte [Regras de tradução no Lync Server 2013](lync-server-2013-translation-rules.md).

  - O IncomingFederation aplica a validação de federação no nível de locatário para mensagens de entrada e entre locatários de implantações externas.

  - O UserServices é o componente de registrador SIP, de presença e de conferência de um Servidor Front-End. Ele fornece recursos bastante integrados de mensagens instantâneas, presença e conferência, construídos sobre o Proxy SIP.

  - O InterClusterRouting é responsável pelo roteamento de chamadas para o pool de registradores primários do receptor. Para obter detalhes, consulte [Componentes VoIP do Servidor Front-End para Lync Server 2013](lync-server-2013-front-end-server-voip-components.md).

  - O IIMFilter (Filtro de IM inteligente) bloqueia mensagens que contenham URLs clicáveis ou que tentem iniciar transferências de arquivo. O IIMFilter também verifica a versão do cliente para o servidor. O IIMFilter afeta as transferências de arquivo iniciadas usando o Lync Server ou o Communicator. Por padrão, os links clicáveis são desabilitados com a inclusão de um caractere sublinhado antes do primeiro caractere do link. O administrador pode alterar esse comportamento para que o link seja bloqueado. Nesse caso, as mensagens que contiverem URLs clicáveis ou que tentarem iniciar uma transferência de arquivo serão bloqueadas pelo servidor e não conseguirão atingir seus destinos. O IIMFilter está instalado em todos os servidores executando o Lync Server, exceto em Servidores proxy e Servidores de arquivamento.

  - UserPinService é usado para verificar os PINs (Números de identificação pessoal) do usuário para conferência discada.

  - O DefaultRouting é o aplicativo de roteamento padrão para servidores que executam o Lync Server. Ele é habilitado por padrão. O aplicativo de roteamento é instalado em todos os servidores Standard Edition e Enterprise Edition.

  - ExumRouting encaminha chamadas à UM (Unificação de mensagens) do Exchange Server. O ExumRouting determina o servidor da UM do Exchange apropriado ao qual rotear a chamada quando há uma nova mensagem para depósito. O ExumRouting também lida com outros aspectos de integração da UM do Exchange, incluindo roteamento para Atendedor Automático e Acesso do Assinante.

  - O OutboundRouting determina o gateway que encaminha uma chamada a um número de telefone, de acordo com número discado e a autorização de discagem do usuário. OutboundRouting também trata do reencaminhamento de chamadas se um gateway não puder processá-las.

  - O QoEAgent recebe relatórios de dados de QoE (Qualidade da experiência) dos pontos de extremidade por meio de solicitações SIP SERVICE e envia os dados à fila de destino no Servidor de monitoramento ou a clientes terceiros usando HTTP POST. Para obter detalhes, consulte [Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md).

  - OutgoingFederation aplica a validação de federação no nível do locatário para mensagens que estão indo a uma implantação externa direcionada.

  - AcpRouting aplica proxies em solicitações INVITE destinadas ao provedor de audioconferência para o gateway do provedor de audioconferência.

Os scripts executados em Servidores de borda incluem o seguinte:

  - IIMFilter

  - OptionsHandler responde às solicitações OPTIONS de entrada com **200 OK** se a solicitação for destinada ao servidor atual. Isso é usado para validação de topologia.

## Consulte Também

#### Tarefas

[Habilitar ou desabilitar um aplicativo do servidor de idiomas de processamento SIP da Microsoft (MSPL)](lync-server-2013-enable-or-disable-a-microsoft-sip-processing-language-mspl-server-application.md)  
[Marcar um aplicativo de idioma de processamento SIP da Microsoft (MSPL) como crítico ou não crítico](lync-server-2013-mark-a-microsoft-sip-processing-language-mspl-application-as-critical-or-not-critical.md)

