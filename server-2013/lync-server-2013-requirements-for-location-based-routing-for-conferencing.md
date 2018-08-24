---
title: Requisitos do roteamento baseado em localização para conferência
TOCTitle: Requisitos do roteamento baseado em localização para conferência
ms:assetid: 766d9286-2c34-4faf-bb3e-f0ca478a70cf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362806(v=OCS.15)
ms:contentKeyID: 56270433
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos do roteamento baseado em localização para conferência

 

_**Tópico modificado em:** 2016-12-08_

Veja a seguir os requisitos necessários para a instalação e configuração do aplicativo de Conferência de Roteamento com Base no Local:

  - A Atualização Cumulativa 2 do Lync Server 2013 deve ser implantada em todos os servidores ou pools da sua topologia.

> [!NOTE]  
> Se um servidor ou pool do Lync não tiver a Atualização Cumulativa 2 ou superior do Lync Server 2013 instalada, não será possível garantir a imposição do Roteamento com Base no Local das reuniões do Lync.

  - O Roteamento com Base no Local do Lync Server 2013 é um pré-requisito para o aplicativo de Conferência de Roteamento com Base no Local. Para obter mais informações sobre como configurar o Roteamento com Base no Local do Lync Server 2013, consulte [Configurando o Roteamento com Base no Local](lync-server-2013-configuring-location-based-routing.md).

  - Os requisitos do aplicativo de Conferência de Roteamento com Base no Local são os mesmos requisitos para o Roteamento com Base no Local do Lync Server 2013. para obter mais informações, consulte [Planejamento para o Roteamento com Base no Local](lync-server-2013-planning-for-location-based-routing.md).

## Servidores com suporte

O aplicativo de Conferência de Roteamento com Base no Local requer que a Atualização Cumulativa 2 do Lync Server 2013 seja implantada em todos os Pools de Front-Ends e servidores Standard Edition em sua topologia. Se a Atualização Cumulativa 2 do Lync Server 2013 não estiver instalada em alguns Lync Servers em sua topologia, as restrições do Roteamento com Base no Local não poderão ser completamente impostas em reuniões do Lync e transferências de chamada consultivas.

A tabela a seguir identifica a combinação de funções de servidor e versões que dão suporte ao Roteamento com Base no Local.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Versão do Pool de Front-End</p></td>
<td><p>Versão do Servidor de Mediação</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="even">
<td><p>Atualização Cumulativa 2 do Lync Server 2013</p></td>
<td><p>Atualização Cumulativa 2 do Lync Server 2013</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="odd">
<td><p>Atualização Cumulativa 2 do Lync Server 2013</p></td>
<td><p>Atualização Cumulativa 1 do Lync Server 2013</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Atualização Cumulativa 2 do Lync Server 2013</p></td>
<td><p>Lync Server 2010</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Atualização Cumulativa 2 do Lync Server 2013</p></td>
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Atualização Cumulativa 1 do Lync Server 2013</p></td>
<td><p>Qualquer</p></td>
<td><p>Não</p></td>
</tr>
<tr class="odd">
<td><p>Lync Server 2010</p></td>
<td><p>Qualquer</p></td>
<td><p>Não</p></td>
</tr>
<tr class="even">
<td><p>Office Communications Server 2007 R2</p></td>
<td><p>Qualquer</p></td>
<td><p>Não</p></td>
</tr>
</tbody>
</table>


## Clientes com suporte

Os clientes do Lync que dão suporte ao Roteamento com Base no Local das reuniões do Lync são os mesmos clientes que dão suporte ao Roteamento com Base no Local do Lync Server 2013. Para obter mais informações, consulte [Suporte ao servidor e cliente do Roteamento com Base no Local](lync-server-2013-client-and-server-support-for-location-based-routing.md).

## Requisitos do Servidor de Mediação para transferências de chamada consultivas

