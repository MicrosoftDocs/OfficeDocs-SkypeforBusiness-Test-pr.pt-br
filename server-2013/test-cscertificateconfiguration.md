---
title: Test-CsCertificateConfiguration
TOCTitle: Test-CsCertificateConfiguration
ms:assetid: 8086bdf7-d283-4666-9f6c-0d5a3a31b3a6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398647(v=OCS.15)
ms:contentKeyID: 49307276
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Test-CsCertificateConfiguration

 

_**Tópico modificado em:** 2015-03-09_

Retorna informações sobre os certificados do Lync Server sendo utilizados no computador local. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Test-CsCertificateConfiguration [-Report <String>]

## Exemplos

## EXEMPLO 1

O comando apresentado no Exemplo 1 retorna informações sobre os certificados que estiverem sendo utilizados (no computador local) pelo Lync Server.

    Test-CsCertificateConfiguration

## EXEMPLO 2

O comando apresentado no Exemplo 2 é uma variação do comando apresentado no Exemplo 1. Neste caso, entretanto, o parâmetro Report é utilizado para especificar o caminho do arquivo de saída (C:\\Logs\\Certificates.xml) gerado ao se executar o cmdlet **Test-CsCertificateConfiguration**.

    Test-CsCertificateConfiguration -Report "C:\Logs\Certificates.xml"

## Descrição detalhada

O cmdlet **Test-CsCertificateConfiguration** é um exemplo de uma "transação sintética". As transações sintéticas são usadas no Lync Server para se certificar de que os usuários sejam capazes de concluir tarefas comuns com sucesso, como fazer logon no sistema, trocar mensagens instantâneas ou realizar chamadas para um telefone localizado na PSTN (rede telefônica pública comutada). Esses testes podem ser conduzidos manualmente por um administrador ou executados automaticamente por um aplicativo como o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager).

O cmdlet **Test-CsCertificateConfiguration** retorna informações sobre os certificados utilizados pelo Lync Server. O cmdlet **Test-CsCertificateConfiguration** destina-se principalmente ao uso pelo assistente de Certificação. Recomenda-se que os administradores usem o cmdlet **Get-CsCertificate** para recuperar informações de certificação.

Quem pode executar esse cmdlet: Para retornar uma lista de todas as funções do controle de acesso baseado em função (RBAC) que receberam a atribuição desse cmdlet (incluindo qualquer função RBAC personalizada criada por você), execute o seguinte comando do prompt Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Test-CsCertificateConfiguration"}

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
<td><p>Permite especificar o caminho do arquivo de log criado ao se executar o cmdlet. Por exemplo: -Report &quot;C:\Logs\Certificates.html&quot;. Se esse arquivo já existir, ele será sobrescrito ao se executar o cmdlet.</p></td>
</tr>
</tbody>
</table>


## Tipos de entrada

Nenhuma. O cmdlet**Test-CsCertificateConfiguration** não aceita entrada em pipeline.

## Tipos de retorno

O cmdlet **Test-CsCertificateConfiguration** retorna instâncias do objeto Microsoft.Rtc.Management.Deployment,CertificateExists.

## Consulte Também

#### Outros Recursos

[Get-CsCertificate](get-cscertificate.md)

