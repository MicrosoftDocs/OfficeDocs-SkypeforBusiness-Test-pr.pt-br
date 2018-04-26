---
title: 'Lync Server 2013: Pré-requisitos para habilitar autenticação Kerberos'
TOCTitle: Pré-requisitos para habilitar autenticação Kerberos
ms:assetid: 3f276a21-7476-4bc0-9fd1-59e844d2e9c1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425909(v=OCS.15)
ms:contentKeyID: 49306496
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos para habilitar autenticação Kerberos no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-21_

Antes de habilitar a autenticação Kerberos, conclua todas as preparações de infraestrutura e configuração de pré-requisito:

  - O esquema do Active Directory é estendido para Lync Server 2013.

  - A preparação da floresta do Active Directory está concluída para o Lync Server 2013.

  - A preparação do domínio do Active Directory está concluída para o Lync Server 2013.

  - O Repositório de Gerenciamento Central foi instalado com êxito e está disponível.

  - A topologia foi criada e publicada usando o Construtor de Topologias.

  - Servidores e funções que exigem o Serviços Web foram definidas e implantadas, incluindo Servidores Front End, servidores Standard Edition e Diretores.

  - O IIS (Serviços de Informações da Internet) é configurado e implantado com os serviços de função recomendados para der suporte ao Serviços Web no Lync Server 2013.

Depois que os pré-requisitos foram atendidos, você deve estar pronto para criar uma ou mais contas para o Serviços Web usar a autenticação Kerberos para sua implantação. No mínimo, você precisa criar uma conta de autenticação Kerberos para cada implantação. No entanto, você pode criar uma conta para cada site, a fim de fornecer a autenticação Kerberos local no site. Você só pode especificar uma conta de autenticação Kerberos por site.

