---
title: 'Lync Server 2013: Associar uma subrede a um site de rede'
TOCTitle: Associar uma subrede a um site de rede
ms:assetid: aa69e3ac-542a-4ba1-9582-2e6bee29f633
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412804(v=OCS.15)
ms:contentKeyID: 49307748
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Associar uma subrede a um site de rede no Lync Server 2013

 

_**Tópico modificado em:** 2014-10-20_

Todas as sub-redes da sua rede devem ser associadas a um local de rede específico, pois as informações da sub-rede são usadas para determinar o local de rede em que um ponto de extremidade se encontra quando uma nova sessão é iniciada. Quando a localização de cada parte for conhecida, os recursos avançados do Enterprise Voice poderão aplicar essas informações para determinar como manipular a configuração ou o encaminhamento da chamada.

> [!IMPORTANT]  
> Todos os endereços IP públicos configurados dos Servidores de Borda de Áudio/Vídeo em sua implantação devem ser adicionados às suas definições de configuração de rede. Estes endereços IP são adicionados como sub-redes com uma máscara de 32. O site de rede associado deve corresponder ao site de rede configurado adequado. Por exemplo, o endereço IP público que corresponde ao Servidor de Borda de A/V no site central Chicago seria o NetworkSiteID de Chicago. Para detalhes sobre endereços IP públicos, consulte <a href="lync-server-2013-determine-external-a-v-firewall-and-port-requirements.md">Determinar firewall A/V externo e requisitos de porta para Lync Server 2013</a> na documentação de Planejamento.

> [!NOTE]  
> Um alerta Key Health Indicator (KHI) é disparado, especificando uma lista de endereços IP presentes em sua rede mas que não estão associados a uma sub-rede ou à sub-rede que inclui os endereços IP não está associada a um site de rede. Este alerta não será disparado mais de uma vez dentro de um período de 8 horas. A informação de alerta relevante e um exemplo são como segue:<br /><strong>Origem:</strong> Serviço de Política de Largura de Banda CS (Núcleo)<br /><strong>Número do evento :</strong> 36034<br /><strong>Nível :</strong> 2<br /><strong>Descrição :</strong> as sub-redes para os seguintes endereços IP: &lt;Lista de Endereços IP&gt; não estão configuradas ou as sub-redes não estão associadas a um Site da Rede.<br /><strong>Causa:</strong> as sub-redes para os endereços IP correspondentes estão ausentes nas definições de configuração da rede ou as sub-redes não estão associadas a um site da rede.<br /><strong>Solução :</strong> adicione sub-redes correspondentes à lista de endereços IP nas definições de configuração da rede e associe todas as sub-redes a um site da rede.<br />Por exemplo, se a lista de endereços IP no alerta especificar 10.121.248.226 e 10.121.249.20, ou estes endereços IP não estão associados a uma sub-rede ou a sub-rede à qual estão associados não pertence a um site da rede. Se 10.121.248.0/24 e 10.121.249.0/24 forem as sub-redes correspondentes para estes endereços, você pode resolver o problema da seguinte forma:<ol>
> 
> <li><p>Certifique-se de que o endereço IP 10.121.248.226 está associado à sub-rede 10.121.248.0/24 e que o endereço IP 10.121.249.20 está associado à sub-rede 10.121.249.0/24.</p></li>
> 
> 
> <li><p>Certifique-se de que ambas as sub-redes 10.121.248.0/24 e 10.121.249.0/24 estejam associadas a um site da rede.</p></li></ol>


Para detalhes sobre como trabalhar com sub-redes da rede, consulte a documentação do Shell de Gerenciamento do Lync Serverpara os seguinte cmdlets:

  - [New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet)

  - [Get-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSubnet)

  - [Set-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkSubnet)

  - [Remove-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkSubnet)


> [!TIP]
> Se estiver trabalhando com um número grande de sub-redes, é recomendável usar um arquivo de valores separados por vírgula (CSV) para associar as sub-redes a sites. O arquivo CSV deve ter as quatro colunas a seguir: <STRONG>IPAddress</STRONG>, <STRONG>mask</STRONG>, <STRONG>description</STRONG>, <STRONG>NetworkSiteID</STRONG>.



## Para associar uma sub-rede a um site da rede, usando o Shell de Gerenciamento

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Execute o cmdlet **New-CsNetworkSubnet** para associar uma sub-rede a um site da rede:
    
        New-CsNetworkSubnet -SubnetID <String> -MaskBits <Int32> -NetworkSiteID <String>
    
    Por exemplo:
    
        New-CsNetworkSubnet -SubnetID 172.11.12.13 - MaskBits 20 -NetworkSiteID Chicago
    
    Neste exemplo, você criou uma associação entre a sub-rede 172.11.12.13 e o site da rede “Chicago”.

3.  Repita a etapa 2 para todas as sub-redes em sua topologia.

## Para associar sub-redes a sites da rede importando um arquivo CSV

1.  Crie um arquivo CSV que inclui todas as sub-redes que deseja adicionar. Por exemplo, crie um arquivo chamado **subnet.csv** como o seguinte conteúdo:
    
    `IPAddress, mask, description, NetworkSiteID`
    
    `172.11.12.0, 24, "NA:Subnet in Portland", Portland`
    
    `172.11.13.0, 24, "NA:Subnet in Reno", Reno`
    
    `172.11.14.0, 25, "EMEA:Subnet in Warsaw", Warsaw`
    
    `172.11.15.0, 31, "EMEA:Subnet in Paris", Paris`

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute o cmdlet a seguir para importar o arquivo **subnet.csv** e armazene seu conteúdo no repositório de gerenciamento do Lync Server:
    
        import-csv subnet.csv | foreach {New-CsNetworkSubnet $_IPAddress -MaskBits $_.mask -Description $_.description -NetworkSiteID $_.NetworkSiteID}

## Para associar uma sub-rede a um site da rede, usando o Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação esquerda, clique em **Configuração de rede**.

3.  Clique no botão de navegação **Sub-rede**.

4.  Clique em **Novo**.

5.  Na página **Nova Sub-rede**, clique em **ID da Sub-rede** e digite o primeiro endereço do intervalo de endereços IP definido pela sub-rede que deseja associar a um site da rede.

6.  Clique em **Máscara** e digite o bitmask a ser aplicado à sub-rede.

7.  Clique em **ID do site da rede** e selecione o ID do site para o qual está adicionando esta sub-rede.
    
    > [!NOTE]  
    > Se sites da rede ainda não estiverem criados, a lista estará vazia. Para obter detalhes sobre o procedimento, consulte <a href="lync-server-2013-create-or-modify-a-network-site.md">Criar ou modificar um site da rede no Lync Server 2013</a>. Você também pode configurar IDs de site para a sua implantação executando o cmdlet <strong>Get-CsNetworkSite</strong>. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.

8.  Opcionalmente, clique em **Descrição** e digite informações adicionais para descrever esta sub-rede.

9.  Clique em **Confirmar**.

Repita estas etapas para adicionar outras sub-redes a um site da rede.

