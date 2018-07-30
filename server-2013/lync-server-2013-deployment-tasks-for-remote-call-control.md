---
title: 'Lync Server 2013: Tarefas de implantação de controle de chamada remota'
TOCTitle: Tarefas de implantação de controle de chamada remota
ms:assetid: 20218871-4f27-4611-9b7e-c0ca55908284
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg558624(v=OCS.15)
ms:contentKeyID: 49306111
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Tarefas de implantação de controle de chamada remota no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Este tópico descreve as tarefas de implantação que devem ser realizadas para habilitar o controle de chamada remota para os usuários no seu ambiente do Lync Server.

> [!NOTE]  
> Se você estiver migrando usuários habilitados anteriormente para controle de chamada remota no Microsoft Office Communicator 2007 R2, você deve realizar uma tarefa de implantação adicional antes de começar a realizar as tarefas de implantação de chamada remota descritas neste tópico. Durante o processo de migração para o Lync Server, as entradas do aplicativo confiável (anteriormente conhecidas como <em>entradas de host autorizadas</em> ) devem ser removidas usando as ferramentas administrativas do Office Communications Server 2007 R2, como adequado.<br />Para obter os detalhes de como remover hosts autorizados, consulte <a href="lync-server-2013-remove-a-legacy-authorized-host-optional.md">Remover um host autorizado herdado no Lync Server 2013 (opcional)</a>.

## Etapa 1: Instale e configure o Gateway SIP/CSTA para se comunicar com seu PBX

Você precisa instalar um gateway de SIP/CSTA que possa se conectar ao Lync Server existente no seu ambiente, para fornecer recursos de controle de chamada remota para seus usuários. Um gateway SIP/CSTA é um gateway entre o SIP e um CSTA (aplicativo de telecomunicações com suporte por computador). Independente de você instalar múltiplos gateways ou somente um, cada usuário pode ser configurado somente com um gateway ou PBX. Se o PBX existente não tiver uma interface SIP/CSTA, implante um gateway SIP/CSTA que possa suportar o PBX, incluindo o suporte para protocolos de sinalização específicos do fornecedor do PBX proprietário. Para obter os detalhes das capacidades, consulte cada fornecedor diretamente.

Quando você estiver pronto para implantar um gateway SIP/CSTA que possa se integrar ao Lync Server para o controle de chamada remota, consulte o fornecedor do gateway ou sua documentação para ver a sintaxe exigida pelo gateway para as informações a seguir:

  - URI do Servidor de linha do gateway

  - URI da linha para usuários que serão atribuídos ao gateway

As configurações acima são exigidas durante a configuração do usuário e devem ser especificadas como esperado pelo gateway, para encaminhar e se conectar corretamente ao PBX.

Consulte os fornecedores no site Comunicações Unificadas Abrir Programa de Interoperabilidade da Microsoft em [http://go.microsoft.com/fwlink/p/?linkId=203309](http://go.microsoft.com/fwlink/p/?linkid=203309).

## Etapa 2: Configurar o Lync Server para rotear solicitações CSTA para o gateway SIP/CSTA

Você deve criar rotas estáticas nos pools do Lync Server para o endereço de destino (URI de servidor) de todos os gateway SIP/CSTA em sua implantação para os quais pretende encaminhar as solicitações de controle de chamada remota. Crie também uma entrada de aplicativo confiável que corresponda a cada endereço de destino. Quando você designa o gateway como um aplicativo confiável, ele recebe o status de confiável para executar como parte do ambiente Lync Server, mesmo que seja desenvolvido por um terceiro (e execute o que é chamado de *serviço externo* por ser um serviço não incorporado ao produto). Por fim, se o Lync Server irá se conectar ao gateway SIP/CSTA usando uma conexão TCP e não TLS, você também deve definir o endereço IP do gateway usando o Construtor de Topologias.

Para obter os detalhes de como configurar rotas estáticas, consulte [Configurar uma rota estática para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md).

Para obter os detalhes de como configurar entradas de aplicativo confiável, consulte [Configurar uma entrada de aplicativo confiável para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md).

Para obter os detalhes de como definir um endereço IP do gateway SIP/CSTA no Construtor de Topologias, consulte [Definir um endereço SIP de gateway SIP/CSTA no Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md).

## Etapa 3: Configurar os usuários do Lync para controle de chamada remota

Depois que os usuários foram habilitados para o Lync Server, você pode usar o Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server para habilitá-los para o controle de chamada remota. É durante esta etapa da implementação que você atribui a cada usuário um URI de servidor de linha e um URI de linha. O URI do servidor de linha é o URI SIP do gateway SIP/CSTA que você planeja atribuir ao usuário. O URI de linha é o número de telefone exclusivo atribuído ao usuário.

Para obter os detalhes de como configurar os usuários para o controle de chamada remota, consulte [Habilitar usuários do Lync para controle de chamada remota no Lync Server 2013](lync-server-2013-enable-lync-users-for-remote-call-control.md).

## Etapa 4: Defina as regras de normalização do número de telefone do Lync Server

Nos cenários de controle de chamada remota, o Lync Server usa as regras de normalização do número de telefone para converter os números de telefone que ele recebe do gateway SIP/CSTA no formato E.164. Os números de telefone devem estar neste formato padronizado para que certos recursos do controle de chamada remota funcionem corretamente. O controle de chamada remota utiliza as mesmas regras de normalização do número de telefone que você configura para o Serviço de Agenda, que são diferentes das regras usadas para o Enterprise Voice.

Para obter detalhes sobre como o controle de chamada remota usa as regras de normalização do número de telefone, consulte [Normalização de controle de chamada remota e de número de telefone no Lync Server 2013](lync-server-2013-remote-call-control-and-phone-number-normalization.md). Para obter detalhes sobre as regras de normalização de número de telefone para o Serviço de Catálogo Telefônico, consulte o tópico [Administrando o serviço de catálogo de endereços no Lync Server 2013](lync-server-2013-administering-the-address-book-service.md) na documentação de Operações.

