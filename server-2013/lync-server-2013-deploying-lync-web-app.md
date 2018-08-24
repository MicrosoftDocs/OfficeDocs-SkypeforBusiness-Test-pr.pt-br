---
title: Implantando o Lync Web App
TOCTitle: Implantando o Lync Web App
ms:assetid: b6301e98-051c-4e4b-8e10-ec922a8f508a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205190(v=OCS.15)
ms:contentKeyID: 49307873
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Implantando o Lync Web App

 

_**Tópico modificado em:** 2016-12-08_

O Lync Web App é um cliente Web dos IIS (Serviços de Informação da Internet) que é instalado com o Lync Server 2013 e está ativado por padrão. Nenhuma etapa adicional é necessária para habilitar o Lync Web App no servidor ou para implantar o cliente Web para usuários. Sempre que um usuário clicar em um URL de reunião, mas não tiver o cliente do Lync 2013 instalado, o usuário recebe a opção de participar de uma reunião usando a versão mais recente do Lync Web App.

Os recursos de voz, vídeo e compartilhamento no Lync Web App requerem um controle Microsoft ActiveX. Você pode instalar o controle ActiveX antecipadamente ou permitir que os usuários o instalem quando solicitado, o que ocorre na primeira vez em que usam o Lync Web App ou na primeira vez que acessam um recurso que requer o controle ActiveX.

> [!NOTE]  
> Nas implantações do Servidor de borda do Lync Server 2013, um proxy HTTPS reverso na rede de perímetro é necessário para o acesso do cliente do Lync Web App. Também é necessário publicar URLs simples. Para obter detalhes, consulte <a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Configurando servidores de proxy reverso para o Lync Server 2013</a> e <a href="lync-server-2013-planning-for-simple-urls.md">Planejamento de URLs simples no Lync Server 2013</a>.

## Habilitando a autenticação multifator para o Lync Web App

A versão do Lync Web App no Lync Server 2013 oferece suporte à autenticação multifator. Além do nome de usuário e da senha, você pode exigir métodos de autenticação adicionais, como cartões inteligentes ou PINs, para autenticar usuários que estar entrando a partir de redes externas ao entrarem em reuniões do Lync. Você pode habilitar a autenticação multifator implantando o servidor de federação do AD FS (Serviço de Federação do Active Directory) e habilitando a autenticação passiva no Lync Server 2013. Depois que o AD FS é configurado, os usuários externos que tentam participar das reuniões do Lync são apresentados a uma página da Web de autenticação multifator do AD FS que contém o nome de usuário e a senha, juntamente com quaisquer métodos de autenticação adicionais que tiver configurado.

> [!IMPORTANT]  
> As considerações a seguir são importantes se você deseja planejar a configuração do AD FS para a autenticação multifator:<ul>
> <li><p>A autenticação do ADFS de vários fatores funciona se o participante da reunião e o organizador estiverem na mesma organização ou forem de uma organização federada do AD FS. A autenticação do ADFS de vários fatores não funciona para usuários federados do Lync porque a infraestrutura da Web do servidor do Lync não dà suporte à ela atualmente.</p></li>
> <li><p>Se você usa balanceadores de carga de hardware, habilite a persistência de cookie nos balanceadores de carga para que todas as solicitações do cliente do Lync Web App sejam manipuladas pelo mesmo cookie de Servidor front-end.</p></li>
> 
> <li><p>Ao estabelecer uma parte confiável entre os servidores do Lync Server e do AD FS, atribua uma vida de token longa o suficiente para considerar a duração máxima de suas reuniões do Lync. Normalmente, uma vida de token de 240 minutos é suficiente.</p></li>
> 
> 
> <li><p>Esta configuração não se aplica aos clientes móveis do Lync.</p></li></ul>


**Configurar a autenticação multifator**

