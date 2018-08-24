---
title: Criar ou modificar subredes
TOCTitle: Criar ou modificar subredes
ms:assetid: 1ba8c4e3-fbc7-4758-88ac-d651fef17bed
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg520957(v=OCS.15)
ms:contentKeyID: 49306047
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou modificar subredes

 

_**Tópico modificado em:** 2013-02-21_

É necessário associar uma subrede da rede com um site de rede para fins de determinar o local geográfico do host que pertence a esta subrede. É possível usar o Painel de Controle do Lync Server para configurar subredes. No Painel de Controle do Lync Server, é possível criar, modificar ou excluir uma subrede. Para obter detalhes sobre como excluir subredes, consulte [Excluir subredes](lync-server-2013-deleting-network-subnets.md)

Na maioria das implantações do Microsoft Lync Server 2013 nas quais o CAC (controle de admissão de chamadas) foi implantado, haverá um grande número de sub-redes. Por isso, normalmente é melhor configurar as sub-redes a partir do Shell de Gerenciamento do Lync Server. Dali é possível chamar o **New-CsNetworkSubnet** juntamente com o cmdlet **Import-CSV** do Windows PowerShell. Ao usar esses cmdlets juntos, é possível ler configurações de sub-rede a partir de um arquivo de valores separados por vírgula (CSV) e criar várias sub-redes de uma só vez. Para obter exemplos de como criar sub-redes a partir de um arquivo .csv, consulte [New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet).

## Para criar uma sub-rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração da rede** e clique em **Sub-rede**.

4.  Na página **Sub-rede** clique em **Novo**.

5.  Em **Nova Sub-rede**, digite um valor no campo **ID da sub-rede**. Esse valor deve ser um endereço IP (por exemplo, 174.11.12.0) e deve ser o primeiro endereço no intervalo de endereço IP definido pela sub-rede.

6.  No campo **Máscara**, digite um valor numérico de 1 a 32.
    
    > [!NOTE]  
    > Este valor é o bitmask que será aplicado na sub-rede criada.

7.  Em **ID do site da rede**, selecione o site ao qual a sub-rede pertence.

8.  (Opcional) Digite um valor no campo **Descrição** para fornecer mais informações essa sub-rede que não pode ser expressa somente pelo nome.

9.  Clique em **Confirmar**.

## Para modificar uma sub-rede de rede

1.  Usando uma conta de usuário que é membro do grupo RTCUniversalServerAdmins (ou tem direitos de usuário equivalentes), ou está atribuída à função CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Configuração da rede** e clique em **Sub-rede**.

4.  Na página **Sub-rede**, clique na sub-rede que deseja modificar.

5.  No menu **Editar**, clique **Exibir detalhes**.

6.  Na página **Editar sub-rede**, é possível modificar o bitmask, o local de rede associado ou a descrição. Se for mudar o bitmask, tenha em mente que o ID da sub-rede deve ser ainda o primeiro endereço do intervalo de endereço IP definido pela sub-rede.

7.  Clique em **Confirmar**.

## Consulte Também

#### Tarefas

[Excluir subredes](lync-server-2013-deleting-network-subnets.md)  

#### Conceitos

[Sobre regiões de rede, sites e subredes no Lync Server 2013](lync-server-2013-about-network-regions-sites-and-subnets.md)  

#### Outros Recursos

[New-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsNetworkSubnet)  
[Set-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsNetworkSubnet)  
[Remove-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsNetworkSubnet)  
[Get-CsNetworkSubnet](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsNetworkSubnet)

