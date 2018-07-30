---
title: 'Lync Server 2013: Delegar permissões de configuração'
TOCTitle: Delegar permissões de configuração
ms:assetid: 9dca1683-4c69-4534-8ebe-6bd635cbae49
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412735(v=OCS.15)
ms:contentKeyID: 49307603
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Delegar permissões de configuração no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-05_

Se você não quiser conceder associação ao grupo Administradores de Domínio para usuários ou grupos que estejam implantando o Lync Server 2013, poderá permitir que os membros do grupo RTCUniversalServerAdmins executem o cmdlet **Enable-CsTopology** do Windows PowerShell em servidores com o Lync Server 2013. Por padrão, os membros do grupo RTCUniversalServerAdmins não podem executar esse cmdlet. Conceda direitos de administrador e permissões para executar **Enable-CsTopology** em servidores com o Lync Server usando o cmdlet **Grant-CsSetupPermission** e especificando uma unidade organizacional em que estejam localizados os objetos computador para o servidor com o Lync Server 2013.

A preparação de domínio que ocorre quando você instala o Lync Server não adiciona automaticamente as permissões que permitem que os membros do grupo RTCUniversalServerAdmins executem o cmdlet Enable-CsTopology. Isso significa que, por padrão, você deve ser um administrador de domínio para habilitar uma topologia. Para dar aos membros do grupo RTCUniversalServerAdmins o direito de habilitar uma topologia, você deve executar o cmdlet Grant-CsSetupPermissions. Além disso, será necessário executar esse cmdlet em relação a cada contêiner do Active Directory que hospeda computadores executando o Lync Server.

Tenha em mente que esse cmdlet somente concede permissões ao grupo RTCUniversalServerAdmins; o cmdlet não pode ser usado para conceder permissões para outros grupos de segurança ou usuários individuais.

> [!NOTE]  
> <strong>Enable-CsTopology</strong> é o principal cmdlet para permitir que membros do grupo RTCUniversalServerAdmins configurem e implantem o Lync Server 2013.

## Para adicionar a habilidade de executar o cmdlet Enable-CsTopology ao grupo RTCUniversalServerAdmins

1.  Faça logon em um servidor como membro do grupo Administradores de Domínio para o domínio em que o usuário delegado executará o cmdlet **Enable-CsTopology**.

2.  Abra o Shell de Gerenciamento do Lync Server 2013. O Shell de Gerenciamento do Lync Server 2013 é instalado automaticamente em cada Servidor Front-End ou computador em que as ferramentas administrativas do Lync Server 2013 estejam instaladas. Para detalhes sobre o Shell de Gerenciamento do Lync Server 2013, consulte [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md) na documentação de Operações.

3.  Execute o cmdlet a seguir a partir do Shell de Gerenciamento do Lync Server 2013:
    
        Grant-CsSetupPermission -ComputerOU <DN of the OU> -Domain <Domain FQDN>
    
    > [!NOTE]  
    > Se OU não for o nível superior, você deve fornecer o nome de domínio completo.    
    No exemplo a seguir, a UO é o "Lync Server", que está no domínio contoso.com.
    
        Grant-CsSetupPermission -ComputerOU "OU=Lync Servers" -Domain contoso.com

