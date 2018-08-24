---
title: Requisitos do Aplicativo Lync da Windows Store para Lync Server 2013
TOCTitle: Requisitos do Aplicativo Lync da Windows Store para Lync Server 2013
ms:assetid: 5f2e0a40-8450-4f61-b6f6-913fc1906020
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ823129(v=OCS.15)
ms:contentKeyID: 52057637
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos do Aplicativo Lync da Windows Store para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Organizações com implantações locais do Lync Server devem atender aos seguintes requisitos para dar suporte ao Aplicativo Lync Windows Store.

> [!NOTE]  
> Para Lync Server 2010, execute as atualizações cumulativas para o Lync Server 2010 de fevereiro de 2012 (disponíveis em <a href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2670352" class="uri">http://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2670352</a>) ou posteriores em todos os servidores. Para permitir que os usuários participem de reuniões, execute as atualizações cumulativas para o Lync Server 2010 de outubro de 2012 (disponíveis em <a href="http://go.microsoft.com/fwlink/?linkid=3052%26kbid=2737915" class="uri">http://go.microsoft.com/fwlink/?linkid=3052&amp;kbid=2737915</a>) nos servidores.

  - Habilite os serviços Descoberta Automática, Lync Web App e Web Ticket no servidor.

  - Habilite a autenticação de certificado no Servidor Front-End ou no Pool de Front-Ends. (O processo de registro de usuário no Servidor Front-End ou no Pool de Front-Ends é geralmente chamado de registrador). Para obter detalhes, consulte [Criar configurações do Registrador](lync-server-2013-create-registrar-configuration-settings.md).

  - Publique os registros de recursos do alias DNS (CNAME) para o serviço Descoberta Automática.

  - Certifique-se de que o Ponto de Distribuição (CDP) da Lista de Certificados Revogados (CRL) para os certificados emitidos para o servidor do Lync aponta para um recurso HTTP, e não para um recurso LDAP. No entanto, certifique-se de que os computadores do cliente têm as mais recentes atualizações do Windows instaladas.

  - Configure os proxies HTTP na organização para possibilitar o tráfego HTTP relacionado ao servidor do Lync.  Adicione exceções para os serviços Descoberta Automática, Lync Web App e WebTicket, se necessário.

  - Nos clientes, instale o Windows 8.1 e a versão mais recente do Aplicativo Lync Windows Store para resolver o problema de conexão que normalmente ocorre ao usar vários domínios (por exemplo, quando o URL do SIP for **userA@domainZ.com** e o Sevidor de Borda for **sip.domainX.com**).

Se sua organização assinar o Lync Online ou o Office 365 e você estiver usando seu próprio nome de domínio, é necessário adotar mais algumas etapas para configurar sua rede para descobrir automaticamente os servidores do Lync. Os requisitos de configuração de rede são os mesmos para o Aplicativo Lync Windows Store e para o Lync em dispositivos móveis. Siga as instruções de "Configurar sua rede” no artigo do wiki do Office 365 “Configurar dispositivos móveis do Lync", disponível em [http://go.microsoft.com/fwlink/?LinkId=271822](http://go.microsoft.com/fwlink/?linkid=271822).

## Consulte Também

#### Conceitos

[Implantar o Lync Windows Store App no Lync Server 2013](lync-server-2013-deploying-lync-windows-store-app.md)

