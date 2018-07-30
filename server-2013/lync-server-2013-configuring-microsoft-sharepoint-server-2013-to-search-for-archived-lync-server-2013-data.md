---
title: Configurando Microsoft SharePoint Server 2013 para buscar dados arquivados no Microsoft Lync Server 2013
TOCTitle: Configurando Microsoft SharePoint Server 2013 para buscar dados arquivados no Microsoft Lync Server 2013
ms:assetid: 17f49365-8778-4962-a41b-f96faf6902f1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687978(v=OCS.15)
ms:contentKeyID: 49886116
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Microsoft SharePoint Server 2013 para buscar dados arquivados no Microsoft Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Uma das maiores vantagens de armazenar transcrições de conferências web e mensagens instantâneas no Microsoft Exchange Server 2013, ao invés de no Microsoft Lync Server 2013, é o fato de que armazenar dados no mesmo local permite que os administradores usem uma unica ferramenta para pesquisar por dados arquivados do Exchange e/ou dados arquivados do Lync Server. Por todos os dados estarem armazenados no mesmo local (Exchange), qualquer ferramenta que possa pesquisar por dados arquivados do Exchange também pode pesquisar por dados arquivados do Lync Server.

Uma ferramenta que facilita a pesquisa por dados arquivados é o Microsoft SharePoint Server 2013. Caso deseje usar o SharePoint para pesquisar por dados do Lync Server, você deve primeiro completar todos os passos envolvidos em configurar o arquivamento do Exchange no Lync Server. Depois que o Exchange 2013 e o Lync Server 2013 tiverem sido integrados com sucesso, você então deve instalar a Exchange Web Services Managed API Version 2.0 em seu servidor do SharePoint; o programa de instalação para esta API pode ser baixado no Centro de Download da Microsoft ([http://go.microsoft.com/fwlink/?linkid=258305\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=258305%26clcid=0x416)). O arquivo baixado (EWSManagedAPI.msi) pode ser salvo em qualquer pasta no seu servidor do SharePoint.

Após o arquivo ter sido baixado, complete o procedimento a seguir no servidor do SharePoint:

1.  Abra uma janela de comando clicando em **Iniciar**, clicando em **Todos os Programas**, clicando em **Acessórios**, clicando com o botão direito em **Prompt de comando**, e então clicando em **Executar como administrador**.

2.  Na janela de comando, use o comando **cd** mada mudar o diretório atual para a pasta onde o arquivo EWSManagedAPI.msi foi salvo. Por exemplo, caso tenha salvo o arquivo em C:\\Downloads, digite o comando a seguir então pressione ENTER:
    
        cd C:\Downloads

3.  Para instalar a API, digite o comando a seguir e então pressione ENTER:
    
        msiexec /I EwsManagedApi.msi addlocal="ExchangeWebServicesApi_Feature,ExchangeWebServicesApi_Gac"

4.  Depois que a API tenha sido instalada, reinicie o IIS digitando o seguinte comando e pressionando ENTER:
    
        iisreset

Depois que os Serviços Web do Exchange tenham sido instalados, você deve configurar a autenticação de servidor a servidor entre o SharePoint Server 2013 e o Exchange 2013. Para fazer isso, primeiro abra o SharePoint 2013 Management Shell e execute o conjunto de comandos a seguir:

    New-SPTrustedSecurityTokenIssuer -Name "Exchange" -MetadataEndPoint "https://autodiscover.litwareinc.com/autodiscover/metadata/json/1"
    $service = Get-SPSecurityTokenServiceConfig
    $service.HybridStsSelectionEnabled = $True
    $service.AllowMetadataOverHttp = $False
    $service.AllowOAuthOverHttp = $False
    $service.Update()

> [!NOTE]  
> Tenha certeza de qual é o URI para seu serviço de descoberta automática e o use. Não use o URI de exemplo https://autodiscover.litwareinc.com/autodiscover/metadata/json/1.

Após ter criado o emissor de token e configurado o serviço de token, execute estes comandos, assegurando-se de substituir a URL de seu site do SharePoint pela URL de exemplo http://atl-sharepoint-001:

    $exchange = Get-SPTrustedSecurityTokenIssuer "Exchange"
    $app = Get-SPAppPrincipal -Site "https://atl-sharepoint-001" -NameIdentifier $exchange.NameID
    $site = Get-SPSite  "https://atl-sharepoint-001"
    Set-SPAppPrincipalPermission -AppPrincipal $app -Site $site.RootWeb -Scope "SiteSubscription" -Right "FullControl" -EnableAppOnlyPolicy

Para configurar autenticação de servidor a servidor para o Exchange 2013, abra o Shell de Gerenciamento do Exchange e execute um comando similar a este (presumindo que o Exchange tenha sido instalado na unidade C: e que usa o caminho de pasta padrão):

    "C:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1 -AuthMetaDataUrl 'https://atl-sharepoint-001/_layouts/15/metadata/json/1' -ApplicationType SharePoint"

Após configurar o aplicativo parceiro, é recomendável que você pare e reinicie o IIS (Serviços de Informações da Internet) em todos os seus servidores de acesso de cliente e de caixa de correio do Exchange. Você pode reiniciar o IIS usando um comando similar a este, que reinicia o serviço no computador atl-exchange-001:

    iisreset atl-exchange-001

Este comando pode ser executado de dentro do Shell de Gerenciamento do Exchange ou de qualquer outra janela de comando.

Depois, execute um comando similar ao seguinte, que dá ao usuário especificado (neste exemplo, kenmyer) o direito de fazer descoberta no Exchange:

    Add-RoleGroupMember "Discovery Management" -Member "kenmyer"

Depois que a autenticação de servidor a servidor tenha sido estabelecida entre o Exchange e o SharePoint, seu próximo site é criar um site de descoberta eletrônica no SharePoint. Isso pode ser feito executando comandos similares a estes do Shell de Gerenciamento do SharePoint:

    $template = Get-SPWebTemplate | Where-Object {$_.Title -eq "eDiscovery Center"}
    New-SPSite -Url "https://atl-sharepoint-001/sites/discovery" -OwnerAlias "kenmyer" -Template $Template -Name "Discovery Center"

> [!NOTE]  
> &quot;eDiscovery&quot; é uma abreviação de &quot;electronic discovery (descoberta eletrônica)&quot;, e normalmente se refere ao processo de pesquisa por itens em arquivos eletrônicos, que possa ser &quot;razoavelmente calculada para levar a provas admissíveis&quot; em tribunal judicial.

Quando o novo site estiver pronto, o passo seguinte é configurar o Exchange 2013 para agir como uma fonte de resultados para o SharePoint. Você pode fazer iso completando o procedimento a seguir da página de Administração Central do SharePoint 2013:

1.  Na página de Administração Central, clique em **Gerenciar Aplicativos de Serviço** e então clique em **Aplicativo de Serviço de Pesquisa**.

2.  Na página Aplicativo de Serviço de Pesquisa: Administração de Pesquisa, clique em **Fontes de Resultado** e então clique em **Nova Fonte de Resultado**.

3.  No painel **Nova Fonte de Resultado** insira um nome para a nova fonte de resultado (por exemplo, **Microsoft Exchange**) na caixa **Nome**. Selecione **Exchange** como o **Protocolo** de fonte de resultado, e então insira a URL da fonte de serviços web para seu servidor do Exchange na caixa **URL da Fonte do Exchange**. A URL da fonte deve parecer com esta:
    
    https://atl-exchange-001.litwareinc.com/ews/exchange.asmx

4.  Assegure-se de que **Usar Descoberta Automática** não está selecionado, e então clique em **OK**.

Finalmente, crie um novo caso de descoberta eletrônica e um novo conjunto de descoberta eletrônica, completando o procedimento a seguir a partir do site de Descoberta do SharePoint (por exemplo, https://atl-sharepoint-001/sites/discovery):

1.  Na página de Conteúdos do Site clique em **Criar um novo caso**.

2.  Na página Conteúdos do Site: Novo Site do SharePoint, insira o alias do email do usuário (por exemplo, **kenmyer**) na caixa **Título**, então adicione esta mesma URL à caixa **Endereço do Site**. Isso resultará em uma URL similar a esta:
    
    https://atl-sharepoint-001/sites/eDiscovery/kenmyer

3.  Clique em **Criar**.

4.  Quando a página de conjunto de descoberta eletrônica aparecer, clique em **novo item** sob **Identidade e Preservação: Conjuntos de Descoberta**.

5.  Na página Novo: Conjunto de Descoberta, insira o alias do email do usuário na caixa **Nome do Conjunto de Descoberta**. Insira **eDiscovery Lync\*** na caixa **Filtro** e então clique em **Adicionar e Gerenciar Fontes**.

6.  Na página Adicionar e Gerenciar Fontes, insira o alias do email do usuário na primeira caixa de texto sob **Caixas de correio**. Clique no ícone de verificação da caixa de correio ao lado da caixa de texto para verificar que o SharePoint consegue se conectar à caixa de correio especificada.

7.  Clique em **OK**.

8.  Na página do conjunto de descoberta eletrônica, clique em **Salvar** para salvar o novo conjunto de descoberta eletrônica.

Nesse momento você pode pesquisar pela caixa de correio especificada (kenmyer) e/ou habilitar Bloqueios In-loco da mesma maneira que você faria para qualquer outra fonte de resultados ou conteúdo do SharePoint.

