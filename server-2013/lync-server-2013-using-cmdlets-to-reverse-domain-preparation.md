---
title: 'Lync Server 2013: Usando cmdlets para reverter a preparação do domínio'
TOCTitle: Usando cmdlets para reverter a preparação do domínio
ms:assetid: 014dba5d-fcb3-44c9-9d63-ae0755276dac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398071(v=OCS.15)
ms:contentKeyID: 49305670
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando cmdlets para reverter a preparação do domínio para o Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

Use o cmdlet **Disable-CsAdDomain** para reverter a etapa de preparação do domínio.

## Para usar cmdlets para reverter a preparação de domínio

1.  Faça logon em qualquer servidor no domínio como membro do grupo Admins. do domínio.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Disable-CsAdDomain [-Domain <Fqdn>] [-DomainController <Fqdn>] [-Force <SwitchParameter>] 
        [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] 
    
    Por exemplo:
    
        Disable-CsAdDomain -Domain domain1.contoso.net -GlobalSettingsDomainController dc01.domain1.contoso.net -Force
    
    Se o parâmetro Force estiver presente, a preparação do domínio é revertido, mesmo se um ou mais Servidores Front-End ou Servidores de Conferência A/V no domínio público estiverem ativados. Se o parâmetro Force não estiver presente, a preparação do domínio revertido é finalizado caso qualquer Servidores Front-End ou Servidores de Conferência A/V no domínio estivere ativado.
    
    > [!NOTE]  
    > O parâmetro GlobalSettingsDomainController permite que você indique onde as configurações globais estão armazenadas. Se suas configurações estão armazenadas no contêiner Sistema (o que é normal com implantações atualizadas que não tiveram a configuração global migrada para o contêiner Configuração), você define um controlador de domínio na raiz de sua floresta Active Directory. Caso as configurações globais estejam no contêiner Configuração (o que é normal com novas implantações ou implantações atualizadas onde as configurações foram migradas para o contêiner Configuração), você define qualquer controlador de domínio na floresta. Caso você não especifique este parâmetro, o cmdlet presume que as configurações estão armazenadas no contêiner Configuração e faz referência a qualquer controlador de domínio no AD DS.


## Consulte Também

#### Tarefas

[Executando preparação de domínio para Lync Server 2013](lync-server-2013-running-domain-preparation.md)  

#### Outros Recursos

[Preparando domínios para Server 2013](lync-server-2013-preparing-domains.md)

