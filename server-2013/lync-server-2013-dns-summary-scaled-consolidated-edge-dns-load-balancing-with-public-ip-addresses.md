---
title: 'Lync Server 2013: Resumo de DNS - Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos'
TOCTitle: Resumo de DNS - Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos
ms:assetid: dc8f096a-a0a4-4f71-8930-88ff8fc089d9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205319(v=OCS.15)
ms:contentKeyID: 49308331
ms.date: 03/09/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos no Lync Server 2013

 

_**Tópico modificado em:** 2017-03-09_

Os requisitos do registro DNS para acesso remoto ao Lync Server 2013 são bastante simples, comparados àqueles para certificados e portas. Além disso, muitos registros são opcionais, dependendo de como os clientes executando o Lync 2013 são configurados e se a federação está habilitada.

Para detalhes sobre os requisitos de DNS do Lync 2013, consulte [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

Para obter detalhes sobre como realizar a configuração automática dos clientes do Lync 2013 se um DNS split-brain não estiver configurado, consulte a seção "Configuração automática sem DNS split-brain" [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

A tabela a seguir contém um resumo dos registros de DNS necessários para dar suporte à topologia de borda consolidada única exibida na figura Topologia de borda consolidada única. Observe que determinados registros de DNS são necessários apenas para a configuração automática dos clientes do Lync 2013. Se você planeja usar os Objetos de Diretiva de Grupo (GPOs) para configurar os clientes do Lync, os registros associados não são necessários.

## IMPORTANTE: Requisitos do Adaptador de Rede do Servidor de Borda

Para evitar problemas de roteamento, verifique se existem pelo menos dois adaptadores de rede em seu Servidores de Borda e que o gateway padrão é definido apenas no adaptador de rede associado com a interface externa. Por exemplo, como mostrado na figura do Cenário de Borda Consolidada Escalonada no [Borda consolidada em escala, balanceamento de carga de DNS com endereços IP públicos no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-dns-load-balancing-with-public-ip-addresses.md) , o gateway padrão apontaria para o firewall externo.

É possível configurar dois adaptadores de rede em cada um dos Servidores de Borda da seguinte forma:

  - **Adaptador de rede 1 - Nó 1 (Interface Interna)**
    
    Interface interna com 172.25.33.10 atribuído.
    
    Nenhum gateway padrão é definido.
    
    Certifique-se de que existe uma rota a partir da rede contendo a interface interna da Borda para quaisquer redes que contenham servidores executando clientes do Lync Server 2013 ou Lync Server 2013 (por exemplo, de 172.25.33.0 para 192.168.10.0).

  - **Adaptador de rede 1 - Nó 2 (Interface Interna)**
    
    Interface interna com 172.25.33.11 atribuído.
    
    Nenhum gateway padrão é definido.
    
    Certifique-se de que existe uma rota a partir da rede contendo a interface interna da Borda para quaisquer redes que contenham servidores executando clientes do Lync Server 2013 ou Lync Server 2013 (por exemplo, de 172.25.33.0 para 192.168.10.0).

  - **Adaptador de rede 2 Nó 1 (Interface Externa)**
    
    Três endereços IP privados são atribuídos a este adaptador de rede, por exemplo 131.107.155.10 para Serviço de Borda de Acesso, 131.107.155.20 para Serviço de Borda de Webconferência, 131.107.155.30 para Serviço de Borda A/V.
    
    O endereço IP público do Serviço de Borda de Acesso é principal com o gateway padrão definido para o roteador público (131.107.155.1).
    
    Os endereços IP privados do Serviço de Borda de Webconferência e Serviço de Borda A/V são endereços IP adicionais na seção **Avançado** das propriedades do **Internet Protocol Version 4 (TCP/IPv4)** e **Internet Protocol Version 6 (TCP/IPv6)** das **Propriedades de Conexão de Área Local** no Windows Server.
    
    > [!NOTE]  
    > É possível, embora não recomendado, usar um único endereço IP para todas as três interfaces de serviço de Borda. embora isto não salve o endereço IP, exige números de porta diferentes para cada serviço. O número de porta padrão é 443/TCP, que garante que a maioria dos firewalls remotos permita o tráfego. Alterar os valores de porta (por exemplo) 5061/TCP para o Serviço de Borda de Acesso, 444/TCP para o Serviço de Borda de Webconferência e 443/TCP para o Serviço de Borda A/V pode causar problemas para usuários remotos onde um firewall que estão utilizando não permite tráfego por 5061/TCP e 444/TCP. Além disso, três endereços IP diferentes torna a resolução de problemas mais fácil porque podem filtrar no endereço IP.

  - **Adaptador de rede 2 Nó 2 (Interface Externa)**
    
    Três endereços IP privados são atribuídos a este adaptador de rede, por exemplo 131.107.155.11 para Serviço de Borda de Acesso, 131.107.155.21 para Serviço de Borda de Webconferência, 131.107.155.31 para Serviço de Borda A/V.
    
    O endereço IP público do Serviço de Borda de Acesso é principal com o gateway padrão definido para o roteador público (131.107.155.1).
    
    Os endereços IP privados do Serviço de Borda de Webconferência e Serviço de Borda A/V são endereços IP adicionais na seção **Avançado** das propriedades do **Internet Protocol Version 4 (TCP/IPv4)** e **Internet Protocol Version 6 (TCP/IPv6)** das **Propriedades de Conexão de Área Local** no Windows Server.


> [!TIP]
> Configurar o Servidor de Borda com dois adaptadores de rede é uma das duas opções. A outra opção é usar um adaptador de rede para o lado interno e três adaptadores de rede para o lado externo no Servidor de Borda. O principal benefício desta opção é distinguir o adaptador de rede por serviço do Servidor de Borda e potencialmente um conjunto de dados mais conciso quando a resolução de problemas é necessária



### Registros DNS necessários para Borda Consolidada Escalonada, Balanceamento de Carga de DNS com Endereço IP Público (Exemplo)

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
<td><p>131.107.155.10 e 131.107.155.11</p></td>
<td><p>Interface externa do Serviço de Borda de Acesso (Contoso) Repita conforme necessário para todos os domínios SIP com usuários habilitados do Lync</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20 e 131.107.155.21</p></td>
<td><p>Interface externa do Serviço de Borda de Webconferência</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30 e 131.107.155.31</p></td>
<td><p>Serviço de Borda A/Vfea-webconfedge-service</p></td>
</tr>
<tr class="even">
<td><p>DNS/SRV/443 Externa</p></td>
<td><p>_sip._tls.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Interface externa do Serviço de Borda de Acesso. Exigido para configuração automática do cliente do Lync 2013 e Lync 2010 funcionarem externamente. Repita conforme necessário para todos os domínios SIP com usuários habilitados do Lync.</p></td>
</tr>
<tr class="odd">
<td><p>DNS/SRV/5061 Externa</p></td>
<td><p>_sipfederationtls._tcp.contoso.com</p></td>
<td><p>sip.contoso.com</p></td>
<td><p>Interface externa do Serviço de Borda de Acesso. Necessário para descoberta DNS automática de parceiros federados conhecidos como “Domínio SIP Permitido” (chamado de federação avançada nas versões anteriores). Repita conforme necessário para todos os domínios SIP com usuários habilitados do Lync</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10 e 172.25.33.11</p></td>
<td><p>Interface interna da Borda Consolidada</p></td>
</tr>
</tbody>
</table>


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
<td><p>Interface externa do SIP Serviço de Borda de Acesso. Exigido para descoberta DNS automática de sua federação para outros parceiros de federação em potencial e é conhecido como “Domínios SIP Permitidos” (chamado federação avançada em versões anteriores).</p>
<div class="alert">
> [!IMPORTANT]  
> Repita conforme necessário para todos os domínios SIP com usuários habilitados do Lync e clientes do Microsoft Lync Mobile que usam o Serviços de Notificação por Push ou Serviços de Notificação por Push da Apple
</div></td>
</tr>
</tbody>
</table>


## Resumo de DNS - Conectividade pública de mensagem instantânea


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
<td><p>Interface externa do Serviço de Borda de Acesso (Contoso) Repita conforme necessário para todos os domínios SIP com usuários habilitados do Lync</p></td>
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
<td><p>Interface externa do proxy XMPP no Serviço de Borda de Acesso ou Pool de borda. Repita conforme necessário para todos os domínios SIP internos com usuários habilitados do Lync onde o contato com contatos XMPP é permitido através da configuração da Política de Acesso Externo de uma política global, política de site onde o usuário está localizado ou política de usuário aplicada para o usuário habilitado para Lync. Um domínio XMPP permitido também deve ser configurado na política de Parceiros Federados XMPP. Veja os tópicos em <strong>Veja também</strong> para obter detalhes adicionais</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>xmpp.contoso.com (por exemplo)</p></td>
<td><p>Endereço IP de Serviço de Borda de Acesso em seu Servidor de Borda ou Pool de borda hospedando o proxy XMPP</p></td>
<td><p>Aponta para o Serviço de Borda de Acesso ou Pool de borda que hospeda o serviço de proxy XMPP. Normalmente, o registro SRV que você cria aponta para esse registro de host (A ou AAAA)</p></td>
</tr>
</tbody>
</table>

