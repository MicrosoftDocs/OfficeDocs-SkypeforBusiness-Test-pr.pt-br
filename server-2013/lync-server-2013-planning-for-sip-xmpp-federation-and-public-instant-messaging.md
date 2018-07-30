---
title: Planejamento para SIP, federação XMPP e mensagens instantâneas públicas no Lync Server 2013
TOCTitle: Planejamento para SIP, federação XMPP e mensagens instantâneas públicas no Lync Server 2013
ms:assetid: 3b234d92-b9ff-4b1d-910e-084c6f17e751
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204825(v=OCS.15)
ms:contentKeyID: 49306446
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejamento para SIP, federação XMPP e mensagens instantâneas públicas no Lync Server 2013

 

_**Tópico modificado em:** 2013-10-28_

O Servidores de Borda pode ser configurado para permitir que seus usuários internos ou externos tenham acesso a contatos em organizações ou serviços de parceiros. As federações, como são conhecidos esse acordos entre parceiros, podem oferecer qualquer uma ou todas as seguintes opções aos contatos de sua organização na federação do parceiro ou contatos na federação do parceiro para sua organização:

  - Mensagens instantâneas e presença

  - Colaboração e conferências, por exemplo, Webconferência

  - Conferência de áudio, conferência de vídeo ou ambas

Em alguns casos, a comunicação, por exemplo, IM (mensagens instantâneas) ou presença entre o Microsoft Lync Server 2013 e um contato XMPP (Extensible Messaging and Presence Protocol) é apenas ponto a ponto e dá suporte apenas a você e ao parceiro federado. Em outros casos, como o Lync Server, o Lync Server 2010 para a federação do Lync Server 2013, múltiplos participantes podem ser convidados para ingressar na conversa.

## Federação do Lync Server e do Office Communications Server

A federação entre o Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server suporta comunicações de ponto a ponto e de várias partes. As conversas de ponto a ponto podem ser posicionadas para conversas de várias partes, permitindo reuniões locais. Reuniões - Conferência da Web ou conferências áudio/visual - podem ser programadas para incluir contatos dentro da sua organização, assim como contatos em parceiros que você federar.

A federação apareceu pela primeira vez no Microsoft Office Live Communications Server 2005 e suportava um tipo de federação, a Federação Direta. A Federação Direta exigia que você conhecesse o domínio SIP do parceiro da federação e o FQDN do Servidor de Borda do parceiro. O Live Communications Server 2005 com SP1 introduziu outros tipos de federação, todos os quais exigem que os registros SRV DNS sejam publicados para parceiro federado para localizar sua Servidor de Borda. A terminologia para esta versão foi::

  - *Federação Avançada Aberta*: aceita qualquer nome de domínio SIP e usa SRV DNS para localizar o parceiro Servidor de Borda

  - *Federação Avançada*: configure o nome de domínio SIP do parceiro como um parceiro de federação para sua organização e use SRV DNS para encontrar o parceiro Servidor de Borda

  - *Federação Direta*: configure o nome de domínio SIP do parceiro e o FQDN para o Servidor de Borda do parceiro.

  - *Lista de Permissão do Servidor*: aceita qualquer domínio, use o SRV DNS para encontrar o Servidor de Borda de um provedor hospedador ou um provedor de conectividade de IM pública

O Microsoft Office Communications Server 2007 introduziu nomeação atualizada para tipos de federação para definir melhor quais tipos de federação realmente foi realizada:

  - A Federação Avançada Aberta se tornou *Domínio de Parceiro Descoberto*

  - A Federação Avançada se tornou *Domínio de Parceiro Permitido*

  - A Federação Direta se tornou *Servidor de Parceiro Permitido*

  - A Lista de Permissão do Servidor se tornou *Provedor de Hospedagem* e *Provedor IM Público*

O Microsoft Lync Server 2010 introduziu uma definição mais detalhada do Provedor de Hospedagem de acordo com o Microsoft Lync Online 2010 e Microsoft Office 365 e também o tornou sujeito à mesma lista de permissão definida pelo tipo de federação de Domínio de Parceiro Permitido.

