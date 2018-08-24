---
title: Criar roteamentos de interregião de rede no Lync Server 2013
TOCTitle: Criar roteamentos de interregião de rede no Lync Server 2013
ms:assetid: 5555262a-a502-4b01-9593-836dd30064f5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398368(v=OCS.15)
ms:contentKeyID: 49306748
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar roteamentos de interregião de rede no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-20_

Uma *rota entre regiões de rede* define a rota entre um par de regiões de rede. Cada par de regiões de rede em sua implantação do serviço de controle de admissão de chamadas exige uma rota entre regiões de rede. Isso permite que cada região da rede dentro da implantação acesse todas as demais regiões.

Enquanto os vínculos de região definem limitações de largura de banda nas conexões entre regiões, uma rota entre regiões de rede determina o caminho vinculado que a conexão percorrerá de uma região à outra.

Para obter detalhes sobre o trabalho com rotas entre regiões de rede, consulte a documentação do Shell de Gerenciamento do Lync Server para verificar os seguintes cmdlets:

  - [New-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkInterRegionRoute)

  - [Get-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkInterRegionRoute)

  - [Set-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkInterRegionRoute)

  - [Remove-CsNetworkInterRegionRoute](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkInterRegionRoute)

Na topologia de exemplo, as rotas entre regiões de rede devem ser definidas para cada um dos três pares de regiões: América do Norte/EMEA, EMEA/APAC e América do Norte/APAC.

## Para criar rotas entre regiões de rede usando o Shell de Gerenciamento do Lync Server

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet **New-CsNetworkInterRegionRoute** para definir as rotas necessárias. Por exemplo, execute:
    
    ```
        New-CsNetworkInterRegionRoute -Identity NorthAmerica_EMEA_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 EMEA -NetworkRegionLinkIDs "NA-EMEA-LINK"
    ```
    ```    
        New-CsNetworkInterRegionRoute -Identity NorthAmerica_APAC_Route -NetworkRegionID1 NorthAmerica -NetworkRegionID2 APAC -NetworkRegionLinkIDs "NA-EMEA-LINK, EMEA-APAC-LINK"
    ```
    ```    
        New-CsNetworkInterRegionRoute -Identity EMEA_APAC_Route -NetworkRegionID1 EMEA -NetworkRegionID2 APAC -NetworkRegionLinkIDs "EMEA-APAC-LINK"
    ```
    
    > [!NOTE]  
    > A rota entre regiões de rede América do Norte/APAC requer dois links de regiões de rede porque não há um link de região de rede direta entre elas.

## Para criar rotas entre regiões de rede usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de Rede**.

3.  Clique no botão de navegações **Rota de Região**.

4.  Clique em **Novo**.

5.  Na página **Nova Rota de Região**, clique em **Nome** e digite um nome para a rota entre regiões de rede.

6.  Clique em **Região de Rede 1** e clique em uma região de rede na lista que você deseja rotear para a Região de Rede 2.

7.  Clique em **Região de Rede 2** e clique em uma região de rede na lista que você deseja rotear para a Região de Rede 1.

8.  Clique em **Adicionar** próximo ao campo **Links de Região de Rede** e adicione um link de região de rede que será usado na rota entre regiões de rede.
    
    > [!NOTE]  
    > Se você estiver criando uma rota para duas regiões de rede que não têm um link de região de rede direta de rede entre elas, deverá adicionar todos os links necessários para concluir a rota. Por exemplo, a rota entre regiões de rede América do Norte/APAC requer dois links de região de rede porque não há nenhum link de região de rede direta entre elas.

9.  Clique em **Confirmar**.

10. Para concluir a criação de rotas entre regiões de rede para sua topologia de rede, repita as etapas 4 a 9 com configurações de outras rotas entre regiões de rede.

