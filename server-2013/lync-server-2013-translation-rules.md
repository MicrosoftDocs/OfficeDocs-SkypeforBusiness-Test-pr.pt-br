---
title: 'Lync Server 2013: Regras de tradução'
TOCTitle: Regras de tradução
ms:assetid: 6e067bd4-4931-4385-81ac-2acae45a16d8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398520(v=OCS.15)
ms:contentKeyID: 49307042
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Regras de tradução no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O Lync Server 2013Enterprise Voice exige que todas as cadeias de caracteres de discagem sejam normalizadas no formato E.164 para fins de execução de pesquisa de número reverso (RNL). No Microsoft Lync Server 2010, as regras de conversão são compatíveis apenas com números chamados. Novas no Microsoft Lync Server 2013, as regras de conversão também são compatíveis com números de chamada. O *par de tronco* (isto é, o troco de gateway, PBX ou SIP associado) pode exigir que os números estejam no formato de discagem local. Para converter os números do formato E.164 em um formato de discagem local, você pode definir uma ou mais regras de conversão para manipular a URI da solicitação antes de roteá-la para o ponto do tronco. Por exemplo, é possível elaborar uma regra de conversão para remover o +44 do início de uma cadeia de caracteres de discagem e substituí-lo por 0144.

Executando a conversão da rota de saída no servidor, você pode reduzir os requisitos de configuração em cada par de tronco individual para converter os números de telefone em um formato de discagem. Ao planejar quais e quantos gateways serão associados a um determinado cluster do Servidor de Mediação, poderá ser útil para os pares de tronco de grupo com requisitos semelhantes de discagem. Isso pode reduzir o número de regras de conversão necessárias e o tempo necessário para gravá-las.

> [!IMPORTANT]  
> A associação de uma ou mais regras de conversão com a uma configuração de tronco do Enterprise Voice deve ser usada como uma alternativa para configurar regras de conversão no ponto de tronco. Não associe as regras de conversão a uma configuração de tronco do Enterprise Voice se você tiver configurado regras de conversão no par de tronco, porque as duas regras podem entrar em conflito.

## Exemplo de regras de conversão

Os exemplos a seguir de regras de conversão mostram como você pode desenvolver as regras no servidor para converter números do formato E.164 para um formato local para o par de tronco.

Para obter detalhes sobre como implementar as regras de conversão, consulte [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação de Implantação.


<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Dígitos iniciais</th>
<th>Comprimento</th>
<th>Dígitos a serem removidos</th>
<th>Dígitos a serem adicionados</th>
<th>Padrão de correspondência</th>
<th>Tradução</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Discagem convencional de longa distância nos EUA</p>
<p>(retirar o '+')</p></td>
<td><p>+1</p></td>
<td><p>Exatamente 12</p></td>
<td><p>1</p></td>
<td><p>0</p></td>
<td><p>^\+(1\d{10})$</p></td>
<td><p>$1</p></td>
<td><p>+14255551010 se torna 14255551010</p></td>
</tr>
<tr class="even">
<td><p>Discagem de longa distância internacional dos EUA</p>
<p>(retirar '+' e adicionar 011)</p></td>
<td><p>+</p></td>
<td><p>Pelo menos 11</p></td>
<td><p>1</p></td>
<td><p>011</p></td>
<td><p>^\+(\d{9}\d+)$</p></td>
<td><p>011$1</p></td>
<td><p>+441235551010 se torna 011441235551010</p></td>
</tr>
</tbody>
</table>

