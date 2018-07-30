---
title: Pré-requisitos para integrar Microsoft Lync Server 2013 e Microsoft Exchange Server 2013
TOCTitle: Pré-requisitos para integrar Microsoft Lync Server 2013 e Microsoft Exchange Server 2013
ms:assetid: ea22beb9-c02e-47cb-836d-97a556969052
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721919(v=OCS.15)
ms:contentKeyID: 49886463
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos para integrar Microsoft Lync Server 2013 e Microsoft Exchange Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Antes que você possa integrar o Microsoft Lync Server 2013 e o Microsoft Exchange Server 2013, você deve assegurar-se de que todos as etapas de pré-requisito foram concluídas. Como poderia se esperar, a integração não pode acontecer até que ambos o Exchange 2013 e o Lync Server 2013 estejam totalmente instalados, configurados e funcionando. Para detalhes sobre a instalação do Exchange, consulte a documentação de Planejamento e Implantação do Exchange 2013 em [http://go.microsoft.com/fwlink/?linkid=268539\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268539%26clcid=0x416). Para detalhes sobre a instalação do Lync Server 2013, consulte a documentação de Planejamento e Implantação em [http://go.microsoft.com/fwlink/?linkid=254806\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=254806%26clcid=0x416).

Depois que os servidores estiverem funcionando, você deve atribuir certificados de autenticação de servidor a servidor para ambos Lync Server 2013 e Exchange 2013; estes certificados permitem que o Lync Server e o Exchange troquem informações e se comuniquem. Ao instalar o Exchange 2013, um certificado autoassinado com o nome Microsoft Exchange Server Auth Certificate é criado para você. Este certificado, que pode ser encontrado no repositório de certificados do computador local, deve ser usado para autenticação de servidor a servidor no Exchange 2013. Para obter detalhes sobre a atribuição de certificados no Exchange 2013, consulte "Configurar Fluxo de Correio e Acesso de Cliente" em [http://go.microsoft.com/fwlink/?linkid=268540\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268540%26clcid=0x416).

Para Lync Server 2013 você pode usar um certificado existente do Lync Server como seu certificado de autenticação de servidor a servidor; por exemplo, seu certificado padrão também pode ser usado como o certificado do OAuthTokenIssuer. O Lync Server 2013 permite que você use qualquer certificado de servidor web como certificado para autenticação de servidor a servidor, desde que:

  - O certificado inclua o nome de seu domínio SIP no campo de Entidade.

  - O mesmo certificado esteja configurado como o certificado do OAuthTokenIssuer em todos os seus servidores Front-End.

  - O certificado tenha no mínimo 2048 bits.

Para obter detalhes sobre certificados para autenticação de servidor a servidor para Microsoft Lync Server 2013, consulte [Atribuindo um Certificado de Autenticação Servidor para Servidor a Microsoft Lync Server 2013](lync-server-2013-assigning-a-server-to-server-authentication-certificate-to-lync-server-2013.md).

Depois que os certificados tenham sido atribuídos, você deve configurar o serviço de descoberta automática no Exchange 2013. No Exchange 2013, o serviço de descoberta automática configura os perfis de usuário e fornece acesso aos serviços do Exchange quando os usuários fazem logon no sistema. Os usuários apresentam seus endereços de email e senhas ao serviço de descoberta automática; por sua vez, os serviços fornecem aos usuários informações como:

  - Informação de conexão tanto para conectividade interna quanto externa para Exchange 2013.

  - A localização do servidor da Caixa de Correio do usuário.

  - URLs para recursos do Outlook como informações de livre/ocupado, Unificação de Mensagens e o catálogo de endereços offline.

  - Configurações do servidor do Outlook Anywhere.

O serviço de descoberta automática deve ser configurado antes que você possa integrar o Lync Server 2013 e o Exchange 2013. Você pode verificar se o serviço de descoberta automática foi configurado ou não executando o comando a seguir, a partir do Shell de Gerenciamento do Exchange, e verificando o valor da propriedade AutoDiscoverServiceInternalUri:

    Get-ClientAccessServer | Select-Object Name, AutoDiscoverServiceInternalUri | Format-List

Caso o valor esteja em branco, você deve atribuir um URI ao serviço de descoberta automática:

    https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml

Você pode atribuir o URI de descoberta automática executando um comando similar a este:

    Get-ClientAccessServer | Set-ClientAccessServer -AutoDiscoverServiceInternalUri "https://autodiscover.litwareinc.com/autodiscover/autodiscover.xml"

Para obter detalhes sobre o serviço de descoberta automática, consulte "Entendendo o Serviço de Descoberta Automática" em [http://go.microsoft.com/fwlink/?linkid=268542\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268542%26clcid=0x416).

Depois que o serviço de descoberta automática tenha sido configurado, você deve modificar as definições de configuração do OAuth do Lync Server ; isso assegura que o Lync Server saiba onde encontrar o serviço de descoberta automática. Para modificar as definições de configuração do OAuth no Lync Server 2013, execute o comando a seguir de dentro do Shell de Gerenciamento do Lync Server. Ao executar este comando, assegure-se de especificar o URI ao serviço de descoberta automática sendo executado em seu servidor do Exchange, e que use o **autodiscover.svc** para indicar a localização do serviço ao invés do **autodiscover.xml** (que aponta o arquivo XML usado pelor serviço):

    Set-CsOAuthConfiguration -Identity global -ExchangeAutodiscoverUrl "https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc

> [!NOTE]  
> O parâmetro Identidade no comando anterior é opcional; isso pois o Lync Server permite apenas que você tenha um conjunto único, global de definições de configuração OAuth. Dentre outras coisas, isso significa que você pode configurar a URL de descoberta automática usando este comando um pouco mais simples:<br />Set-CsOAuthConfiguration–ExchangeAutodiscoverUrl &quot;https://autodiscover.litwareinc.com/autodiscover/autodiscover.svc&quot;<br />Caso não esteja familiarizado com a tecnologia, o OAuth é um protocolo de autorização padrão usado por vários websites importantes. Com o OAuth, as credenciais de usuário e senhas não são passadas de um computador a outro. Ao invés disso, a autenticação e autorização são baseadas na troca de tokens de segurança; estas tokens concedem acesso a um conjunto específico de recursos por um período determinado de tempo.

Além de configurar o serviço de descoberta automática, você também deve criar um registro DNS para o serviço que aponta para o seu servidor do Exchange. Por exemplo, caso seu serviço de descoberta automática esteja localizado em autodiscover.litwareinc.com você deverá criar um registro DNS para autodiscover.litwareinc.com resolve para o nome de domínio totalmente qualificado de seu servidor do Exchange (por exemplo, atl-exchange-001.litwareinc.com).

