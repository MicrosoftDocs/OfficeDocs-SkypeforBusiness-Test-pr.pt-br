---
title: "Lync Server 2013: Habil. a integ. c/ serv. de Office Web Apps e Lync Server 2013"
TOCTitle: Habilitando a integração com servidor de Office Web Apps e Lync Server 2013
ms:assetid: 3370ab55-9949-4f32-b88b-5cffed6aaad8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204792(v=OCS.15)
ms:contentKeyID: 49306328
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a integração com servidor de Office Web Apps e Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 emprega o Servidor Office Web Apps para lidar com as apresentações do PowerPoint. Para obter informações sobre as vantagens dessa abordagem, consulte [Visão Geral de Webconferência no Lync Server 2013](lync-server-2013-web-conferencing-overview.md).

Para usar esses novos recursos, os administradores devem instalar o Servidor Office Web Apps e configurar o Lync Server 2013 para a comunicação com o Servidor Office Web Apps. Esta documentação oferece informações sobre como configurar o Lync Server 2013 para que funcione com o Servidor Office Web Apps. Esta documentação não oferece informações sobre como instalar o próprio Servidor Office Web Apps. Para obter essas informações, consulte o site de implantação de aplicativos Web do Microsoft Office em [http://go.microsoft.com/fwlink/?linkid=257525\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=257525%26clcid=0x416). Este guia contém informações completas de pré-requisitos do Servidor Office Web Apps. Observe que o Servidor Office Web Apps deve ser instalado em um computador autônomo, que não esteja executando o Lync Server, o Microsoft SQL Server ou qualquer outro aplicativo de servidor (nenhuma versão do Microsoft Office deve estar instalada no computador). Todos os computadores que executavam o Servidor Office Web Apps também deverão ter um conjunto específico de produtos de software instalados (inclusive o .NET Framework 4.5 e o Windows PowerShell 3.0). Esses requisitos, junto com as informações sobre a configuração de certificados e do IIS (Serviços de Informações da Internet), são analisados em detalhes no site de implantação de aplicativos da Web do Microsoft Office, em [http://go.microsoft.com/fwlink/?linkid=257525\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=257525%26clcid=0x416).

Este documento aborda as seguintes áreas do tópico:

  - [Configurando Lync Server 2013 para trabalhar com o servidor de Office Web Apps](lync-server-2013-configuring-lync-server-2013-to-work-with-office-web-apps-server.md)

  - [Publicando o servidor do Office Web Apps no Lync Server 2013 usando um servidor de proxy reverso](lync-server-2013-publishing-office-web-apps-server-using-a-reverse-proxy-server.md)

  - [Validando a Configuração do servidor do Office Web Apps no Lync Server 2013](lync-server-2013-validating-the-configuration-of-office-web-apps-server.md)

  - [Configurando Clientes do Lync Server 2013 para Uso com o Servidor Office Web Apps](lync-server-2013-configuring-clients-for-use-with-office-web-apps-server.md)

