---
title: Configurando Microsoft Lync Server 2013 em um Ambiente Entre Instalações
TOCTitle: Configurando Microsoft Lync Server 2013 em um Ambiente Entre Instalações
ms:assetid: 700639ec-5264-4449-a8a6-d7386fad8719
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204990(v=OCS.15)
ms:contentKeyID: 49307067
ms.date: 02/21/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Microsoft Lync Server 2013 em um Ambiente Entre Instalações

 

_**Tópico modificado em:** 2017-02-21_

Em uma configuração entre locais, alguns dos usuários são hospedados em uma instalação local do Microsoft Lync Server 2013, enquanto outros são hospedados na versão Office 365 do Lync Server. Para configurar a autenticação servidor a servidor em um ambiente entre locais, primeiro você deve configurar a instalação local do Lync Server 2013 para confiar no servidor de autorização do Office 365. A etapa inicial desse processo pode ser realizada por meio de execução do seguinte script do Shell de Gerenciamento do Lync Server:

    $TenantID = (Get-CsTenant -Filter {DisplayName -eq "Fabrikam.com"}).TenantId
    
    $sts = Get-CsOAuthServer microsoft.sts -ErrorAction SilentlyContinue
            
       if ($sts -eq $null)
          {
             New-CsOAuthServer microsoft.sts -MetadataUrl "https://accounts.accesscontrol.windows.net/$TenantId/metadata/json/1"
          }
       else
          {
             if ($sts.MetadataUrl -ne  "https://accounts.accesscontrol.windows.net/$TenantId/metadata/json/1")
                {
                   Remove-CsOAuthServer microsoft.sts
                   New-CsOAuthServer microsoft.sts -MetadataUrl "https://accounts.accesscontrol.windows.net/$TenantId/metadata/json/1"
                }
            }
    
    $exch = Get-CsPartnerApplication microsoft.exchange -ErrorAction SilentlyContinue
            
    if ($exch -eq $null)
       {
          New-CsPartnerApplication -Identity microsoft.exchange -ApplicationIdentifier 00000002-0000-0ff1-ce00-000000000000 -ApplicationTrustLevel Full -UseOAuthServer
        }
    else
        {
           if ($exch.ApplicationIdentifier -ne "00000002-0000-0ff1-ce00-000000000000")
              {
                 Remove-CsPartnerApplication microsoft.exchange
                 New-CsPartnerApplication -Identity microsoft.exchange -ApplicationIdentifier 00000002-0000-0ff1-ce00-000000000000 -ApplicationTrustLevel Full -UseOAuthServer 
              }
           else
              {
                 Set-CsPartnerApplication -Identity microsoft.exchange -ApplicationTrustLevel Full -UseOAuthServer
              }
       }
    
    Set-CsOAuthConfiguration -ServiceName 00000004-0000-0ff1-ce00-000000000000

Tenha em mente que o nome do realm de um locatário é normalmente diferente do nome da organização; na realidade, o nome do realm é quase sempre igual ao do ID do locatário. Por causa disso, a primeira linha do script é usada para retornar o valor da propriedade TenantId do locatário especificado (neste caso, fabrikam.com) e atribuir o nome à variável $TenantId:

    $TenantID = (Get-CsTenant -DisplayName "Fabrikam.com").TenantId

Após a conclusão do script, você deverá configurar um relacionamento de confiança entre o Lync Server 2013 e o servidor de autorização. Deverá também configurar mais um relacionamento de confiança, entre o Exchange 2013 e esse mesmo servidor. Isso só pode ser feito usando os cmdlets do Microsoft Online Services.

> [!NOTE]  
> Caso não tenha instalado os cmdlets do Microsoft Online Services, será necessário fazer duas coisas antes de continuar. Primeiro, baixe e instale a versão de 64 bits do Assistente de Conexão do Microsoft Online Services. Após a conclusão da instalação, baixe a instale a versão de 64 bits do Módulo do Microsoft Online Services para Windows PowerShell. As informações detalhadas de instalação e uso do Módulo do Microsoft Online Services podem ser encontradas no site do Office 365. Essas instruções também mostrarão como configurar o logon único, a federação e a sincronização entre o Office 365 e o Active Directory.<br />Se você não tiver instalado esses cmdlets, seu script falhará porque o cmdlet Get-CsTenant não estará disponível.

