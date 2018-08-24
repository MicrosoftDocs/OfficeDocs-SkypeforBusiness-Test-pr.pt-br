---
title: 'Lync Server 2013: Criar ou modificar um site da rede'
TOCTitle: Criar ou modificar um site da rede
ms:assetid: 14e24856-9996-4da4-9f31-300940bdf5aa
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398218(v=OCS.15)
ms:contentKeyID: 49305973
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar um site da rede no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-24_

O controle de admissão de chamada (CAC), E9-1-1 e as implantações de desvio de mídia se baseiam na configuração de *locais de rede* , que são definidos dentro de uma região da rede e sempre associados a ela. Um local de rede representa um local da filial, um complexo de edifícios ou um campus. Locais de rede representam coleções de subredes com largura de banda semelhante.

Use os procedimentos a seguir para criar ou modificar sites de rede. Por exemplo, se você já criou sites de rede para um recurso de Voz, você não precisa criar sites de rede novos, outros recursos de Voz usarão esses mesmos sites. Você pode, porém, precisar modificar uma definição de site de rede existente para aplicar configurações específicas do recurso. Por exemplo, se você criou um site de rede para o E9-1-1, você precisa modificar o site de rede durante a implantação do controle de admissão de chamada para aplicar um perfil de política de largura de banda.

> [!NOTE]  
> Onde eles existirem, você pode encontrar exemplos e requisitos específicos para sites de rede à medida que eles pertencem a um recurso de Voz avançado na documentação de Implantação para cada recurso:<ul>
> 
> 
> <li><p><a href="lync-server-2013-configure-network-sites-for-cac.md">Configurar locais de rede para CAC no Lync Server 2013</a></p></li></ul>


Para obter detalhes sobre como trabalhar com sites de rede, consulte a documentação do Shell de Gerenciamento do Lync Server para os cmdlets a seguir:

  - [New-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSite)

  - [Get-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSite)

  - [Set-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkSite)

  - [Remove-CsNetworkSite](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkSite)

## Criar um site de rede

Crie uma região de rede que pode ser usada pelo controle de admissão de chamada, E9-1-1 ou bypass de mídia.

## Para criar um site de rede usando o Shell de Gerenciamento

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet do New-CsNetworkSite para criar sites de rede:
    
        New-CsNetworkSite -NetworkSiteID <string>
    
    Por exemplo:
    
        New-CsNetworkSite -NetworkSiteID Chicago -Description "Corporate headquarters"-NetworkRegionID NorthAmerica
    
    Neste exemplo, você criou um site de rede chamado “Chicago” que está na região da rede “NorthAmerica”.
    
    > [!NOTE]  
    > A região da rede NorthAmerica já deve existir para que esse comando seja executado com sucesso.

3.  Para concluir a criação de sites de rede para a sua topologia, repita a etapa 2 com as configurações de outros sites.

## Para criar um site de rede usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de rede** .

3.  Clique no botão de navegação **Site** .

4.  Clique em **Novo** .

5.  Na página **Novo Site** , clique em **Nome** e depois digite um nome para o site de rede.

6.  Clique em **Região** , e depois clique em uma região na lista.

7.  De modo opcional, clique em **Política de largura de banda** e depois clique em uma das larguras de banda da lista.
    
    > [!NOTE]  
    > A política de largura de banda é solicitada apenas se você implantar o controle de admissão de chamada no site.

8.  De modo opcional, clique em **Política de Local** , depois clique em uma política de local na lista.
    
    > [!NOTE]  
    > A política de local é solicitada se você implantar E9-1-1 no site.

9.  Como opção, clique em **Descrição** e digite as informações adicionais para descrever esse site de rede.

10. Clique em **Confirmar** .

11. Para concluir a criação de sites de rede para a sua topologia, repita as etapas 4 a 10 com as configurações de outros sites.

## Modificar um site de rede

Modificar uma região de rede que pode ser usada pelo controle de admissão, E9-1-1 ou desvio de mídia.

## Para modificar um local de rede

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsNetworkSite para modificar os sites de rede:
    
        Set-CsNetworkSite -Identity <string>
    
    Por exemplo:
    
        Set-CsNetworkSite -Identity Albuquerque -NetworkRegionID NorthAmerica
    
    Neste exemplo, o site chamado “Albuquerque” é movido para a região “NorthAmerica”. Para modificar a configuração do site de rede para implantar o controle de admissão de chamada, o E9-1-1 ou desvio de mídia, modifique o site de rede executando o cmdlet Set-CsNetworkSite ou com os parâmetros do BWPolicyProfileID ou do LocationPolicy, respectivamente.
    
    > [!NOTE]  
    > Embora o parâmetro do BypassID exista para o desvio de mídia, recomendamos que você não sobreponha IDs de desvio geradas automaticamente. Você não precisa especificar parâmetros adicionais para configurar um site de rede para o desvio de mídia.

3.  Para concluir a modificação dos sites de rede para sua topologia, repita a etapa 2 com as configurações de outros sites.

## Para modificar um site de rede usando um Painel de Controle Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de rede** .

3.  Clique no botão de navegação **Site** .

4.  Na tabela, clique no site de rede que você quer modificar.

5.  Clique em **Editar** e em **Mostrar detalhes…** .

6.  Na página **Editar Site** , mude os valores dessas configurações de site de rede conforme apropriado.

7.  Clique em **Confirmar** .

8.  Para concluir a modificação de sites de rede, repita as etapas de 4 a 7 com configurações de outros sites.

