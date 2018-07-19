---
title: Excluir o objeto de contato de um telefone de área comum
TOCTitle: Excluir o objeto de contato de um telefone de área comum
ms:assetid: f4c139dc-f07c-4c75-9345-e291aea41173
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ994087(v=OCS.15)
ms:contentKeyID: 52057770
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir o objeto de contato de um telefone de área comum

 

_**Tópico modificado em:** 2013-02-20_

Talvez você queira excluir os objetos de contato associados a um telefone de área comum. Por exemplo, se você remover o telefone da sala de um funcionário, não haverá a necessidade de ter um objeto de contato associado a esse telefone. O cmdlet **Remove-CsCommonAreaPhone** oferece uma forma de excluir as contas de um telefone de área comum. Quando você executa esse cmdlet, o telefone é excluído da lista de telefones de área comum retornada pelo **Get-CsCommonAreaPhone**. Além disso, os objetos de contato associados ao telefone serão excluídos do Serviços de Domínio Active Directory.

Use o **Remove-CsCommonAreaPhone** para remover um telefone de área comum ou todos os telefones de área comum que tenham um elemento em comum, como nome de exibição ou país e código de área. Você pode executar esse cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).


## Removendo um telefone de área comum especificado

  - O comando a seguir remove o telefone de área comum de endereço IP sip:mainlobby@litwareinc.com:
    
        Remove-CsCommonAreaPhone -Identity "sip:mainlobby@litwareinc.com"

## Removendo telefones de área comum com base no nome de exibição

  - Este comando remove todos os telefones de área comum cujo nome de exibição contém o valor da cadeia de caracteres "Edifício 14":
    
        Get-CsCommonAreaPhone | Where-Object {$_.DisplayName -match "Building 14"} | Remove-CsCommonAreaPhone

## Removendo telefones de área comum com base no país e nos códigos de área

  - Este comando remove todos os telefones de área comum dos Estados Unidos (código do país 1), com o código de área 425:
    
        Get-CsCommonAreaPhone | Where-Object {$_.LineUri  -match "^tel:\+1425"} | Remove-CsCommonAreaPhone

Para obter detalhes, consulte os tópicos da Ajuda para o cmdlet [Remove-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsCommonAreaPhone).

## Consulte Também

#### Outros Recursos

[Get-CsCommonAreaPhone](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsCommonAreaPhone)

