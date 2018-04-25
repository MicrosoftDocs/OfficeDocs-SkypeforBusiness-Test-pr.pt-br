---
title: Gerenciando o Cliente Lync
TOCTitle: Gerenciando o Cliente Lync
ms:assetid: d1ccc7b6-99ff-4ffd-bd29-9088fb8fe837
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362847(v=OCS.15)
ms:contentKeyID: 56270474
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando o Cliente Lync

 

_**Tópico modificado em:** 2015-06-22_

Os cmdlets a seguir gerenciam o cliente Lync :


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
<td><p><a href="get-csimfilterconfiguration.md">Get-CsImFilterConfiguration</a></p></td>
<td><p>Recupera informações sobre as restrições do URI em uso na sua organização.</p>
<p>Ao enviar mensagens instantâneas, os usuários podem incorporar um URI dentro do texto da mensagem para sugerir a outros participantes da conversa um determinado site ou compartilhamento da Web. Skype for Business Online pode ser configurado para que hiperlinks com certos prefixos sejam bloqueados ou desativados. Isso ajuda a prevenir que os participantes não sejam encaminhados para o site referente ao URI ao clicar no link. Em vez disso, estes devem copiar e colar o link manualmente no navegador.</p></td>
</tr>
<tr class="even">
<td><p><a href="get-cspresencepolicy.md">Get-CsPresencePolicy</a></p></td>
<td><p>Retorna informações sobre dois aspectos importantes da assinatura de presenças: assinantes solicitados e categorias de assinaturas.</p>
<p>Quando se é adicionado à lista de Contatos de alguém, o recebimento de notificação pop-up informando que se foi adicionado àquela lista é o comportamento padrão. Até que se feche o pop-up, cada notificação conta como um assinante solicitado.</p>
<p>As categorias de assinaturas representam uma solicitação para uma categoria de informação específica - por exemplo, um aplicativo que requeira um dado de calendário.</p></td>
</tr>
<tr class="odd">
<td><p><a href="get-csprivacyconfiguration.md">Get-CsPrivacyConfiguration</a><br />
<a href="set-csprivacyconfiguration.md">Set-CsPrivacyConfiguration</a></p></td>
<td><p>Configura valores de privacidade padrão no Skype for Business Online, enquanto ainda dá aos usuários a opção de alteração desses valores.</p>
<p>Skype for Business Online dá aos usuários a oportunidade de compartilhar uma gama de informações de presença com outras pessoas. Os usuários podem publicar uma fotografia de si mesmos, fornecer informações de localização detalhada e disponibilizar automaticamente informações de presença a todas as pessoas da organização (em vez de disponibilizá-las somente para pessoas da lista de Contatos). Os cmdlets <strong>CsPrivacyConfiguration</strong> permitem que os administradores configurem os valores de privacidade padrão em Skype for Business Online, enquanto ainda possibilitam aos usuários alterar esses valores.</p></td>
</tr>
</tbody>
</table>


Você também pode gerenciar um subconjunto de definições de privacidade usando a central administrativa Skype for Business Online :

![Configurações do modo privado de presença do centro de administração do Lync](images/Dn362847.eb206b74-844d-4a7b-b1b3-0cfcb6e3614b(OCS.15).png "Configurações do modo privado de presença do centro de administração do Lync")

## Consulte Também

#### Conceitos

[Os cmdlets do Lync Online](the-skype-for-business-online-cmdlets.md)  
[Referência rápida: usando o Windows PowerShell para realizar tarefas comuns de gerenciamento do Lync Online](quick-reference-using-windows-powershell-to-do-common-skype-for-business-online-management-tasks.md)

