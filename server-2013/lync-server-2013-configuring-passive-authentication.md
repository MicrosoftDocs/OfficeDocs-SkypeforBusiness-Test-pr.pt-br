---
title: Configurando a autenticação passiva do Lync Server
TOCTitle: Configurando a autenticação passiva do Lync Server
ms:assetid: 9a904b8d-9fce-4abf-be73-5c8e48cfb53a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308569(v=OCS.15)
ms:contentKeyID: 56270448
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a autenticação passiva do Lync Server

 

_**Tópico modificado em:** 2013-07-11_

A seção a seguir descreve como configurar o Lync Server 2013 com as Atualizações Cumulativas de julho de 2013 para dar suporte à autenticação passiva. Depois de habilitada, os usuários do Lync habilitados para a autenticação de dois fatores terão de usar um cartão inteligente físico ou virtual e um PIN válido para se conectar usando o cliente do Lync 2013 com Atualizações Cumulativas de julho de 2013.

> [!NOTE]  
> Recomendamos que os clientes habilitem a autenticação passiva para o Registrador e para os Serviços Web no nível de serviço. Caso a autenticação passiva esteja habilitada para o Registrador e para os Serviços Web no nível global, é provável que ocorram falhas de autenticação em toda a organização para usuários que não estão se conectando com o cliente de desktop do 2013 com Atualizações Cumulativas de julho de 2013.

## Configuração dos Serviços Web

As etapas a seguir descrevem como criar uma configuração personalizada de serviços Web para servidores Diretores, pools Enterprise e Standard Edition que serão habilitados para a autenticação passiva.

**Para criar uma configuração personalizada de serviços Web**

1.  Faça o logon em seu Lync Server 2013 com o servidor Front End de Atualizações Cumulativas de julho de 2013 usando uma conta de administrador do Lync.

2.  Inicie o Shell de Gerenciamento do Lync Server 2013.

3.  Na linha de comando Shell de Gerenciamento do Lync Server, crie uma nova configuração do Serviço Web para cada Diretor, pool Enterprise e servidor Standard Edition que será habilitado para a autenticação passiva executando o seguinte comando:
    
        New-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
    

    > [!WARNING]
    > O valor para o FQDN WsFedPassiveMetadataUri é o Nome de Serviço de Federação do seu servidor AD FS 2.0. O valor do Nome de Serviço de Federação pode ser encontrado no Console de Gerenciamento do AD FS 2.0 clicando com o botão direito do mouse em <STRONG>Serviço</STRONG> a partir do painel de navegação, selecionando em seguida <STRONG>Editar propriedades do serviço de federação</STRONG>.



4.  Verifique se os valores UseWsFedPassiveAuth e WsFedPassiveMetadataUri foram definidos corretamente executando o seguinte comando:
    
        Get-CsWebServiceConfiguration -identity "Service:WebServer:LyncPool01.contoso.com" | format-list UseWsFedPassiveAuth, WsFedPassiveMetadataUri

5.  Para clientes, a Autenticação Passiva é o método de autenticação menos indicado para autenticação de webticket. Para todos os servidores Diretores, pools Enterprise e Standard Edition que serão habilitados para autenticação passiva, todos os outros tipos de autenticação devem ser desabilitados nos Serviços Web do Lync executando o seguinte comando:
    
        Set-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" -UseCertificateAuth $false -UsePinAuth $false -UseWindowsAuth NONE

6.  Verifique se todos os outros tipos de autenticação foram desabilitados com sucesso executando o seguinte comando:
    
        Get-CsWebServiceConfiguration -Identity "Service:WebServer:LyncPool01.contoso.com" | format-list UseCertificateAuth, UsePinAuth, UseWindowsAuth

## Configuração de proxy

Quando a autenticação de certificado for desabilitada para os Serviços Web do Lync, o cliente do Lync usará um tipo de autenticação menos preferencial, como o Kerberos ou NTLM, para autenticar o serviço do Registrador. A autenticação de certificado ainda é necessária para permitir que o cliente do Lync recupere um webticket. No entanto, os tipos Kerberos e NTLM devem ser desabilitados para o serviço do Registrador.

As etapas a seguir descrevem como criar uma configuração personalizada de proxy para servidores de pools Edge, pools Enterprise e Standard Edition que serão habilitados para a autenticação passiva.

**Para criar uma configuração personalizada de proxy**

1.  Na linha de comandoShell de Gerenciamento do Lync Server, crie uma nova configuração de proxy para cada servidor de pool Edge, pool Enterprise e Standard Edition do Lync Server 2013 com Atualizações Cumulativas de julho de 2013 que será habilitado para a autenticação passiva executando os seguintes comandos:
    
```
        New-CsProxyConfiguration -Identity "Service:EdgeServer:EdgePool01.contoso.com" 
        -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
```
```    
        New-CsProxyConfiguration -Identity "Service:Registrar:LyncPool01.contoso.com" 
        -UseKerberosForClientToProxyAuth $False -UseNtlmForClientToProxyAuth $False
```

2.  Verifique se todos os outros tipos de autenticação de proxy foram desabilitados com sucesso executando o seguinte comando:
    
        Get-CsProxyConfiguration -Identity "Service:Registrar:LyncPool01.contoso.com"
         | format-list UseKerberosForClientToProxyAuth, UseNtlmForClientToProxyAuth, UseCertifcateForClientToProxyAuth

