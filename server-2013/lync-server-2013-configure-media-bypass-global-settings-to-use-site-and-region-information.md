---
title: Definir as configurações globais de bypass de mídia para usar informações locais e da região
TOCTitle: Definir as configurações globais de bypass de mídia para usar informações locais e da região
ms:assetid: 0a21cdf1-f350-49da-b346-70806f256bea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398150(v=OCS.15)
ms:contentKeyID: 49305825
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definir as configurações globais de bypass de mídia para usar informações locais e da região

 

_**Tópico modificado em:** 2012-09-21_

> [!NOTE]  
> Este tópico considera que você já tenha configurado o desvio de mídia em todas as conexões de tronco do Servidor de Mediação para um ponto (gateway PSTN, PBX IP ou Controlador de Limite de Sessões no Provedor de Serviços de Telefonia pela Internet) de um site ou serviço específico no qual deseja que a mídia ignore o Servidor de Mediação.<br />Este tópico também considera que você já tenha definido todos os sites centrais e sites de filial no Construtor de Topologias de uma forma que sejam compatíveis com a rede regional, ao site da rede e à configuração de sub-rede que você realizou, de acordo com as etapas em <a href="lync-server-2013-create-or-modify-a-network-region.md">Criar ou modificar uma região de rede no Lync Server 2013</a>, <a href="lync-server-2013-create-or-modify-a-network-site.md">Criar ou modificar um site da rede no Lync Server 2013</a> e <a href="lync-server-2013-associate-a-subnet-with-a-network-site.md">Associar uma subrede a um site de rede no Lync Server 2013</a>. Se elas não forem compatíveis, o desvio de mídia não será bem-sucedido.

Além de habilitar o desvio de mídia para conexões de tronco individuais associadas a um par, você também precisa definir as configurações globais. Se você usar as etapas deste tópico para definir as configurações globais do desvio de mídia, a hipótese é de que uma ou ambas as situações a seguir afetem sua configuração:

  - Você *não* tem boa conectividade entre os pontos de extremidade do Lync Server e os pares para os quais você configurou o desvio de mídia na conexão do tronco.

  - O controle de admissão de chamadas (CAC) para gerenciamento de largura de banda está habilitado.
    
    > [!NOTE]  
    > Para detalhes sobre as considerações para o controle de admissão de chamadas e para o desvio de mídia, consulte a seção &quot;Controle de admissão de chamadas das conexões PSTN&quot; no <a href="lync-server-2013-media-bypass-and-mediation-server.md">Bypass de mídia e Servidor de Mediação no Lync Server 2013</a> na documentação de Planejamento.

As informações de região de rede e de site de rede são compartilhadas entre os recursos avançados do Enterprise Voice de controle de admissão de chamadas e de desvio de mídia quando os dois estão habilitados. Portanto, se você já configurou o controle de admissão de chamadas, não é preciso usar o procedimento a seguir para editar as informações do site e da região especificamente para o desvio de mídia. Siga as etapas neste procedimento se você ainda não tiver configurado as regiões e os sites de rede quanto ao controle de admissão de chamadas e se quiser alterar as configurações do desvio de chamada.

Ou siga estas etapas se quiser usar as informações do site e da região para tomar a decisão do desvio de mídia, mas não tem a intenção de habilitar o controle de admissão de chamadas. Nesse caso, os links restritos de largura de banda ainda precisarão ser representados por meio de políticas intersites de rede, conforme descrito em [Criar políticas entre locais de rede no Lync Server 2013](lync-server-2013-create-network-intersite-policies.md). As restrições atuais de largura de banda não são tão importantes nesse caso porque o controle de admissão de chamada ainda não foi habilitado. Em vez disso, esses links são usados para sub-redes de partição para especificar aquelas sem limites de largura de banda e podem empregar desvios de mídia. Note que isso também ocorre quando o controle de admissão de chamada e o desvio de mídia estão habilitados.

Além disso, para que o desvio de mídia funcione corretamente, deve haver consistência entre um site conforme sua definição no Construtor de Topologias e sua definição ao configurar as regiões e os sites de rede. Por exemplo, se você tiver um site de filial que foi definido no Construtor de Topologias como tendo apenas um gateway de PSTN implantado, então o site de filial deve estar configurado com uma política do Enterprise Voz que habilite seus usuários a ter suas chamadas de PSTN roteadas através de um gateway de PSTN no site de filial.

## Para configurar informações de site e de região para desvio de mídia

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação à esquerda, clique em **Configurações de rede**.

3.  Dê dois cliques na configuração **Global** na tabela.

4.  Na página **Editar Configurações Globais**, marque a caixa de seleção **Habilitar desvio de mídia**.

5.  Clique em **Usar as configurações de sites e região**.

6.  Se necessário, marque a caixa de seleção **Habilitar desvio de mídia para sites não mapeados**.
    
    > [!NOTE]  
    > Marque essa caixa de seleção somente se você tiver um ou mais sites grandes associados na mesma região e que não possuem restrições de largura de banda (por exemplo, um grande site central), mas também tem sites de filial associados à mesma região e que possuem restrições de largura de banda. Ao habilitar o desvio para sites não mapeados, a configuração é simplificada de forma que você especifica apenas as sub-redes associadas com os sites de filial em vez de precisar especificar todas as sub-redes associadas com todos os sites. Recomendamos que você não marque essa caixa de seleção se o controle de admissão de chamadas estiver habilitado.

7.  Clique em **Confirmar**.

Depois, adicione sub-redes ao site de região conforme descrito em [Associar subredes com locais de rede para bypass de mídia](lync-server-2013-associate-subnets-with-network-sites-for-media-bypass.md). (Os procedimentos atuais para a associação de sub-redes a sites de rede estão descritos em [Associar uma subrede a um site de rede no Lync Server 2013](lync-server-2013-associate-a-subnet-with-a-network-site.md).) Depois de associar todas as sub-redes com os sites de rede, a implantação do desvio de mídia estará completa.

> [!IMPORTANT]  
> Se ainda não tiverem sido criadas as regiões e os sites de rede, é preciso criá-los antes de prosseguir com a implantação do desvio de mídia. Para obter detalhes, consulte <a href="lync-server-2013-create-or-modify-a-network-region.md">Criar ou modificar uma região de rede no Lync Server 2013</a> e <a href="lync-server-2013-create-or-modify-a-network-site.md">Criar ou modificar um site da rede no Lync Server 2013</a>.

## Consulte Também

#### Conceitos

[Associar subredes com locais de rede para bypass de mídia](lync-server-2013-associate-subnets-with-network-sites-for-media-bypass.md)

