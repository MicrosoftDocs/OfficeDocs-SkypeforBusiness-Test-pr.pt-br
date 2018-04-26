---
title: 'Lync Server 2013: requisitos de infraestrutura de certificado'
TOCTitle: Requisitos de infraestrutura de certificado
ms:assetid: 0051aa23-0bbe-4e72-9f29-e01c6bcc6190
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398066(v=OCS.15)
ms:contentKeyID: 49305661
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de infraestrutura de certificado para o Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 requer uma infraestrutura de chave pública (PKI) para dar suporte a conexões TLS e TLS (MTLS) mútuo.

Lync Server utiliza certificados para os seguintes propósitos:

  - Conexões TLS entre cliente e servidor

  - Conexões MTLS entre servidores

  - Federação usando a descoberta automática de parceiros no DNS

  - Acesso de usuários remotos a IM (mensagens instantâneas)

  - Acesso de usuário externo a sessões A/V (áudio/vídeo), compartilhamento de aplicativos e conferência

  - Solicitações móveis utilizando descoberta automática de Serviços Web

Para Lync Server, aplicam-se os seguintes requisitos comuns:

  - Todos os certificados de servidor devem oferecer suporte à autorização de servidor (EKU de servidor).

  - Todos os certificados de servidor devem conter um CDP (Ponto de Distribuição de CRL).

  - Todos os certificados devem ser assinados com o uso de um algoritmo de assinatura que seja compatível com o sistema operacional. O Lync Server 2013 é compatível com os pacotes SHA-1 e SHA-2 de tamanhos compactos (224, 256, 384 e 512 bits) e atende ou supera os requisitos do sistema operacional. Para suporte ao sistema operacional, consulte [http://go.microsoft.com/fwlink/?LinkId=287002](http://go.microsoft.com/fwlink/?linkid=287002).

  - Registro automático é suportado para servidores internos executando Lync Server.

  - Registro automático não é suportado para Servidores de Borda Lync Server.

  - Quando você envia uma solicitação de certificado baseado em web para uma AC Windows Server 2003, você deve submete-la de um computador que esteja executando Windows Server 2003 com SP2 ou Windows XP.
    
    Observe que, embora o KB922706 oferece suporte para resolver problemas com o registro de certificados de web contra registro de web de Serviços de Certificado do Windows Server 2003, ele não torna possível utilizar o Windows Server 2008, Windows Vista, ou Windows 7 para solicitar um certificado de uma AC Windows Server 2003.

  - Os comprimentos de chave de criptografia de 1024, 2048 e 4096 têm suporte. Comprimentos de pelo menos 2048 são recomendados.

  - O algoritmo de hash de assinatura ou sumário padrão é RSA. Os algoritmos ECDH\_P256, ECDH\_P384 e ECDH\_P521 também têm suporte. 

## Nesta seção

  - [Requisitos de certificado para servidores internos no Lync Server 2013](lync-server-2013-certificate-requirements-for-internal-servers.md)

  - [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md)

  - [Requisitos de certificado para o servidor de Chat Persistente no Lync Server 2013](lync-server-2013-certificate-requirements-for-persistent-chat-server.md)

  - [Requisitos de certificado para mobilidade no Lync Server 2013](lync-server-2013-certificate-requirements-for-mobility.md)

