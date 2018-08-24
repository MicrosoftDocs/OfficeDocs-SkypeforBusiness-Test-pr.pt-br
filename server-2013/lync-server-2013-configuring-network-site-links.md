---
title: Configurando links locais de rede
TOCTitle: Configurando links locais de rede
ms:assetid: 7e9147ae-e727-46c8-8c1a-6c13201f09be
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg521023(v=OCS.15)
ms:contentKeyID: 49307252
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando links locais de rede

 

_**Tópico modificado em:** 2012-11-01_

Em uma configuração de controle de admissão de chamada, você pode criar políticas entre locais de rede que definem as limitações de largura de banda entre os locais que estejam diretamente vinculados. Quando os locais de uma rede compartilham um link direto, é possível definir limitações de largura de banda às conexões audiovisuais entre esses dois locais. Você não pode usar o Painel de Controle do Lync Server para configurar políticas de locais de rede, isso só pode ser feito usando cmdlets do Shell de Gerenciamento do Lync Server. Você pode criar, modificar e remover um link de local de rede (também conhecido como política entre locais de rede) do Shell de Gerenciamento do Lync Server.

## Para criar um link de site de rede

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  No prompt de comando, digite o seguinte comando, substituindo os valores que são válidos para a sua configuração:
    
        New-CsNetworkInterSitePolicy -Identity Reno_Portland -NetworkSiteID1 Reno -NetworkSiteID2 Portland -BWPolicyProfileID LowBWLimits
    
    Este exemplo cria um novo link de site de rede chamado Reno\_Portland que define as limitações de largura de banda entre os sites de rede Reno e Portland. Os sites de rede e o perfil da política de largura de banda já devem existir antes de executar este comando.

Para obter descrições detalhadas de parâmetro, consulte [New-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterSitePolicy) na documentação do Shell de Gerenciamento do Lync Server. Para recuperar uma lista de perfis de políticas de largura de banda que podem ser aplicada ao link de site de rede, chame o cmdlet de **Get-CsNetworkBandwidthPolicyProfile**. Para obter detalhes, consulte [Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile) na documentação do Shell de Gerenciamento do Lync Server.

## Para modificar um link de site de rede

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Use o cmdlet **Set-CsNetworkInterSitePolicy** para modificar as propriedades de um link de site de rede fornecido. Você pode modificar um (ou ambos) dos sites conectados e modificar o perfil da política de largura de banda associado ao link. Aqui está um exemplo de modificação do perfil da política de largura de banda do link de um site chamado Reno\_Portland:
    
        Set-CsNetworkInterSitePolicy -Identity Reno_Portland -BWPolicyProfileID HighBWLimits

Para obter descrições detalhadas do parâmetro, consulte [Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterSitePolicy) na documentação do Shell de Gerenciamento do Lync Server.

## Para excluir um link de site de rede

1.  Faça logon no computador onde o Shell de Gerenciamento do Lync Server está instalado como um membro do grupo RTCUniversalServerAdmins ou com os direitos de usuário necessários, conforme descrito em [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Use o cmdlet **Remove-CsNetworkInterSitePolicy** para remover um link de site de rede. O seguinte exemplo exclui o link de site de rede Reno\_Portland:
    
        Remove-CsNetworkInterSitePolicy -Identity Reno_Portland

Para obter descrições detalhadas do parâmetro, consulte [Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterSitePolicy) na documentação do Shell de Gerenciamento do Lync Server.

## Consulte Também

#### Conceitos

[Cmdlets de controle de admissão de chamadas](https://docs.microsoft.com/en-us/powershell/module/skype/)  

#### Outros Recursos

[New-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterSitePolicy)  
[Set-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterSitePolicy)  
[Remove-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterSitePolicy)  
[Get-CsNetworkInterSitePolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterSitePolicy)  
[Get-CsNetworkBandwidthPolicyProfile](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkBandwidthPolicyProfile)

