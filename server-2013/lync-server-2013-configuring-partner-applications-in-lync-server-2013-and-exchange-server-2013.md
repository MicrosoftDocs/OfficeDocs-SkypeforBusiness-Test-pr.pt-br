---
title: Configurando Inscrição de Parceiro no Microsoft Lync Server 2013 e Microsoft Exchange Server 2013
TOCTitle: Configurando Inscrição de Parceiro no Microsoft Lync Server 2013 e Microsoft Exchange Server 2013
ms:assetid: 9c3a3054-6201-433f-b128-4c49d3341370
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688151(v=OCS.15)
ms:contentKeyID: 49886331
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Inscrição de Parceiro no Microsoft Lync Server 2013 e Microsoft Exchange Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A autenticação entre servidores geralmente envolve três entidades: os dois servidores que precisam se comunicam entre si e um terceiro servidor de token de segurança. Se dois servidores (por exemplo, Servidor A e Servidor B) precisarem se comunicar, então ambos geralmente iniciam entrando em contato com o servidor de token, obtendo um token de segurança mutuamente confiável. O Servidor A então apresenta esse token de segurança ao Servidor B (e vice-versa), como uma forma de garantir autenticidade e confiabilidade.

No entanto, esta é uma regra geral. O Lync Server 2013, Microsoft Exchange Server 2013 e Microsoft SharePoint Server 2013 não precisam usar um terceiro servidor de token ao se comunicam uns com ou outros; isso porque esses produtos de servidores podem criar tokens de segurança que podem ser aceitos pelos outros sem a necessidade de um servidor de token separado. (Esse recurso está disponível somente no Lync Server 2013, Exchange 2013 e SharePoint Server 2013. Se você precisar configurar uma autenticação entre servidores com outros servidores, incluindo outros produtos de servidor da Microsoft, então será necessário fazer isso usando um terceiro servidor de token.

Para configurar a autenticação entre servidores entre o Lync Server e Exchange, você deve fazer duas coisas: 1) atribuir os certificados apropriados a cada servidor; e 2) configurar cada servidor para ser um aplicativo parceiro de outro servidor: isso significa que você deve configurar o Lync Server 2013 para ser um aplicativo parceiro do Exchange 2013, e você deve configurar o Exchange 2013 para ser um aplicativo parceiro do Lync Server 2013.

## Como configurar o Lync Server 2013 para ser um Aplicativo Parceiro do Exchange 2013

A forma mais fácil de configurar um Lync Server 2013 para ser um aplicativo parceiro do Exchange 2013 é executar o script Configure-EnterprisePartnerApplication.ps1, um script do Windows PowerShell enviado com o Exchange 2013. Para executar esse script, você deverá fornecer o URL do documento de metadados de autenticação do Lync Server; isso geralmente será o nome de domínio totalmente qualificado do pool do SharePoint seguido pelo sufixo /metadata/json/1. Por exemplo:

    https://atl-cs-001.litwareinc.com/metadata/json/1

Para configurar o Lync Server como aplicativo parceiro, abra o Exchange Management Shell e execute um comando similar a esse (supondo que o Exchange tenha sido instalado na unidade C: e que ele use o caminho de pasta padrão):

    "C:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl 'https://atl-cs-001.litwareinc.com/metadata/json/1' -ApplicationType Lync"

Após configurar o aplicativo parceiro, recomenda-se que você interrompa e reinicie os Serviços de Informações da Internet (IIS) em sua caixa de correio e servidores de acesso ao cliente do Exchange. Você pode reiniciar o IIS usando um comando similar a esse, que reinicia o serviço no atl-exchange-001 do computador:

    iisreset atl-exchange-001

Este comando pode ser executado dentro do Exchange Management Shell ou de qualquer outra execução de janela de comando sob privilégios de administrador.

## Configuração do Exchange 2013 para ser aplicativo parceiro Lync Server 2013

Após configurar o Lync Server 2013 para ser um aplicativo parceiro do Exchange 2013, é necessário então configurar o Exchange para ser um aplicativo parceiro do Lync Server. Isso pode ser feito usando o Shell de Gerenciamento do Lync Server e especificando o documento de metadados de autenticação do Exchange; isso geralmente será a URI do serviço de autodescoberta do Exchange seguido pelo sufixo /metadata/json/1. Por exemplo:

    https://autodiscover.litwareinc.com/autodiscover/metadata/json/1

No Lync Server, os aplicativos parceiros são configurados usando o cmdlet [New-CsPartnerApplication](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsPartnerApplication). Além de especificar a URI de metadados, você deverá também definir o nível de confiança para Total; isso permitirá que o Exchange represente a si mesmo e qualquer usuário autorizado no domínio. Por exemplo:

    New-CsPartnerApplication -Identity Exchange -ApplicationTrustLevel Full -MetadataUrl "https://autodiscover.litwareinc.com/autodiscover/metadata/json/1"

Como alternativa, você pode criar um aplicativo parceiro copiando e modificando o código do script encontrado na documentação de autenticação entre servidores do Lync Server 2013. Consulte o artigo [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) para obter mais informações.

Se você tiver configurado os aplicativos parceiros com sucesso para Lync Server e Exchange, isso significa que você também configurou com sucesso a autenticação entre servidores entre os dois produtos. O Lync Server 2013 contém um cmdlet Windows PowerShell,[Test-CsExStorageConnectivity](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsExStorageConnectivity) que permite que você verifique se a autenticação entre servidores foi corretamente configurada e se o serviço de armazenamento do Lync Server pode se conectar ao Exchange 2013. O cmdlet faz isso se conectando à caixa de correio de um usuário do Exchange 2013, gravando um item na pasta Histórico da Conversa desse usuário e, depois, opcionalmente, excluindo esse item.

Para testar ar integração do Lync Server 2013 e Exchange 2013, execute um comando similar a esse de dentro do Shell de Gerenciamento do Lync Server:

    Test-CsExStorageConnectivity -SipUri "sip:kenmyer@litwareinc.com"

No comando anterior, o SipUri representa o endereço SIP de um usuário com uma conta no Exchange 2013; seu comando falhará se não for uma conta de usuário válida.

Se o teste for bem sucedido e a conectividade for estabelecida, será possível então prosseguir para configurar recursos opcionais, como integração de arquivamento e o armazenamento de contato unificado.

