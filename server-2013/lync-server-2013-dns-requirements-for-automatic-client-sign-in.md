---
title: Requisitos DNS para conexão automática de clientes no Lync Server 2013
TOCTitle: Requisitos DNS para conexão automática de clientes no Lync Server 2013
ms:assetid: 3bcd4bb3-a022-4ffa-b005-1a95ad2b1796
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425884(v=OCS.15)
ms:contentKeyID: 49306440
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos DNS para conexão automática de clientes no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção explica os registros do DNS (Sistema de Nomes de Domínio) que são necessários para entrada automática de clientes. Quando você implanta servidores Standard Edition ou pools de Front-Ends, é possível configurar os clientes para que eles usem a descoberta automática para entrar no servidor Standard Edition ou no pool Front-End. Se você planeja exigir que os clientes se conectem manualmente ao Lync Server 2013, poderá pular este tópico.

Para dar suporte à entrada automática de clientes, você deve:

  - Designar um único servidor ou pool para distribuir e autenticar as solicitações de entrada dos clientes. Ele pode ser um servidor ou pool existente em sua organização que hospede usuários, ou você pode designar para essa finalidade um servidor ou pool dedicado que não hospede usuários. Para que haja alta disponibilidade, recomendamos que você designe um pool Front-End para essa função.

  - Criar um registro SRV de DNS interno para dar suporte à entrada automática de clientes nesse servidor ou pool.
    
    > [!NOTE]  
    > Nos requisitos de registro a seguir, o domínio SIP se refere à parte de host dos URIs do SIP atribuídos aos usuários. Por exemplo, se os URIs do SIP estiverem no formato *@contoso.com, contoso.com será o domínio SIP. O domínio SIP é geralmente diferente do domínio interno do Active Directory. Uma organização também poderá oferecer suporte a vários domínios SIP.

Para habilitar a configuração automática para seus clientes, você precisa criar um registro SRV de DNS interno que mapeie um dos seguintes registros para o FQDN (nome de domínio totalmente qualificado) do pool Front-End ou servidor Standard Edition que distribua solicitações de entrada a partir de clientes do Lync:

  - \_sipinternaltls.\_tcp.*\<domínio\>* - para conexões TLS internas

Você só precisa criar um único registro SRV para o pool Front-End ou servidor Standard Edition que distribuirá as solicitações de entrada.

A tabela a seguir mostra alguns exemplos de registros necessários para a empresa fictícia Contoso, que oferece suporte aos domínios SIP contoso.com e retail.contoso.com.

### Exemplo de registros DNS necessários para entrada automática de clientes com vários domínios SIP

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>FQDN do pool Front-End usado para distribuir solicitações de entrada</th>
<th>Domínio SIP</th>
<th>Registro SRV de DNS</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>pool01.contoso.com</p></td>
<td><p>contoso.com</p></td>
<td><p>Um registro SRV para o domínio _sipinternaltls._tcp.contoso.com através da porta 5061 que mapeie para pool01.contoso.com</p></td>
</tr>
<tr class="even">
<td><p>pool01.contoso.com</p></td>
<td><p>retail.contoso.com</p></td>
<td><p>Um registro SRV para o domínio _sipinternaltls._tcp.retail.contoso.com através da porta 5061 que mapeie para pool01.contoso.com</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Por padrão, as consultas de registros DNS seguem uma correspondência estrita de nomes de domínio entre o domínio no nome do usuário e o registro SRV. Se, em vez disso, você preferir que as consultas de DNS dos clientes usem a correspondência de sufixo, poderá configurar a política de grupo DisableStrictDNSNaming. Para obter detalhes, consulte <a href="lync-server-2013-planning-for-clients-and-devices.md">Planejando clientes e dispositivos no Lync Server 2013</a> na documentação de Planejamento.

## Exemplo dos certificados e dos registros DNS necessários para a entrada automática de clientes

Esse exemplo usa os mesmos nomes de exemplo da tabela anterior. A organização Contoso oferece suporte aos domínios SIP contoso.com e retail.contoso.com, e todos os seus usuários têm um URI do SIP em um dos seguintes formatos:

  - *\<usuário\>*@retail.contoso.com

  - *\<usuário\>*@contoso.com

