---
title: 'Lync Server 2013: Gerenciando de federação e acesso externo ao Lync Server 2013'
TOCTitle: Gerenciando de federação e acesso externo ao Lync Server 2013
ms:assetid: 26f806c1-f284-4637-b06b-06270336c540
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520966(v=OCS.15)
ms:contentKeyID: 49306193
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando de federação e acesso externo ao Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A implantação de um Servidor de Borda ou um pool de Borda é a primeira etapa para oferecer suporte a usuários externos. Para obter detalhes sobre como implantar os Servidores de Borda, consulte [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) na documentação Implantação.

Após instalar e configurar sua implantação interna do Lync Server 2013, os usuários internos na sua organização podem colaborar com outros usuários internos que possuem contas SIP em seus Serviços de Domínio do Active Directory (AD DS). A colaboração pode incluir o envio e recebimento de mensagens instantâneas e a atualização do status de presença e participação nas conferências (também conhecido como "reuniões). Você habilita e configura o acesso do usuário externo para controlar se os usuários externos suportados podem colaborar com usuários internos do Lync Server. Os usuários externos podem incluir usuários remotos da sua implantação, usuários federados (incluindo usuários suportados de provedores de serviço de mensagem instantânea (IM) pública, federação XMPP e participantes anônimos em conferências.

Se sua implantação incluiu a instalação de um Lync Server 2013  Servidor de Borda ou um Pool de borda, o escopo dos possíveis tipos de comunicação é muito aumentado com um número de opções para acesso do usuário externo, comunicação com membros de outros domínios federados SIP, provedores federados SIP e usuários federados XMPP. Após configurar o Servidor de Borda ou Pool de borda, é possível habilitar os tipos de acesso de usuário externo que você deseja oferecer e configurar as políticas para controlar o acesso externo. No Lync Server 2013, você habilita e configura o acesso do usuário externo e as políticas utilizando o Painel de Controle do Lync Server, o Shell de Gerenciamento do Lync Server ou ambos, com base nos requisitos da tarefa. Para obter detalhes sobre estas ferramentas de gerenciamento, consulte [Ferramentas administrativas do Lync Server 2013](lync-server-2013-lync-server-administrative-tools.md) na documentação de Operações, [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md) na documentação de Operações e [Instalar ferramentas administrativas do Lync Server 2013](lync-server-2013-install-lync-server-administrative-tools.md) na documentação de Operações.

> [!IMPORTANT]  
> Ao projetar sua configuração e políticas para acesso do usuário externo, você deve compreender a precedência das políticas e como as políticas são aplicadas. As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto.

Por padrão, nenhuma política é configurada para suportar acesso do usuário externo, incluindo acesso do usuário remoto, acesso do usuário federado, mesmo se você já habilitou o suporte de acesso do usuário externo para sua organização. Para controlar o uso do acesso de usuário externo, você deve configurar uma ou mais políticas, especificando o tipo de acesso do usuário externo suportado para cada política. Isto inclui as seguintes políticas de acesso externo:

  - **Política global**   A política global é criada quando você implanta seus Servidores de Borda. Por padrão, nenhuma opção de acesso de usuário externo está habilitada na política global. Para suportar o acesso de usuário externo em nível global, configure a política global para suportar um ou mais tipos de opções de acesso de usuário externo. A política global se aplica a todos os usuários na sua organização, mas as políticas de site e de usuário substituem a política global. Se você excluir a política global, ela não será removida. Em vez disso, ela será redefinida para a configuração padrão.

  - **Política de site**   Você pode criar e configurar uma ou mais políticas de site para limitar o suporte ao acesso de usuário externo para sites específicos. A configuração da política de site substitui a política global, mas somente para o site específico coberto pela política de site. Por exemplo, se você habilitar o acesso de usuário remoto na política global, deve ser especificada uma política de site que desabilita o acesso de usuário remoto para um site específico. Por padrão, uma política do site é aplicada a todos os usuários do site, mas você pode atribuir uma política de usuário para um usuário para substituir a configuração da política do site.

  - **Política de usuário**   Você pode criar e configurar uma ou mais políticas de usuário para limitar o suporte para acesso de usuário remoto a usuários específicos. A configuração da política de usuário substitui a política global e de site, mas somente para os usuários específicos para os quais a política de usuário for atribuída. Por exemplo, se você habilitar o acesso de usuário remoto na política global e de site, deve ser especificada uma política de usuário que desabilita o acesso de usuário remoto e, em seguida, atribuir essa política de usuário para usuários específicos. Se você criar uma política de usuário, você deve aplicá-la a um ou mais usuários antes que ela entre em vigor.

Para determinar quais definições de configurações e quais políticas você precisa criar ou editar, consulte os seguintes pontos de decisão:

**Deseja permitir que usuários internos e externos do seu domínio possam colaborar usando mensagem instantânea, conferência da Web e Áudio/Vídeo?**

Definir as configurações conforme detalhado nos tópicos [Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013](lync-server-2013-configure-policies-to-control-remote-user-access.md) e [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md)

**Deseja permitir que usuários anônimos participem e sejam convidados para conferências hospedadas por usuários em sua implantação?**

Definir as configurações, conforme detalhado no tópico [Atribuir políticas de conferência para suporte de usuários anônimos no Lync Server 2013](lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md), [Criar ou Modificar uma Política de Conferência no Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md) e [Referência das configurações da política de conferência para Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md)

**Deseja permitir que os usuários se comuniquem com contatos do Domínio Federado SIP?**

Definir as configurações, conforme detalhado nos tópicos [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md), [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) e [Gerenciar domínios SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)

**Se você habilitou a comunicação com Domínios Federados SIP, deseja habilitar comunicações com contatos do Parceiro Federado XMPP?**

Definir as configurações, conforme detalhado no tópico [Configurar políticas para controlar o acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md) e [Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md).

**Se você habilitou a comunicação com Domínios Federados SIP, deseja habilitar a descoberta automática da Federação SIP?**

Definir as configurações, conforme detalhado no tópico [Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013](lync-server-2013-enable-or-disable-discovery-of-federation-partners.md).

**Se você habilitou a comunicação com Domínios Federados SIP, você não desejam habilitar o envio de uma declaração para contatos Federados notificando-os que você usa o arquivamento e as comunicações podem ser arquivadas?**

Definir as configurações, conforme detalhado no tópico [Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados no Lync Server 2013](lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md).

**Não deseja permitir que os usuários se comuniquem com Provedores Federados SIP que permitem a comunicação com provedores públicos, como Windows Live Messenger, AOL e Yahoo\!?**

Definir as configurações, conforme detalhado nos tópicos [Configurar políticas para controlar o acesso de usuário público no Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)[Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) e [Criar ou editar fornecedores SIP públicos federados no Lync Server 2013](lync-server-2013-create-or-edit-public-sip-federated-providers.md).

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


**Deseja permitir que os usuários se comuniquem com Provedores Federados SIP hospedados executando o Microsoft Office 365, Microsoft Lync Online e Microsoft Lync Online 2010?**

Definir as configurações, conforme detalhados nos tópicos [Criar ou editar fornecedores SIP públicos federados no Lync Server 2013](lync-server-2013-create-or-edit-public-sip-federated-providers.md), [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) e [Criar ou editar provedores hospedados federados SIP no Lync Server 2013](lync-server-2013-create-or-edit-hosted-sip-federated-providers.md)

**Sua implantação está configurada em um domínio dividido (também conhecido como híbrido), onde alguns usuários possuem seus servidor inicial em uma implantação local e outros usuários configurados com um servidor inicial em um ambiente online?**

Definir as configurações, conforme detalhados nos tópicos [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md), [Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013](lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md) e [Criar ou editar provedores hospedados federados SIP no Lync Server 2013](lync-server-2013-create-or-edit-hosted-sip-federated-providers.md)

Se você prefere uma tabela que lista os requisitos:


<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th>Guia na Federação e Acesso Externo (Across) Tipo de Acesso Externo ou Federação (Down)</th>
<th>Política de Acesso Externo</th>
<th>Configuração de Borda de Acesso</th>
<th>Domínios Federados SIP</th>
<th>Provedores Federados SIP</th>
<th>Parceiro Federado XMPP</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Usuários Remotos</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-remote-user-access.md">Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Contatos Federados SIP</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Configurar políticas para controlar acesso de usuário federado no Lync Server 2013</a></p>
<p></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p>
<p><a href="lync-server-2013-enable-or-disable-discovery-of-federation-partners.md">Habilitar ou desabilitar descoberta de parceiros de federação no Lync Server 2013</a></p>
<p><a href="lync-server-2013-enable-or-disable-sending-an-archiving-disclaimer-to-federated-partners.md">Habilitar ou desabilitar o envio de um aviso de isenção de responsabilidade de Arquivamento a parceiros federados no Lync Server 2013</a></p></td>
<td><p><a href="lync-server-2013-manage-sip-federated-domains-for-your-organization.md">Gerenciar domínios SIP federados para sua organização no Lync Server 2013</a></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Contatos Federados XMPP</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Configurar políticas para controlar acesso de usuário federado no Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md">Configurar políticas para controlar o acesso de usuário federado no Lync Server 2013</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md">Gerenciar parceiros XMPP federados no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Domínio Dividido/Usuários Híbridos</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-federated-user-access.md">Configurar políticas para controlar acesso de usuário federado no Lync Server 2013</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-create-or-edit-hosted-sip-federated-providers.md">Criar ou editar provedores hospedados federados SIP no Lync Server 2013</a></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Contatos de Serviço de IM Público</p></td>
<td><p><a href="lync-server-2013-configure-policies-to-control-public-user-access.md">Configurar políticas para controlar o acesso de usuário público no Lync Server 2013</a></p></td>
<td><p><a href="lync-server-2013-enable-or-disable-federation-and-public-im-connectivity.md">Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013</a></p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-create-or-edit-public-sip-federated-providers.md">Criar ou editar fornecedores SIP públicos federados no Lync Server 2013</a></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Acesso do usuário anônimo para reuniões e conferências</p></td>
<td><p></p></td>
<td><p><a href="lync-server-2013-assign-conferencing-policies-to-support-anonymous-users.md">Atribuir políticas de conferência para suporte de usuários anônimos no Lync Server 2013</a></p>
<div class="alert">
> [!NOTE]  
> Você também deve considerar as seguintes definições de configuração nas políticas de Configuração: <a href="lync-server-2013-create-or-modify-a-conferencing-policy.md">Criar ou Modificar uma Política de Conferência no Lync Server 2013</a> e <a href="lync-server-2013-conferencing-policy-settings-reference.md">Referência das configurações da política de conferência para Lync Server 2013</a>
</div></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


É possível definir as configurações de acesso de usuário externo, incluindo quaisquer políticas que você deseja usar para controlar o acesso de usuário externo, mesmo se você não tiver habilitado o acesso de usuário externo para sua organização. No entanto, as políticas e outras configurações que você definir entrarão em vigor somente quandoo acesso de usuário externo estiver habilitado para sua organização. Usuários externos não podem se comunicar com usuários de sua organização quando o acesso de usuário externo estiver desabilitado ou se não houver políticas de acesso de usuário externo configuradas para oferecer suporte a ele.

Sua implantação de borda autentica os tipos de usuários externos (exceto para usuários anônimos que são autenticados pela ID de conferência e uma senha enviada para o participante anônimo ao criar a conferência e convidar participantes) e controla o acesso com base no modo como você configura o suporte de borda. Para controlar a comunicação através do firewall, é possível configurar uma ou mais políticas e definir outras configurações que definem como os usuários de dentro e fora do firewall se comunicam entre si. Isso inclui a política global para acesso de usuário externo, além de políticas de usuário e de site que você pode criar e configurar para habilitar um ou mais tipos de acesso de usuário externo para sites ou usuários específicos.

## Nesta seção

  - [Gerenciar política de acesso externo no Lync Server 2013](lync-server-2013-manage-external-access-policy-for-your-organization.md)

  - [Gerenciar configuração da borda de acesso para sua organização no Lync Server 2013](lync-server-2013-manage-access-edge-configuration-for-your-organization.md)

  - [Gerenciar domínios SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)

  - [Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

  - [Gerenciar parceiros XMPP federados no Lync Server 2013](lync-server-2013-manage-xmpp-federated-partners-for-your-organization.md)

  - [Configurando o suporte de federação para um cliente do Lync Online](lync-server-2013-configuring-federation-support-for-a-lync-online-customer.md)

