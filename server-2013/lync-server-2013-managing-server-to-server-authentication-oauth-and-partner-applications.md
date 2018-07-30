---
title: Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013
TOCTitle: Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013
ms:assetid: 38848373-c8c6-4097-bf7f-699fe471348d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204817(v=OCS.15)
ms:contentKeyID: 49306394
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013

 

_**Tópico modificado em:** 2015-05-14_

O Microsoft Lync Server 2013 deve poder se comunicar de forma segura e simples com outros produtos de aplicativo e servidor. Por exemplo, é possível configurar o Lync Server 2013 para que os dados do contato e/ou do arquivamento sejam armazenados no Microsoft Exchange Server 2013; no entanto, isso só poderá ser feito se o Lync Server e o Exchange puderem se comunicar de forma segura um com o outro. Da mesma forma, é possível agendar uma conferência do Lync Server a partir do Microsoft SharePoint Server; novamente, isso só poderá ser feito se dois servidores (SharePoint e Lync Server) confiarem um no outro. Embora seja possível usar um mecanismo de autenticação para a comunicação do Lync para o Exchange e um mecanismo separado para a comunicação do Lync para o SharePoint, uma abordagem melhor e mais eficiente é usar um método padronizado para todas as autenticações e autorizações de servidor para servidor.

O uso de um único método padronizado para a autenticação de servidor para servidor é a abordagem feita pelo Lync Server 2013. Na versão de 2013, o Lync Server 2013 (bem como outros produtos do Microsoft Server, inclusive Exchange 2013 e Microsoft SharePoint Server) dão suporte ao protocolo OAuth (Open Authorization) para autenticação e autorização de servidor para servidor. Com o OAuth, um protocolo de autorização padrão usado por vários dos sites principais, as credenciais e senhas do usuário não são passadas de um computador a outro. Em vez disso, a autenticação e autorização são baseadas na troca de tokens de segurança; esses tokens concedem acesso a um conjunto específico de recursos por um período determinado.

A autenticação com o OAuth geralmente envolve três partes: um servidor de autorização individual e dois realms que precisam se comunicar entre si. (Também é possível usar autenticação de servidor para servidor sem usar um servidor de autorização, um processo que será analisado mais tarde neste documento.) Os tokens de segurança são emitidos pelo servidor de autorização (também conhecido como servidor do token de segurança) para os dois realms que precisam se comunicar; esse tokens verificam se as comunicações originadas de um realm devem ser confiadas pelo outro realm. Por exemplo, o servidor de autorização pode emitir tokens que verificam se os usuários de um realm do Lync Server 2013 específico podem acessar um relam do Exchange 2013 e vice-versa.

> [!NOTE]  
> Um realm é simplesmente um contêiner de segurança, Por padrão, o Lync Server 2013 usa seu domínio SIP padrão como realm de OAuth.

O Lync Server 2013 dá suporte a três cenários de autenticação de servidor para servidor. Com o Lync Server 2013, é possível:

  - Configurar uma autenticação de servidor para servidor entre uma instalação no local do Lync Server 2013 e uma instalação no local do Exchange 2013 e/ou Microsoft SharePoint Server.

  - Configurar a autenticação de servidor para servidor de componentes do Office (por exemplo, entre o Microsoft Exchange e o Microsoft Lync Server ou entre o Microsoft Lync Server e o Microsoft SharePoint).

  - Configurar a autenticação de servidor para servidor em um ambiente ente locais (isto é, autenticação de servidor para servidor entre o servidor no local e um componente do Office 365).

Observe que, neste ponto, apenas o Exchange 2013, o SharePoint Server e o Lync Server 2013 dão suporte à autenticação de servidor para servidor; se não estiver executando um desses servidores, não será possível implementar completamente a autenticação de OAuth.

Deve ser indicado também que não é preciso usar a autenticação de servidor para servidor: essa autenticação não é exigida para implantar o Lync Server 2013. Se o Lync Server 2013 não precisa se comunicar com outros servidores (como o Exchange 2013), a autenticação de servidor para servidor não é necessária.

No entanto, a autenticação de servidor para servidor será exigida ser você quiser usar os novos recursos do Lync Server, como o "armazenamento de contato unificado". Com o armazenamento de contato unificado, as informações de contato do Lync Server 2013 são armazenadas no Exchange 2013 em vez do Lync Server; isso permite que os usuários tenham um único conjunto de contatos já acessível pelo Lync, Microsoft Outlook ou Microsoft Outlook Web Access. Em virtude de o armazenamento de contato unificado precisar do Lync Server 2013 para compartilhar informações com o Exchange 2013, é preciso usar a autenticação de servidor para servidor a fim de implantar o recurso. A autenticação de servidor para servidor também será exigida se você optar por usar o arquivamento do Exchange, no qual as transcrições das sessões de mensagens instantâneas são salvas como emails do Exchange 2013 em vez de registros do banco de dados individual.

Para que a versão do Office 365 do Lync Server se comunique com o respectivo equivalente do Exchange, o Lync Server 2013 deve obter primeiro um token de segurança do servidor de autorização. Então, o Lync Server usa esse token de segurança para se identificar com o Exchange. A versão do Office 365 do Exchange deve passar pelo mesmo processo para se comunicar com o Lync Server 2013.

No entanto, para uma autenticação de servidor para servidor ente dois servidores da Microsoft, não é preciso usar um servidor de token terceirizado. Produtos de servidor, como o Lync Server 2013 e o Exchange 2013 têm um servidor de token integrado que pode ser usado para fins de autenticação com outros servidores da Microsoft (como o SharePoint Server) que dão suporte à autenticação de servidor para servidor. Por exemplo, o Lync Server 2013 pode ele mesmo gerar e assinar um token de segurança e usá-lo para se comunicar com o Exchange 2013. Em um caso como esse, não há a necessidade de um servidor de token terceirizado.

Para configurar uma autenticação de servidor para servidor de uma implantação local do Lync Server 2013, é preciso fazer duas coisas:

  - Atribuir um certificado ao emissor de token integrado do Lync Server.

  - Configurar o servidor com que o Lync Server 2013 se comunicará para que seja um "aplicativo de parceiro". Por exemplo, se o Lync Server 2013 precisa se comunicar com o Exchange 2013, será preciso configurar o Exchange para que ele seja um aplicativo de parceiro.

> [!NOTE]  
> Um &quot;aplicativo de parceiro&quot; é qualquer aplicativo com o qual o Lync Server 2013 pode trocar diretamente tokens de segurança sem ter que atravessar um servidor de token de segurança terceirizado.

Observe que o OAuth é uma parte essencial do produto e não pode ser desabilitado, nem removido.

## Consulte Também

#### Conceitos

[Atribuindo um Certificado de Autenticação Servidor para Servidor a Microsoft Lync Server 2013](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md)  
[Configurando Microsoft Lync Server 2013 em um Ambiente Entre Instalações](lync-server-2013-configuring-lync-server-in-a-cross-premises-environment.md)

