---
title: Planejamento para Federação do Servidor Lync Server e Office Communications
TOCTitle: Planejamento para Federação do Servidor Lync Server e Office Communications
ms:assetid: c9eaf06b-054f-41a4-ad0c-499400d6c4c7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205335(v=OCS.15)
ms:contentKeyID: 49308092
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para Federação do Servidor Lync Server e Office Communications

 

_**Tópico modificado em:** 2013-02-13_

Federação entre Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server suporta comunicações ponto a ponto e de várias partes. As conversas ponto a ponto podem ser posicionadas para conversas de várias partes, permitindo reuniões locais. Reuniões - Conferência da Web ou conferências áudio/visual - podem ser programadas para incluir contatos dentro da sua organização, assim como contatos em parceiros que você federar.

A federação apareceu pela primeira vez no Microsoft Office Live Communications Server 2005 e suportou um tipo de federação, Federação Direta. A Federação Direta exige que você conheça o domínio SIP do parceiro de federação e o FQDN do Servidor de Borda do parceiro. O Live Communications Server 2005 com SP1 introduziu outros tipos de federação, todos os quais exigem que os registros SRV DNS sejam publicados para parceiro federado para localizar sua Servidor de Borda. A terminologia para esta versão foi:

  - *Federação Avançada Aberta*: Aceita qualquer nome de domínio SIP e usa SRV DNS para localizar o parceiro Servidor de Borda

  - *Federação Avançada*: Configure o nome de domínio SIP do parceiro como um parceiro de federação para sua organização e usa SRV DNS para encontrar o parceiro Servidor de Borda

  - *Federação Direta*: Configure o nome de domínio SIP do parceiro e o FQDN para o Servidor de Borda parceiro

  - *Lista de Permissão do Servidor*: Aceita qualquer domínio, use o SRV DNS para encontrar o Servidor de Borda de um provedor hospedador ou um provedor de conectividade de IM pública

O Microsoft Office Communications Server 2007 introduziu nomeação atualizada para tipos de federação para definir melhor quais tipos de federação realmente foi realizada:

  - A Federação Avançada Aberta se tornou *Domínio de Parceiro Descoberto*

  - A Federação Avançada se tornou *Domínio de Parceiro Permitido*

  - A Federação Direta se tornou *Servidor de Parceiro Permitido*

  - A Lista de Permissão do Servidor se tornou *Provedor de Hospedagem* e *Provedor IM Público*

O Microsoft Lync Server 2010 introduziu uma definição mais detalhada do Provedor de Hospedagem de acordo com o Microsoft Lync Online 2010 e Microsoft Office 365 e também o tornou sujeito à mesma lista de permissão definida pelo tipo de federação de Domínio de Parceiro Permitido.

