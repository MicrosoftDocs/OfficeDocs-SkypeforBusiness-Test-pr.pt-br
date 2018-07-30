---
title: 'Lync Server 2013: Resumo de DNS - única borda consolidada com endereços IP privados usando NAT'
TOCTitle: Resumo de DNS - única borda consolidada com endereços IP privados usando NAT
ms:assetid: a7e5d792-f397-45e5-af85-20d0f4bf405f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412787(v=OCS.15)
ms:contentKeyID: 49307722
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - única borda consolidada com endereços IP privados usando NAT no Lync Server 2013

 

_**Tópico modificado em:** 2017-03-09_

Os requisitos do registro DNS para acesso remoto ao Lync Server 2013 são bastante simples, comparados àqueles para certificados e portas. Além disso, muitos registros são opcionais, dependendo de como os clientes executando o Lync 2013 são configurados e se a federação está habilitada.

Para detalhes sobre os requisitos de DNS do Lync 2013, consulte [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

Para detalhes sobre a configuração automática de clientes executando o Lync 2013 se o split-brain DNS não estiver configurado, consulte "Configuração Automática sem Split-Brain DNS" em [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

A tabela a seguir contém um resumo dos registros DNS requeridos para oferecer suporte à topologia de borda consolidada única exibida na imagem Topologia de Borda Consolidada Única. Observe que determinados registros DNS são necessários somente para configuração automática de clientes Lync 2013 e Lync 2010. Se você planeja usar objetos de política de grupo (GPOs) para configurar clientes do Lync, os registros associados não são necessários.

## IMPORTANTE: Requisitos do Adaptador de Rede do Servidor de Borda

Para evitar problemas de roteamento, verifique se existem no mínimo dois adaptadores de rede em seus Servidores de Borda e que o gateway padrão está configurado somente no adaptador de rede associado à interface externa. Por exemplo, como mostra a figura Topologia de Borda Consolidada Única em [Única borda consolidada com endereços IP privados e NAT no Lync Server 2013](lync-server-2013-single-consolidated-edge-with-private-ip-addresses-and-nat.md), o gateway padrão apontaria para o firewall externo (10.45.16.1).

Você pode configurar dois adaptadores de rede em seu Servidor de Borda da seguinte forma:

  - **Adaptador de rede 1 (Interface Interna)**
    
    Interface interna com 172.25.33.10 atribuído.
    
    Nenhum gateway padrão é definido.
    
    Certifique-se de que existe uma rota a partir da rede contendo a interface interna da Borda para quaisquer redes que contenham servidores executando clientes do Lync Server 2013 ou Lync Server 2013 (por exemplo, de 172.25.33.0 para 192.168.10.0).

  - **Adaptador de rede 2 (Interface Externa)**
    
    Três endereços IP privados são atribuídos a esse adaptador de rede, por exemplo 10.45.16.10 para acesso de borda, 10.45.16.20 para borda de webconferência, 10.45.16.30 para borda de AV
    
    > [!NOTE]  
    > É possível, embora não seja recomendado, usar um único endereço IP para todas as três interfaces de serviço de borda. Embora economize endereços IP, isso exige diferentes números de porta para cada serviço. O número de porta padrão é 443/TCP, que garante que a maioria dos firewalls remotos permitirá o tráfego. Alterar os valores de porta para (por exemplo) 5061/TCP para borda de acesso, 444/TCP para borda de webconferência e 443/TCP para borda de AV pode causar problemas para usuários remotos quando eles estiverem atrás de um firewall que não permite tráfego através de 5061/TCP e 444/TCP. Além disso, três endereços IP distintos tornam a solução de problemas mais fácil, devido a possibilidade de filtrar os endereços IP.    
    O endereço IP da Borda de Acesso é principal com o gateway padrão definido para o roteador integrado (10.45.16.1).
    
    Webconferências e endereços IP de Borda de A/V secundários.


> [!TIP]
> Configurar o Servidor de Borda com dois adaptadores de rede é uma das duas opções. A outra opção é usar um adaptador de rede para o lado interno e três adaptadores de rede para o lado externo no Servidor de Borda. O principal benefício desta opção é distinguir o adaptador de rede por serviço do Servidor de Borda e potencialmente um conjunto de dados mais conciso quando a resolução de problemas é necessária



### Registros DNS requeridos para Topologia de Borda Consolidada Única com Endereços IP Privados usando NAT (Exemplo)

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>Registro de FQDN/DNS</th>
<th>Endereço IP/FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>131.107.155.10</p></td>
<td><p>Interface externa da borda de acesso (Contoso)Repetir conforme o necessário para todos os domínios SIP com usuários habilitados do Lync</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>Interface externa da borda de webconferências</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>Interface externa da Borda de A/V</p></td>
</tr>
<tr class="even">
<td><p>DNS/SRV/443 Externa</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Interface externa da borda de acesso. Obrigatória para configuração automática dos clientes Lync 2013 e Lync 2010 para trabalhar externamente. Repita conforme o necessário para todos os domínios SIP com usuários habilitados do Lync.</p></td>
</tr>
<tr class="odd">
<td><p>DNS/SRV/5061 Externa</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Interface externa de borda de acesso SIP obrigatória para descoberta de DNS automática de parceiros federados, conhecida como &quot;Domínio SIP Permitido&quot; (chamada de federação avançada em versões anteriores). Repita conforme o necessário para todos os domínios SIP com usuários habilitados do Lync.</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>Interface interna da Borda Consolidada</p></td>
</tr>
</tbody>
</table>


> [!IMPORTANT]  
> Os registros listados na tabela anterior são exibidos com uma extensão <em>.net</em> ou <em>.com</em> para destacar em qual zona eles devem ser hospedados se você não estiver usando DNS split-brain. Se você estiver usando DNS split-brain, todos os registros estariam na mesma zona <em>.com</em> , com apenas uma diferença sendo se eles estão na versão de zona DNS interna ou externa. Para obter mais detalhes, consulte &quot;DNS Split-Brain&quot; em <a href="lync-server-2013-determine-dns-requirements.md">Determinar requisitios de DNS para Lync Server 2013</a>

## Registros necessários para federação


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>FQDN</th>
<th>Endereço IP/Registro de host FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/SRV/5061 Externa</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Interface externa de borda de acesso SIP obrigatória para descoberta de DNS automática de sua federação para outros parceiros potenciais de federação, conhecida também como &quot;Domínio SIP Permitido&quot; (chamada de federação avançada em versões anteriores). Repita conforme o necessário para todos os domínios SIP com usuários habilitados do Lync.</p>
<div class="alert">
> [!IMPORTANT]  
> Esse registro SRV é obrigatório para mobilidade e Push Notification Clearing House (PNCH)
</div></td>
</tr>
</tbody>
</table>


## Resumo de DNS - Conectividade de mensagem instantânea pública


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>Registro de FQDN/DNS</th>
<th>Endereço IP/FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>interface Serviço de Borda de Acesso</p></td>
<td><p>Interface externa da borda de acesso (Contoso)Repetir conforme o necessário para todos os domínios SIP com usuários habilitados do Lync</p></td>
</tr>
</tbody>
</table>


## Resumo DNS para Protocolo de Presença e Mensagem Extensível


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Local/TIPO/Porta</th>
<th>FQDN</th>
<th>Endereço IP/Registro de host FQDN</th>
<th>Mapeia para/Comenta</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DNS/SRV/5269 Externa</p></td>
<td><p>_xmpp-server._tcp.contoso.com</p></td>
<td><p>xmpp.contoso.com</p></td>
<td><p>A interface externa do proxy XMPP no Serviço de Borda de Acesso ou Pool de borda. Repita conforme for necessário para todos os domínios SIP internos com usuários habilitados para Lync, onde o contato com contatos XMPP é permitido através da configuração da Política de Acesso Externo por meio de uma política global, política local de onde o usuário está, ou política de usuário aplicada ao usuário habilitado para Lync. Um domínio XMPP permitido deve ser também configurado na política de Parceiros Federados XMPP. Consulte os tópicos em <strong>Consulte também</strong> para obter mais detalhes</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>xmpp.contoso.com (por exemplo)</p></td>
<td><p>Endereço IP de Serviço de Borda de Acesso em seu Servidor de Borda ou Pool de borda hospedando o proxy XMPP</p></td>
<td><p>Aponta para o Serviço de Borda de Acesso ou Pool de borda que hospeda o serviço de proxy XMPP. Normalmente, o registro SRV que você cria aponta para esse registro de host (A ou AAAA)</p></td>
</tr>
</tbody>
</table>

