---
title: 'Lync Server 2013: Definir um endereço SIP de gateway SIP/CSTA'
TOCTitle: Definir um endereço SIP de gateway SIP/CSTA
ms:assetid: ae944057-3ad6-4474-a09b-81a3d27bd50f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg602125(v=OCS.15)
ms:contentKeyID: 49307786
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir um endereço SIP de gateway SIP/CSTA no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Se Lync Server se conectará ao gateway SIP/CSTA implantada para controle de chamadas remoto usando uma conexão de protocolo TCP (Transmission Control Protocol), então você deve definir o endereço IP do gateway em Construtor de Topologias. Esta etapa não é necessária para gateways que oferecem suporte a conexões por protocolo TLS. Para qualquer gateway que suporta conexões TLS, é possível ignorar esse procedimento e continue a implantação de controle de chamada remota seguindo as etapas em [Habilitar usuários do Lync para controle de chamada remota no Lync Server 2013](lync-server-2013-enable-lync-users-for-remote-call-control.md).

## Para definir o endereço IP do gateway SIP/CSTA usando o Construtor de Topologias

1.  Faça logon no computador no qual o Construtor de Topologias está instalado como um membro do grupo Admins. do Domínio ou do grupo RTCUniversalServerAdmins.

2.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

3.  Escolha a opção para fazer download de uma topologia existente.

4.  Expanda o nó **Servidor de aplicativos confiáveis**.

5.  Clique com o botão direito no pool de aplicativo confiável criado, como descrito em [Configurar uma entrada de aplicativo confiável para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md) e clique em **Editar propriedades**.

6.  Desmarque a opção **Habilitar replicação dos dados de configuração para este pool**.

7.  Clique em **Limitar o uso do serviço para os endereços IP selecionados**. A configuração padrão é **Usar todos os endereços IP configurados**.

8.  Na caixa de texto **Endereço IP Principal**, insira o endereço IP do gateway SIP/CSTA.

9.  Para atualizar a topologia no repositório de Gerenciamento Central, na árvore de console, clique em **Lync Server** e, em seguida, no painel **Ações**, clique em **Publicar**.

## Consulte Também

#### Tarefas

[Configurar uma rota estática para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md)  
[Configurar uma entrada de aplicativo confiável para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md)

