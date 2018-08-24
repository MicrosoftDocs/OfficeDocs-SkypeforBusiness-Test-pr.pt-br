---
title: 'Lync Server 2013: Modificando certificados para mobilidade'
TOCTitle: Modificando certificados para mobilidade
ms:assetid: 4e9107af-20f4-4c2a-8c98-ca35b39a4e2d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh690015(v=OCS.15)
ms:contentKeyID: 49306670
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificando certificados para mobilidade no Lync Server 2013

 

_**Tópico modificado em:** 2014-06-20_

Para oferecer suporte a conexões seguras entre o ambiente do Lync e os clientes móveis, os certificados SSL (Secure Socket Layer) para o Pool de diretores, Pool de Front-Ends e proxy reverso precisarão ser atualizados com algumas entradas adicionais de SAN (Nome Alternativo da Entidade). Casos seja necessário consultar mais detalhes sobre os requisitos de certificado para mobilidade, consulte a seção Requisitos de Certificado em [Requisitos técnicos para mobilidade no Lync Server 2013](lync-server-2013-technical-requirements-for-mobility.md), mas basicamente será necessário obter novos certificados da Autoridade de Certificação com as entradas adicionais de SAN incluídas e adicionar esses certificados utilizando as etapas deste artigo.

Antes de começar, recomenda-se conhecer quais nomes alternativos da entidade seus certificados já possuem. Se você não tem certeza do que já foi configurado, existem diversas maneiras de descobrir. Embora exista a opção de executar o **Get-CsCertificate** e outros comandos do PowerShell para exibir estas informações (que detalhamos a seguir), por padrão esses dados serão truncados, portanto é possível que você não veja todas as propriedades necessárias. Para exibir o certificado e suas propriedades, vá para o MMC (Console de Gerenciamento Microsoft) e carregue o snap-in de Certificados (que também detalhamos a seguir), ou apenas verifique no Assistente de Implantação do Lync Server.

Conforme observado acima, as etapas a seguir detalharão como atualizar os certificados utilizando o Shell de Gerenciamento do Lync Server e o MMC. Se você estiver interessado em usar o Assistente de Certificados no Assistente de Implantação do Lync Server para isso, pesquise sobre Diretor e pool de Diretores em [Configurar certificados do Diretor no Lync Server 2013](lync-server-2013-configure-certificates-for-the-director.md) se você configurou um (talvez você não o tenha feito). Para o Servidor de Front-End Server ou pool de Front-Ends, consulte [Configurar certificados para servidores no Lync Server 2013](lync-server-2013-configure-certificates-for-servers.md).

Outro ponto importante a ser lembrado é que você pode ter um único certificado padrão no ambiente do Lync Server 2013 ou certificados diferentes para padrão (que é tudo, exceto os serviços Web), WebServicesExternal e WebServicesInternal. Independente de sua configuração, estas etapas devem ajudar.

## Para atualizar certificados com novos nomes alternativos da entidade usando o Shell de Gerenciamento do Lync Server

1.  É necessário fazer logon no servidor do Lync Server 2013 utilizando uma conta com direitos e permissões de administrador local. Além disso, se você estiver executando o PowerShell **Request-CsCertificate** nas Etapas 12 e posteriores, a conta precisará ter direitos à Autoridade de Certificação (AC) especificada.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Antes de atribuir um certificado atualizado, é necessário descobrir quais certificados foram atribuídos ao servidor e para qual tipo de uso. Na linha de comando, digite:
    
        Get-CsCertificate

4.  Examine o resultado da etapa anterior para ver se um único certificado foi atribuído a vários usos ou se um certificado diferente foi atribuído para cada uso. Examine o parâmetro Use para descobrir como um certificado é usado. Compare o parâmetro Thumbprint dos certificados exibidos para ver se o mesmo certificado tem vários usos. Preste atenção no parâmetro Thumbprint.

5.  Atualize o certificado. Na linha de comando, digite:
    
        Set-CsCertificate -Type <type of certificate as displayed in the Use parameter> -Thumbprint <unique identifier>
    
    Por exemplo, se o cmdlet **Get-CsCertificate** exibiu um certificado com Use de Default, outro com um Use de WebServicesInternal e outro com um Use de WebServicesExternal, e todos eles tinham o mesmo valor de Thumbprint, digite na linha de comando:
    
        Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
    
    **Importante:**
    
    Se um certificado separado é atribuído para cada uso (e o valor de Thumbprint marcado acima é diferente para cada certificado), é importante que você **não** execute o cmdlet **Set-CsCertificate** com vários tipos, conforme no exemplo acima. Nesse caso, execute o cmdlet **Set-CsCertificate** separadamente para cada use. Por exemplo:
    
        Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
        Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>

6.  Para exibir o certificado (ou certificados), clique em **Iniciar** e em **Executar…**. Digite MMC para abrir o Console de Gerenciamento Microsoft.

7.  No menu do MMC, selecione **Arquivo**, selecione **Adicionar/Remover snap-in…**, selecione Certificados. Clique em **Adicionar**. Quando lhe for solicitado, selecione **Conta do computador** e, em seguida, clique em **Avançar**.