Habilitar a federação entre Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server usa o Servidores de Borda e proxies inversos para forçar as regras e os domínios de parceiro permitido que você definir. Em uma perspectiva de planejamento, a federação com outro Lync Server, Office Communications Server exige o seguinte:

  - Habilitar federação no Construtor de Topologia. Para obter detalhes, consulte o tópico de Implantação [Configurando federação SIP, federação XMPP e sistema de mensagens instântaneas público no Lync Server 2013](lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md).

  - Determine seus requisitos para descoberta do domínio federado:
    
       Para configuração manual da federação, você deve ter o FQDN do Servidor de Borda parceiro e o nome de domínio ou um nome de domínio online, que é inserido no Painel de Controle do Lync Server, **Acesso Externo e Federação**, **Domínios Federados SIP**. Crie uma política **Novo** ou **Edite** uma política existente para permitir ou bloquear domínios pelo FQDN.
        

      > [!WARNING]
      > A configuração manual de um Servidor de Borda parceiro de federação é propenso a falhar em casos onde o parceiro mude o endereço IP de seu Servidor de Borda.

        
      > [!NOTE]  
      > Para <strong>Novos domínios federados SIP</strong>, você deve fornecer o <strong>Nome de domínio (ou FQDN)</strong> para Microsoft Lync Online, Microsoft Office 365. Para o Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server você também deve oferecer um <strong>Serviço de Borda de Acesso (FQDN)</strong>    
       Para federação parceira descoberta, onde os parceiros podem descobrir seu Servidor de Borda, você cria um registro SRV em seu DNS externo - \_sipfederationtls.\_tcp.contoso.com – que aponta para a porta 5061 e o registro de host (A) do seu Servidor de Borda
        
      > [!IMPORTANT]  
      > Se você está suportando clientes do Microsoft Lync Mobile no Windows Phone ou Apple iPhone, iPad ou outro dispositivo da Apple e está usando o Serviços de Notificação por Push ou Serviços de Notificação por Push, você deve planejar por _sipfederationtls._tcp. <em>&lt;Domínio SIP&gt;</em> registros SRV para cada domínio SIP que você possui clientes do Lync Mobile. Android e Nokia Symbian Lync Mobile não usam notificações de push e não estão sujeitos a este requisito.

  - Configure políticas de acesso do usuário externo para suportar domínios federados

  - Abra portas de firewall para SIP, conferência da Web e áudio/visual para acomodar a federação ou contatos que estiver habilitando. Para obter detalhes, consulte: [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

A informação a seguir ajudará você na definição do certificado, porta/protocolo e requisitos DNS para federação com o Microsoft Lync Server 2013 e Lync Server 2010.

Planejamento para certificados, firewall e requisitos de porta/protocolo e requisitos de DNS é geralmente um processo simplificado se você planejou ou implantou seu Microsoft Lync Server 2013 Servidores de Borda. Como a federação é um recurso adicional que utiliza o Servidor de Borda existente, os requisitos de planejamento são geralmente atendidos pelo planejamento e implantação do Servidor de Borda. Você deve usar as seguintes tabelas para determinar quais de seus requisitos são atendidos e faz mudanças na porta/protocolo e DNS da mesma forma.

> [!IMPORTANT]  
> Se você possui um pool de Servidores de Borda e estão federando com o Lync Server 2013 ou parceiros do Lync Server 2010, é possível usar o balanceamento de carga DNS ou balanceadores de carga de hardware em lados internos e externos do Servidores de Borda. Se você está federando com Office Communications Server 2007 ou Office Communications Server 2007 R2, o balanceamento de carga de hardware oferecerá suporte de failover no evento de um Servidor de Borda. Office Communications Server 2007 e Office Communications Server 2007 R2 não tem balanceamento de carga DNS. O Servidores de Borda parceiro irá estabelecer comunicação com o primeiro Servidor de Borda em seu pool que responde. Se este Servidor de Borda falhar, a comunicação não realiza um failover automaticamente.

Os requisitos de certificado são geralmente atendidos através do planejamento de certificados para seu Servidor de Borda escolhido ou plano do Servidor de Borda agrupado.

## Nesta seção

  - [Resumo de certificado - SIP, federação XMPP e mensagens instantâneas públicas](lync-server-2013-certificate-summary-sip-xmpp-federation-and-public-instant-messaging.md)

  - [Resumo de porta - SIP, federação XMPP e mensagens instantâneas públicas](lync-server-2013-port-summary-sip-xmpp-federation-and-public-instant-messaging.md)

  - [Resumo de DNS - SIP, federação XMPP e mensagens instantâneas públicas](lync-server-2013-dns-summary-sip-xmpp-federation-and-public-instant-messaging.md)

## Consulte Também

#### Tarefas

[Configurar políticas para controlar acesso de usuário federado no Lync Server 2013](lync-server-2013-configure-policies-to-control-federated-user-access.md)  

#### Conceitos

[Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md)  
[Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)  
[Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md)  

#### Outros Recursos

[Gerenciar configuração da borda de acesso para sua organização no Lync Server 2013](lync-server-2013-manage-access-edge-configuration-for-your-organization.md)  
[Gerenciar domínios SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-domains-for-your-organization.md)  
[Gerenciar fornecedores SIP federados para sua organização no Lync Server 2013](lync-server-2013-manage-sip-federated-providers-for-your-organization.md)

