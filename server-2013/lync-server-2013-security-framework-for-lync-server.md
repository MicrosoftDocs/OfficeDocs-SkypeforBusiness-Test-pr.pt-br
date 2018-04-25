---
title: Security Framework do Lync Server 2013
TOCTitle: Security Framework do Lync Server 2013
ms:assetid: 01131e28-b38e-40d9-8524-06725b9c6608
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn481316(v=OCS.15)
ms:contentKeyID: 59682889
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Security Framework do Lync Server 2013

 

_**Tópico modificado em:** 2013-11-08_

Esta seção oferece uma visão geral dos elementos fundamentais que compõem a estrutura de segurança para Microsoft Lync Server 2013. Compreender como esses elementos funcionam em conjunto é essencial para tomar decisões conscientes sobre como proteger sua implantação específica do Lync Server 2013.

Esses elementos são:

  - Serviços de Domínio Active Directory (AD DS) fornece um único repositório de back-end confiável para contas de usuários e recursos de rede.

  - O controle de acesso baseado em função (RBAC) permite delegar tarefas administrativas enquanto mantém altos padrões de segurança.

  - A infraestrutura de chave pública (PKI) utiliza certificados emitidos por autoridades de certificação (CAs) confiáveis para autenticar servidores e garantir a integridade de dados.

  - A segurança da camada de transporte (TLS), HTTPS sobre SSL (HTTPS) e TLS mútuo (MTLS) possibilitam a autenticação de ponto de extremidade e criptografia IM. Os fluxos de áudio e vídeo ponto a ponto e de compartilhamento de aplicativos são criptografados utilizando protocolo de transporte em tempo real seguro (SRTP).

  - Protocolos padrão do setor para autenticação do usuário, onde possível.

  - Windows PowerShell fornece recursos de segurança que estão ativados por padrão para que os usuários não possam executar scripts com facilidade ou de forma inadvertida.

Esses elementos de segurança fundamentais funcionam em conjunto para definir usuários, servidores, conexões e operações confiáveis para ajudar a garantir uma fundação segura para Lync Server 2013.

## Nesta seção

Os tópicos nesta seção descrevem como cada um desses elementos fundamentais funciona para aprimorar a segurança da infraestrutura de Lync Server.

  - [Active Directory Domain Services para Lync Server 2013](lync-server-2013-active-directory-domain-services-for-lync-server.md)

  - [Função de controle de acesso baseado em função (RBAC) do Lync Server 2013](lync-server-2013-role-based-access-control-rbac.md)

  - [Infraestrutura de Chave Pública para o Lync Server 2013](lync-server-2013-public-key-infrastructure.md)

  - [TLS e MTLS para o Lync Server 2013](lync-server-2013-tls-and-mtls.md)

  - [Criptografia do Lync Server 2013](lync-server-2013-encryption.md)

  - [Autenticação de Usuário e Cliente para o Lync Server 2013](lync-server-2013-user-and-client-authentication.md)

  - [Ferramentas de gerenciamento do Windows PowerShell e do Lync Server 2013](lync-server-2013-windows-powershell-and-lync-server-management-tools.md)

