---
title: Configuração dos Serviços de Federação do Active Directory (AD FS 2.0)
TOCTitle: Configuração dos Serviços de Federação do Active Directory (AD FS 2.0)
ms:assetid: 0ba8657f-55b8-41b3-960c-fdc5eeee6978
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn308561(v=OCS.15)
ms:contentKeyID: 56270368
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração dos Serviços de Federação do Active Directory (AD FS 2.0)

 

_**Tópico modificado em:** 2016-12-08_

A seção a seguir descreve como configurar o Serviços de Federação do Active Directory (AD FS 2.0) para dar suporte à autenticação multifator. Para obter mais informações sobre como instalar o AD FS 2.0, consulte os Guias passo a passo e os tutoriais do AD FS 2.0 em [http://go.microsoft.com/fwlink/p/?LinkId=313374](http://go.microsoft.com/fwlink/p/?linkid=313374).

> [!NOTE]  
> Ao instalar o AD FS 2.0, não use o Windows Server Manager para adicionar a função do Active Directory Federation. Em vez disso, baixe e instale o pacote do Serviços de Federação do Active Directory 2.0 RTW em <a href="http://go.microsoft.com/fwlink/p/?linkid=313375">http://go.microsoft.com/fwlink/p/?LinkId=313375</a>.


**Para configurar o AD FS para autenticação de dois fatores**

1.  Faça o logon no computador do AD FS 2.0 usando uma conta de Administrador de Domínio.

2.  Inicie o Windows PowerShell.

3.  Na linha de comando do Windows PowerShell, execute o seguinte comando:
    
        add-pssnapin Microsoft.Adfs.PowerShell

4.  Estabeleça uma parceria com cada servidor Diretor, pool de Enterprise e Standard Edition do Lync Server 2013 com Atualizações Cumulativas para o Lync Server 2013 de julho de 2013 que serão habilitados para autenticação passiva executando o seguinte comando, substituindo pelo nome do servidor da sua implantação:
    
        Add-ADFSRelyingPartyTrust -Name LyncPool01-PassiveAuth -MetadataURL https://lyncpool01.contoso.com/passiveauth/federationmetadata/2007-06/federationmetadata.xml

5.  No menu Ferramentas Administrativas, inicie o Console de Gerenciamento do AD FS 2.0.

6.  Expanda **Relações Confiáveis** \> **Objeto de confiança de terceira parte confiável**.

7.  Verifique se uma nova parte confiável foi criada para o seu servidor de pool Enterprise ou Standard Edition com Lync Server 2013 com Atualizações Cumulativas para Lync Server 2013 de julho de 2013.

8.  Crie e atribua uma Regra de Autorização de Emissão para seu objeto de confiança de terceira parte confiável usando o Windows PowerShell executando os seguintes comandos:
    
    ```
        $IssuanceAuthorizationRules = '@RuleTemplate = "AllowAllAuthzRule" => issue(Type = "http://schemas.microsoft.com/authorization/claims/permit", Value = "true");'
    ```
    ```    
        Set-ADFSRelyingPartyTrust -TargetName LyncPool01-PassiveAuth 
        -IssuanceAuthorizationRules $IssuanceAuthorizationRules
    ```


9.  Crie e atribua uma Regra de Transformação de Emissão para seu objeto de confiança de terceira parte confiável usando o Windows PowerShell executando os seguintes comandos:
    
```
        $IssuanceTransformRules = '@RuleTemplate = "PassThroughClaims" @RuleName = "Sid" c:[Type == "http://schemas.microsoft.com/ws/2008/06/identity/claims/primarysid"]=> issue(claim = c);'
```
```    
        Set-ADFSRelyingPartyTrust -TargetName LyncPool01-PassiveAuth -IssuanceTransformRules $IssuanceTransformRules
```

10. No Console de Gerenciamento do AD FS 2.0, clique com o botão direito no seu objeto de confiança de terceira parte confiável e selecione **Editar Regras de Declaração**.

11. Selecione a guia **Regras de Autorização de Emissão** e verifique se a nova regra de autorização foi criada com sucesso.

12. Selecione a guia **Regras de Transformação de Emissão** e verifique se a nova regra de transformação foi criada com sucesso.

