---
title: 'Lync Server 2013: Definir um gateway no Construtor de Topologia'
TOCTitle: Definir um gateway no Construtor de Topologia
ms:assetid: 456e5a96-d9f6-42a6-862c-a69464391628
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425945(v=OCS.15)
ms:contentKeyID: 49306562
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir um gateway no Construtor de Topologia no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-04_

Siga estas etapas para usar o Construtor de Topologias para definir um *ponto* ao qual você possa associar um Servidor de Mediação para fornecer conectividade à Rede Telefônica Pública Comutada (PSTN) para usuários habilitados para o Enterprise Voice. Um ponto para o Servidor de Mediação pode ser um gateway PSTN, um PBX IP ou um SBC (Controlador de Limite de Sessões) para um ITSP (Provedor de Serviços de Telefonia pela Internet) ao qual você se conecta configurando um tronco SIP.

> [!NOTE]  
> Este tópico pressupõe que você tenha configurado pelo menos um Pool de Front-Ends ou Servidor Standard Edition interno em pelo menos um site central com um Servidor de Mediação independente ou posicionado, como descrito em <a href="lync-server-2013-define-and-configure-a-front-end-pool-or-standard-edition-server.md">Definir e configurar um pool Front-End ou um servidor Standard Edition no Lync Server 2013</a> and <a href="lync-server-2013-publish-the-topology.md">Publicar a topologia no Lync Server 2013</a> na seção de Implantação. Este tópico também pressupõe que você tenha verificado se sua infraestrutura atende aos pré-requisitos descritos em <a href="lync-server-2013-software-prerequisites-for-enterprise-voice.md">Pré-requisitos de software para Enterprise Voice no Lync Server 2013</a> e <a href="lync-server-2013-security-and-configuration-prerequisites-for-enterprise-voice.md">Pré-requisitos de configuração e segurança para Entreprise Voice no Lync Server 2013</a>.

## Definir um ponto para o Servidor de Mediação

1.  Inicie o Construtor de Topologias: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Construtor de Topologias do Lync Server**.

2.  Em Lync Server 2013, o nome do site, Componentes Compartilhados, clique com o botão direito do mouse no nó **Gateways PSTN** e clique em **Novo Gateway PSTN** .
    
    ![Lync Server 2013 de Construtor de Topologia](images/Gg425945.d898c3c1-8798-4b74-8f02-b994ef3db4c1(OCS.15).png "Lync Server 2013 de Construtor de Topologia")

3.  Em **Definir Novo Gateway IP/PSTN** , digite o nome de domínio totalmente qualificado (FQDN) ou o endereço IP do ponto e clique em **Avançar** .
    
    ![Gateway IP/PSTN](images/Gg425945.8017ba5e-41bc-48d4-97d9-fd306cd322b8(OCS.15).png "Gateway IP/PSTN")
    
    > [!NOTE]  
    > Caso especifique TLS (Transport Layer Security) como o tipo de transporte, você deve especificar o FQDN ao invés do endereço IP do ponto da Servidor de Mediação.

4.  Defina um modo de ouvinte (IPv4 ou IPv6) ou o endereço IP do seu novo gateway PSTN e clique em **Avançar** .
    
    ![Endereço de IP](images/Gg425945.c7fc0d12-adc8-45a7-aca1-b376e1d2fcec(OCS.15).png "Endereço de IP")

5.  Defina um *tronco raiz* par ao gateway PSTN. Um tronco é uma conexão lógica entre um Servidor de Mediação e um gateway identificado de forma única pela tupla.
    
    {FQDN da Servidor de Mediação, porta de escuta (TLS ou TCP) da Servidor de Mediação: FQDN e IP do gateway, porta de escuta do gateway}
    
      - Ao definir um gateway PSTN no Construtor de Topologias, você deve definir um tronco de raiz para adicionar com sucesso o gateway PSTN à sua topologia.
    
      - A árvore de raiz não pode ser removida até que o gateway PSTN associado seja removido.
    
    ![Definir gateway: tronco raiz](images/Gg425945.3b030757-eb35-4616-bb6b-74ee67507e3d(OCS.15).png "Definir gateway: tronco raiz")

6.  Em **Porta de Escuta do Gateway IP/PSTN** , digite a porta de escuta que o gateway, o PBX ou o SBC usará para mensagens de SIP do Servidor de Mediação que será associado à árvore de raiz do gateway do PSTN. (Por padrão, as portas são 5066 para protocolo TCP e 5067 para protocolo TLS em um gateway PSTN, PBX ou SBC. Em um Aparelho de Filial Persistente de uma filial, as portas padrão são 5081 para TCP e 5082 para TLS.)

7.  Em **Protocolo de Transporte SIP** , clique no tipo de transporte que o ponto usa e clique em **OK** .
    
    > [!NOTE]  
    > Por motivos de segurança, recomendamos que você implante um par para o Servidor de Mediação que possa usar o TLS.

8.  Em **Associado Servidor de Mediação**, selecione Pool do servidor de mediação para associar com a árvore de raiz deste Gateway PSTN.

9.  Em **Porta Servidor de Mediação associada** , digite a porta de ouvinte que o Servidor de Mediação utilizará para mensagens SIP a partir do gateway.
    
    > [!NOTE]  
    > Com o suporte a diversas árvores no Lync Server 2013, diversas portas de sinalização SIP podem ser definidas no Servidor de Mediação para serem usadas para comunicação com vários gateways PSTN. Ao definir uma árvore, a <strong>Porta Servidor de Mediação associada</strong> deve estar dentro da faixa das portas de ouvinte para o protocolo respectivo permitido pelo Servidor de Mediação. Essa faixa de porta é definida em Lync Server 2013 e em Pools de mediação. Clique com o botão direito do mouse no Pool do servidor de mediação do seu interesse e selecione <strong>Editar propriedades</strong> . Especifique a faixa de porta no campo <strong>Portas de ouvinte</strong> .

10. Clique em **Concluir** .

> [!IMPORTANT]  
> Antes de finalizar esta etapa, certifique-se se o ponto definido está funcionando e usando o FQDN ou o endereço IP que você especificou.

Em seguida, para adicionar o ponto à topologia, siga os procedimentos na [Publicar a topologia no Lync Server 2013](lync-server-2013-publish-the-topology.md) na documentação de Implantação. Você deve publicar sua topologia toda vez que usar o Construtor de Topologias para criar ou modificar a topologia, para que os dados podem ser usados para instalar os arquivos de servidores que estão executando o Lync Server.

## Consulte Também

#### Tarefas

[Modificar um tronco no Construtor de Topologia no Lync Server 2013](lync-server-2013-modify-a-trunk-in-topology-builder.md)

