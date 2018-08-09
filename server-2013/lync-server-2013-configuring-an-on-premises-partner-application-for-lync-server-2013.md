---
title: "Configurando um Aplicativo de Parceiro no Local p/ Microsoft Lync Server 2013"
TOCTitle: "Configurando um Aplicativo de Parceiro no Local p/ Microsoft Lync Server 2013"
ms:assetid: 696f2b26-e5d0-42b5-9785-a26c2ce25bb7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204975(v=OCS.15)
ms:contentKeyID: 49306992
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando um Aplicativo de Parceiro no Local para Microsoft Lync Server 2013

 

_**Tópico modificado em:** 2013-02-04_

Depois que você tiver atribuído o certificado OAuthTokenIssuer, precisará configurar os aplicativos parceiros do Microsoft Lync Server 2013 (o procedimento que será abordado a seguir configura o Microsoft Exchange Server 2013 e o Microsoft SharePoint para atuarem como aplicativos parceiros). Para configurar um aplicativo parceiro local, você precisa começar copiando o seguinte script do Windows PowerShell e colando o código no Bloco de Notas (ou em qualquer editor de texto):

    if ((Get-CsPartnerApplication -ErrorAction SilentlyContinue) -ne $Null)
       {
           Remove-CsPartnerApplication app
       }
    
    $exch = Get-CsPartnerApplication microsoft.exchange -ErrorAction SilentlyContinue
            
    if ($exch -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.exchange -MetadataUrl https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 -ApplicationTrustLevel Full 
        }
    else
        {
           if ($exch.ApplicationIdentifier -ne "00000002-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.exchange
    New-CsPartnerApplication -Identity microsoft.exchange -MetadataUrl https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 -ApplicationTrustLevel Full 
               }
            else
               {
                 Set-CsPartnerApplication -Identity microsoft.exchange -ApplicationTrustLevel Full 
               }
         }
    
    $shp = Get-CsPartnerApplication microsoft.sharepoint -ErrorAction SilentlyContinue
            
    if ($shp -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.sharepoint -MetadataUrl http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx -ApplicationTrustLevel Full 
        }
    else
        {
           if ($shp.ApplicationIdentifier -ne "00000003-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.sharepoint
      
                 New-CsPartnerApplication -Identity microsoft.sharepoint -MetadataUrl http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx -ApplicationTrustLevel Full 
               }
            else
               {
                 Set-CsPartnerApplication -Identity microsoft.sharepoint -ApplicationTrustLevel Full 
                }
       }
    
    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

Depois de copiar o código, salve o script usando a extensão de arquivo .PS1 (por exemplo, C:\\Scripts\\ServerToServerAuth.ps1). Observe que, antes de executar esse script, você precisa substituir as URLs de metadados https://atl-exchange-001.litwareinc.com/autodiscover/metadata/json/1 e http://atl-sharepoint-001.litwareinc.com/jsonmetadata.ashx pelas URLs de metadados usadas por seus servidores do Exchange 2013 e do SharePoint, respectivamente. Consulte a documentação do produto do Exchange 2013 e do SharePoint para obter informações sobre como identificar a URL de metadados de cada produto.

Se você observar a última linha do script, perceberá que o cmdlet Set-CsOAuthConfiguration é chamado com o uso da sintaxe:

    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

Como o parâmetro Realm não foi usado para chamar Set-CsOAuthConfiguration, o realm automaticamente será definido como o FQDN (nome de domínio totalmente qualificado) de sua organização (por exemplo, litwareinc.com). Se o seu realm for diferente do nome da sua organização, inclua o nome do realm da seguinte maneira:

    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000 -Realm "contoso.com"

Após fazer essas alterações, você poderá executar o script e configurar o Exchange 2013 e o SharePoint como aplicativos parceiros executando o arquivo de script a partir do Shell de Gerenciamento do Lync Server 2013. Por exemplo:

    C:\Scripts\ServerToServerAuth.ps1

Você poderá executar esse script mesmo se não tiver o Exchange 2013 e o SharePoint Server instalados. Não haverá problemas se, por exemplo, você configurar o SharePoint Server como um aplicativo parceiro mesmo que ele não esteja instalado.

Ao executar esse script, você talvez receba uma mensagem de erro semelhante à seguinte:

    New-CsPartnerApplication : Cannot bind parameter 'MetadataUrl' to the target. Exception setting "MetadataUrl": "The metadata document could not be downloaded from the URL in the MetadataUrl parameter or downloaded data is not a valid metadata document."

Essa mensagem de erro geralmente significa que: 1) uma das URLs especificadas no script não é válida (ou seja, uma das URLs de metadados não é realmente uma URL de metadados); ou 2) não foi possível acessar uma das URLs de metadados. Se isso acontecer, verifique se as URLs estão corretas e acessíveis e execute o script novamente.

Após a criação do aplicativo parceiro do Lync Server 2013, você precisa configurar o Lync Server para ser um aplicativo parceiro do Exchange 2013. Você pode configurar aplicativos parceiros para o Exchange 2013 executando o script Configure-EnterprisePartnerApplication.1. Basta especificar a URL de metadados do Lync Server e indicar que o Lync Server é o novo aplicativo parceiro.

Para configurar o Lync Server como um aplicativo parceiro do Exchange, abra o Shell de Gerenciamento do Exchange e execute um comando semelhante ao seguinte:

    "c:\Program Files\Microsoft\Exchange Server\V15\Scripts\Configure-EnterprisePartnerApplication.ps1" -AuthMetadataUrl "https://lync.contoso.com/metadata/json/1" -ApplicationType "Lync"

