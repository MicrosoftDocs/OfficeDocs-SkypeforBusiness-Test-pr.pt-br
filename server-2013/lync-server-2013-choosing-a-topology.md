---
title: 'Lync Server 2013: Escolhendo uma topologia'
TOCTitle: Escolhendo uma topologia
ms:assetid: 23f2aeb6-fed9-4349-8fba-dcbf18ee4b04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425716(v=OCS.15)
ms:contentKeyID: 49306137
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Escolhendo uma topologia no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Ao escolher uma topologia, é possível usar uma das seguintes opções de topologia suportadas:

> [!NOTE]  
> A não ser observado de forma diferente, se você tem experiência com o Microsoft Lync Server 2010, descobrirá que o guia aqui permanece praticamente o mesmo.

  - [Única borda consolidada com endereços IP privados e NAT no Lync Server 2013](lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md)

  - [Única borda consolidada com endereços IP públicos no Lync Server 2013](lync-server-2013-single-consolidated-edge-with-public-ip-addresses.md)

  - [Borda consolidada em escala, balanceamento de carga de DNS com endereços IP privados usando NAT no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-private-ip-addresses-using-nat.md)

  - [Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md)

  - [Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md)

> [!IMPORTANT]  
> A interface de Borda interna e externa devem usar o mesmo tipo de balanceamento de carga. Não é possível usar o balanceamento de carga DNS na interface de Borda e o balanceamento de carga de hardware na outra interface de Borda.

A tabela a seguir resume a funcionalidade disponível com as topologias do Microsoft Lync Server 2013 suportadas. Os cabeçalhos da coluna indicam a funcionalidade disponível para uma determinada opção de configuração de Borda. Usando a opção Borda Escalonável (balanceada com carga DNS) como um exemplo, é possível ver que suporta alta disponibilidade, pode usar endereços IP privados não roteáveis (com NAT) ou endereços IP públicos roteáveis para interfaces externas de Borda e reduz custos porque o balanceador de carga de hardware não é exigidos.

Cenários de failover de borda suportados com Balanceamento de Borda DNS são sessões ponto a ponto Lync-to- Lync, sessões de conferência do Lync, sessões Lync-para-PSTN e Office 365. Os cenários de failover de Borda que não se beneficiam do Balanceamento de Carga DNS são failover para usuário remoto do Unificação de Mensagens (UM) do Exchange (antes do Exchange 2010 SP1), conectividade de mensagem instantânea (IM) público e federação com servidores executando o Office Communications Server.

### Resumo das opções de topologia de servidor de borda

<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Topologia</th>
<th>Alta disponibilidade</th>
<th>Registro DNS A externo adicional necessário para Servidor de Borda no pool de Borda</th>
<th>Failover de borda para sessões Lync para Lync</th>
<th>Failover de borda para sessões de federação EUM/PIC/OCS Lync para Lync</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Borda única usando NAT</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Borda única usando IP público</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Borda escalonável (Balanceamento de carga DNS) usando NAT</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>*</p></td>
</tr>
<tr class="even">
<td><p>Borda escalonável (Balanceamento de carga DNS) usando IP público</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>*</p></td>
</tr>
<tr class="odd">
<td><p>Borda escalonável (Balanceamento de carga de hardware)</p></td>
<td><p>Sim</p></td>
<td><p>Não (um registro DNS A por VIP)</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
</tbody>
</table>


**\*** Failover para conectividade de mensagem instantânea (IM) pública e federação com servidores executando o Office Communications Server não está disponível com balanceamento de carga DNS. Failover do UM do Exchange (usuário remoto) usando balanceamento de carga DNS exige o Exchange Server 2010 SP1 ou mais recente.

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Gg425756.note(OCS.15).gif" title="note" alt="note" />Observação:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><br />As topologias de Borda única e Borda escalonável (balanceamento de carga DNS) podem usar:<ul><li><p>Endereço IP público roteável</p></li><li><p>Endereço IP privado não roteável se a tradução de endereço de rede (NAT) simétrica for usada</p>

> [!NOTE]  
> Se você usar endereço IP público ou privado com NAT, você ainda usará o mesmo número de endereços IP baseados na sua opção de configuração no Construtor de Topologias. Você pode configurar o Servidor de Borda para usar um único endereço IP com portas distintas por serviço ou usar endereços IP distintos por serviço, mas use a mesma porta (por padrão, TCP 443).

</li></ul>
Se você decidir usar endereços IP privados não roteáveis com NAT:<ul><li><p>Você deve usar endereços IP privados roteáveis em todas as três interfaces externas</p></li><li><p>Você deve configurar NAT simétrico para tráfego de entrada e saída</p></li></ul>
Topologia de borda escalonável (balanceamento de carga de hardware) deve usar endereços IP públicos.</td>
</tr>
</tbody>
</table>


O Lync Server 2013 suporta interfaces externas de Acesso, Conferência da Web e Borda A/V por trás de um roteador ou firewall que realiza NAT para topologias do Servidor de Borda consolidada única ou escalonável.

