---
title: Requisitos de DNS para pools de front-end
TOCTitle: Requisitos de DNS para pools de front-end
ms:assetid: ba28919c-fbbe-4c54-8bf9-2b0cd3fa39c7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412910(v=OCS.15)
ms:contentKeyID: 49307913
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de DNS para pools de front-end

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve os registros de DNS (Sistema de Nomes de Domínio) necessários para a implantação dos pools de Front-Ends.

## Registros DNS para pools Front-End

A tabela a seguir especifica requisitos DNS para uma implantação de pool Front-End do Lync Server 2013.

### Requisitos DNS para um pool Front-End

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cenário da implantação</th>
<th>Requisito de DNS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Pool Front-End com múltiplos servidores Front-End e um balanceador de carga de hardware (mesmo que o balanceamento de carga DNS também esteja implantado nesse pool)</p></td>
<td><p>Ao utilizar ambos o balanceamento de carga DNS e um balanceador de carga de hardware, você precisa hospedar registros (A). Crie um registro interno A que resolva o nome de domínio totalmente qualificado (FQDN) do pool de Front End para o balanceamento de carga DNS. Crie um registro de host interno (A) para os serviços Web internos para o endereço IP virtual (VIP) do balanceador de carga. Você precisa utilizar o nome dos serviços Web internos conforme definido em Construtor de Topologias.</p>
<p>Por exemplo, se você utilizar ambos o balanceamento de carga DNS e um balanceador de carga de hardware, você teria um registro A para cada Servidor Front-End em um pool para balanceamento de carga DNS, e um registro A para os serviços Web internos apontando para o IP virtual do balanceador de carga de hardware:</p>
<ul>
<li><p>Balanceamento de carga DNS:   Pool01.contoso.net   Endereço IP do pool   10.10.10.5</p>
<div class="alert">

> [!WARNING]
> Cada Servidor Front-End também terá um registro A distinto:


</div>
<ol>
<li><p>FE01.contoso.net    10.10.10.1</p></li>
<li><p>FE02.contoso.net    10.10.10.2</p></li>
<li><p>FE03.contoso.net    10.10.10.3</p></li>
<li><p>FE04.contoso.net    10.10.10.4</p></li>
</ol></li>
<li><p>Balanceamento de carga de hardware:   WebInternal.contoso.net   Endereço IP do HLB VIP   192.168.10.5</p></li>
</ul>
<p>Todo o tráfego, exceto o de tipo HTTP/HTTPS, utilizará o registro Pool01.contoso.net record. Tráfego HTTP/HTTPS utilizará o endereço definido para serviços Web internos, 192.168.10.5</p></td>
</tr>
<tr class="even">
<td><p>Pool Front-End com balanceamento de carga DNS implantado</p></td>
<td><p>Um conjunto de registros A internos que resolvem o FQDN do pool para o endereço IP de cada servidor no pool. É preciso ter um registro A para cada servidor no pool.</p></td>
</tr>
<tr class="odd">
<td><p>Pool Front-End com balanceamento de carga DNS implantando</p></td>
<td><p>Um conjunto de registros A internos que resolvem o FQDN de cada servidor no pool para o endereço IP desse servidor. Para obter detalhes, consulte <a href="lync-server-2013-dns-load-balancing.md">Balanceamento de carga DNS no Lync Server 2013</a> na documentação Planejamento.</p></td>
</tr>
<tr class="even">
<td><p>Pool Front-End com um único Servidor Front-End e um banco de dados back-end dedicado, mas sem balanceador de carga</p></td>
<td><p>Um registro A interno que resolve o FQDN do pool Front-End para o endereço IP do Servidor Front-End Enterprise Edition único.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>Entrada automática do cliente</p></td>
<td><p>Para cada domínio SIP suportado, um registro SRV para _sipinternaltls._tcp.&lt;domain&gt; sobre a porta 5061 que mapeia para o FQDN do pool Front-End que autentica e redireciona as solicitações de cliente para entrada. Para obter detalhes, consulte <a href="lync-server-2013-dns-requirements-for-automatic-client-sign-in.md">Requisitos DNS para conexão automática de clientes no Lync Server 2013</a>.</p></td>
</tr>
<tr class="even">
<td><p>Descoberta do Serviço Web de Atualização de Dispositivo por dispositivos UC (comunicações unificadas)</p></td>
<td><p>Um registro A interno com o nome ucupdates-r2.&lt;SIP domain&gt; que resolve para o endereço IP do pool Front-End que hospeda o Serviço Web de Atualização de Dispositivo. Na situação na qual um dispositivo UC é ativado, mas um usuário nunca entrou no dispositivo, o registro A permite que o dispositivo descubra o pool Front-End que hospeda o Serviço Web de Atualização de Dispositivo e obtenha atualizações. Caso contrário, os dispositivos obtêm essas informações por meio do fornecimento em banda na primeira vez que um usuário faz login.</p>

> [!IMPORTANT]  
> Se você tiver uma implantação existente do Serviço Web de Atualização de Dispositivo no Lync Server 2010, você já terá criado um registro A interno com o nome ucupdates.<em>&lt;SIP domain&gt;</em>. Para o Microsoft Office Communications Server 2007 R2, é necessário criar um registro DNS A adicional com o nome ucupdates-r2.<em>&lt;SIP domain&gt;</em>.

</td>
</tr>
<tr class="odd">
<td><p>Um proxy reverso para suportar o tráfego HTTP</p></td>
<td><p>Um registro A externo que resolve o FQDN da web farm externa para o endereço IP externo do proxy reverso. Dispositivos clientes e UC usam esse registro para se conectar ao proxy reverso. Para obter detalhes, consulte <a href="lync-server-2013-determine-dns-requirements.md">Determinar requisitios de DNS para Lync Server 2013</a> na documentação Planejamento.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir mostra um exemplo dos registros DNS exigidos para o FQDN da web farm interna.

### Exemplos de registros DNS para FQDN da web farm interna

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>FQDN da web farm interna</th>
<th>FQDN do pool</th>
<th>Registro(s) A de DNS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>webcon.contoso.com</p></td>
<td><p>ee-pool.contoso.com</p></td>
<td><p>Registro A de DNS do ee-pool.contoso.com que se resolva como o endereço VIP do balanceador de carga usado pelos Servidores Front-End.</p>
<p>Registro A de DNS do webcon.contoso.com que se resolva como o endereço VIP do balanceador de carga usado pelos Servidores Front-End.</p></td>
</tr>
<tr class="even">
<td><p>ee-pool.contoso.com</p></td>
<td><p>ee-pool.contoso.com</p></td>
<td><p>Registro A de DNS do ee-pool.contoso.com que se resolva como o endereço VIP (IP virtual) do balanceador de carga usado pelos servidores Enterprise Edition no pool Front-End.</p>
<p>Observe que se você estiver usando o balanceamento de carga DNS nesse pool, seu pool Front-End e web farm interna não poderão ter o mesmo FQDN.</p></td>
</tr>
</tbody>
</table>