O aplicativo de Conferência de Roteamento com Base no Local requer a implantação de Servidores de Mediação autônomos para impor as restrições do Roteamento com Base no Local em transferências de chamada consultivas.

Para impor o Roteamento com Base no Local de transferências de chamada consultivas, o Servidor de Mediação deve ser associado a apenas um par de Servidor de Mediação (ou seja, PBX, gateway SIP etc.) em regiões da rede onde o Roteamento com Base no Local seja necessário. Se pares adicionais de Servidor de Mediação forem implantados na mesma região da rede, o par de Servidor de Mediação deverá ser associado a outro Servidor de Mediação. Esse requisito é detalhado da seguinte forma:

  - Um único Servidor de Mediação por vários pares de Servidor de Mediação Quando uma transferência de chamada consultiva é roteada para um par de Servidor de Mediação por meio de um Servidor de Mediação configurado com vários troncos SIP para vários pares (ou seja, PBXs e gateways), a transferência de chamada consultiva é bloqueada para impedir o bypass de chamadas tarifadas PSTN se a transferência de chamada consultiva é permitida por meio de alguns trunks SIP, mas não permitida por meio de outros troncos SIP.
    
    Por exemplo, no caso de um único Servidor de Mediação servindo um Par de Servidor de Mediação de Gateway PSTN e um Par de Servidor de Mediação PBX, o seguinte comportamento será observado:
    
      - Quando um usuário do Lync de um determinado site (ou seja, site 1) tentar transferir uma chamada com um ponto de extremidade PSTN para um usuário do Lync de outro site (ou seja, site 2) por meio de transferência consultiva, a chamada não será permitida para impedir o bypass de chamadas tarifadas PSTN.
    
      - Quando um usuário do Lync de um determinado site (ou seja, site 1) tentar transferir uma chamada com um ponto de extremidade PSTN para um usuário do Lync de outro site (ou seja, site 2) por meio de transferência consultiva, a chamada não será permitida mesmo se não implicar o possível bypass de chamadas tarifadas PSTN.

  - Servidores de Mediação separados por par de Servidor de Mediação
    
    Quando uma transferência consultiva for direcionada para um Par de Servidor de Mediação, ela será avaliada em relação ao único Par de Servidor de Mediação servido pelo Servidor de Mediação. A chamada será permitida ou não com base em seu potencial em implicar um bypass de chamadas tarifadas PSTN, independentemente de todos os outros Pares de Servidor de Mediação no site, pois eles são servidos por Servidores de Mediação separados.
    
    Por exemplo, no caso de um Servidor de Mediação separado servindo um Par de Servidor de Mediação de Gateway PSTN e um Par de Servidor de Mediação PBX, o seguinte comportamento será observado:
    
      - Quando um usuário do Lync de um determinado site (ou seja, site 1) tentar transferir uma chamada com um ponto de extremidade PSTN para um usuário do Lync de outro site (ou seja, site 2) por meio de transferência consultiva, a chamada não será permitida para evitar o bypass de chamadas tarifadas PSTN.
    
      - Quando um usuário do Lync de um determinado site (ou seja, site 1) tentar transferir uma chamada com um ponto de extremidade PBX no mesmo site (site 1) para um usuário do Lync de outro site (ou seja, site 2) por meio de transferência consultiva, a chamada será permitida, pois não implica o possível bypass de chamadas tarifadas PSTN.

## Recursos sem suporte no aplicativo de Conferência de Roteamento com Base no Local

Os seguintes recursos não têm suporte no aplicativo de Conferência de Roteamento com Base no Local:

  - Conferência discada. Não é possível impor o Roteamento com Base no Local para conferência discada. Qualquer solicitação discada para uma determinada conferência não será restrita pelo Roteamento com Base no Local, mesmo se o organizador da conferência for um usuário do Lync habilitado para Roteamento com Base no Local.

  - É recomendável não provisionar números de acesso a conferência em regiões onde seja necessário impor restrições de Roteamento com Base no Local.

