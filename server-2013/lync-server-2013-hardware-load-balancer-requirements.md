---
title: 'Lync Server 2013: Requisitos do balanceador de carga do hardware'
TOCTitle: Requisitos do balanceador de carga do hardware
ms:assetid: 32891268-2059-43d0-adf4-af4ff1e9ce66
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ656815(v=OCS.15)
ms:contentKeyID: 49886168
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos do balanceador de carga do hardware para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

A topologia de borda consolidada em escala do Lync Server 2013 é otimizada para balanceamento de carga de DNS de novas implantações federadas principalmente com outras organizações que usam o Lync Server. Se for exigida alta disponibilidade para qualquer um dos cenários a seguir, um balanceador de carga de hardware deverá ser usado em pools do Servidor de Borda para o seguinte:

  - Federação com organizações que usam o Office Communications Server 2007 R2 ou o Office Communications Server 2007

  - UM do Exchange para usuários remotos que usam o UM do Exchange antes do Exchange 2010 com SP1

  - Conectividade para usuários públicos de mensagens instantâneas

> [!IMPORTANT]  
> O uso do balanceamento de carga de DNS em uma interface e do balanceamento de carga de hardware na outra não é suportado. É preciso usar o balanceamento de carga de hardware ou de DNS nas duas interfaces.

> [!NOTE]  
> Se estiver usando um balanceador de carga de hardware, o balanceador de carga implantado para conexões com a rede interna deverá ser configurado para balancear apenas cargas do tráfego de servidores que executam o serviço de Borda de Acesso e o serviço de Borda A/V. Ele não poderá balancear a carga do tráfego do serviço interno de Borda de Webconferência ou do serviço interno de Proxy XMPP.

> [!NOTE]  
> O NAT do DSR (devolução do servidor direto) não é suportado com o Lync Server 2013.

