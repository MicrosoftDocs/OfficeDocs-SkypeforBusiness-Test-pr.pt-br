---
title: 'Lync Server 2013: Suporte à infraestrutura de DNS'
TOCTitle: Suporte à infraestrutura de DNS (Domain Name System)
ms:assetid: 37777c16-94ce-436d-b517-bcf53a564513
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425850(v=OCS.15)
ms:contentKeyID: 49306389
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte à infraestrutura de DNS no Lync Server 2013

 

_**Tópico modificado em:** 2013-03-08_

O Lync Server 2013 exige DNS (Sistema de Nomes de Domínio) e o utiliza das seguintes formas:

  - Para descobrir pools ou servidores internos para a comunicação entre servidores.

  - Para permitir que os clientes descubram o pool de front-ends ou o servidor Standard Edition usado em diversas transações SIP.

  - Para associar URLs simples de conferências com os servidores que as hospedam.

  - Para permitir que os servidores e clientes externos se conectem aos servidores de borda ou ao proxy reverso HTTP para fazer uso de IM (mensagens instantâneas) ou conferências.

  - Para permitir que os dispositivos de UC (comunicações unificadas) que não estejam conectados descubram o pool de front-ends ou o servidor Standard Edition que está executando o serviço Web de atualização de dispositivo obtenham atualizações e enviem logs.

  - Para permitir que os clientes móveis descubram automaticamente os recursos dos serviços Web, sem exigir que os usuários insiram as URLs manualmente nas configurações do dispositivo.

  - Para o balanceamento de carga de DNS.

> [!NOTE]  
> O Lync Server 2013 não suporta nomes de domínio internacionalizados (IDNs).

> [!IMPORTANT]  
> O nome especificado deve ser idêntico ao nome do computador configurado no servidor. Por padrão, o nome do computador de um computador que não tiver ingressado em um domínio deverá ser um nome curto, não um nome de domínio totalmente qualificado (FQDN). O Construtor de Topologias usa FQDNs, não nomes curtos. Portanto, você deverá configurar um sufixo DNS no nome do computador a ser implantado no Servidor de Borda que não ingressou no domínio. <strong>Use apenas caracteres padrão</strong> (incluindo A–Z, a–z, 0–9 e hifens) ao atribuir FQDNs de seus Lync Servers, Servidores de Borda e pools. Não use caracteres Unicode ou sublinhados. Normalmente, caracteres não padrão no FQDN não são suportados por DNS externo e CAs públicas (ou seja, quando o FQDN deve ser atribuído ao SN no certificado).
