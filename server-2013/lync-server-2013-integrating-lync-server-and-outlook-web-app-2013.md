---
title: Integrando o Microsoft Lync Server 2013 e o Microsoft Outlook Web App 2013
TOCTitle: Integrando o Microsoft Lync Server 2013 e o Microsoft Outlook Web App 2013
ms:assetid: 513d4cc7-aa87-4f68-b99d-d58b63bdf242
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688055(v=OCS.15)
ms:contentKeyID: 49886219
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Integrando o Microsoft Lync Server 2013 e o Microsoft Outlook Web App 2013

 

_**Tópico modificado em:** 2016-12-08_

Além da integração com o Microsoft Outlook 2013, o Microsoft Lync Server 2013 pode ser totalmente integrado com o Microsoft Outlook Web App 2013; entre outras coisas, ele acrescenta mensagens instantâneas e a presença do Outlook Web App e permite que a sua lista de contatos unificada seja compartilhada entre o Outlook Web App e o Microsoft Lync 2013. A fim de integrar o Lync Server 2013 e o Outlook Web App, você deve primeiro verificar se o Unified Communications Managed API 4.0 Runtime foi instalado no seu servidor back-end do Microsoft Exchange Server 2013. Você pode fazer isso verificando a existência do seguinte valor de registro:

HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Services\\MSExchange OWA\\InstantMessaging\\ImplementationDLLPath

O ImplementationDLLPath deve apontar para a localização da pasta do arquivo Micrsooft.Rtc.Internal.Ucweb.dll. Se isso não ocorrer ou se o valor do registro não existir, você deve fazer download e instalar o programa de instalação do UCMA Runtime a partir do Centro de Download da Microsoft em <http://www.microsoft.com/pt-br/download/details.aspx?id=34992>.

**Retrocompatibilidade**