Usando o NAT em todas as interfaces externas de Borda exige o uso do balanceamento de carga DNS. Quando comparado ao uso de balanceadores de carga de hardware, o balanceamento de carga de DNS sem NAT permite reduzir o número de endereços IP públicos por Servidor de Borda em um pool de Borda, conforme descrito na seguinte lista:

  - A Borda consolidada dimensionada do Lync Server 2013 (balanceamento de carga DNS) exige três endereços IP públicos para cada Servidor de Borda em um pool de Borda.

  - A Borda consolidada dimensionada do Lync Server 2013 (balanceamento de carga de hardware) exige três endereços IP públicos para os endereços IP virtuais do balanceador de carga (um requisito exclusivo que não é incrementado conforme mais Servidores de Borda são adicionadas ao pool), além de três endereços IP públicos por Servidor de Borda em um pool.

### Requisitos de endereço IP para Borda consolidada dimensionada (endereço de IP por função)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Número de Servidores de Borda por pool</th>
<th>Número de endereços IP necessários do Lync Server 2013 (carga balanceada por DNS)</th>
<th>Número de endereços IP necessários do Lync Server 2013 (carga balanceada por hardware)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>6</p></td>
<td><p>3 (1 por VIP) + 6</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>9</p></td>
<td><p>3 (1 por VIP) + 9</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>12</p></td>
<td><p>3 (1 por VIP) + 12</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>15</p></td>
<td><p>3 (1 por VIP) + 15</p></td>
</tr>
</tbody>
</table>


### Requisitos de endereço IP para Borda consolidada dimensionada (endereço de IP único para todas as funções)

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Número de Servidores de Borda por pool</th>
<th>Número de endereços IP necessários do Lync Server 2013 (carga balanceada por DNS)</th>
<th>Número de endereços IP necessários do Lync Server 2013 (carga balanceada por hardware)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>2</p></td>
<td><p>2</p></td>
<td><p>1 (1 por VIP) + 2</p></td>
</tr>
<tr class="even">
<td><p>3</p></td>
<td><p>3</p></td>
<td><p>1 (1 por VIP) + 3</p></td>
</tr>
<tr class="odd">
<td><p>4</p></td>
<td><p>4</p></td>
<td><p>1 (1 por VIP) + 4</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p>5</p></td>
<td><p>1 (1 por VIP) + 5</p></td>
</tr>
</tbody>
</table>


Os pontos de decisão principal para seleção de topologia são alta disponibilidade e balanceamento de carga. A necessidade de alta disponibilidade pode influenciar a decisão de balanceamento de carga.

  - **Alta disponibilidade** Se precisar de alta disponibilidade, implante pelo menos dois Servidores de Borda em um pool. Um único pool de Borda oferecerá suporte para até dez Servidores de Borda. Se mais capacidade for necessária, é possível implantar vários pools de Borda. Como regra geral, 10% de uma determinada base de usuários precisará de acesso externo.
    
    > [!IMPORTANT]  
    > O Construtor de Topologias permitirá que você configure até vinte Servidores de Borda em um único Pool de borda. O número máximo suportado e testado de Servidores de Borda em um pool é doze, e o Construtor de Topologias que permite um número maior que doze não deve ser interpretado como suporte implícito para mais de doze Servidores de Borda em um único Pool de borda.

  - **Balanceamento de carga de hardware** O balanceamento de carga de hardware é suportado para balanceamento de carga do Lync Server 2013  Servidores de Borda ao usar endereços IP roteáveis publicamente para as interfaces externas de Borda. Por exemplo, você usaria essa abordagem em situações onde o failover é necessário para qualquer um dos seguintes aplicativos:
    
      - Conectividade a redes públicas de mensagens instantâneas
    
      - Federação com empresas executando o Microsoft Office Communications Server 2007 ou Microsoft Office Communications Server 2007 R2
    
      - Acesso externo ao Exchange 2007 Unified Messaging (UM) ou Exchange 2010 UM
        
        > [!IMPORTANT]  
        > Balanceamento de carga DNS para Exchange 2010 SP1 e mais recente é suportado para UM do Exchange.    
    Esses três aplicativos continuarão a operar, mas eles não estão cientes do balanceamento de carga DNS e só se conectam ao primeiro Servidor de Borda no pool. Se este servidor não estiver disponível, a conexão falhará. Por exemplo, se vários Servidores de Borda são implantados em um pool para manipular a carga de tráfego federado, apenas um proxy de acesso realmente recebe tráfego enquanto outros ficam ociosos.

> [!IMPORTANT]  
> Usar o balanceamento de carga DNS é recomendado se você está federando com empresas usando o Lync Server 2010 e o Microsoft Office 365. Esteja ciente de que existem impactos de desempenho significativos se a maioria dos parceiros federados estiverem usando o Office Communications Server 2007 ou Office Communications Server 2007 R2.