8.  Se este for o servidor em que o certificado está localizado, selecione **Computador local**. Se o certificado estiver localizado em outro computador, selecione **Outro computador** digite o nome de domínio totalmente qualificado do computador ou clique em **Procurar** em **Digitar o nome do objeto a ser selecionado** e digite o nome do computador. Clique em **Verificar Nomes**. Quando o nome do computador for resolvido, será sublinhado..Clique em **OK**, depois em **Concluir**. Clique em **OK** para confirmar a seleção e encerrar a caixa de diálogo **Adicionar ou Remover Snap-ins**.

9.  Para exibir as propriedades do certificado, expanda **Certificados**, expanda **Pessoal** e selecione **Certificados**. Selecione o certificado para exibição, clique com o botão direito do mouse em certificado e selecione **Abrir**.

10. Na exibição **Certificado**, selecione **Detalhes**. Aqui, você pode escolher o nome da entidade do certificado ao selecionar **Assunto** e o nome da entidade atribuída e as propriedades atribuídas serão exibidos.

11. Para exibir os nomes alternativos de entidades atribuídos, selecione **Nome Alternativo de Entidade**. Todos os nomes alternativos de entidades atribuídos são exibidos aqui. Os nomes alternativos de entidades encontrados aqui são do tipo **Nome DNS** por padrão. Você deve ver os seguintes membros (todos devem ser nomes de domínio completamente qualificados) como representado nos registros de host DNS (A ou, se IPv6, AAAA):
    
      - Nome do pool para esse pool ou um nome de servidor único se esse não for um pool
    
      - Nome do servidor ao qual o certificado está atribuído
    
      - Registros de URL Simples, normalmente reunir e discar
    
      - Nomes de Serviços Web interno e externo (por exemplo, webpool01.contoso.net, webpool01.contoso.com), com base em escolhas feitas no Construtor de Topologias e nas seleções de serviços web substituídas.
    
      - Caso já estejam atribuídos, os registros lyncdiscover.\<sipdomain\> e lyncdiscoverinternal.\<sipdomain\>.
    
    O último item é o mais interessante – se houver uma entrada SAN lyncdiscover e lyncdiscoverinternal..
    
    Repita estas etapas se houver vários certificados para verificação. Assim que obtiver essa informação, você pode fechar o certificado exibido e o MMC.

12. Se um nome alternativo de entidade do serviço Descoberta Automática estiver ausente, e você está usando um certificado Padrão para os tipos Padrão, WebServicesInternal e WebServiceExternal, faça o seguinte:
    
      - No prompt da linha de comando Shell de Gerenciamento do Lync Server, digite:
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        Se você tiver muitos domínios SIP, você não pode utilizar o novo parâmetro AllSipDomain. Em vez disso, você deve usar o parâmetro DomainName. Quando você usar o parâmetro DomainName, você deve definir o FQDN para os registros lyncdiscoverinternal e lyncdiscover. Por exemplo:
        
            Request-CsCertificate -New -Type Default,WebServicesInternal,WebServicesExternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - Para atribuir o certificado, digite o seguinte:
        
            Set-CsCertificate -Type Default,WebServicesInternal,WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        Onde “Thumbprint” é o thumbprint exibido para o certificado emitido recentemente.

13. Para um SAN Autodiscover interno ausente ao usar certificados separados para Default, WebServicesInternal e WebServicesExternal, faça o seguinte:
    
      - No prompt da linha de comando Shell de Gerenciamento do Lync Server, digite:
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -AllSipDomain -verbose
        
        Se você tiver muitos domínios SIP, você não pode utilizar o novo parâmetro AllSipDomain. Em vez disso, você deve usar o parâmetro DomainName. Quando você usar o parâmetro DomainName, você deve usar um prefixo adequado para o FQDN do domínio SIP. Por exemplo:
        
            Request-CsCertificate -New -Type WebServicesInternal -Ca dc\myca -DomainName "LyncdiscoverInternal.contoso.com, LyncdiscoverInternal.contoso.net" -verbose
    
      - Para obter um nome alternativo da entidade de Descoberta Automática externo, digite na linha de comando:
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -AllSipDomain -verbose
        
        Se você tiver muitos domínios SIP, você não pode utilizar o novo parâmetro AllSipDomain. Em vez disso, você deve usar o parâmetro DomainName. Quando você usar o parâmetro DomainName, você deve usar um prefixo adequado para o FQDN do domínio SIP. Por exemplo:
        
            Request-CsCertificate -New -Type WebServicesExternal -Ca dc\myca -DomainName "Lyncdiscover.contoso.com, Lyncdiscover.contoso.net" -verbose
    
      - Para atribuir os tipos de certificados individuais, digite o seguinte:
        
            Set-CsCertificate -Type Default -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesInternal -Thumbprint <Certificate Thumbprint>
            Set-CsCertificate -Type WebServicesExternal -Thumbprint <Certificate Thumbprint>
        
        Onde “Thumbprint” é o thumbprint exibido para os certificados individuais emitidos recentemente.
    
    > [!NOTE]  
    > Observe que as Etapas 12 e 13 devem ser executadas somente se a conta que as executa tiver acesso à Autoridade de Certificação com permissões adequadas. Se você não conseguir fazer logon com uma conta com essas permissões ou se estiver usando uma Autoridade de Certificação pública ou remota para seus certificados, é necessário solicitá-las por meio do Assistente de Implantação do Lync Server, que foi mencionado no início deste artigo.
