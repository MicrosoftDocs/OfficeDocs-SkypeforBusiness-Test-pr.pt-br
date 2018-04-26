---
title: Test-CsComputer
TOCTitle: Test-CsComputer
ms:assetid: 0b33d951-510d-445c-9b01-c6431fda6d47
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398162(v=OCS.15)
ms:contentKeyID: 49305848
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsComputer

 

_**Tópico modificado em:** 2015-03-09_

O cmdlet **Test-CsComputer** verifica o status dos serviços do Lync Server em execução no computador local. O cmdlet também verifica se os grupos do Active Directory do Lync Server foram adicionados aos grupos locais correspondentes no computador e se as portas de firewall do computador necessárias foram abertas. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsComputer [-Report <String>]

## Exemplos

## EXEMPLO 1

O comando mostrado no Exemplo 1 verifica o status de ativação do serviço do computador local. O parâmetro Verbose é incluído no comando para verificar se o sucesso (ou a falha) da operação é totalmente informado na tela.

    Test-CsComputer -Verbose

## EXEMPLO 2

O Exemplo 2 também verifica o status de ativação do serviço do computador local. Além disso, esse comando grava informações detalhadas sobre o status de ativação no arquivo C:\\Logs\\Computer.html. Esse log é gerado incluindo-se o parâmetro Report seguido do caminho completo do arquivo de log no qual as informações devem ser gravadas.

    Test-CsComputer -Verbose -Report C:\Logs\Computer.html

## Descrição detalhada

O cmdlet **Test-CsComputer** é um exemplo de uma "transação sintética" do Lync Server. As transações sintéticas são usadas no Lync Server para verificar se os usuários podem concluir tarefas comuns, como fazer logon no sistema, trocar mensagens instantâneas ou fazer chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador, ou ser executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

O cmdlet **Test-CsComputer**, que só pode ser executado no computador local, verifica o status de todos os serviços do Lync Server nesse computador. O cmdlet também verifica se as portas de firewall apropriadas foram abertas no computador e determina se os grupos do Active Directory criados quando você instalou o Lync Server foram adicionados aos grupos locais correspondentes. Por exemplo, o cmdlet **Test-CsComputer** verificará se o grupo do Active Directory RTCUniversalUserAdmins foi adicionado ao grupo Administradores local.

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
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite especificar um caminho de arquivo para o arquivo de log criado quando o cmdlet é executado. Por exemplo: -Report &quot;C:\Logs\Computer.html&quot;. Se já existir, esse arquivo será substituído quando você executar o cmdlet.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet **Test-CsComputer** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Test-CsComputer** retorna uma instância do objeto Microsoft.Rtc.SyntheticTransactions.TaskOutput.

## Consulte Também

#### Outros Recursos

[Disable-CsComputer](disable-cscomputer.md)  
[Enable-CsComputer](enable-cscomputer.md)  
[Get-CsComputer](get-cscomputer.md)

