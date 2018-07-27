---
title: 'Lync Server 2013: Verificar ou configurar autenticação e certificação nos diretórios virtuais de IIS'
TOCTitle: Verificar ou configurar autenticação e certificação nos diretórios virtuais de IIS
ms:assetid: 3ca90be0-1d64-447c-807a-3a2ee3bf625e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429702(v=OCS.15)
ms:contentKeyID: 49306447
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar ou configurar autenticação e certificação nos diretórios virtuais de IIS no Lync Server 2013

 

_**Tópico modificado em:** 2012-05-25_

Use o procedimento a seguir para configurar a certificação dos diretórios virtuais do IIS (Serviços de Informações da Internet) ou verificar se a certificação está configurada corretamente. Execute o procedimento a seguir em cada servidor que estiver executando o ISS no pool Lync Server e os servidores opcionais Diretor ou Pool de diretores.

> [!NOTE]  
> O procedimento a seguir define um procedimento para solicitar um certificado combinado que é utilizado para todos os propósitos de Lync Server, Internal Web Site e External Web Site no IIS. Lync Server 2010 introduziu um conjunto de cmdlets Shell de Gerenciamento do Lync ServerWindows PowerShell para o propósito expresso de gerenciamento de solicitação de certificado, importação e atribuição. O procedimento assume que há uma autoridade de certificação (CA) implantada internamente que pode processar a solicitação. Se você usa certificados públicos para propósitos Lync Server ou o CA requer uma solicitação offline, consulte a sintaxe detalhada neste tópico para informações sobre o –Output parâmetro <a href="https://docs.microsoft.com/en-us/powershell/module/skype/Request-CsCertificate">Request-CsCertificate</a>

## Para configurar autenticação e certificados em diretórios virtuais de ISS

1.  Para completar com sucesso o seguinte, você deve estar logado no computador ( Servidor Front-End ou Diretor) onde os serviços da web estão instalados e ser o administrador local. Você deve ter as permissões de **leitura** e **registrar** na autoridade de certificação que você estará solicitando certificados, caso a autoridade de certificação seja a sua organização. Você não precisa de permissões da autoridade de certificação se for configurar e enviar solicitações de certificado offline.

2.  Clique em **Iniciar**, selecione **Todos os programas**, selecione **Ferramentas administrativas** e clique em **Gerenciador dos Serviços de Informações da Internet (IIS)**.

3.  Em **Gerenciador do Serviços de Informações da Internet (IIS)**, selecione **ServerName**. Em **Exibição de recursos**, selecione **Certificados do servidor**, clique com o botão direito e selecione **Abrir recurso**.
    

    > [!TIP]
    > Na Exibição de recursos dos Certificados do servidor, caso haja certificados atribuídos ao servidor, eles aparecerão aí. Caso exista um certificado que corresponda aos requisitos para o External Web Site no IIS, você pode reutilizar tal certificado. Para visualizar um certificado, clique com o botão direito no certificado e selecione <STRONG>Visualizar…</STRONG>



4.  No Servidor Front-End ou Diretor o qual você está solicitando o certificado, clique em **Iniciar**, selecione **Todos os programas**, selecione **Microsoft Lync Server 2013** e, então, clique em **Shell de Gerenciamento do Lync Server**.

5.  No Shell de Gerenciamento do Lync Server, digite o seguinte:
    
        Get-CsCertificate
    
    A saída é uma lista dos certificados que estão atualmente no servidor, no repositório de certificados do Pessoal do Computador. Observe que, no certificado combinado (isto é, onde por padrão os serviços da web internos e externos estão utilizando o mesmo certificado), você verá que a propriedade Uso estará populado com Padrão, WebServicesInternal and WebServicesExternal. Além disso, a propriedade Thumbprint será a mesma para cada um dos tipos de Uso. Um exemplo de saída de Get-CsCertificate é exibido neste exemplo:
    
    ![Informações do Get-CsCertificate sobre o status de scert atual](images/Gg429702.664f6326-6cd5-48e2-8235-fc3950ea43b4(OCS.15).jpg "Informações do Get-CsCertificate sobre o status de scert atual")

6.  No Shell de Gerenciamento do Lync Server, digite o seguinte:
    
        Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -CA <CA Server FQDN\CA Instance> -Verbose -DomainName "<FQDN entries to be added to the Subject Alternative Name>"
    
    Onde o comando completo se parecerá com o seguinte exemplo:
    
        Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -CA dc01.contoso.net\contoso-DC01-CA -Verbose -DomainName "LyncdiscoverInternal.Contoso.com,Lyncdiscover.Contoso.com"
    

    > [!TIP]
    > Por padrão, o Request-CsCertificate preencherá o nome da entidade com o nome do pool ou servidor, além das entradas no nome de entidade alternativo com o FQDN do servidor, o FQDN do pool, FQDNs de URL simples e FQDNs de serviços web internos e externos. Isso é feito ao fazer referência ao documento de topologia na sua implantação. Caso exista um valor faltando e você tenha especificado o parâmetro -Verbose, você será notificado de que os valores atuais e computados para os nomes alternativos são diferentes, mas não será informado qual valor está faltando. É fornecido apenas o valor computado completo ao qual o cmdlet fez referência. Utilize a cadeia de nomes alternativos computados na saída para solicitar novamente um novo certificado que incluirá todos os valores.

    
    ![Saída da solicitação de certificado usando Request-CsCertifica](images/Gg429702.9e59a657-fa75-4454-8fd3-57c81e829f7b(OCS.15).jpg "Saída da solicitação de certificado usando Request-CsCertifica")

7.  No Shell de Gerenciamento do Lync Server, digite o seguinte:
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Thumbprint of certificate to use>
    
    Onde o comando completo se parecerá com o seguinte exemplo:
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint 466D9BB0E8B928B65AF38FA2D9F41E1B301ECE9D
    
    A saída do cmdlet Set-CsCertificate mostrará que o mesmo certificado (identificado pelo thumbprint do certificado) é atribuído para utilização Padrão, WebServicesExternal e WebServicesInternal.
    
    ![Saída do Set-CsCertificate em IIS WebExt](images/Gg429702.dd451c9d-7b49-4408-8071-c868cb1e678c(OCS.15).jpg "Saída do Set-CsCertificate em IIS WebExt")

## Para verificar ou configurar a autenticação e certificados em diretórios virtuais do IIS

1.  Clique em **Iniciar**, selecione **Todos os programas**, selecione **Ferramentas administrativas** e clique em **Gerenciador dos Serviços de Informações da Internet (IIS)**.

2.  Em **Gerenciador do Serviços de Informações da Internet (IIS)**, expanda **Nome do Servidor** e expanda **Sites**.

3.  Clique com o botão direito do mouse em **Lync Server External Web Site** e clique em **Editar Ligações**

4.  Verifique se o https está associado à porta 4443 e clique em **https**.

5.  Selecione a entrada HTTPS, clique em **Editar** e, então, verifique que Lync Server WebServicesExternalCertificate está vinculado a este protocolo. Compare o thumbprint do cmdlet Set-CsCertificate para garantir que o certificado esperado está corretamente associado ao HTTPS.

## Consulte Também

#### Outros Recursos

[Get-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCertificate)  
[Set-CsCertificate](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate)

