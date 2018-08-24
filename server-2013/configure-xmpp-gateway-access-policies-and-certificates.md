---
title: Configurar políticas e certificados de acesso ao gateway de XMPP
TOCTitle: Configurar políticas e certificados de acesso ao gateway de XMPP
ms:assetid: fac02f4e-d14d-4be3-b53c-74c82436fd93
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721945(v=OCS.15)
ms:contentKeyID: 49886493
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar políticas e certificados de acesso ao gateway de XMPP

 

_**Tópico modificado em:** 2012-10-15_

A federação XMPP define uma implantação externa com base no Protocolo de mensagens instantâneas e presença extensível (XMPP). Uma configuração de XMPP permite aos usuários Lync acessarem os usuários do domínio XMPP por:

  - IM e presença - apenas entre duas pessoas

  - Criação de contatos federados XMPP no cliente Lync

Quando configurar as políticas para suprote dos parceiros federados de protocolo de mensagens instantâneas e presença extensível (XMPP), as políticas se aplicam a usuários de domínios federados de XMPP, mas não em usuários de provedores de serviço de mensagem instantânea (IM) do protocolo de início de sessão (SIP) (por exemplo, Windows Live) ou domínios federados SIP. Configure um parceiro federado XMPP para cada domínio federado XMPP que desejar para permitir que os usuários adicionem contatos e se comuniquem entre si. Quando as políticas forem implementadas, você deve configurar os certificados de Gateway de XMPP.

> [!NOTE]  
> Para iniciar a migração do Gateway de XMPP, você deve implantar o Lync Server 2013 Gateway de XMPP e configurar as políticas de acesso para habilitar os usuários ao Lync Server 2013 Gateway de XMPP. Todos os usuários devem ser movidos à implantação de Lync Server 2013 antes de realizar essas etapas. Para detalhes, consulte <a href="configure-xmpp-gateway-on-lync-server-2013.md">Configurar gateway XMPP no Lync Server 2013</a>.

## Configure uma Política de Acesso Externo para habilitar os usuários ao Gateway do XMPP do Lync Server 2013

1.  Abrir o Painel de Controle do Lync Server.

2.  Na barra de navegação à esquerda, clique em **Acesso Externo e Federação** e clique em **Política de Acesso Externo** .

3.  Clique em **Novo** e em **Política do usuário** .

4.  Insira um nome para a política de acesso externo do usuário.

5.  Forneça uma descrição para a política de acesso externo do usuário.

6.  Selecione **Habilitar comunicações com usuários federados** .

7.  Selecione **Habilitar comunicações com usuários federados XMPP** .

8.  Clique em **Confirmar** para salvar suas mudanças para a política local ou do usuário.

