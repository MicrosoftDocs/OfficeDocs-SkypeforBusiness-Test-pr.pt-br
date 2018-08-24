---
title: 'Lync Server 2013: Configurar política de conferência para discagem'
TOCTitle: Configurar política de conferência para discagem
ms:assetid: 9bf926d6-0248-4352-98c3-9c5a333debbc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398810(v=OCS.15)
ms:contentKeyID: 49307589
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar política de conferência para discagem no Lync Server 2013

 

_**Tópico modificado em:** 2014-03-21_

A política de conferência é uma configuração de conta de usuário que especifica a experiência de conferência para os participantes. Você pode criar políticas de conferência com um escopo de site ou um escopo de usuário. As configurações de política de conferência englobam vários aspectos do agendamento da conferência e da participação. Várias configurações de política de conferência oferecem suporte à conferência discada para participantes. Ao configurar a conferência discada, você deve verificar se estes campos foram definidos adequadamente para sua organização e modificá-los conforme necessário.

Verifique os seguintes campos em sua política de conferência:

  - **Permitir que os participantes convidem usuários anônimos**    Esta configuração permite que organizadores de reunião convidem participantes anônimos (ou seja, não autenticados) para reuniões. Esta configuração é opcional para conferência discada e é selecionada por padrão na política de conferência global padrão.

  - **Habilitar conferência discada PSTN**    Esta configuração permite que usuários participem do áudio de uma conferência discando a partir do PSTN. Esta configuração é requerida para conferências discadas e é selecionada por padrão na política de conferência global padrão.

  - **Permitir que os participantes anônimos façam chamadas**    Esta configuração permite que usuários anônimos, que já entraram em uma reunião, disquem para um número de telefone externo para participar da parte de áudio da conferência. Esta configuração é opcional para conferências discadas. Esta configuração não é selecionada por padrão na política de conferência global padrão.

  - **Permitir que os participantes não habilitados para Enterprise Voice façam chamadas**    Esta configuração permite que os participantes e organizadores da reunião, que não estão não habilitados para Enterprise Voice façam chamadas para um número de telefone externo para participar da parte de áudio da conferência. A chamada externa é autorizada baseando-se nas políticas de voz atribuída do organizador. Esta configuração não é selecionada por padrão na política de conferência global padrão. O valor padrão da configuração é desativado.
    
    > [!NOTE]  
    > Para habilitar esse recurso, um organizador da reunião que não está habilitado para Enterprise Voice deve ter uma política de voz adequada atribuída a ele para autorizar a discagem externa a partir de uma conferência organizada por esse usuário. Uma política de voz pode ser atribuída a um usuário que não está habilitado para Enterprise Voice do Shell de Gerenciamento do Lync Server. Se o usuário não tiver uma política de voz atribuída explicitamente a ele, a política de voz do site será utilizada para autorizar a solicitação de discagem externa. Se não houver política de voz do site, a política de voz global será utilizada. 

O procedimento nesta seção descreve como modificar uma política de conferência. Para obter detalhes sobre como configurar todas as configurações que definem a experiência do participante na política de conferência padrão, consulte [Criar ou Modificar um Conjunto de Configurações de Reunião no Lync Server 2013](lync-server-2013-create-or-modify-a-collection-of-meeting-configuration-settings.md). Para obter detalhes sobre como criar uma política de conferência para um usuário ou grupo de usuários específicos, consulte [Criar ou Modificar uma Política de Conferência no Lync Server 2013](lync-server-2013-create-or-modify-a-conferencing-policy.md). Para obter uma lista de todas as configurações de política de conferência disponíveis, consulte [Referência das configurações da política de conferência para Lync Server 2013](lync-server-2013-conferencing-policy-settings-reference.md).

## Para modificar a política de conferência para discagem interna

1.  Faça logon no computador como membro do grupo RTCUniversalServerAdmins ou como membro da função **Cs-ServerAdministrator** ou **CsAdministrator**.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Conferência**.

4.  Na guia **Política de Conferência**, dê um duplo clique no nome de uma política de conferência para abrir a caixa de diálogo **Editar Política de Conferência**.

5.  Verifique se os campos para conferência discada estão de acordo com a sua organização e modifique as configurações se necessário.

6.  Clique em **Confirmar**.

