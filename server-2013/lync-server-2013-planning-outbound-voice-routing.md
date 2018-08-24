---
title: 'Lync Server 2013: Planejando roteamento de voz de saída'
TOCTitle: Planejando roteamento de voz de saída
ms:assetid: 37c55fa4-175a-4190-b9e4-c2e5ac7b9261
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425853(v=OCS.15)
ms:contentKeyID: 49306387
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planejando roteamento de voz de saída no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O roteamento de chamadas de saída é aplicado a chamadas destinadas a um gateway PSTN (Rede Telefônica Pública Comutada), tronco ou PBX (central privada de comutação telefônica). Quando um usuário faz uma chamada, o servidor normaliza o número de telefone para o formato E.164, se necessário, e tenta correspondê-lo a um URI do SIP. Se o servidor não conseguir fazer a correspondência, ele aplicará a lógica de roteamento de chamadas de saída baseada na cadeia de caracteres de discagem especificada. Especifique essa lógica definindo as configurações do servidor descritas na tabela a seguir.

### Configurações de roteamento de chamadas de saída do Lync Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Objeto</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Plano de discagem</p></td>
<td><p>Um plano de discagem é um conjunto nomeado de regras de normalização que converte números de telefone de um local nomeado, usuário individual ou objeto de contato em um formato padrão único (E.164) para fins de roteamento de chamadas e autorização.</p></td>
</tr>
<tr class="even">
<td><p>Regra de normalização</p></td>
<td><p>As regras de normalização definem como os números de telefone expressos em vários formatos são roteados para cada local, usuário ou objeto de contato especificado. A mesma cadeia de caracteres de discagem pode ser interpretada e convertida de maneira diferente, conforme o local do qual é discada e da pessoa ou objeto de contato que está fazendo a chamada. Um conjunto de regras de normalização associadas a um local específico constitui um plano de discagem.</p></td>
</tr>
<tr class="odd">
<td><p>Política de voz</p></td>
<td><p>Uma política de voz associa um ou mais registros de uso de PSTN a um usuário ou grupo de usuários. Também fornece uma lista de recursos de chamada que você pode ativar ou desativar.</p></td>
</tr>
<tr class="even">
<td><p>Registro de uso de PSTN</p></td>
<td><p>Um registro de uso de PSTN especifica uma classe de chamada (por exemplo, interna, local ou interurbana) que pode ser feita por vários usuários ou grupos de usuários em uma organização.</p></td>
</tr>
<tr class="odd">
<td><p>Rota de chamada</p></td>
<td><p>Uma rota de chamada associa os números de telefone de destino com troncos específicos e registros de uso de PSTN. Um gateway PSTN é considerado um tronco.</p></td>
</tr>
</tbody>
</table>


## Nesta seção

Esta seção fornece diretrizes para definir as seguintes configurações do servidor de roteamento de chamadas de saída

   [Planos de discagem e regras de normalização no Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md)

   [Políticas de voz no Lync Server 2013](lync-server-2013-voice-policies.md)

   [Registros de uso de PSTN no Lync Server 2013](lync-server-2013-pstn-usage-records.md)

   [Rotas de voz no Lync Server 2013](lync-server-2013-voice-routes.md)

## Consulte Também

#### Conceitos

[Tronco SIP no Lync Server 2013](lync-server-2013-sip-trunking.md)  
[Conexões SIP diretas no Lync Server 2013](lync-server-2013-direct-sip-connections.md)

