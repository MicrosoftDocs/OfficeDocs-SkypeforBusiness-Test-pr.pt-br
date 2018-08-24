---
title: 'Lync Server 2013: Configurando troncos'
TOCTitle: Configurando troncos
ms:assetid: 0c339511-a185-484e-94f0-dbe918b7e48a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398170(v=OCS.15)
ms:contentKeyID: 49305854
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando troncos no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Como parte da implantação do Enterprise Voice onfigure um tronco entre um Servidor de Mediação e um ou mais dos itens a seguir para fornecer conectividade PSTN aos clientes Enterprise Voice e dispositivos do Enterprise Voice na sua organização:

  - Conexão tronco SIP em um provedor de serviço de telefonia por Internet (ITSP)

  - Gateway PSTN

  - Central privada de comutação telefônica (PBX)

Para obter detalhes, consulte [Planejamento de conectividade de PSTN no Lync Server 2013](lync-server-2013-planning-for-pstn-connectivity.md) na documentação de Planejamento.

> [!IMPORTANT]  
> Antes de iniciar a configuração de tronco, verifique se a topologia foi criada e se o Servidor de Mediação e seu par foram configurados e associados um ao outro, conforme descrito em <a href="lync-server-2013-define-a-gateway-in-topology-builder.md">Definir um gateway no Construtor de Topologia no Lync Server 2013</a> na documentação de Implantação.

> [!NOTE]  
> Como parte da configuração por tronco, você pode habilitar o recurso de desvio de mídia do Lync Server 2013, que permite que a mídia desvie para o Servidor de Mediação. Os troncos podem ser configurados com ou sem o desvio de mídia habilitado, mas recomendamos fortemente que você o habilite. Para obter detalhes, consulte <a href="lync-server-2013-planning-for-media-bypass.md">Planejamento de bypass de mídia no Lync Server 2013</a>, na documentação de Planejamento.

## Nesta seção

  - [Suporte a vários troncos no Lync Server 2013](lync-server-2013-multiple-trunk-support.md)

  - [Roteamento entre troncos no Lync Server 2013](lync-server-2013-inter-trunk-routing.md)

  - [Visualizar Informações de Configuração do Tronco no Lync Server 2013](lync-server-2013-view-trunk-configuration-information.md)

  - [Configurar um tronco com bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-with-media-bypass.md)

  - [Configurar um tronco sem bypass de mídia no Lync Server 2013](lync-server-2013-configure-a-trunk-without-media-bypass.md)

  - [Cria um novo conjunto de definições de configuração de tronco no Lync Server 2013](lync-server-2013-create-a-new-collection-of-trunk-configuration-settings.md)

  - [Excluir um conjunto existente das configurações do Tronco SIP no Lync Server 2013](lync-server-2013-delete-an-existing-collection-of-sip-trunk-configuration-settings.md)

  - [Modificar as Configurações do Tronco SIP no Lync Server 2013](lync-server-2013-modify-sip-trunk-configuration-settings.md)

  - [Testar as Configurações do Tronco SIP no Lync Server 2013](lync-server-2013-test-sip-trunk-configuration-settings.md)

  - [Exibir Informações sobre Troncos SIP Individuais no Lync Server 2013](lync-server-2013-view-information-about-individual-sip-trunks.md)

## Consulte Também

#### Tarefas

[Definir um gateway no Construtor de Topologia no Lync Server 2013](lync-server-2013-define-a-gateway-in-topology-builder.md)  

#### Outros Recursos

[Planejamento de conectividade de PSTN no Lync Server 2013](lync-server-2013-planning-for-pstn-connectivity.md)  
[Planejamento de bypass de mídia no Lync Server 2013](lync-server-2013-planning-for-media-bypass.md)