Após a configuração do Office 365 e a criação de entidades de serviço do Office 365 para Lync Server 2013 e Exchange 2013, você deverá registrar as credenciais com essas entidades de serviço. Para isso, primeiro você deve obter um certificado X.509 Base64 salvo como um arquivo .CER. Ele será aplicado às entidades de serviço do Office 365.

Após obter o certificado X.509, inicie o Módulo do Microsoft Online Services (clique em **Iniciar**, **Todos os Programas**, **Microsoft Online Services** e **Módulo do Microsoft Online Services para Windows PowerShell**). Após a abertura do Módulo do Services, digite o seguinte para importar o módulo do Windows PowerShell do Microsoft Online que contenha os cmdlets que podem ser usados para gerenciar entidades de serviço:

    Import-Module MSOnlineExtended

Após a importação do módulo, digite o seguinte comando e pressione ENTER para conectar ao Office 365:

    Connect-MsolService

Depois de pressionar ENTER, uma caixa de diálogo de credenciais será exibida. Informe seu nome de usuário e senha do Office 365 na caixa de diálogo e clique em OK.

Assim que estiver conectado ao Office 365, você poderá executar o comando a seguir para retornar informações sobre as entidades de serviço:

    Get-MsolServicePrincipal

Você deverá obter informações semelhantes a estas para todas as entidades de serviço:

    ExtensionData        : System.Runtime.Serialization.ExtensionDataObject
    AccountEnabled       : True
    Addresses            : {}
    AppPrincipalId       : 00000004-0000-0ff1-ce00-000000000000
    DisplayName          : Microsoft Lync Server
    ObjectId             : aada5fbd-c0ae-442a-8c0b-36fec40602e2
    ServicePrincipalName : LyncServer/litwareinc.com
    TrustedForDelegation : True

A próxima etapa é importar, codificar e atribuir o certificado X.509. Para importar e codificar o certificado, use os seguintes comandos do Windows PowerShell, certificando-se de especificar o caminho completo do arquivo .CER quando chamar o método Import:

    $certificate = New-Object System.Security.Cryptography.X509Certificates.X509Certificate
    $certificate.Import("C:\Certificates\Office365.cer")
    $binaryValue = $certificate.GetRawCertData()
    $credentialsValue = [System.Convert]::ToBase64String($binaryValue)

Após a importação e codificação do certificado, você poderá atribuir o certificado às entidades de serviço do Office 365. Para isso, use primeiro Get-MsolServicePrincipal a fim de recuperar o valor da propriedade AppPrincipalId para as entidades de serviço do Lync Server e do Microsoft Exchange; o valor da propriedade AppPrincipalId será usado para identificar a entidade de serviço atribuída ao certificado. Com o valor da propriedade AppPrincipalId para Lync Server 2013 disponível, use o seguinte comando para atribuir o certificado à versão do Office 365 do Lync Server (as propriedades StartDate e EndDate devem corresponder ao período de validade do certificado):

    New-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -Type Asymmetric -Usage Verify -Value $credentialsValue -StartDate 6/1/2012 -EndDate 5/31/2013

Em seguida, você deve repetir o comando, desta vez usando o valor da propriedade AppPrincipalId para Exchange 2013.

Caso precise excluir o certificado posteriormente, faça isso recuperando KeyId do certificado primeiro:

    Get-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000

O comando retornará dados como estes:

    Type      : Asymmetric
    Value     : 
    KeyId     : bc2795f3-2387-4543-a95d-f92c85c7a1b0
    StartDate : 6/1/2012 8:00:00 AM
    EndDate   : 5/31/2013 8:00:00 AM
    Usage     : Verify

Você pode excluir o certificado usando um comando semelhante a este:

    Remove-MsolServicePrincipalCredential -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -KeyId bc2795f3-2387-4543-a95d-f92c85c7a1b0

Além de atribuir um certificado, você também deve configurar a entidade de serviço do Exchange Online e a versão local do Lync Server 2013 como uma entidade de serviço do Office 365. Isso pode ser feito executando os dois comandos a seguir:

    Set-MSOLServicePrincipal -AppPrincipalID 00000002-0000-0ff1-ce00-000000000000 -AccountEnabled $true
    
    $lyncSP = Get-MSOLServicePrincipal -AppPrincipalID 00000004-0000-0ff1-ce00-000000000000
    $lyncSP.ServicePrincipalNames.Add("00000004-0000-0ff1-ce00-000000000000/lync.contoso.com")
    Set-MSOLServicePrincipal -AppPrincipalID 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $lyncSP.ServicePrincipalNames