O Lync Server 2013 pode ser integrado com as versões Microsoft Exchange Server 2010 tanto de envio de mensagens unificado quanto do Outlook Web App. Para mais informações, consulte o artigo Implantando Envio de Mensagens Unificado do Exchange no Local Para Oferecer Correio de Voz do Lync Server 2010, em [http://technet.microsoft.com/pt-br/library/gg398768.aspx](lync-server-2013-deploying-on-premises-exchange-um-to-provide-lync-server-2013-voice-mail.md). Se você integrá-lo com o Exchange 2010. não terá recursos específicos do Lync Server como o repositório unificado de contatos e o arquivamento de Lync para Exchange.

O Microsoft Lync 2013 também pode ser utilizado em conjunto com o Exchange 2010 e o Outlook 2010. Novamente, porém, novas funcionalidades como o repositório unificado de contatos e fotos em alta resolução não estarão disponíveis para usuários do Lync 2013. Esses novos recursos exigem ambos o Lync Server 2013 e o Exchange 2013.

**Para criar um pool de aplicativo confiável para o Outlook Web App**

Se você instalou o serviço Roteador de Unificação de Mensagens Microsoft Exchange e o serviço de Unificação de Mensagens Microsoft Exchange no mesmo computador, não é necessário criar um pool de aplicativos confiáveis para o Outlook Web App (assumindo que o servidor em questão esteja hospedando um plano de discagem de UM SipName). Se você estiver utilizando um único computador para hospedar ambos esses serviços, você então poderá pular para a seção deste documento intitulada **Para habilitar envio de mensagens instantâneas no Outlook Web App**.

O Lync Server 2013 pode descobrir automaticamente qualquer servidor Exchange que hospede um plano de discagem de unificação de mensagens SipName; esses servidores são automaticamente adicionados à lista de servidores conhecidos do Lync Server. Não é necessário criar um pool de aplicativos confiáveis e adicionar esses servidores à lista de servidores conhecidos. Na verdade fazer isso pode até fazer com que a integração do Outlook Web App pare de funcionar.

> [!NOTE]  
> Isso ocorre devido ao fato de que a topologia do Lync Server terá agora duas entradas para o mesmo computador: a entrada obtida por Descoberta Automática e a entrada adicionada manualmente. Para corrigir esse problema e fazer com que o Outlook Web App volte a funcionar, use o Windows PowerShell para remover as entradas de pool confiável e aplicativo confiável para o servidor. Consulte os tópicos de ajuda para os cmdlets <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsTrustedApplicationPool">Remove-CsTrustedApplicationPool</a> e <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsTrustedApplication">Remove-CsTrustedApplication</a> para obter mais informações.

Se esses dois serviços estiverem funcionando então em computadores separados, depois de ter verificado se o Unified Communications Managed API 4.0 Runtime foi instalado, você deve criar um pool de aplicativos confiáveis do Lync Server e um aplicativo confiável associado ao Outlook Web App; isso adicionará o servidor à lista de servidores conhecidos. Para fazer isso, primeiro execute um comando semelhante a este de dentro do Shell de Gerenciamento do Lync Server:

    New-CsTrustedApplicationPool -Identity atl-owa-001.litwareinc.com -Registrar atl-cs-001.litwareinc.com -Site Redmond -RequiresReplication $False

No comando anterior, o atl-owa-001.litwareinc.com é o nome de domínio totalmente qualificado do pool do Outlook Web App, ele deve ter o mesmo nome que é exibido nos campos Nome da Entidade e Nome Alternativo da Entidade (SAN) do certificado que fornece acesso ao Otlook Web App. Do mesmo modo, o atl-cs-001.litwareinc.com é o nome de domínio totalmente qualificado do pool do Lync Server 2013 que hospedará o novo pool de aplicativos confiáveis. Observe também que o site especificado, Redmond, representa o SiteID do site do Lync Server. O SiteID não é necessariamente o mesmo que DisplayName do site, você pode recuperar SiteIDs para seus sites do Lync Server, executando o seguinte comando do Shell de Gerenciamento do Lync Server:

    Get-CsSite | Select-Object DisplayName, SiteID

Após criar um pool de aplicativos confiáveis, utilize um comando semelhante para prosseguir com a configuração de um aplicativo Identity e uma porta para o Outlook Web App:

    New-CsTrustedApplication -ApplicationId OutlookWebApp -TrustedApplicationPoolFqdn atl-owa-001.litwareinc.com  -Port 5199

No comando anterior, o ApplicationID é simplesmente um identificador amigável usado para distinguir aplicativos confiáveis. O ApplicationID pode ser qualquer cadeia de caracteres de texto que não inclua espaços em branco ou outros caracteres proibidos. (Para garantir que você criará um identificador válido, é recomendado que apenas letras e números sejam utilizados ao especificar um ApplicationId.) O valor atribuído ao parâmetro Porta também é deixado ao critério do administrador: ela pode ser qualquer porta de rede disponível.

Após criar o aplicativo confiável, você deve executar o seguinte comando para habilitar as alterações para a topologia do seu Lync Server:

    Enable-CsTopology

Observe que você também precisa adicionar o acesso de cliente Exchange e servidor de caixa postal para todos os seus planos de discagem Uri SIP. Isso por sua vez vai configurar os servidores como parcerias SIP confiáveis com a topologia ExUmRouting para o Lync Server.

**Para habilitar envio de mensagens instantâneas no Outlook Web App**

Com o Lync Server configurado corretamente, você pode começar a configurar o Outlook Web App. O primeiro passo no processo é habilitar as mensagens instantâneas em todos os seus diretórios virtuais do Outlook Web App nos seus servidores front-end (não há necessidade de habilitar envio de mensagens instantâneas para os diretórios virtuais nos seus servidores de back-end; na verdade, é recomendável que para esses servidores você não o habilite). A habilitação de IM pode ser feita nos servidores de acesso do cliente executando o seguinte comando a partir do Shell de Gerenciamento do Exchange:

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -InstantMessagingEnabled $True -InstantMessagingType OCS

> [!NOTE]  
> Por padrão, o envio de mensagens instantâneas é habilitado quando você instala o Outlook Web App; ou seja, a propriedade InstantMessagingEnabled é definida como True. Porém, você ainda precisa executar o comando anterior para definir o tipo de envio de mensagens instantâneas como OCS. Como padrão, InstantMessagingType é definido com o valor Nenhum.

Em seguida, você deve adicionar as linhas a seguir ao arquivo Web.config do Outlook Web App (esse arquivo está, normalmente, localizado na pasta C:\\Program Files\\Microsoft\\Exchange Server\\V15\\ClientAccess\\Owa). Essas duas linhas devem ser adicionadas sob o nó AppSettings, no arquivo Web.config, sendo que esse procedimento só deve ser realizado naqueles servidores de back-end em que o Outlook Web App tenha sido instalado:

    <add key="IMCertificateThumbprint" value="EA5A332496CC05DA69B75B66111C0F78A110D22d"/>
    <add key="IMServerName" value="atl-cs-001.litwareinc.com"/>

No exemplo anterior, o valor para IMCertificateThumbprint deve ser a impressão digital para o certificado do Exchange 2013 instalado em seus servidores de back-end. Você pode recuperar essas informações, executando o seguinte comando a partir do Shell de Gerenciamento do seu Exchange:

    Get-ExchangeCertificate

Observe, também, que o valor atribuído ao IMServerName é o nome de domínio totalmente qualificado do pool do Lync Server, no qual você criou o pool de aplicativos confiáveis ​​para o Outlook Web App.

O certificado que você utiliza para o Outlook Web App precisa ser um certificado confiável para o Lync Server. Um modo de garantir que o certificado será confiável para ambos o Lync Server e Exchange é utilizar a sua autorizade de certificado interno para criar um certificado no servidor de caixa postal, assegurando que o servidor FQDN seja usado para o nome da entidade e que esse FQDN apareça no campo de nome alternativo do certificado. Após o certificado ter sido criado, ele pode ser importado para os seus servidores de back-end. O resultado final é que o mesmo certificado é usado para dois fins: o primeiro é a comunicação entre unificação de mensagens de Exchange e Lync Server; o segundo é a integração entre o Outlook Web App e o Lync Server.

Depois de ter atualizado o arquivo Web.config, você deve executar o seguinte comando no servidor de back-end do Exchange, para reciclar o pool do Outlook Web App:

    C:\Windows\System32\Inetsrv\Appcmd.exe recycle apppool /apppool.name:"MSExchangeOWAAppPool"

Se a operação de reciclagem for bem sucedida, você verá a seguinte mensagem no Shell de Gerenciamento do Exchange:

    "MSExchangeOWAAppPool" successfully recycled

**Para configurar as políticas de caixa postal do Outlook Web App**

Nesse ponto, você pode usar o comando a seguir para configurar as mensagens instantâneas na política (ou políticas) de caixa de correio apropriada do seu Outlook Web App. Por exemplo, esse comando executado em um de seus servidores de caixa postal habilita as mensagens instantâneas na política padrão:

    Set-OwaMailboxPolicy -Identity "Default" -InstantMessagingEnabled $True -InstantMessagingType "OCS"

E esse comando habilita as mensagens instantâneas para todas as suas políticas de caixa de correio do Outlook Web App:

    Get-OwaMailboxPolicy | Set-OwaMailboxPolicy -InstantMessagingEnabled $True -InstantMessagingType "OCS"

Após a política de caixa de correio ser habilitada, todos os usuários gerenciados por essa política terão a integração total entre o Lync Server e o Outlook Web App, desde que:

  - O usuário possui uma caixa de correio no Exchange 2013.

  - O usuário foi habilitado para o Lync Server 2013.

  - O usuário possui um endereço de proxy SIP válido.

**Para desabilitar envio de mensagens instantâneas no Outlook Web App**

Como observado anteriormente, mensagens instantâneas estão habilitadas por padrão no Outlook Web App. Isso significa que se você não integrar o Outlook Web App com o Lync Server, os usuários verão ícones de presença em branco e uma mensagem de erro cada vez que fizerem login no Outlook Web App. Para evitar esse problema, use o comando de Shell de Gerenciamento Exchange a seguir para desabilitar as mensagens instantâneas no Outlook Web App:

    Get-OwaVirtualDirectory | Set-OwaVirtualDirectory -InstantMessagingEnabled $False

**Para verificar a integração com o Outlook Web App**

Para verificar se as mensagens instantâneas e a presença foram integradas ao Outlook Web App, entre no Outlook Web App 2013. No canto superior direito da tela, você verá o seu nome para exibição do Exchange. Se houver um ícone de presença ao lado do seu nome (por exemplo, um ícone verde indicando que seu status atual é Disponível) indica que você fez com sucesso a integração do Lync Server com o Outlook Web App.

Após a inscrição inicial no Outlook Web App, verifique se um evento com a ID de evento 112 (e a fonte sendo Outlook Web App MSExchange) foi gravado no log de eventos no servidor da caixa postal. Esse evento indica que o gerenciador de ponto de extremidade para mensagens instantâneas foi inicializado com sucesso. Se as mensagens instantâneas não aparentarem funcionar nesse momento, acesse o servidor de caixa postal e procure por arquivos de log na pasta C:\\Program Files\\Microsoft\\Exchange server\\V15\\Logging\\OWA\\InstantMessaging. Se qualquer uma das pastas Logging ou InstantMessaging não existirem, isso indica que a integração falhou. Nesse caso, você pode utilizar rastreamento SIPStack no Lync Server (todos os níveis e todos os marcadores) para tentar determinar porque a integração falhou.

