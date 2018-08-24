---
title: Configurando certificados para a descoberta automática
TOCTitle: Configurando certificados para a descoberta automática
ms:assetid: 1842191d-df9a-41e0-9286-08c25f9b5dca
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945617(v=OCS.15)
ms:contentKeyID: 52057561
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando certificados para a descoberta automática

 

_**Tópico modificado em:** 2012-12-12_

Os certificados para o seu Pool de diretores, Pool de Front-Ends e proxy reverso necessitam de entradas de nome alternativo de assunto adicionais para fornecer suporte à conexões seguras com clientes Lync.

> [!NOTE]  
> Você pode usar o cmdlet <strong>Get-CsCertificate</strong> para exibir as informações sobre os certificados atualmente atribuídos. No entanto, a visualização padrão trunca as propriedades do certificado e não exibe todos os valores na propriedade SubjectAlternativeNames. Você pode usar o <strong>Get-CsCertificate</strong> , o CsCertificate <strong>Request-</strong> e os cmdlets <strong>Set-CsCertificate</strong> para visualizar alguma informação e para solicitar e atribuir certificados. Porém, não é o melhor método a ser usado se você não está certo das propriedades do SAN (nomes alternativos da entidade) no certificado atual. Para exibir o certificado e todos os membros da propriedade, sugere-se o uso de snap-in de certificados no <em>Console de Gerenciamento Microsoft (MMC)</em> ou usar o Assistente de Implantação do Lync Server. No Assistente de Implantação do Lync Server, você pode usar o Assistente de certificado para exibir as propriedades do certificado. Os procedimentos para a exibição, solicitação e atribuição de um certificado que usa o Shell de Gerenciamento do Lync Server e o <em>Console de Gerenciamento Microsoft (MMC)</em> se encontram detalhados nos procedimentos seguintes. Para usar o Assistente de Implantação do Lync Server, informe-se mais detalhadamente aqui se você implementou o Diretor ou o Pool de diretores opcionais: <a href="lync-server-2013-configure-certificates-for-the-director.md">Configurar certificados do Diretor no Lync Server 2013</a>. Para o Servidor Front-End ou o Pool de Front-Ends, consulte informações mais detalhadas aqui: <a href="lync-server-2013-configure-certificates-for-servers.md">Configurar certificados para servidores no Lync Server 2013</a><br />As etapas iniciais nesse procedimento são de preparação para te orientar sobre a função do certificado atual. Por padrão, o certificado não terá uma entrada lyncdiscover.&lt;sipdomain&gt; ou lyncdiscoverinternal.&lt;internal domain name&gt; salvo se você tiver previamente instalado os Mobility Services ou tiver preparado seu certificado com antecedência. Esse procedimento utiliza o exemplo do nome do domínio SIP ‘contoso.com’ e o exemplo do nome do domínio interno ‘contoso.net’.<br />A configuração padrão do certificado de Lync Server 2013 e Lync Server 2010 é para usar um único certificado (denominado ‘Padrão’) com os propósitos Padrão (para todos os propósitos exceto para serviços web), WebServicesExternal e WebServicesInternal. Uma configuração opcional seria usar certificados separados para cada propósito. Os certificados podem ser gerenciados utilizando-se dos cmdlets Shell de Gerenciamento do Lync Server e Windows PowerShell ou dos Assistentes de Certificado no Assistente de Implantação do Lync Server.

## Para atualizar certificados com novos nomes alternativos da entidade usando o Shell de Gerenciamento do Lync Server

1.  Faça logon no computador usando uma conta que tenha permissões e direitos de administrador local.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Descubra quais certificados foram atribuídos ao servidor e para qual tipo de uso. Você precisará dessas informações na próxima etapa para atribuir o certificado atualizado. Na linha de comando, digite:
    
        Get-CsCertificate

4.  Examine o resultado da etapa anterior para ver se um único certificado foi atribuído a vários usos ou se um certificado diferente foi atribuído para cada uso. Examine o parâmetro Use para descobrir como um certificado é usado. Compare o parâmetro Thumbprint dos certificados exibidos para ver se o mesmo certificado tem vários usos.

5.  Atualize o certificado. Na linha de comando, digite:
    
        Set-CsCertificate -Type <type of certificate as displayed in the Use parameter> -Thumbprint <unique identifier>
    
    Por exemplo, se o cmdlet **Get-CsCertificate** exibiu um certificado com Use de Default, outro com um Use de WebServicesInternal e outro com um Use de WebServicesExternal, e todos eles tinham o mesmo valor de Thumbprint, digite na linha de comando:
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
    
    **Importante:**
    
    Quando é atribuído um certificado separado para cada uso (valor de Thumbprint é diferente para cada certificado), é importante que você não execute o cmdlet **Set-CsCertificate** com vários tipos. Nesse caso, execute o cmdlet **Set-CsCertificate** separadamente para cada uso. Por exemplo:
    
        Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>

