---
title: 'Lync Server 2013: Solicitar certificados para componentes de borda'
TOCTitle: Solicitar certificados para componentes de borda
ms:assetid: 8c72b877-febc-428f-89dc-389e7a7ac849
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398708(v=OCS.15)
ms:contentKeyID: 49307413
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Solicitar certificados para componentes de borda no Lync Server 2013

 

_**Tópico modificado em:** 2013-11-07_

Os certificados necessários para dar suporte ao acesso de usuário externo incluem certificados emitidos por uma autoridade de certificação pública e certificados emitidos por uma autoridade corporativa interna:

  - Os certificados necessários para a interface externa do Servidor de Borda e do proxy reverso devem ser emitidos por uma autoridade de certificação pública.

  - Os certificados necessários para a interface interna podem ser emitidos por uma AC pública ou uma AC corporativa interna. Recomendamos usar uma AC interna do Windows Server 2008, uma AC do Windows Server 2008 R2 ou AC do Windows Server 2012 ou do Windows Server 2012 R2 para criar esses certificados para economizar em despesas de certificados públicos.

> [!IMPORTANT]  
> Pode levar tempo para processar solicitações de certificados, especialmente as solicitações para ACs públicas; portanto, você deve solicitar os certificados para seus Servidores de Borda com antecedência suficiente para garantir que estejam disponíveis ao iniciar a implantação dos componentes do Servidor de Borda. Para obter um resumo dos requisitos de certificado para Servidores de Borda, consulte <a href="lync-server-2013-certificate-requirements-for-external-user-access.md">Requisitos de certificado para acesso do usuário externo no Lync Server 2013</a>.

Embora você possa optar pelo uso de uma AC pública para o certificado da borda interna, é recomendável o uso de uma AC corporativa interna para os outros certificados, para minimizar o custo de certificados. Para um resumo das exigências de certificado do Servidores de Borda, consulte [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md).

> [!NOTE]  
> Ao instalar um Servidor de Borda, a instalação inclui um assistente de certificado que facilita as tarefas de solicitação, atribuição e instalação de certificados, conforme descrito na seção <a href="lync-server-2013-set-up-edge-certificates.md">Configurar certificados de Borda para Lync Server 2013</a>. Se você deseja solicitar certificados antes de instalar um Servidor de Borda (por exemplo, para economizar tempo durante a implantação real dos componentes do Servidor de Borda), você pode fazê-lo usando servidores internos, desde que garanta que os certificados sejam exportáveis e contenham todos os nomes alternativos de entidade necessários. Esta documentação não fornece procedimentos para usar servidores internos para solicitar certificados.

## Solicitar certificados de uma AC pública

Sua implantação do Servidor de Borda requer um certificado público único para as interfaces externas dos Servidores de Borda, que será usado para o serviço de Serviço de Borda de Acesso, o Serviço de Borda de Webconferência, e o serviço de autenticação de A/V. Este certificado deve ter uma chave privada exportável para garantir que o serviço de autenticação de A/V use as mesmas chaves em todos os Servidores de Borda em um pool. O proxy reverso, que é usado com o Microsoft Internet Security and Acceleration (ISA) Server 2006 ou o Microsoft Forefront Threat Management Gateway 2010, também requer um certificado público.

## Solicitar certificados de uma AC empresarial interna

Os certificados necessários para a interface de borda interna podem ser emitidos por uma autoridade de certificação (CA) pública ou interna. Você pode usar uma CA corporativa interna para ajudar a minimizar o custo dos certificados. Se sua organização tiver uma CA interna implantada, os certificados da borda interna deverão ser emitidos por ela. O uso de uma CA corporativa interna para certificados internos pode reduzir o custo dos certificados.

Para obter um resumo dos requisitos de certificado para componentes de borda, consulte [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md). Para obter detalhes sobre como usar uma CA pública para obter os certificados, consulte [Solicitar certificados para componentes de borda no Lync Server 2013](lync-server-2013-request-certificates-for-edge-components.md). Para obter detalhes sobre como solicitar, instalar e atribuir certificados, consulte [Configurar certificados de Borda para Lync Server 2013](lync-server-2013-set-up-edge-certificates.md).

