---
title: Configurar o bypass de mídia para sempre ignorar o Servidor de Mediação
TOCTitle: Configurar o bypass de mídia para sempre ignorar o Servidor de Mediação
ms:assetid: 370c4f54-e520-4d77-96a3-84c5e84a9996
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425846(v=OCS.15)
ms:contentKeyID: 49306370
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar o bypass de mídia para sempre ignorar o Servidor de Mediação

 

_**Tópico modificado em:** 2013-02-25_

> [!NOTE]  
> Este tópico assume que você já configurou o desvio de mídia em qualquer conexão de tronco para um par (um gateway PSTN (Rede Telefônica Pública Comutada), um IP-PBX ou SBC (Controlador de Borda da Sessão) no ITSP (Provedor de Serviços de Telefonia da Internet)) de um local ou serviço específico no qual deseja que a mídia ignore o servidor de mediação.<br />Você não pode configurar a mídia para sempre desviar do Servidor de Mediação, enquanto também ativa o controle de admissão de chamada. Essas configurações são incompatíveis, e portanto mutuamente exclusivas, na interface de usuário do Painel de Controle do Lync Server.

Além de ativar o desvio de mídia para as conexões de tronco individuais associadas a um ponto para o Servidor de Mediação, você também deve definir as configurações globais para o desvio de mídia. Se você usar as etapas deste tópico para fazer essas configurações, supõe-se que tenha uma boa conectividade entre os pontos de extremidade do Lync e qualquer ponto para o qual tenha configurado desvios de mídia na conexão de tronco.

Se você não tiver uma boa conectividade entre os pontos de extremidade do Lync Server e todos os pontos do servidor de mediação cujas respectivas conexões de tronco foram habilitadas para o desvio de mídia, defina as configurações globais do desvio de mídia para usar as informações de local e região ao empregar esse desvio. Isso permite maior controle ao determinar quando a mídia desvia do servidor de mediação. Para isso, siga as etapas em [Definir as configurações globais de bypass de mídia para usar informações locais e da região](lync-server-2013-configure-media-bypass-global-settings-to-use-site-and-region-information.md) e [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md).

## Para habilitar o desvio de mídia globalmente para que sempre ignore o servidor de mediação

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação da esquerda, clique em **Configuração da Rede**.

3.  Clique duas vezes na configuração **Global** na lista.

4.  Na página **Editar Configuração Global**, marque a caixa de seleção **Ativar desvio de mídia**.

5.  Clique em **Sempre desviar**.

6.  Clique em **Comprometer**.

## Consulte Também

#### Conceitos

[Configurar bypass de mídia no Lync Server 2013](lync-server-2013-configure-media-bypass.md)  
[Opções de bypass de mídia global no Lync Server 2013](lync-server-2013-global-media-bypass-options.md)  
[Bypass de mídia e Servidor de Mediação no Lync Server 2013](lync-server-2013-media-bypass-and-mediation-server.md)  

#### Outros Recursos

[Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

