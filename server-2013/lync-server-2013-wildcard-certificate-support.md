---
title: 'Lync Server 2013: Suporte a certificado curinga'
TOCTitle: Suporte a certificado curinga
ms:assetid: 0bae2aa8-b6dc-46f5-a3be-3fe7581809d4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202161(v=OCS.15)
ms:contentKeyID: 49305852
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte a certificado curinga no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-21_

O Lync Server 2013 usa os certificados para fornecer criptografias de comunicações e autenticação de identidade do servidor. Em alguns casos, como em publicações na web através do proxy reverso, uma entrada forte de nome alternativo da entidade (SAN) que corresponda ao nome de domínio totalmente qualificado (FQDN) do servidor apresentando o serviço não é necessária. Nesses casos, é possível usar certificados com entradas curingas de SAN (comumente conhecidos como "certificados curinga") para reduzir o custo de um certificado solicitado por uma autoridade de certificação pública e para reduzir a complexidade do processo de planejamento para certificados.


> [!WARNING]
> Para reter a funcionalidade de dispositivos de comunicações unificadas (UC) (por exemplo, telefones de mesa), você deve testar o certificado implantado com cuidado para garantir que os dispositivos funcionem adequadamente depois de implantar um certificado curinga.



Não há suporte para uma entrada curinga como nome de entidade (também conhecido como nome comum ou CN) para nenhuma função. As funções do servidor apresentadas a seguir são suportadas quando são usadas entradas curinga no SAN:

   **Proxy reverso.**   A entrada de SAN curinga tem suporte do certificado de publicação de URL simples (reunir e discar).

   **Proxy reverso.**   A entrada de SAN curinga tem suporte do certificado de publicação do LyncDiscover.

   **Diretor.** A entrada de SAN curinga tem suporte de URLs simples (reunir e e discar) e por entradas do LyncDiscover e LyncDiscoverInternal nos componentes de Web do Diretor.

   **Servidor Front-End ( Standard Edition) e Pool de Front-Ends ( Enterprise Edition).** A entrada de SAN curinga é suportada para URLs simples (reunir e discar) e por entradas SAN para o LyncDiscover e LyncDiscoverInternal de componentes da Web de Front-Ends.

   **Unificação de Mensagens (UM) do Exchange.** O servidor não usa entradas de SAN quando implantado como um servidor autônomo.

   Servidor de Acesso para Cliente do **Microsoft Exchange Server.** As entradas curinga no SAN são suportadas por clientes internos e externos.

   Servidor de Acesso para Cliente **Unificação de Mensagens (UM) do Exchange e Microsoft Exchange Server no mesmo servidor.** As entradas curinga de SAN são suportadas.

As funções do servidor que não são abordadas neste tópico:

  - Funções do servidor interno (incluindo, mas não limitado ao Servidor de Mediação, ao Servidor de Arquivamento e Monitoramento, ao Aparelho de Filial Persistente ou ao Servidor de Filial Persistente)

  - Interfaces externas do Servidor de Borda

  - Servidor de Borda interno
    
    > [!NOTE]  
    > Para a interface interna do Servidor de Borda, uma entrada curinga pode ser designada ao SAN e é suportada. O SAN no Servidor de Borda interno não é consultado, e uma entrada curinga de SAN tem valor limitado.

Para obter detalhes sobre o uso de certificados no Exchange, consulte o seguinte:

  - [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md)

  - [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md)

  - [Resumo de certificado - Cargas de DNS e de HLB balanceadas no Lync Server 2013](lync-server-2013-certificate-summary-dns-and-hlb-load-balanced.md)

  - [Resumo do certificado - Diretor único no Lync Server 2013](lync-server-2013-certificate-summary-single-director.md)

  - [Resumo de certificado - pool Certificate summary - pool de diretores em escala, balanceador de carga de hardware no Lync Server 2013](lync-server-2013-certificate-summary-scaled-director-pool-hardware-load-balancer.md)

  - [Resumo de certificado - Proxy reverso no Lync Server 2013](lync-server-2013-certificate-summary-reverse-proxy.md)

  - [Orientações para integração de Unificação de Mensagens local e Lync Server 2013](lync-server-2013-guidelines-for-integrating-on-premises-unified-messaging.md)

Para detalhes sobre como configurar certificados para o Exchange, incluindo o uso de curingas, consulte a documentação do produto Exchange 2013.

