---
title: 'Lync Server 2013: Suporte à infraestrutura de certificado'
TOCTitle: Suporte à infraestrutura de certificado
ms:assetid: 47aa5c95-eb60-4d4b-81d5-7fdaef1a1145
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425950(v=OCS.15)
ms:contentKeyID: 49306584
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte à infraestrutura de certificado no Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

O Lync Server 2013 requer uma PKI (infraestrutura de chave pública) para dar suporte a conexões de protocolo TLS e TLS mútuo (MTLS). Por padrão, o Lync Server 2013 é configurado para usar o TLS para conexões de cliente a servidor. O MTLS é usado para conexões entre servidores.

Os certificados MTLS devem ser emitidos por CAs (autoridades de certificação) confiáveis para o Lync Server 2013. O Lync Serveroferece suporte a certificados emitidos pelas seguintes CAs:

  - Certificados emitidos por uma autoridade de certificação interna
    
      - A AC do Sistema operacional Windows Server 2003
    
      - A AC do Sistema operacional Windows Server 2008
    
      - A AC do Sistema operacional Windows Server 2008 R2
    
      - A AC do sistema operacional Windows Server 2012
    
      - A AC do sistema operacional Windows Server 2012 R2

  - Certificados emitidos por uma autoridade de certificação pública

A comunicação com outros aplicativos e servidores, como um Exchange 2013, requer um certificado que é suportado por outros aplicativos e produtos. Para a versão 2013, o Lync Server 2013 e outros produtos de servidor da Microsoft, incluindo Exchange 2013 e SharePoint Server, suportam o protocolo de Autorização Aberta para autenticação e autorização de servidor para servidor. Para detalhes, consulte [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) na documentação de Implantação ou Operações.

Para conexões de clientes que executam o Sistema operacional Windows 7, o Sistema operacional Windows Server 2008 R2 e o Microsoft Office Communicator 2007 Phone Edition, Lync Server 2013, inclui suporte (mas não é necessário) para certificados assinados usando a função hash criptográfica SHA-256. Para oferecer suporte ao acesso externo usando SHA-256, o certificado externo é emitido por uma CA pública usando SHA-256.

Para detalhes sobre requisitos de certificado, consulte [Requisitos de infraestrutura de certificado para o Lync Server 2013](lync-server-2013-certificate-infrastructure-requirements.md) na documentação de Planejamento. Para detalhes sobre o uso de curingas com certificados, consulte [Suporte a certificado curinga no Lync Server 2013](lync-server-2013-wildcard-certificate-support.md) na documentação de Suporte.

