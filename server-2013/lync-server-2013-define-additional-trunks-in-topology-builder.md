---
title: 'Lync Server 2013: Definir troncos adicionais no Construtor de Topologia'
TOCTitle: Definir troncos adicionais no Construtor de Topologia
ms:assetid: e68b8377-50a2-452a-bf5c-910929e34236
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721915(v=OCS.15)
ms:contentKeyID: 49886453
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir troncos adicionais no Construtor de Topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-04_

Siga estes passos para usar a Construtor de Topologias para definir um tronco adicional ao qual você pode associar um *ponto* a uma Servidor de Mediação. Um ponto oferece conectividade a usuários habilitados para Enterprise Voice à rede PSTN (Rede Telefônica Pública Comutada). Um ponto pode ser um gateway PSTN, um PBX IP, ou um SBC (controlador de borda da sessão) para um ITSP (Provedor de Serviço Telefônico de Internet. O tronco define essa conexão entre a Servidor de Mediação e o ponto. Múltiplos troncos podem ser definidos por Servidor de Mediação. Uma Servidor de Mediação pode ser associada a múltiplos pontos.

Um tronco é uma conexão lógica entre uma Servidor de Mediação e um gateway exclusivamente identificado pela tupla:

{FQDN da Servidor de Mediação, porta de escuta (TLS ou TCP) da Servidor de Mediação: FQDN e IP do gateway, porta de escuta do gateway}

> [!NOTE]  
> Este tópico presume que você configurou um gateway PSTN e tronco raiz com ao menos uma Servidor de Mediação colocada ou autônoma, ou pool, como descrito em <a href="lync-server-2013-define-a-gateway-in-topology-builder.md">Definir um gateway no Construtor de Topologia no Lync Server 2013</a>, na documentação de Implantação.

> [!NOTE]  
> Este tópico presume que você configurou ao menos um Pool de Front-Ends ou uma Servidor Standard Edition em ao menos um site central, como descrito em <a href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013</a> e <a href="lync-server-2013-publish-the-topology.md">Publicar a topologia no Lync Server 2013</a>, na documentação de Implantação.

## Para definir um tronco adicional entre uma Servidor de Mediação e um ponto de gateway

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Sob Lync Server 2013, o nome do seu site, **Componentes Compartilhados** , clique com o botão direito no nó **Troncos** , e então clique em **Novo Tronco** .
    
    ![Tela da estrutura de arquivos do Construtor de Topologias do Lync Server](images/JJ721915.90d5b349-aa1e-407a-87ed-fa112f478560(OCS.15).png "Tela da estrutura de arquivos do Construtor de Topologias do Lync Server")

3.  Em **Definir Novo Tronco** , especifique um nome amigável para identificar exclusivamente o tronco. Você não pode ter dois troncos com o mesmo nome.
    
    > [!NOTE]  
    > Caso especifique TLS (Transport Layer Security) como o tipo de transporte, você deve especificar o FQDN ao invés do endereço IP do ponto da Servidor de Mediação.

4.  Sob **Gateway PSTN associado** , selecione o ponto de gateway PSTN para associar a este tronco.
    
    ![Configurações de propriedade para o par de gateway PSTN para o tronco](images/JJ721915.7c3fe8ee-8f4c-4413-8462-8347228e61bb(OCS.15).png "Configurações de propriedade para o par de gateway PSTN para o tronco")

5.  Sob **Porta de escuta para gateway PSTN** , digite a porta de escuta pela qual o ponto (gateway PSTN, PBX IP ou SBC) receberá mensagens SIP da Servidor de Mediação que será associada a este tronco. As portas de ponto padrão são 5066 para TCP (Transmission Control Protocol) e 5067 para TLS (Transport Layer Security). As portas de Aparelho de Filial Persistente padrão são 5081 para TCP e 5082 para TLS.

6.  Sob **Protocolo de Transporte SIP** , clique no tipo de transporte usado pelo ponto.
    
    > [!NOTE]  
    > Por motivos de segurança, recomendamos que você implante um par para o Servidor de Mediação que possa usar o TLS.

7.  Sob **Servidor de Mediação Associado** , selecione o pool de Servidor de Mediação a ser associado ao tronco raiz deste ponto

8.  Sob **Porta do Servidor de Mediação Associado** , digite a porta de escuta pela qual a Servidor de Mediação receberá mensagens SIP do ponto.
    
    > [!NOTE]  
    > Com suporte a troncos múltiplos no Lync Server 2013, dois troncos com nomes de tronco diferentes podem ser configurados com o a mesma <strong>Porta de Servidor de Mediação Associado</strong> e <strong>Porta de escuta para gateway IP/PSTN</strong>    
    > [!NOTE]  
    > Com suporte a troncos múltiplos no Lync Server 2013, mútiplas portas de sinalização SIP podem ser definidas na Servidor de Mediação para comunicação com múltiplos pontos. Ao definir um tronco, o número da <strong>Porta de Servidor de Mediação Associado</strong> deve estar dentro do intervalo de portas de escuta para o respectivo protocolo permitido pela Servidor de Mediação. Esse intervalo de portas é definida sob Lync Server 2013 e Pools do servidor de mediação. Clique com o botão direito no Pool do servidor de mediação, e selecione <strong>Editar Propriedades</strong> . Especifique o intervalo de portas no campo <strong>Portas de escuta</strong> .

9.  Clique em **OK** .

## Consulte Também

#### Tarefas

[Modificar um tronco no Construtor de Topologia no Lync Server 2013](lync-server-2013-modify-a-trunk-in-topology-builder.md)