Habilitar a federação entre Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server usa o Servidores de Borda e proxies inversos para forçar as regras e os domínios de parceiro permitido que você definir. Em uma perspectiva de planejamento, a federação com outro Lync Server, Office Communications Server exige o seguinte:

  - Habilitar federação no Construtor de Topologia. Para obter detalhes, consulte o tópico de Implantação [Configurando federação SIP, federação XMPP e sistema de mensagens instântaneas público no Lync Server 2013](lync-server-2013-configuring-sip-federation-xmpp-federation-and-public-instant-messaging.md).

  - Determine seus requisitos para descoberta do domínio federado:
    
       Para a configuração manual da federação, você deve ter o FQDN do Servidor de Borda do parceiro e o nome do domínio, ou nome do domínio online, que é inserido no Painel de Controle do Lync Server, **Acesso Externo e Federação**, **Domínio Federados SIP**. Crie uma **Nova** política ou **Edite** uma política existente para permitir ou bloquear domínios pelo FQDN.
        

        > [!WARNING]
        > A configuração manual de um Servidor de Borda parceiro de federação é propensa a falhar em casos onde o parceiro muda o endereço IP de seu Servidor de Borda.

        
        > [!NOTE]  
        > Para <strong>Novos domínios federados SIP</strong>, você deve fornecer o <strong>Nome de domínio (ou FQDN)</strong> para Microsoft Lync Online, Microsoft Office 365. Para o Microsoft Lync Server 2013, Lync Server 2010 e Office Communications Server você também deve fornecer um <strong>Serviço de Borda de Acesso (FQDN)</strong>    
       Para federação de parceiro descoberto, onde os parceiros podem descobrir seu Servidor de Borda, você pode criar um registro SRV em seu DNS externo - \_sipfederationtls.\_tcp.contoso.com – que aponta para a porta 5061 e o registro de host (A) de seu Servidor de Borda
        
        > [!IMPORTANT]  
        > Se você estiver dando suporte aos clientes do Microsoft Lync Mobile no Windows Phone ou no Apple iPhone, iPad, ou em outros dispositivos da Apple e estiver usando o Serviços de Notificação por Push ou Serviços de Notificação por Push, você deve planejar para o_sipfederationtls._tcp. <em>&lt;Domínio SIP&gt;</em> registros SRV para cada domínio SIP que você possui clientes do Lync Mobile. O Android e Nokia Symbian Lync Mobile não utilizam a notificação de push e não estão sujeitos a essa exigência.

  - Configurar as políticas de acesso externo para dar suporte a domínios federados

  - Abra portas de firewall para SIP, webconferência e áudio/visual para acomodar a federação ou contatos que você estiver habilitando. Para obter detalhes, consulte: [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md)

As seguintes informações o ajudarão a definir os requisitos de DNS, porta/protocolo e certificado para a federação com o Microsoft Lync Server 2013 e o Lync Server 2010.

O planejamento de certificados, firewall e requisitos de porta/protocolo e requisitos de DNS é geralmente um processo simplificado se você planejou ou implantou seu Microsoft Lync Server 2013 Servidores de Borda. Como a federação é um recurso adicional que utiliza o Servidor de Borda existente, os requisitos de planejamento são geralmente atendidos pelo planejamento e implantação do Servidor de Borda. Você deve usar as seguintes tabelas para determinar quais de seus requisitos são atendidos e fazer mudanças na porta/protocolo e DNS da mesma forma.

> [!IMPORTANT]  
> Se você possui um pool de Servidores de Borda e estiver federando com parceiros do Lync Server 2013 ou Lync Server 2010, é possível usar o balanceamento de carga DNS ou balanceadores de carga de hardware em lados internos e externos do Servidores de Borda. Se você estiver federando com o Office Communications Server 2007 ou o Office Communications Server 2007 R2, o balanceamento de carga de hardware oferecerá suporte de failover no evento de um Servidor de Borda. O Office Communications Server 2007 e Office Communications Server 2007 R2 não têm balanceamento de carga DNS. O Servidores de Borda parceiro irá estabelecer comunicação com o primeiro Servidor de Borda em seu pool que responde. Se esse Servidor de Borda falhar, a comunicação não realizará um failover automaticamente.

Os requisitos de certificado são geralmente atendidos através do planejamento de certificados para seu Servidor de Borda escolhido ou plano do Servidor de Borda agrupado.

