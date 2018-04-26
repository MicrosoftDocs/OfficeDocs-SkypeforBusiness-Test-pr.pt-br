---
title: Remove-CsClientVersionConfiguration
TOCTitle: Remove-CsClientVersionConfiguration
ms:assetid: 42065d1d-a0ef-4fa4-826b-d65b14b343c9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425925(v=OCS.15)
ms:contentKeyID: 49306523
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsClientVersionConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Remove a coleção especificada de definições de configuração da versão do cliente. As definições de configuração de versão do cliente determinam se o Lync Server verifica ou não o número da versão de cada aplicativo cliente que se registra no sistema. Se a filtragem da versão do cliente for habilitada, a habilidade desse aplicativo cliente de acessar o sistema terá como base as definições configuradas na política relevante de versão do cliente. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsClientVersionConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando apresentado no Exemplo 1 exclui as definições de configuração da versão do cliente que tiverem a identidade "site:Redmond".

    Remove-CsClientVersionConfiguration -Identity site:Redmond

## EXEMPLO 2

No Exemplo 2, serão excluídas todas as definições de configuração da versão do cliente que tiverem sido aplicadas no escopo de site. Para realizar essa tarefa, o comando chama primeiramente o cmdlet **Get-CsClientVersionConfiguration** e o parâmetro -Filter. O valor de filtro "site:\*" garante que apenas as definições de configuração da versão do cliente que tiverem a identidade iniciada pelo valor da cadeia de caracteres "site:" serão retornadas. Em seguida, essa coleção filtrada é redirecionada para o cmdlet **Remove-CsClientVersionConfiguration**, que exclui cada item da coleção.

    Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration

## EXEMPLO 3

No Exemplo 3, serão excluídas todas as definições de configuração de versão cliente que estiverem desabilitadas. Para fazer isso, o comando usa primeiramente o cmdlet **Get-CsClientVersionConfiguration**, retornando uma coleção de todas as definições de configuração de versão cliente em uso na organização. Depois que esses dados forem retornados, a coleção será canalizada para o cmdlet **Where-Object**, que selecionará somente as configurações cuja propriedade Enable for igual a False. A partir daí, a coleção filtrada será canalizada para **Remove-CsClientVersionConfiguration**, que excluirá cada item na coleção.

    Get-CsClientVersionConfiguration | Where-Object {$_.Enabled -eq $False} | Remove-CsClientVersionConfiguration

## Descrição detalhada

O Lync Server fornece aos administradores uma margem de manobra considerável na especificação do software cliente (e, igualmente importante, no número de versão do software) que os usuários podem utilizar para efetuar o registro no sistema. Por exemplo, não há razão técnica que exija dos usuários o registro no Lync Server utilizando o Lync; do ponto de vista técnico, não há nada que impeça as pessoas de efetuarem o registro no sistema utilizando o Microsoft Office Communicator 2007 R2.

No entanto, é possível que haja alguns motivos não-técnicos pelos quais você prefira que seus usuários não se registrem usando Office Communicator 2007 R2. Por exemplo, o Office Communicator 2007 R2 não oferece apoio a todos os recursos e capacidades encontradas no Lync. Consequentemente, os usuários que efetuarem o registro com o Office Communicator 2007 R2 terão experiência diferente da de usuários que efetuarem o registro utilizando o Lync. Isto pode criar dificuldades para os usuários e também para os funcionários da assistência técnica, que deverão fornecer suporte para alguns aplicativos cliente diferentes.

Se criar problemas para sua organização, é possível implementar um filtro de versão do cliente que especifique quais aplicativos cliente poderão ser utilizados para efetuar o registro no Lync Server. Ao se instalar o Lync Server, será instalado e habilitado um conjunto global de definições de configuração de versão cliente. Além das definições globais, as definições de configuração de versão do cliente também podem ser aplicadas no escopo do site.

Quaisquer definições de site que forem criadas poderão ser posteriormente excluídas utilizando-se o cmdlet **Remove-CsClientVersionConfiguration**. Observe que também é possível executar o cmdlet **Remove-CsClientVersionConfiguration** concomitantemente às definições globais. Neste caso, essas definições não serão removidas. Em vez disso, as propriedades globais reassumirão os seus valores padrão.

Quem pode executar esse cmdlet: Por padrão, membros dos seguintes grupos são autorizados a executar o cmdlet **Remove-CsClientVersionConfiguration** localmente: RTCUniversalServerAdmins. Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsClientVersionConfiguration"}

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
<td><p><em>Identity</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Identificador exclusivo da coleção de definições de configuração da versão do cliente a ser removida. Para remover a coleção global, use a seguinte sintaxe: -Identity global (tenha em mente que as definições globais não serão removidas. Em vez disso, as propriedades globais serão redefinidas com os seus valores padrão.) Para remover uma coleção de site, utilize uma sintaxe similar a esta: -Identity site:Redmond. Observe que não é possível utilizar caracteres curinga ao se especificar a identidade.</p></td>
</tr>
<tr class="even">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Objeto Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration. O cmdlet **Remove-CsClientVersionConfiguration** aceita instâncias canalizadas do objeto de configuração de versão do cliente.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet exclui instâncias do objeto Microsoft.Rtc.Management.WritableConfig.Policy.ClientVersion.ClientVersionConfiguration.

## Consulte Também

#### Outros Recursos

[Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md)  
[New-CsClientVersionConfiguration](new-csclientversionconfiguration.md)  
[Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md)

