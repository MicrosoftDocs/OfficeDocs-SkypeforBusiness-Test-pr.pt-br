---
title: Disable-CsComputer
TOCTitle: Disable-CsComputer
ms:assetid: e64128f1-2b53-4569-bf37-90cbbba01b36
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399023(v=OCS.15)
ms:contentKeyID: 49308430
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Disable-CsComputer

 

_**Tópico modificado em:** 2015-03-09_

Desabilita um serviço ou uma função de servidor que tiver sido removida de um computador que executa o Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Disable-CsComputer [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-Scorch <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 desabilita o computador local.

    Disable-CsComputer 

## EXEMPLO 2

O comando exibido no Exemplo 2 também desabilita o computador local. No entanto, além de desabilitar o computador, esse comando também registra informações sobre o sucesso (ou falha) dessa tarefa no arquivo C:\\Logs\\Disable.html. Esse arquivo de registro é gerado adicionando-se o parâmetro Report, seguido do caminho do arquivo de registro no qual se deseja gravar as informações.

    Disable-CsComputer -Report C:\Logs\Disable.html

## Descrição detalhada

A remoção de um serviço ou função de servidor de um computador não atualiza automaticamente a topologia do Lync Server. Em vez disso, esse serviço ou função deve ser desativado antes que as alterações sejam atualizadas completamente na topologia. O cmdlet **Disable-CsComputer** permite aos administradores desabilitar qualquer serviço ou função de servidor que tiver sido removido do computador local.

A menos que se utilize o parâmetro Scorch, o cmdlet **Disable-CsComputer** não desinstalará o software do Lync Server. Em vez disso, ele simplesmente interromperá a atuação do computador em sua função designada previamente.

Quem pode executar esse cmdlet: É necessário que você seja um administrador local e um membro do domínio, para poder executar o cmdlet **Disable-CsComputer** localmente.

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
<th>Digite</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>Confirm</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Solicita confirmação antes da execução do comando.</p></td>
</tr>
<tr class="even">
<td><p><em>Force</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Suprime a exibição de qualquer mensagem de erro não-fatal que possa ocorrer durante a execução do comando.</p></td>
</tr>
<tr class="odd">
<td><p><em>GlobalCatalog</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN (nome de domínio totalmente qualificado) de um servidor de catálogo global no domínio. Este parâmetro não será necessário se você estiver executando o cmdlet <strong>Disable-CsComputer</strong> em um computador com uma conta de seu domínio.</p></td>
</tr>
<tr class="even">
<td><p><em>GlobalSettingsDomainController</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Deploy.Fqdn</p></td>
<td><p>FQDN de um controlador de domínio onde estão armazenadas as definições globais. Se as definições globais estiverem armazenadas no contêiner Sistema do Serviços de Domínio Active Directory, este parâmetro deverá apontar para o controlador de domínio raiz. Se as definições globais estiverem armazenadas no contêiner Configuration, qualquer controlador de domínio poderá ser utilizado e este parâmetro poderá ser omitido.</p></td>
</tr>
<tr class="odd">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar o caminho do arquivo de log criado ao se executar o cmdlet. Por exemplo: -Report &quot;C:\Logs\DisableComputer.html&quot;</p></td>
</tr>
<tr class="even">
<td><p><em>Scorch</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Desinstala todos os serviços e as funções de servidor do Lync Server no computador local.</p></td>
</tr>
<tr class="odd">
<td><p><em>WhatIf</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Descreve o que aconteceria se o comando fosse executado sem ser executado de fato.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Disable-CsComputer** não aceita a entrada por pipeline.

## Tipos de retorno

Nenhum. Em vez disso, o cmdlet **Disable-CsComputer** publica as instâncias do objeto Microsoft.Rtc.Management.Deploy.Internal.Machine.

## Consulte Também

#### Outros Recursos

[Enable-CsComputer](enable-cscomputer.md)  
[Get-CsComputer](get-cscomputer.md)  
[Test-CsComputer](test-cscomputer.md)