Para determinar se o seu balanceador de carga de hardware oferece suporte aos recursos necessários exigidos pelo Lync Server 2013, consulte "Lync Server 2010 Parceiros do Balanceador de Carga" em [http://go.microsoft.com/fwlink/p/?linkId=202452](http://go.microsoft.com/fwlink/p/?linkid=202452).

## Requisitos do balanceador de carga de hardware para servidores de borda que executam o serviço de Borda A/V

A seguir, são apresentados os requisitos do balanceador de carga de hardware do Servidores de Borda que executa o serviço de Borda A/V:

  - Desative o nagling de TCP para as portas interna e externa 443. Nagling é o processo de combinação de diversos pacotes pequenos em um único pacote maior para uma transmissão mais eficiente.

  - Desative o nagling de TCP para o intervalo de portas externas 50.000 a 59.999.

  - Não use NAT no firewall interno ou externo.

  - A interface interna da borda precisa estar em uma rede diferente da interface externa do Servidor de Borda e o roteamento entre elas deve ser desativado.

  - A interface externa do Servidor de Borda que executa o serviço de Borda A/V precisa usar os endereços IP publicamente roteáveis e não NAT ou conversão de porta em qualquer um dos endereços IP externos da borda.

## Requisitos do Balanceador de Carga de Hardware

Os requisitos de afinidade baseados em cookie foram drasticamente reduzidos no Lync Server 2013 para serviços Web. Se estiver implantando o Lync Server 2013 e não estiver retendo nenhum Lync Server 2010Servidores Front-End ou Pools de Front-Ends, a persistência baseada em cookie não será necessária. No entanto, se você for reter temporária ou permanentemente qualquer Lync Server 2010Servidores Front-End ou Pools de Front-Ends, continue a usar a persistência baseada em cookie, pois ela é implantada e configurada para o Lync Server 2010.

> [!NOTE]  
> <strong>Se decidir usar a afinidade baseada em cookie mesmo que sua implantação não exija</strong>, isso não causará um impacto negativo.

Para implantações que **não usarão** afinidade baseada em cookie:

  - No proxy reverso que publica a regra da porta 4443, defina **Encaminhar cabeçalho de host** como Verdadeiro. Isso garantirá que a URL original seja encaminhada.

Para implantações que **usarão** afinidade baseada em cookie:

  - No proxy reverso que publica a regra da porta 4443, defina **Encaminhar cabeçalho de host** como Verdadeiro. Isso garantirá que a URL original seja encaminhada.

  - O cookie do balanceador de carga de hardware NÃO DEVE ser marcado como httpOnly

  - O cookie do balanceador de carga de hardware NÃO DEVE conter uma data de vencimento

  - O cookie do balanceador de carga de hardware DEVE ser nomeado como **MS-WSMAN** (este é o valor que o serviço Web espera e não pode ser alterado)

  - O cookie do balanceador de carga de hardware DEVE ser definido em todas as respostas HTTP para as quais a solicitação HTTP recebida não contém um cookie, independentemente de uma resposta HTTP anterior na mesma conexão TCP já ter obtido um cookie. Se o balanceador de carga otimiza a inserção de cookie para apenas uma ocorrência por conexão TCP, essa otimização NÃO DEVE ser usada

> [!NOTE]  
> As configurações típicas do balanceador de carga de hardware usam afinidade com endereço de origem e tempo de vida de 20 minutos da sessão de TCP, o que é suficiente para os clientes do Lync Server e do Lync 2013, pois o estado da sessão é mantido em todo o uso do cliente e/ou interação do aplicativo.

Se estiver implantando dispositivos móveis, o balanceador de carga de hardware deverá ser capaz de balancear a carga da solicitação individual em uma sessão TCP (na verdade, você deve poder balancear a carga de uma solicitação individual com base no endereço IP de destino).


> [!WARNING]
> Os balanceadores de carga de hardware F5 têm um recurso chamado OneConnect que assegura que todas as solicitações de uma conexão TCP tenham a carga balanceada individualmente. Se estiver implantando dispositivos móveis, verifique se o fornecedor do balanceador de carga de hardware tem o mesmo recurso. Os aplicativos móveis mais recentes do Apple iOS exigem a versão 1.2 do protocolo TLS. O F5 oferece configurações específicas para isso.<BR>Para obter informações sobre balanceadores de carga de hardware de terceiros, consulte <A href="http://go.microsoft.com/fwlink/p/?linkid=230700">http://go.microsoft.com/fwlink/p/?linkId=230700</A>



A seguir, são apresentados os requisitos do balanceador de carga de hardware para serviços Web do pool de diretores e de front-end:

  - Para VIPs de serviços Web internos, defina a persistência Source\_addr (porta interna 80, 443) no balanceador de carga de hardware. Para o Lync Server 2013, a persistência Source\_addr significa que múltiplas conexões vindas de um único endereço IP são sempre enviadas a um servidor para manter o estado da sessão.

  - Use um tempo de ociosidade de TCP de 1.800 segundos.

  - No firewall entre o proxy reverso e o balanceador de carga de hardware do pool de próximo salto, crie uma regra que permita o tráfego https: na porta 443 do proxy reverso para o balanceador de carga de hardware. O balanceador de carga de hardware deve ser configurado para ouvir as portas 80, 443 e 4443.

## Resumo dos requisitos de afinidade do balanceador de carga de hardware


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Local do cliente/usuário</th>
<th>Requisitos de afinidade de FQDN de serviços Web externos</th>
<th>Requisitos de afinidade de FQDN de serviços Web internos</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync Web App (usuários internos e externos)</p>
<p>Dispositivo móvel (usuários internos e externos)</p></td>
<td><p>Sem afinidade</p></td>
<td><p>Afinidade do endereço de origem</p></td>
</tr>
<tr class="even">
<td><p>Lync Web App (apenas usuários externos)</p>
<p>Dispositivo móvel (usuários internos e externos)</p></td>
<td><p>Sem afinidade</p></td>
<td><p>Afinidade do endereço de origem</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App (apenas usuários internos)</p>
<p>Dispositivo móvel (não implantado)</p></td>
<td><p>Sem afinidade</p></td>
<td><p>Afinidade do endereço de origem</p></td>
</tr>
</tbody>
</table>


## Monitoramento de portas dos balanceadores de carga de hardware

Defina o monitoramento de portas nos balanceadores de carga de hardware para determinar quando serviços específicos não estão mais disponíveis devido a uma falha de hardware ou comunicação. Por exemplo, se o serviço de Servidor Front-End (RTCSRV) for interrompido por uma falha do Servidor Front-End ou do Pool de Front-Ends, o monitoramento de HLB deve parar de receber tráfego também do Serviços Web. Implante o monitoramento de portas no HLB para monitorar o seguinte:

### Pool de usuários do Servidor Front-End - Interface interna de HLB

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
<th>IP/porta virtual</th>
<th>Porta do nó</th>
<th>Máquina/monitor do nó</th>
<th>Perfil de persistência</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;pool&gt;web-int_mco_443_vs</p>
<p>443</p></td>
<td><p>443</p></td>
<td><p>Front End</p>
<p>5061</p></td>
<td><p>Origem</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>&lt;pool&gt;web-int_mco_80_vs</p>
<p>80</p></td>
<td><p>80</p></td>
<td><p>Front End</p>
<p>5061</p></td>
<td><p>Origem</p></td>
<td><p>HTTP</p></td>
</tr>
</tbody>
</table>


### Pool de usuários do Servidor Front-End - Interface externa de HLB

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
<th>IP/porta virtual</th>
<th>Porta do nó</th>
<th>Máquina/monitor do nó</th>
<th>Perfil de persistência</th>
<th>Notas</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>&lt;pool&gt;web_mco_443_vs</p>
<p>443</p></td>
<td><p>4443</p></td>
<td><p>Front End</p>
<p>5061</p></td>
<td><p>Nenhum</p></td>
<td><p>HTTPS</p></td>
</tr>
<tr class="even">
<td><p>&lt;pool&gt;web_mco_80_vs</p>
<p>80</p></td>
<td><p>8080</p></td>
<td><p>Front End</p>
<p>5061</p></td>
<td><p>Nenhum</p></td>
<td><p>HTTP</p></td>
</tr>
</tbody>
</table>

