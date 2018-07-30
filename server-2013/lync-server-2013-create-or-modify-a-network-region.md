---
title: 'Lync Server 2013: Criar ou modificar uma região de rede'
TOCTitle: Criar ou modificar uma região de rede
ms:assetid: bf7a3dc4-71a2-4559-a547-d90305d4f904
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412933(v=OCS.15)
ms:contentKeyID: 49307966
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar uma região de rede no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-19_

*Regiões de rede* são hubs de rede ou backbones usados na configuração do serviço de controle de admissão de chamadas, E9-1-1 e desvio de mídia. Execute os procedimentos a seguir para criar ou modificar as regiões de rede. Por exemplo, se você já criou regiões de rede para um recurso de Voz, não precisará criar novas regiões de rede; outros recursos avançados do Enterprise Voice usarão essas mesmas regiões de rede. Porém, talvez seja necessário modificar uma definição de região de rede existente para aplicar configurações específicas ao recurso. Por exemplo, se você cria regiões de rede para o E9-1-1 (que não exige um local central associado) e depois implanta o controle de admissão de chamadas, precisará modificar as definições de região de rede para especificar um local central. Para obter detalhes, consulte [Configurar regiões de rede para CAC no Lync Server 2013](lync-server-2013-configure-network-regions-for-cac.md).

> [!NOTE]  
> Quaisquer requisitos específicos ao recurso para definições de região de rede são documentados nos tópicos de Implantação do recurso.

Para obter detalhes sobre como trabalhar com regiões de rede, consulte a documentação do Shell de Gerenciamento do Lync Server para os seguintes cmdlets:

  - [New-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkRegion)

  - [Get-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkRegionLink)

  - [Set-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkRegion)

  - [Remove-CsNetworkRegion](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkRegion)

## Criar uma região de rede

Crie uma região de rede que pode ser usada pelo controle de admissão de chamada, E9-1-1 ou bypass de mídia.

## Para criar uma região de rede usando o Shell de Gerenciamento do Lync Server

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet New-CsNetworkRegion para criar regiões de rede:
    
        New-CsNetworkRegion -Identity <String> -CentralSite <String>
    
    Por exemplo:
    
        New-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "All North America Locations"
    
    Neste exemplo, você criou uma região de rede chamada “NorthAmerica” que é associada a um site central com o ID de site CHICAGO.

3.  Para concluir a criação das regiões de rede para sua topologia, repita a etapa 2 com as configurações para cada região de rede.

## Para criar uma região de rede usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de rede**.

3.  Clique em **Região**.

4.  Clique em **Novo**.

5.  Na página **Nova Região**, clique em **Nome** e digite um nome para a região de rede.

6.  Clique em **Site central** e clique em um site central na lista.

7.  Como opção, clique em **Descrição** e digite as informações adicionais para descrever esse site de rede.

8.  Clique em **Confirmar**.

9.  Para concluir a criação das regiões de rede para sua topologia, repita as etapas 4 a 8 com as configurações de outras regiões.

## Modificar uma região de rede

Modifique as configurações de uma região de rede existente a fim de acomodar as alterações das informações básicas de região ou as alterações exigidas por um novo recurso.

## Para modificar uma região de rede usando o Shell de Gerenciamento do Lync Server

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet Set-CsNetworkRegion para modificar uma região de rede existente:
    
        Set-CsNetworkRegion -Identity <String> -CentralSite <String>
    
    Por exemplo:
    
        Set-CsNetworkRegion -Identity NorthAmerica -CentralSite CHICAGO -Description "North American Region"
    
    Neste exemplo, você modificou uma região de rede existente chamada “NorthAmerica” (criada usando os procedimentos acima neste tópico) alterando a descrição. Se houver uma descrição para a região “NorthAmerica”, esse comando a substituirá por esse valor; se não houver uma descrição, esse comando a definirá.

3.  Para modificar outras regiões de rede, repita a etapa 2 com as configurações de outras regiões.

## Para modificar uma região de rede usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de rede**.

3.  Clique no botão de navegação **Região**.

4.  Na tabela, clique na região de rede que você deseja modificar.

5.  Clique em **Editar** e em **Mostrar detalhes…**.

6.  Na página **Editar Região**, altere os valores das configurações dessa região de rede conforme apropriado.

7.  Clique em **Confirmar**.

8.  Para concluir a modificação das regiões de rede, repita as etapas 4 a 7 com as configurações de outras regiões.

