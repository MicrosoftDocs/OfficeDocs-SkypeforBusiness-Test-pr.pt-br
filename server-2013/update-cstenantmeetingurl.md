---
title: Update-CsTenantMeetingUrl
TOCTitle: Update-CsTenantMeetingUrl
ms:assetid: 9aed3ede-bbd3-405a-997f-f7553e66aecd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn424754(v=OCS.15)
ms:contentKeyID: 59602782
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Update-CsTenantMeetingUrl

 

_**Tópico modificado em:** 2015-03-09_

Atualiza a URL da reunião para o inquilino do Skype for Business Online especificado. A URL atualizada usa um formato mais simples e mais padronizado que torna mais fácil para os clientes localizar e conectar-se a reuniões.

Este cmdlet é destinado para uso somente com Skype for Business Online.

## Sintaxe

    Update-CsTenantMeetingUrl [-Tenant] <guid> [-Force] [-WhatIf] [-Confirm]

## Exemplos

## Exemplo 1

O comando mostrado no Exemplo 1 atualiza a URL da reunião para o inquilino com o ID inquilino 38aad667-af54-4397-AAA7-e94c79ec2308. (Observe que você deve fornecer a ID de inquilino para que este comando seja concluído.) Após pressionar ENTER para executar o comando, lhe será perguntado se tem certeza de que deseja atualizar a URL da reunião. Você deve responder sim a esta prompt antes que Update-CsTenantMeetingUrl realmente faça quaisquer alterações nas suas definições de configurações do Skype for Business Online.

    Update-CsTenantMeetingUrl -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308"

## Exemplo 2

Exemplo 2 também atualiza a URL da reunião para o inquilino com o ID de inquilino 38aad667-af54-4397-AAA7-e94c79ec2308. Neste caso, porém, o parâmetro Force está incluído; isso evita o prompt de confirmação que normalmente aparece quando você executa o Update-CsTenantMeetingUrl. Neste caso, assim que você pressionar Enter, o comando será executado e suas definições de configuração do Skype for Business Online serão modificadas.

    Update-CsTenantMeetingUrl -Tenant "38aad667-af54-4397-aaa7-e94c79ec2308" -Force

## Descrição Detalhada

O Update-CsTenantMeetingUrl atualiza a URL de reunião do Skype for Business Online para um formato mais simples e padronizado; o que ajuda a eliminar problemas que ocasionalmente ocorreram com a URL de reunião original. Por exemplo, suponha que uma organização estabeleça um domínio do Office 365 com o nome contoso.onmicrosoft.com. Quando eles o fizerem, as reuniões terão URLs similares a este:

https://meet.lync.com/onmicrosoft/contoso/user1/45GZFH99

Agora, suponha que a organização passe por algumas alterações e decida usar a URL intuitiva" litwareinc.com em vez da URL onmicrosoft.com. A organização modifica seus endereços de email para usar o domínio litwareinc.com. No entanto, as URLs da reunião ainda usarão o antigo nome de domínio:

https://meet.lync.com/contoso/user1/45GZFH99

Para corrigir esse problema, os administradores devem executar o cmdlet Update-CsTenantMeetingUrl. Isso irá substituir a antiga URL da reunião pela nova, que contém a URL intuitiva:

https://meet.lync.com/litwareinc.com/user1/37JYLP71

Executar o cmdlet Update-CsTenantMeetingUrl é a única maneira de fazer essa alteração.

Observe que, quando você executar Update-CsTenantMeetingUrl, seu locatário do Skype for Business Online mudará para a nova URL após um pequeno atraso de sincronização. Isso não criará problemas para novas reuniões que os usuários venham a agendar: essas reuniões serão automaticamente agendadas usando a nova URL após um curto atraso da sincronização. No entanto, as reuniões previamente agendadas terão problemas, porque elas foram agendadas usando a URL antiga, desativada. A única maneira de resolver esse problema é fazer com que seus usuários reagendem essas reuniões

Como isso poderia criar problemas em algumas organizações (principalmente em organizações onde um grande número de reuniões já foram agendadas), por padrão o Update-CsTenantMeetingUrl exibirá uma mensagem antes de realmente atualizar a URL da reunião:

AVISO: Esta é uma alteração significativa para os usuários nesta inquilino. A configuração da URL de reunião será atualizada\! As URLs de reunião antigas deixarão de funcionar. Esta alteração não pode ser revertida.  
Tem certeza de que deseja continuar?  
\[Y\] Sim \[A\] Sim para todos \[N\] Não \[L\] Não para todos \[S\] Suspender \[?\] Ajuda (o padrão é “Y”):

Você deve responder "Sim" ou "Sim para todos" antes que o comando seja executado; se você responder "não", então o comando será cancelado e a URL da reunião não será atualizada. Tenha em mente que uma vez alterada a URL da reunião, não há mais como reverter para a URL original. Uma vez que o comando for executado, a URL será alterada e todas as reuniões previamente agendadas terão de ser remarcadas. Isto também significa que você só precisa executar este comando uma vez por inquilino. Não há necessidade de executar periodicamente o comando e atualizar novamente a URL da reunião.

Se você preferir executar o comando sem ter que ver o prompt de confirmação, inclua o parâmetro Force. Nesse caso, Update-CsTenantMeetingUrl será executado sem exibir o prompt de confirmação:

AVISO: Esta é uma alteração significativa para os usuários neste inquilino. A configuração da URL de reunião será atualizada\!

## Parâmetros


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Parâmetro</th>
<th>Obrigatório</th>
<th>Tipo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Tenant</strong></p></td>
<td><p>Obrigatório</p></td>
<td><p>System.Guid</p></td>
<td><p>Identificador global exclusivo (GUID) da conta do inquilino cujas configurações de federação estão sendo retornadas. Por exemplo:</p>
<p>–Tenant &quot;38aad667-af54-4397-aaa7-e94c79ec2308&quot;</p>
<p>É possível retornar o ID do locatário para cada um de seus locatários, executando este comando:</p>
<p>Get-CsTenant | Select-Object DisplayName, TenantID</p>
<p>Se você não incluir o parâmetro Tenant, o Update-CsMeetingUrl pedirá que você insira esse parâmetro antes de continuar.</p></td>
</tr>
<tr class="even">
<td><p><strong>Confirm</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p>
<p>Observe que o comportamento padrão do Update-CsMeetingUrl é exibir o prompt de confirmação antes de fazer qualquer atualização. Isso significa que, se você quiser exibir o prompt de confirmação, não precisa incluir o parâmetro Confirm.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Force</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição do prompt de confirmação que apareceria antes de o Update-CsMeetingUrl fazer uma atualização.</p></td>
</tr>
<tr class="even">
<td><p><strong>WhatIf</strong></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de Entrada

Nenhum. O Update-CsMeetingUrl não aceita entrada por pipeline.

## Tipos de Retorno

Nenhum.

## Consulte Também

#### Outros Recursos

[Get-CsSimpleUrlConfiguration](get-cssimpleurlconfiguration.md)

