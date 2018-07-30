---
title: 'Lync Server 2013: Gerenciar política de acesso externo para sua organização'
TOCTitle: Gerenciar política de acesso externo para sua organização
ms:assetid: 5571811e-34c8-443a-b94c-1ab5d4275581
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520995(v=OCS.15)
ms:contentKeyID: 49306750
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar política de acesso externo no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-07_

Após implantar um ou mais Servidores de Borda, você deverá habilitar os tipos de acesso externo que serão suportados pela sua organização.

Por padrão, não há políticas configuradas para suportar o acesso de usuário externo, incluindo o acesso de usuário remoto, acesso de usuário federado, mesmo que você já tenha habilitado o suporte de acesso de usuário externo para sua organização. Para controlar o uso de acesso de usuário externo, você deve configurar uma ou mais políticas, especificando o tipo de acesso de usuário externo suportado para cada política. Os escopos da política a seguir estão disponíveis para criação e configuração. Por padrão, a política global é criada, mas não pode ser excluída.

  - **Política global**   A política global é criada quando você implanta seus Servidores de Borda. Por padrão, nenhuma opção de acesso de usuário externo está habilitada na política global. Para suportar o acesso de usuário externo em nível global, configure a política global para suportar um ou mais tipos de opções de acesso de usuário externo. A política global se aplica a todos os usuários na sua organização, mas as políticas de site e de usuário substituem a política global. Se você excluir a política global, ela não será removida. Em vez disso, ela será redefinida para a configuração padrão.

  - **Política de site**   Você pode criar e configurar uma ou mais políticas de site para limitar o suporte ao acesso de usuário externo para sites específicos. A configuração da política de site substitui a política global, mas somente para o site específico coberto pela política de site. Por exemplo, se você habilitar o acesso de usuário remoto na política global, deve ser especificada uma política de site que desabilita o acesso de usuário remoto para um site específico. Por padrão, uma política do site é aplicada a todos os usuários do site, mas você pode atribuir uma política de usuário para um usuário para substituir a configuração da política do site.

  - **Política de usuário**   Você pode criar e configurar uma ou mais políticas de usuário para limitar o suporte para acesso de usuário remoto a usuários específicos. A configuração da política de usuário substitui a política global e de site, mas somente para os usuários específicos para os quais a política de usuário for atribuída. Por exemplo, se você habilitar o acesso de usuário remoto na política global e de site, deve ser especificada uma política de usuário que desabilita o acesso de usuário remoto e, em seguida, atribuir essa política de usuário para usuários específicos. Se você criar uma política de usuário, você deve aplicá-la a um ou mais usuários antes que ela entre em vigor.

> [!IMPORTANT]  
> As definições de política do Lync Server que são aplicadas em um nível de política podem substituir definições que são aplicadas em outro nível de política. A precedência de política do Lync Server é: política de Usuário (maior influência) substitui uma política de Site e esta substitui uma política Global (menor influência). Isso significa que, quão mais perto a definição de política está do objeto que ela está afetando, maior a influência que ela terá no objeto.

Essas opções incluem os seguintes tipos de acesso externo:

  - **Habilitar comunicações com usuários federados**    Habilite essa opção se você quiser suportar o acesso de usuário para domínios de parceiros federados. Essa configuração define a capacidade dos usuários de estabelecerem comunicação com outros domínios SIP federados, bem como prestadores hospedados como Microsoft Office 365. Selecionar essa configuração permite que você selecione a opção para permitir a comunicação com domínios XMPP federados.
    
    Como opção, você pode selecionar **Permitir comunicações com parceiros XMPP federados** se você primeiro selecionar **Permitir comunicações com usuários federados** . A federação XMPP é uma federação com organizações que utilizam o XMPP (extensible messaging and presence protocol).
    
    > [!NOTE]  
    > Se você habilitar a federação XMPP, será necessário também selecionar para implantar a <strong>federação XMPP</strong> na seção de configuração do Pools de bordaConstrutor de Topologias. Configurar a federação XMPP implanta um proxy XMPP no Servidor de Borda e um gateway XMPP no Servidor Front-End.

  - **Permitir comunicações com usuários remotos** Habilite essa opção se desejar que os usuários na sua organização fora do firewall, como telecomutadores e usuários que estão viajando, possam se conectar ao Lync Server pela internet.

  - **Habilitar comunicações com usuários públicos**    Habilite essa opção se desejar que os usuários internos sejam capazes de estabelecer comunicação com os contatos do provedor de IM público, como fornecido pelo Windows Live, Yahoo\! e America Online (AOL).
    
    > [!IMPORTANT]  
    > <ul>    
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>    
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>    
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li>    </ul>


> [!NOTE]  
> Além de habilitar o suporte ao acesso de usuário externo, você também deve configurar políticas para controlar o uso do acesso de usuário externo na organização antes de qualquer tipo de acesso de usuário externo estar disponível para os usuários. Para obter detalhes sobre como criar, configurar e aplicar políticas de acesso de usuário externo, consulte <a href="lync-server-2013-enable-or-disable-remote-user-access.md">Habilitar ou desabilitar acesso de usuário remoto no Lync Server 2013</a>.

**Para visualizar as políticas de acesso externo utilizando os cmdlets Windows PowerShell**

  - É possível visualizar as políticas de acesso externo utilizando Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsExternalAccessPolicy**. Você pode executar esse cmdlet do Shell de Gerenciamento do Lync Server 2013 ou a partir de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).
    
    Para visualizar as informações sobre todas as suas políticas de acesso externo, digite o seguinte comando no Shell de Gerenciamento do Lync Server e pressione ENTER:
    
        Get-CsExternalAccessPolicy
    
    Este comando retorna informações semelhantes para o seguinte:
    
        Identity                          : Global
        Description                       :
        EnableFederationAccess            : False
        EnableXmppAccess                  : False
        EnablePublicCloudAccess           : False
        EnablePublicCloudAudioVideoAccess : False
        EnableOutsideAccess               : False

## Nesta seção

  - [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md)

  - [Configurar políticas para controlar o acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-xmpp-federated-user-access.md)

  - [Configurar políticas para controle de acesso de usuário remoto no Lync Server 2013](lync-server-2013-configure-policies-to-control-remote-user-access.md)

  - [Configurar políticas para controlar o acesso de usuário público no Lync Server 2013](lync-server-2013-configure-policies-to-control-public-user-access.md)

  - [Atribuir uma política de usuário externo a um usuário habilitado do Lync no Lync Server 2013](lync-server-2013-assign-an-external-user-access-policy-to-a-lync-enabled-user.md)

  - [Redefinindo ou excluindo políticas de acesso de usuário externo no Lync Server 2013](lync-server-2013-resetting-or-deleting-external-user-access-policies.md)

