---
title: 'Lync Server 2013: Configurar certificados para o proxy reverso'
TOCTitle: Configurar certificados para o proxy reverso
ms:assetid: c03a08ec-a67b-4f11-b0d7-6677461beaaa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412938(v=OCS.15)
ms:contentKeyID: 49307998
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurar certificados para o proxy reverso no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

Cada servidor proxy reverso requer um certificado de servidor Web para ser usado pelo serviço de escuta. O certificado de servidor Web deve ser emitido por uma autoridade de certificação pública.

Para detalhes sobre este e outros requisitos de certificado, consulte [Requisitos de certificado para acesso do usuário externo no Lync Server 2013](lync-server-2013-certificate-requirements-for-external-user-access.md).

## Para configurar um certificado de Serviços Web para o proxy reverso

  - Você já deve ter configurado seu proxy reverso, incluindo a configuração do certificado de Serviços Web. Se você não tiver feito isso antes de iniciar a implantação de seus Servidores de Borda, use os procedimentos no [Configurando servidores de proxy reverso para o Lync Server 2013](lync-server-2013-setting-up-reverse-proxy-servers.md) para criar, solicitar e instalar o certificado de Serviços Web, e crie cada regra de publicação na web e configure-a para usar o certificado.

