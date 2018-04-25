---
title: Gerenciando comunicações com usuários e organizações externos
TOCTitle: Gerenciando comunicações com usuários e organizações externos
ms:assetid: 8a64f0fe-1e79-47d8-835e-548d7ac0757e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362813(v=OCS.15)
ms:contentKeyID: 56270440
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando comunicações com usuários e organizações externos

 

_**Tópico modificado em:** 2015-06-22_

Os seguintes cmdlets podem ser usados para gerenciar a federação com domínios externos e com provedores públicos de mensagens instantâneas:


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlet</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="new-csedgeallowallknowndomains.md">New-CsEdgeAllowAllKnownDomains</a></p></td>
<td><p>Permite que os usuários se comuniquem com todos os domínios, com exceção dos especificados na lista de domínios bloqueados.</p>
<p>Federação é um serviço que permite aos usuários trocar informações de presença e mensagens instantâneas com usuários de outros domínios. Em geral, os administradores usam listas de domínios permitidos e bloqueados para especificar os domínios externos com os quais os usuários podem se comunicar.</p></td>
</tr>
<tr class="even">
<td><p><a href="new-csedgeallowlist.md">New-CsEdgeAllowList</a></p></td>
<td><p>Limita a comunicação do usuário a um conjunto especificado de domínios.</p>
<p>Os usuários têm permissão de se comunicar apenas com domínios que aparecem na lista de domínios permitidos.</p></td>
</tr>
<tr class="odd">
<td><p><a href="new-csedgedomainpattern.md">New-CsEdgeDomainPattern</a></p></td>
<td><p>Modifica as listas de domínios permitidos ou bloqueados.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cstenantfederationconfiguration.md">Get-CsTenantFederationConfiguration</a><br />
<a href="set-cstenantfederationconfiguration.md">Set-CsTenantFederationConfiguration</a></p></td>
<td><p>Habilita e desabilita a federação com outros domínios e a federação com provedores públicos.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-cstenanthybridconfiguration.md">Get-CsTenantHybridConfiguration</a><br />
<a href="set-cstenanthybridconfiguration.md">Set-CsTenantHybridConfiguration</a></p></td>
<td><p>Atribui os valores apropriados a definições de configuração híbridas.</p>
<p>Em uma implantação híbrida ou de &quot;domínio dividido&quot;, uma organização tem alguns usuários com contas hospedadas no Skype for Business Online e tem, simultaneamente, outros usuários com contas hospedadas no Lync Server 2013. Por padrão, os usuários hospedados no Skype for Business Online não têm acesso à gama completa de recursos oferecida pelo Enterprise Voice. Para fornecer acesso a esses recursos do Enterprise Voice aos usuários do Skype for Business Online, os administradores precisam atribuir os valores apropriados às definições de configuração híbridas. Esses valores podem ser gerenciados apenas usando os cmdlets <strong>CsTenantHybridConfiguration</strong>.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cstenantpublicprovider.md">Get-CsTenantPublicProvider</a><br />
<a href="set-cstenantpublicprovider.md">Set-CsTenantPublicProvider</a></p></td>
<td><p>Gerencia a federação com provedores públicos.</p>
<p>Provedores públicos são organizações que fornecem serviços de comunicação SIP para o público geral. Quando você estabelece uma relação de federação com um provedor público, estabelece efetivamente a federação com qualquer usuário que tenha uma conta hospedada por esse provedor.</p></td>
</tr>
</tbody>
</table>


Você também pode gerenciar configurações de federação, tanto para domínios federados quanto para provedores públicos, usando o centro de administração do Skype for Business Online:

![Configurações de organização do centro de administração do Lync Online](images/Dn362813.f860d03f-5906-49b0-bcc7-7634afe7005e(OCS.15).png "Configurações de organização do centro de administração do Lync Online")

## Consulte Também

#### Conceitos

[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)  
[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

