---
title: 'Lync Server 2013: DNS summary - Resumo de DNS - borda consolidada em escala com balanceadores de carga de hardware'
TOCTitle: Resumo de DNS - borda consolidada em escala com balanceadores de carga de hardware
ms:assetid: 8453297c-da1d-4b9e-a37e-6721458c6feb
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398670(v=OCS.15)
ms:contentKeyID: 49307330
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Resumo de DNS - borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os requisitos do registro DNS para acesso remoto ao Lync Server 2013 são bastante simples, comparados àqueles para certificados e portas. Além disso, muitos registros são opcionais, dependendo de como os clientes executando o Lync 2013 são configurados e se a federação está habilitada.

Para detalhes sobre os requisitos de DNS do Lync 2013, consulte [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

Para obter detalhes sobre como realizar a configuração automática dos clientes do Lync 2013 se um DNS split-brain não estiver configurado, consulte a seção "Configuração automática sem DNS split-brain" [Determinar requisitios de DNS para Lync Server 2013](lync-server-2013-determine-dns-requirements.md).

A tabela a seguir contém um resumo dos registros DNS necessários para oferecer suporte à Topologia de borda consolidada dimensionada (balanceamento de carga de hardware). Observe que determinados registros DNS são necessários somente para a configuração automática dos clientes de Lync. Se planejar usar objetos de política de grupo (GPOs) para configurar os clientes de Lync, os registros associados não serão necessários.

## IMPORTANTE: Requisitos do Adaptador de Rede do Servidor de Borda

Para evitar problemas de roteamento, verifique se há pelo menos dois adaptadores de rede em seu Servidores de Borda e se o gateway padrão foi configurado apenas no adaptador de rede associado à interface externa. Por exemplo, como mostrado na figura de Cenário da Borda Consolidada em Escala em [Borda consolidada em escala com balanceadores de carga de hardware no Lync Server 2013](lync-server-2013-scaled-consolidated-edge-with-hardware-load-balancers.md), o gateway padrão apontará para o firewall externo.

É possível configurar dois adaptadores de rede em cada um dos Servidores de Borda da seguinte forma:

  - **Adaptador de rede 1 (Interface Interna)**
    
    Interface interna com 172.25.33.10 atribuído.
    
    Nenhum gateway padrão.
    
    Verifique se há uma rota da rede que contém a interface interna de Servidor de Borda para as redes que contêm clientes ou servidores do Lync Server que executam o Lync Server (por exemplo, de 172.25.33.0 a 192.168.10.0).

  - **Adaptador de rede 2 (Interface Externa)**
    
    Três endereços IP públicos são designados a este adaptador de rede, por exemplo, 131.107.155.10 para Serviço de Borda de Acesso, 131.107.155.20 para Serviço de Borda de Webconferência e 131.107.155.30 para Serviço de Borda A/V.
    
    > [!NOTE]  
    > Os endereços IP que estão atribuídos às interfaces de rede externas atuais do Servidor de Borda podem depender de qual balanceador de carga de hardware você escolheu. Consulte a documentação do seu balanceador de carga de hardware para entender os requisitos do endereço IP atual.<br />    É possível, embora não recomendado, usar um único endereço IP para todas as três interfaces de serviço de Borda. embora isto não salve o endereço IP, exige números de porta diferentes para cada serviço. O número de porta padrão é 443/TCP, que garante que a maioria dos firewalls remotos permita o tráfego. Alterar os valores de porta (por exemplo) 5061/TCP para o Serviço de Borda de Acesso, 444/TCP para o Serviço de Borda de Webconferência e 443/TCP para o Serviço de Borda A/V pode causar problemas para usuários remotos onde um firewall que estão utilizando não permite tráfego por 5061/TCP e 444/TCP. Além disso, três endereços IP diferentes torna a resolução de problemas mais fácil porque podem filtrar no endereço IP.    
    O endereço IP de Serviço de Borda de Acesso é primário com o gateway padrão definido para o roteador voltado para a Internet (131.107.155.1).
    
    Endereços IP de Serviço de Borda de Webconferência e Serviço de Borda A/V secundários.


> [!TIP]
> Configurar o Servidor de Borda com dois adaptadores de rede é uma das duas opções. A outra opção é usar um adaptador de rede para o lado interno e três adaptadores de rede para o lado externo no Servidor de Borda. O principal benefício desta opção é distinguir o adaptador de rede por serviço do Servidor de Borda e potencialmente um conjunto de dados mais conciso quando a resolução de problemas é necessária



### Registros DNS necessários para borda consolidada dimensionada com balanceamento de carga de hardware (exemplo)

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
<td><p>Interface externa do Serviço de Borda de Acesso (Contoso). Repita conforme necessário para todos os domínios SIP com usuários Lync habilitados</p></td>
</tr>
<tr class="even">
<td><p>DNS/A externo</p></td>
<td><p>webcon.contoso.com</p></td>
<td><p>131.107.155.20</p></td>
<td><p>Interface externa do Serviço de Borda de Webconferência</p></td>
</tr>
<tr class="odd">
<td><p>DNS/A externo</p></td>
<td><p>av.contoso.com</p></td>
<td><p>131.107.155.30</p></td>
<td><p>Interface externa Serviço de Borda A/V</p></td>
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
<td><p>Interface externa do SIP Serviço de Borda de Acesso, necessária para a descoberta de DNS automática de parceiros federados conhecidos como “Domínio SIP permitido” (chamada de federação aprimorada em versões anteriores). Repita conforme necessário para todos os domínios SIP com usuários Lync habilitados e clientes Microsoft Lync Mobile que usem o serviço Serviços de Notificação por Push ou o Serviços de Notificação por Push da Apple.</p></td>
</tr>
<tr class="even">
<td><p>DNS/A interno</p></td>
<td><p>lsedge.contoso.net</p></td>
<td><p>172.25.33.10</p></td>
<td><p>Interface interna da Borda Consolidada</p></td>
</tr>
</tbody>
</table>