1.  Instale uma função de servidor de federação do AD FS. Para obter detalhes, consulte o Guia de implantação dos Serviços de Federação do Active Directory 2.0 em [http://go.microsoft.com/fwlink/?linkid=267511\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=267511%26clcid=0x416)

2.  Crie certificados para AD FS. Para obter mais informações, consulte a seção "Certificados do servidor da federação" do tópico Planejar para e implementar AD FS para uso com o logon único em [http://go.microsoft.com/fwlink/p/?LinkId=285376](http://go.microsoft.com/fwlink/p/?linkid=285376).

3.  No Interface da linha de comando do Windows PowerShell, execute o seguinte comando:
    
        add-pssnapin Microsoft.Adfs.powershell

4.  Estabeleça uma parceria executando o seguinte comando:
    
        Add-ADFSRelyingPartyTrust -Name ContosoApp -MetadataURL https://lyncpool.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  Defina as seguintes regras de confiabilidade de parte:
    
```
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.contoso.com/authorization/claims/permit", Value = "true");'
        $IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.contoso.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
```
```    
        Set-ADFSRelyingPartyTrust -TargetName ContosoApp -IssuanceAuthorizationRules $IssuanceAuthorizationRules -IssuanceTransformRules $IssuanceTransformRules
```
```    
        Set-CsWebServiceConfiguration -UseWsFedPassiveAuth $true -WsFedPassiveMetadataUri https://dc.contoso.com/federationmetadata/2007-06/federationmetadata.xml
```

## Configuração de BranchCache

O recurso BranchCache no Windows 7 e no Windows Server 2008 R2 pode interferir com os componentes Web do Lync Web App. Para impedir problemas dos usuários do Lync Web App, certifique-se de que BranchCache não está ativado.

Para obter detalhes sobre como desativar o BranchCache, consulte o Guia de Implantação do BranchCache, disponível no formato Word na Central de Download da Microsoft em [http://go.microsoft.com/fwlink/?linkid=268788\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268788%26clcid=0x416) e no formato HTML na Biblioteca Técnica do Windows Server 2008 R2 em [http://go.microsoft.com/fwlink/?linkid=268789\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268789%26clcid=0x416).

## Verificando a implantação do Lync Web App

Você pode usar o cmdlet Test-CsUcwaConference para verificar se um par de usuários de teste pode participar de uma conferência usando a UCWA (Unified Communications Web API). Para obter detalhes sobre este cmdlet, consulte [Test-CsUcwaConference](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsUcwaConference) na documentação do Shell de Gerenciamento do Lync Server.

## Solução de problemas de instalação de plug-in no Windows Server 2008 R2

Se a instalação do plug-in falhar em um computador com Windows Server 2008 R2, pode ser necessário modificar as configuração de segurança do Internet Explorer ou a configuração da chave do registro DisableMSI.

**Modificar a configuração de segurança no Internet Explorer**

1.  Abra o Internet Explorer.

2.  Clique em **Ferramentas**, **Opções da Internet** e em **Avançado**.

3.  Role até a seção **Segurança**.

4.  Desmarque **Não salvar páginas criptografadas no disco** e clique em **OK**.
    
    > [!NOTE]  
    > Se estiver selecionada, esta configuração também causará um erro ao tentar baixar um anexo de Lync Web App.

5.  Reingresse na reunião. O download do plug-in deve ocorrer sem erros.

**Modificar a configuração do Registro DisableMSI**

1.  Clique em **Iniciar** e em **Executar**.

2.  Para acessar o Editor de registro, digite **regedit**.

3.  Navegue até HKEY\_LOCAL\_MACHINE\\Software\\Policies\\Microsoft\\Windows\\Installer.

4.  Editar ou adicionar a chave do registro DisableMSI do tipo REG\_DWORD e configure como 0.

5.  Reingresse na reunião.

## Consulte Também

#### Conceitos

[Configurando a página de ingresso na reunião no Lync Server 2013](lync-server-2013-configuring-the-meeting-join-page.md)  
[Plataformas compatíveis com o Lync Web App para Lync Server 2013](lync-server-2013-lync-web-app-supported-platforms.md)

