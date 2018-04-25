---
title: Remove-CsCertificate
TOCTitle: Remove-CsCertificate
ms:assetid: b7a83a58-9d3f-458a-867e-44466c9817dc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412895(v=OCS.15)
ms:contentKeyID: 49307885
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Remove-CsCertificate

 

_**Tópico modificado em:** 2015-03-09_

Remove um certificado previamente marcado como disponível para uso pelo Lync Server. Este cmdlet foi introduzido no Lync Server 2010.

## Sintaxe

    Remove-CsCertificate -Type <CertType[]> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-Identity <XdsIdentity>] [-Previous <SwitchParameter>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

## Exemplos

## EXEMPLO 1

O comando exibido no Exemplo 1 exclui todos os certificados WebServicesExternal disponíveis para o Lync Server. Se qualquer um desses certificados estiver sendo usado, o cmdlet **Remove-CsCertificate** perguntará se você tem certeza de que deseja exclui-lo; é necessário responder a essa solicitação para que o comando prossiga. Para ignorar a solicitação de confirmação, use o parâmetro Force:

Remove-CsCertificate –Type WebServicesExternal -Force

    Remove-CsCertificate -Type WebServicesExternal

## Descrição detalhada

O Lync Server usa certificados como uma forma de servidores e funções de servidores verificarem suas identidades. Por exemplo: um Servidor de Borda utiliza certificados para verificar se o computador com o qual está se comunicando é realmente um Servidor Front-End e vice-versa. Para implementar integralmente o Lync Server, será necessário ter os certificados apropriados atribuídos às funções de servidor apropriadas.

O cmdlet **Remove-CsCertificate** permite remover certificados que estiverem sendo usados pelo Lync Server. Na realidade, o cmdlet **Remove-CsCertificate** não exclui o certificado em si. Em vez disso, marca o certificado como indisponível para uso pelo Lync Server, remove todas as associações do certificado e revoga as permissões de acesso ao certificado (presumindo-se que nenhum outro serviço o esteja usando). Entre outras coisas, isso significa que o certificado não aparecerá mais quando o cmdlet **Get-CsCertificate** for executado.

Para usar novamente o certificado com o Lync Server, é necessário atribuir novamente o certificado ao Lync Server usando o cmdlet **Set-CsCertificate**.

Se você tentar remover um certificado que estiver em uso, o cmdlet **Remove-CsCertificate** perguntará se você tem certeza de que deseja remover o certificado. O certificado não poderá ser removido enquanto não se responder a essa solicitação. Para ignorar a solicitação e excluir silenciosamente um certificado, mesmo se ele estiver em uso, adicione o parâmetro Force ao comando:

Remove-CsCertificate –Type WebServicesExternal -Force

Quem pode executar esse cmdlet: É necessário que você seja um administrador local e um membro do domínio para poder executar o cmdlet **Remove-CsCertificate** localmente. Para retornar uma lista de todas as funções de controle de acesso baseado em função (RBAC) às quais este cmdlet foi atribuído (inclusive qualquer função RBAC personalizada que tenha sido criada por você), execute o seguinte comando no prompt do Windows PowerShell:

Get-CsAdminRole | Where-Object {$\_.Cmdlets –match "Remove-CsCertificate"}

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
<td><p><em>Type</em></p></td>
<td><p>Obrigatório</p></td>
<td><p>Microsoft.Rtc.Management.Deployment.CertType[]</p></td>
<td><p>Tipo de certificado a ser excluído. Os tipos de certificado incluem (mas não se limitam a):</p>
<p>AccessEdgeExternal</p>
<p>AudioVideoAuthentication</p>
<p>DataEdgeExternal</p>
<p>Default</p>
<p>External</p>
<p>Internal</p>
<p>PICWebService (apenas Microsoft Lync Online 2010)</p>
<p>ProvisionService (apenas Microsoft Lync Online 2010)</p>
<p>WebServicesExternal</p>
<p>WebServicesInternal</p>
<p>WsFedTokenTransfer</p>
<p>Por exemplo: essa sintaxe exclui o certificado Default: -Type Default.</p>
<p>É possível excluir diversos tipos em um único comando, separando os tipos de certificado por vírgulas:</p>
<p>-Type Internal,External,Default</p></td>
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
<td><p>Ignora a solicitação de confirmação que aparece normalmente ao tentar excluir um certificado que estiver em uso.</p></td>
</tr>
<tr class="even">
<td><p><em>Identity</em></p></td>
<td><p>Opcional</p></td>
<td><p>Microsoft.Rtc.Management.Xds.XdsIdentity</p></td>
<td><p>Quando definido como Global, remove o certificado do escopo global. Quando não especificado, os certificados são removidos do computador local.</p></td>
</tr>
<tr class="odd">
<td><p><em>Previous</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.Management.Automation.SwitchParameter</p></td>
<td><p>Quando especificado, remove o certificado atribuído anteriormente em vez do certificado atribuído no momento.</p></td>
</tr>
<tr class="even">
<td><p><em>Report</em></p></td>
<td><p>Opcional</p></td>
<td><p>System.String</p></td>
<td><p>Permite registrar informações detalhadas sobre os procedimentos realizados pelo cmdlet <strong>Remove-CsCertificate</strong>. O valor do parâmetro deve ser o caminho completo do arquivo HTML a ser gerado; por exemplo: -Report C:\Logs\Certificates.html. Se o arquivo especificado já existir,as novas informações o substituirão automaticamente.</p></td>
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

Nenhuma. O cmdlet Remove-CsCertificate não aceita entrada por pipeline.

## Tipos de retorno

Nenhuma. Em vez disso, o cmdlet **Remove-CsCertificate** exclui instâncias do objeto Microsoft.Rtc.Management.Deployment.CertificateReference.

## Consulte Também

#### Outros Recursos

[Get-CsCertificate](get-cscertificate.md)  
[Import-CsCertificate](import-cscertificate.md)  
[Request-CsCertificate](request-cscertificate.md)  
[Set-CsCertificate](set-cscertificate.md)

