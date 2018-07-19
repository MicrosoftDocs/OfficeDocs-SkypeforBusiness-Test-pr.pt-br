---
title: 'Lync Server 2013: Configurando suporte para acesso de usuário externo'
TOCTitle: Configurando suporte para acesso de usuário externo
ms:assetid: f8424f8c-f965-4414-8485-30f07e10214a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413051(v=OCS.15)
ms:contentKeyID: 49308663
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando suporte para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Implantar um Servidor de borda ou um pool de Borda é a primeira etapa para suportar usuários externos. Para obter detalhes sobre a implantação de Servidores de borda, consulte [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação de Implantação. Uma consideração importante sobre a configuração de políticas é entender a precedência das políticas e como elas são aplicadas. As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto.

Após concluir a configuração de um servidor de borda ou pool de borda, você deve habilitar os tipos de acesso do usuário externo que deseja oferecer e, depois, definir as configurações do acesso externo. Em Lync Server 2013, habilite e configure o acesso e as políticas do usuário externo usando o Painel de Controle do Lync Server, o Shell de Gerenciamento do Lync Server ou os dois, com base nos requisitos da tarefa.

Para suportar o acesso de usuário externo, você deve fazer o seguinte:

  - **Habilitar o suporte da sua organização** Para habilitar o suporte para acesso de usuário externo na sua implantação, habilite cada tipo de acesso externo que deseja suportar. Você habilita e desabilita o suporte para acesso de usuário externo editando as configurações globais ou criando e configurando uma política de usuário ou local na página de **Política de acesso externo** no grupo **Acesso externo e federação** do Painel de Controle do Lync Server ou usando o cmdlet Shell de Gerenciamento do Lync Server e os cmdlets associados. Os cmdlets para gerenciar a **Política de acesso externo** podem ser encontrados no tópico [Cmdlets de federação e acesso externo no Lync Server 2013](https://docs.microsoft.com/en-us/powershell/module/skype/). Habilitar o suporte para acesso externo especifica que seus servidores executando o Lync Server  Serviço de Borda de Acesso suporta comunicações com usuários e servidores externos. Os usuários externos e internos não podem se comunicar quando o acesso de usuário externo está desabilitado ou se nenhuma política estiver configurada para suportá-los.

  - **Configurar e atribuir uma ou mais políticas** Para suportar o acesso de usuário externo, você configura políticas para abordar os requisitos que incluem:
    
      - **Políticas de acesso externo** Criadas com um escopo de site ou usuário (uma política global existe por padrão e não tem configurações para ser habilitada). Você cria e configura políticas para controlar o uso de um ou mais tipos de acesso de usuário externo, incluindo o acesso para usuários federados (incluindo, se selecionado, domínios XMPP federados), o acesso para usuários remotos e o acesso para provedores de serviço de IM público suportados. Você configura as políticas externas no Painel de Controle do Lync Server usando a política global ou uma ou mais políticas do usuário e local criadas para administração, na página **Política de acesso externo** no grupo **Acesso externo e federação** . A política global não pode ser excluída. Você cria e configura qualquer política do usuário e local que deseja usar para limitar o acesso de usuário externo a locais ou usuários específicos. As políticas locais e globais são atribuídas automaticamente. Se você criar e configurar uma política de usuário, deve atribui-las a usuários específicos usando a página de configuração do usuário no Painel de Controle do Lync Server na página **Usuários** . Localize o usuário ou os usuários aos quais deseja aplicar esta política e atribua a política. Para atribuir uma política de usuário configurada a um usuário, consulte [Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md). Cada política de acesso do usuário externo pode suportar um ou mais dos seguintes: acesso de usuário remoto, acesso de usuário federado SIP, acesso de usuário federado XMPP e conectividade de IM pública.
    
      - **Políticas de conferência**   Você cria e configura políticas para controlar as conferências na sua organização, incluindo quais usuários na sua organização podem convidar usuários anônimos para as conferências que realizam. Na página Painel de Controle do Lync Server  **Conferências** há configurações de política em escopo global, local e do usuário que controlam as configurações das conferências atuais. Para obter mais informações, consulte [Gerenciando reuniões e conferências no Lync Server 2013](lync-server-2013-managing-meetings-and-conferences.md). Você habilita usuários anônimos, usuários remotos e federados para conferências na página **Configuração da borda de acesso** . A política na **Configuração de borda de acesso** é global em escopo. Não há opções para definir uma política de local ou de usuário. O escopo é controlado na página **Política de acesso externo** por meio da utilização de configurações de políticas globais, de local ou do usuário.
        
        Por exemplo, se você quiser permitir aos usuários criar, convidar e gerenciar conferências com usuários remotos, você deve definir **Habilitar comunicações com usuários remotos** na **Política de acesso externo** global, de local ou do usuário, e **Habilitar comunicações com usuários remotos** na página **Configuração de borda de acesso** . De forma semelhante, para permitir conferências com usuários anônimos ou parceiros federados com os quais você tem um relacionamento definido (como domínios e parceiros SIP federados configurados - a federação XMPP não suporta conferências), você deve definir **Habilitar comunicações com usuários públicos** e **Habilitar comunicações com usuários federados** na **Política de acesso externo** global, de site ou do usuário. Após, você deve selecionar as configurações complementares de política global **Habilitar acesso de usuário anônimo a conferências** e **Habilitar conectividade de IM pública e federada** na página **Configuração da borda de acesso** .

É possível definir as configurações de acesso de usuário externo, incluindo quaisquer políticas que você deseja usar para controlar o acesso de usuário externo, mesmo se você não tiver habilitado o acesso de usuário externo para sua organização. No entanto, as políticas e outras configurações que você definir entrarão em vigor somente quandoo acesso de usuário externo estiver habilitado para sua organização. Usuários externos não podem se comunicar com usuários de sua organização quando o acesso de usuário externo estiver desabilitado ou se não houver políticas de acesso de usuário externo configuradas para oferecer suporte a ele.

Sua implantação de borda autentica os tipos de usuários externos (exceto para usuários anônimos que são autenticados pela ID de conferência e uma senha enviada para o participante anônimo ao criar a conferência e convidar participantes) e controla o acesso com base no modo como você configura o suporte de borda. Para controlar a comunicação através do firewall, é possível configurar uma ou mais políticas e definir outras configurações que definem como os usuários de dentro e fora do firewall se comunicam entre si. Isso inclui a política global para acesso de usuário externo, além de políticas de usuário e de site que você pode criar e configurar para habilitar um ou mais tipos de acesso de usuário externo para sites ou usuários específicos.

## Nesta seção

  - [Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013](lync-server-2013-configure-policies-to-control-remote-user-access.md)

  - [Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013](lync-server-2013-enable-or-disable-remote-user-access.md)

  - [Habilitar ou desabilitar acesso de usuário anônimo no Lync Server 2013](lync-server-2013-enable-or-disable-anonymous-user-access.md)

  - [Atribuir políticas de conferência para suporte de usuários anônimos no Lync Server 2013](lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md)