6.  Para exibir o certificado, clique em **Iniciar**, clique em **Executar…**. Digite MMC para abrir o Console de Gerenciamento Microsoft.

7.  No menu do MMC, selecione **Arquivo**, selecione**Adicionar/Remover snap-in…**, selecione Certificados. Clique em **Adicionar**. Quando lhe for solicitado, selecione **Conta do computador** e, em seguida, clique em **Avançar**.

8.  Se o certificado estiver localizado neste computador, selecione **Computador local**. Se o certificado estiver em outro computador, selecione **Outro computador**, digite o nome de domínio totalmente qualificado do computador ou clique em **Procurar**. Em **Digitar o nome do objeto a ser selecionado**, digite o nome do computador. Clique em **Verificar Nomes**. Quando o nome do computador for resolvido, será sublinhado. Clique em **OK**, em seguida, clique em **Concluir**. Clique em **OK** para confirmar a seleção e encerrar a caixa de diálogo **Adicionar ou Remover Snap-ins**.
    
    > [!IMPORTANT]  
    > Se o certificado não aparecer no console, certifique-se de não ter selecionado Usuário ou Serviço. Você deve selecionar Computador, ou não poderá localizar o certificado adequado.

9.  Para exibir as propriedades do certificado, expanda **Certificados**, expanda **Pessoal** e selecione **Certificados**. Selecione o certificado para exibição, clique com o botão direito do mouse em certificado e selecione **Abrir**.

10. Na exibição **Certificado**, selecione **Detalhes**. Aqui, você pode escolher o nome da entidade do certificado ao selecionar **Assunto** e o nome da entidade atribuída e as propriedades atribuídas serão exibidos.

11. Para exibir os nomes alternativos de entidades atribuídos, selecione**Nome Alternativo de Entidade**. Todos os nomes alternativos de entidade atribuídos são exibidos. Os nomes alternativos de entidade encontrados na propriedade são do tipo **Nome DNS** por padrão. Você deve ver os seguintes membros (todos deveriam ser nomes de domínio completamente qualificados) como representado nos registros de host DNS (A ou, se IPv6, AAAA):
    
      - Nome do pool para esse pool ou um nome de servidor único se esse não for um pool
    
      - Nome do servidor ao qual o certificado está atribuído
    
      - Registros de URL Simples, normalmente reunir e discar
    
      - Nomes de Serviços Web interno e externo (por exemplo, webpool01.contoso.net, webpool01.contoso.com), com base em escolhas feitas no Construtor de Topologias e nas seleções de serviços web substituídas.
    
      - Caso já estejam atribuídos, os registros lyncdiscover.\<sipdomain\> e lyncdiscoverinternal.\<sipdomain\>.
    
    O último item é o mais interessante – se houver uma entrada SAN lyncdiscover e lyncdiscoverinternal.
    
    Assim que obtiver essa informação, você pode fechar o certificado exibido e o MMC.

12. Se um nome alternativo de entidade do Serviço de Descoberta Automática ou lyncdiscover.\>domain name\> e lyncdiscoverinternal.\<domain name\> (com base se for um certificado interno ou externo) estiver faltando, você estará usando um único certificado Padrão para os tipos Default, WebServicesInternal e WebServiceExternal. Faça o seguinte:
    
      - No prompt da linha de comando Shell de Gerenciamento do Lync Server, digite:
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        Se você tiver muitos domínios SIP, você não pode utilizar o novo parâmetro AllSipDomain. Em vez disso, você deve usar o parâmetro DomainName. Quando você usar o parâmetro DomainName, você deve definir o FQDN para os registros lyncdiscoverinternal e lyncdiscover. Por exemplo:
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - Para atribuir o certificado, digite o seguinte:
        
            Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        Onde “Thumbprint” é o thumbprint exibido para o novo certificado emitido.

13. Para nomes alternativos de entidades de Descoberta Automática interna ausente quando usam certificados separados por Padrão, WebServicesInternale e WebServicesExternal, faça o seguinte:
    
      - No prompt da linha de comando Shell de Gerenciamento do Lync Server, digite:
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -AllSipDomain -verbose
        
        Se você possui vários domínios SIP, não é possível usar o novo parâmetro AllSipDomain. Ao invés, você deve usar o parâmetro DomainName. Quando utilizar o parâmetro DomainName, você deve usar um prefixo adequado para o FQDN de domínio SIP. Por exemplo:
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - Para obter um nome alternativo da entidade de Descoberta Automática externo, digite na linha de comando:
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        Se você possui vários domínios SIP, não é possível usar o novo parâmetro AllSipDomain. Ao invés, você deve usar o parâmetro DomainName. Quando utilizar o parâmetro DomainName, você deve usar um prefixo adequado para o FQDN de domínio SIP. Por exemplo:
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -DomainName "Lyncdiscover.contoso.com, Lyncdiscover.contoso.net" -verbose
    
      - Para atribuir os tipos de certificados individuais, digite o seguinte:
        
            Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        Onde “Thumbprint” é o thumbprint exibido para os novos certificados individuais emitidos.