## Conectividade de Mensagens Instantâneas Públicas

A Conectividade do Sistema de Mensagens Instantâneas Públicas é uma classe de federação e está configurada para permitir que seus usuários internos e externos do Lync Server 2013 adicionem contatos a partir de qualquer uma das seguintes opções:

  - Contatos do Messenger

  - Contatos do Yahoo\!

  - Contatos do America Online (AOL)

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1° de setembro de 2012, a PIC USL (Licença de Assinatura de Usuário da Conectividade de Mensagens Instantâneas Públicas) do Microsoft Lync não está mais disponível para compra nos contratos novos ou renovados. Os clientes com licenças ativas poderão continuar a federar o Yahoo! Messenger até a data de encerramento do serviço (a data exata ainda será decidida, mas não será antes de junho de 2013).</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por usuário e por mês exigida para que o Lync Server ou o Office Communications Server faça a federação com o Yahoo! Messenger. A capacidade de a Microsoft oferecer esse serviço tem sido dependente do suporte do Yahoo!, cujo contrato subjacente não será renovado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


Essa classe de federação requer as seguintes considerações de planejamento:

  - Os usuários do Windows Live Messenger podem ter comunicação audiovisual ponto a ponto com usuários do Lync Server 2013, além do sistema de mensagens instantâneas. Suas Servidores de Borda devem atender a requisitos de portas e protocolos específicos. Para obter detalhes, consulte [Determinar firewall A/V externo e requisitos de porta para Lync Server 2013](lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md).

  - O sistema de mensagens instantâneas do Yahoo não tem exigências exclusivas, a não ser as geralmente usadas no planejamento e na implantação da Servidor de Borda típica que está fornecendo a federação.

  - A America Online requer que o certificado de sua Servidor de Borda atribuída ao Serviço de Borda de Acesso tenha um EKU (uso avançado de chave).

## Mensagens Extensíveis e Federação de Protocolo de Presença (XMPP)

As versões anteriores do Lync Server e Office Communications Server forneceram um gateway de protocolo XMPP que poderia ser implantada como uma função de servidor separada para permitir a federação com implantações de XMPP. No Microsoft Lync Server 2013, a funcionalidade XMPP pode ser implantada como um recurso. A funcionalidade XMPP é instalada em duas partes: como um proxy XMPP que funciona no Servidor de Borda e o gateway XMPP que funciona no Servidores Front-End.

A implantação e configuração do XMPP são abordadas no [Implantação de acesso do usuário externo no Lync Server 2013](lync-server-2013-deploying-external-user-access.md) Planeje o suporte a XMPP em sua organização definindo as regras de porta e de protocolo em seu firewall, a configuração de certificados, e adicionando registros DNS. Os tópicos a seguir nesta seção resumem as informações necessárias para planejar federação XMPP com sucesso para sua implantação.

> [!IMPORTANT]  
> O recurso XMPP do Lync Server 2013 é testado pela Microsoft e ela oferece suporte para federação de mensagens instantâneas com o Google Talk. Para quaisquer outros sistemas XMPP, entre em contato com o fornecedor do mesmo para verificar se eles suportam federação com o Lync Server 2013, e para quaisquer recomendações de implantação ou solução de problemas.

> [!IMPORTANT]  
> Federação XMPP não é suportada para usuários que são hospedados em aparelhos de filial persistentes. Isso se aplica tanto à visualização de informações de presença quanto à troca de mensagens de IM.

Os tópicos a seguir contêm orientações para a definição de certificados, portas de firewall e entradas de DNS para os tipos de cenários de federação com suporte.

   [Resumo de certificado - SIP, federação XMPP e mensagens instantâneas públicas](lync-server-2013-certificate-summary-sip-xmpp-federation-and-public-instant-messaging.md)

   [Resumo de porta - SIP, federação XMPP e mensagens instantâneas públicas](lync-server-2013-port-summary-sip-xmpp-federation-and-public-instant-messaging.md)

   [Resumo de DNS - SIP, federação XMPP e mensagens instantâneas públicas](lync-server-2013-dns-summary-sip-xmpp-federation-and-public-instant-messaging.md)

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

