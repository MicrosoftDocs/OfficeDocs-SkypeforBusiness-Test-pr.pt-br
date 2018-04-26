---
title: 'Lync Server 2013: Configurando uma rota de failover'
TOCTitle: Configurando uma rota de failover
ms:assetid: 76e48df4-3b78-4fb7-b1f7-c1e604b81bad
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398581(v=OCS.15)
ms:contentKeyID: 49307155
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando uma rota de failover no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

O exemplo abaixo mostra como um administrador pode definir uma rota de failover para utilizar se o Dallas-GW1 for desativado para manutenção ou estiver indisponível por qualquer outro motivo. As seguintes tabelas ilustram a alteração de configuração necessária.

### Tabela 1. Política de usuário

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Política de usuário</th>
<th>Uso do telefone</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Política de Chamada Padrão</p></td>
<td><p>Local</p>
<p>GlobalPSTNHopoff</p></td>
</tr>
<tr class="even">
<td><p>Política Local de Redmond</p></td>
<td><p>RedmondLocal</p></td>
</tr>
<tr class="odd">
<td><p>Política de Chamada de Dallas</p></td>
<td><p>DallasUsers</p>
<p>GlobalPSTNHopoff</p></td>
</tr>
</tbody>
</table>


### Tabela 2. Rotas

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
<th>Nome da rota</th>
<th>Padrão do número</th>
<th>Uso do telefone</th>
<th>Tronco</th>
<th>Gateway</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rota Local de Redmond</p></td>
<td><p>^\+1(425|206|253)(\d{7})$</p></td>
<td><p>Local</p>
<p>RedmondLocal</p></td>
<td><p>Tronco 1</p>
<p>Tronco 2</p></td>
<td><p>Red-GW1</p>
<p>Red-GW2</p></td>
</tr>
<tr class="even">
<td><p>Rota Local de Dallas</p></td>
<td><p>^\+1(972|214|469)(\d{7})$</p></td>
<td><p>Local</p></td>
<td><p>Tronco 3</p></td>
<td><p>Dallas-GW1</p></td>
</tr>
<tr class="odd">
<td><p>Rota Universal</p></td>
<td><p>^\+?(\d*)$</p></td>
<td><p>GlobalPSTNHopoff</p></td>
<td><p>Tronco 1</p>
<p>Tronco 2</p>
<p>Tronco 3</p></td>
<td><p>Red-GW1</p>
<p>Red-GW2</p>
<p>Dallas-GW1</p></td>
</tr>
<tr class="even">
<td><p>Rota de Usuários de Dallas</p></td>
<td><p>^\+?(\d*)$</p></td>
<td><p>DallasUsers</p></td>
<td><p>Tronco 3</p></td>
<td><p>Dallas-GW1</p></td>
</tr>
</tbody>
</table>


Na tabela 1, um uso de telefone de GlobalPSTNHopoff é adicionado após o uso de telefone DallasUsers na Política de Chamada de Dallas. Isso permite que as chamadas com a política de chamada de Dallas usem rotas configuradas para o uso de telefone GlobalPSTNHopoff, caso uma rota para o uso do telefone DallasUsers não esteja disponível.

