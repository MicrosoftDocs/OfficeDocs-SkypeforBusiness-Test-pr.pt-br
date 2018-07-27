---
title: 'Lync Server 2013: Habilitar ou desabilitar federação e conectividade de IM pública'
TOCTitle: Habilitar ou desabilitar federação e conectividade de IM pública
ms:assetid: 8ec58f4b-9f6d-47b4-a187-d18a83fe4577
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182549(v=OCS.15)
ms:contentKeyID: 49307431
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar ou desabilitar federação e conectividade de IM pública no Lync Server 2013

 

_**Tópico modificado em:** 2013-06-24_

O suporte para federação é necessário para permitir que os usuários que possuem uma conta com um cliente confiável ou com uma organização parceira, incluindo domínios parceiros e usuários de provedores públicos de IM (serviços de mensagens instantâneas) aos quais você oferece suporte, colaborem com os usuários em sua organização. A federação também é necessária para usar um provedor de serviço do Exchange hospedado, para fornecer correio de voz aos usuários do Enterprise Voice cujas caixas de correio estão localizadas em um serviço do Exchange hospedado, como o Microsoft Exchange Online. Após estabelecer um relacionamento confiável com esses domínios externos, é possível autorizar os usuários nesses domínios a acessar sua implantação e participar das comunicações do Lync Server. Essa relação de confiança é chamada de federação e não tem associação ou dependência com uma relação de confiança do Active Directory.

Para suportar o acesso pelos usuários dos domínios federados, é necessário habilitar a federação. Se você habilitar a federação para sua organização, também será necessário especificar se as seguintes opções devem ser implementadas:

  - **Permitir a descoberta do domínio parceiro**    Se você habilitar essa opção, o Lync Server usará os registros DNS (Sistema de Nomes de Domínio) para tentar descobrir domínios não listados na lista de domínios permitidos, avaliando automaticamente o tráfego de entrada de parceiros federados descobertos e limitando ou bloqueando esse tráfego com base no nível de confiança, quantidade de tráfego e configurações de administrador. Se você não selecionar essa opção, o acesso ao usuário federado será habilitado somente para usuários nos domínios que você incluiu na lista de domínios permitidos. Mesmo que você não selecione essa opção, é possível especificar o bloqueio ou permissão de domínios individuais, incluindo restrição do acesso a servidores específicos executando o serviço Borda de Acesso no domínio federado. Para obter detalhes sobre como controlar o acesso dos domínios federados, consulte [Configurar suprote para domínios externos permitidos no Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md).

  - **Enviar um aviso de isenção de responsabilidade de arquivamento aos parceiros federados**     O aviso de isenção de responsabilidade de arquivamento é enviado aos parceiros federados a fim de orientá-los de que as comunicações são gravadas. Se você suportar o arquivamento de comunicações externas com domínios de parceiro federado, habilite a notificação do aviso de isenção de responsabilidade de arquivamento a fim de alertar os parceiros de que suas mensagens estão sendo arquivadas

Se posteriormente você quiser impedir o acesso dos domínios federados pelos usuários, de forma permantente ou temporária, você poderá desabilitar a federação para sua organização. Use o procedimento nesta seção para habilitar ou desabilitar o acesso do usuário federado para sua organização, incluindo a especificação das opções de federação apropriadas a serem suportadas para sua organização.

> [!NOTE]  
> A habilitação da federação para sua organização especifica apenas que seus servidores que executam o serviço Borda de Acesso suportam o roteamento para domínios federados. Usuários em domínios federados não podem participar de IM ou conferências em sua organização, até que você também configure pelo menos uma política para suportar o acesso do usuário federado. Usuários de provedores de serviço de IM pública não podem participar de IM ou conferências em sua organização, até que você também configure pelo menos uma política para suportar a conectividade de IM pública. O Lync Server não pode usar um serviço do Exchange hospedado para fornecer atendimento de chamada, Outlook Voice Access (incluindo correio de voz) ou serviços de atendedor automático para usuários cujas caixas de correio estão localizadas em um serviço do Exchange hospedado até que você configure uma política de correio de voz hospedada que forneça informações de roteamento. Para obter detalhes sobre como configurar as políticas para comunicação com usuários de domínios federados em outras organizações, consulte <a href="lync-server-2013-manage-sip-federated-domains-for-your-organization.md">Gerenciar domínios SIP federados para sua organização no Lync Server 2013</a> na documentação de Operações. Além disso, se você quiser suportar a comunicação com usuários de provedores de serviço de IM, é necessário configurar as políticas para suportá-la e também configurar o suporte para provedores de serviço individuais que você deseja suportar. Para obter detalhes, consulte <a href="lync-server-2013-manage-sip-federated-providers-for-your-organization.md">Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013</a> na documentação Implantação ou na documentação Operações. Para obter detalhes sobre como criar uma política de correio de voz hospedada, consulte <a href="lync-server-2013-manage-hosted-voice-mail-policies.md">Gerenciar políticas de caixa postal hospedada no Lync Server 2013</a> na documentação Implantação.

## Para habilitar ou desabilitar o acesso do usuário federado para sua organização

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Acesso de Usuário Externo** e clique em **Configuração da Borda de Acesso**.

4.  Na página **Configuração da Borda de Acesso**, clique em **Global**, **Editar** e em **Exibir detalhes**.

5.  Em **Editar Configuração da Borda de Acesso**, execute um dos procedimentos a seguir:
    
      - Para habilitar o acesso ao usuário federado para sua organização, marque a caixa de seleção **Habilitar comunicações com usuários federados**.
    
      - Para desabilitar o acesso ao usuário federado para sua organização, desmarque a caixa de seleção **Habilitar comunicações com usuários federados**.

6.  Se você marcou a caixa de seleção **Habilitar comunicações com usuários federados**, faça o seguinte:
    
    1.  Se você quiser suportar a descoberta automática de domínios de parceiros, marque a caixa de seleção **Habilitar a descoberta de domínio de parceiro**.
    
    2.  Se sua organização suporta o arquivamento de comunicações externas, marque a caixa de seleção **Enviar aviso de isenção de responsabilidade de arquivamento para parceiros federados**.

7.  Clique em **Confirmar**.

Para habilitar os usuários federados para colaborar com usuários em sua implantação do Lync Server 2013, também é necessário configurar pelo menos uma política de acesso externa para suportar o acesso de usuário federado. Para obter detalhes, consulte [Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md) na documentação Implantação ou na documentação Operações. Para controlar o acesso a domínios federados específicos, consulte [Configurar suprote para domínios externos permitidos no Lync Server 2013](lync-server-2013-configure-support-for-allowed-external-domains.md) na documentação Implantação ou na documentação Operações.

## Ativação e desativação de federação e conectividade de IM pública usando os cmdlets Windows PowerShell

A federação e conectividade de IM pública podem ser também gerenciadas usando o Windows PowerShell e o cmdlet Set-CsAccessEdgeConfiguration. Esse cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para ativar a federação e a conectividade de IM pública

  - Para habilitar a federação e conectividade de IM pública, defina o valor da propriedade **AllowFederatedUsers** como Verdadeira ($True):
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $True

## Para desativar a federação e a conectividade de IM pública

  - Para desabilitar a federação e conectividade de IM pública, defina o valor da propriedade **AllowFederatedUsers** como Falsa ($False):
    
        Set-CsAccessEdgeConfiguration -AllowFederatedUsers $False

