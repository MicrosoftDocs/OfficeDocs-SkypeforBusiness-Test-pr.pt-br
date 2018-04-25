---
title: Parâmetros obrigatórios e opcionais
TOCTitle: Parâmetros obrigatórios e opcionais
ms:assetid: e766362f-e2e9-4598-a595-fdf5eedd9ad6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362851(v=OCS.15)
ms:contentKeyID: 56270481
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Parâmetros obrigatórios e opcionais

 

_**Tópico modificado em:** 2015-06-22_

Os parâmetros Windows PowerShell ficam em duas categorias: obrigatórios ou opcionais. Um *parâmetro obrigatório* é aquele que deve ser incluído quando você executa o comando. Por exemplo, o cmdlet [Remove-CsUserAcp](remove-csuseracp.md) é usado para cancelar a atribuição de um provedor de audioconferência que foi atribuído anteriormente a um usuário. Quando você executa o cmdlet **the Remove-CsUserAcp**, deve incluir o parâmetro Identity. Esse parâmetro informa ao cmdlet que o usuário precisa ter seu provedor de audioconferência removido. Como esperado, executar esse comando sem qualquer parâmetro não faria muito sentido:

    Remove-CsUserAcp

Em um caso assim, o cmdlet não teria ideia de qual usuário precisa ter seu provedor de audioconferência removido. Ao contrário, você deve especificar a identidade do usuário:

    Remove-CsUserAcp -Identity "Ken Myer"

Em geral, Windows PowerShell solicitará se você omitir um parâmetro obrigatório ao tentar executar um comando. Por exemplo, você pode digitar o seguinte, então, pressionar ENTER:

    Remove-CsUserAcp

Se você fizer isso, Windows PowerShell não executará este comando incompleto. Ao contrário, solicitará o parâmetro obrigatório que falta:

    cmdlet Remove-CsUserAcp na posição de comando 1 do pipeline
    Supply values for the following parameters:
    Identity:

Se você digitar um parâmetro Identity válido e pressionar ENTER, Windows PowerShell execurará o cmdlet **Remove-CsUserAcp** e removerá o provedor de audioconferência. Se você mudar de ideia e decidir não executar o comando afinal, pressione Ctrl-C para terminar o comando.

Isto não é um sistema infalível e Windows PowerShell nem sempre consegue solicitar o conjunto de parâmetros requerido. Por exemplo, alguns cmdlets são construídos para que o parâmetro A ou o parâmetro B (mas não ambos) seja obrigatório. Windows PowerShell pode solicitar os dois parâmetros A e B; contudo, seu comando falhará porque você não pode usar o parâmetro A e o parâmetro B no mesmo comando, Por causa de situações como esta, é melhor incluir todos os parâmetros requeridos antes de executar o comando e não contar com Windows PowerShell para solicitar as informações necessárias.

Note, também, que formatar o valor do parâmetro pode, algumas vezes, ser um processo difícil. Por exemplo, ao incluir um valor do parâmetro com espaço em branco, você precisará colocar esse valor entre aspas duplas:

    -Identity "Ken Myer"

Porém, usar aspas é necessário apenas quando você digita o parâmetro e o valor do parâmetro como parte do comando a ser executado. Se você tentar executar o cmdlet **Remove-CsUserAcp**, mas omitir sem querer o parâmetro Identity, Windows PowerShell solicitará a identidade do usuário:

    cmdlet Remove-CsUserAcp na posição de comando 1 do pipeline
    Supply values for the following parameters:
    Identity:

Então digite Ken Myer, com o parâmetro Identity entre aspas duplas:

    cmdlet Remove-CsUserAcp na posição de comando 1 do pipeline
    Supply values for the following parameters:
    Identity: "Ken Myer"

Se você fizer isso, o comando falhará, com a seguinte mensagem de erro:

    Remove-CsUserAcp : Objeto de gerenciamento não encontrado para a identidade ""Ken Myer"".

Neste caso, foi pesquisado um usuário com a identidade "Ken Myer", com aspas duplas incluídas como parte do parâmetro Identity. Se foi solicitado que você digite um valor do parâmetro, não inclua aspas duplas:

    cmdlet Remove-CsUserAcp na posição de comando 1 do pipeline1
    Supply values for the following parameters:
    Identity: Ken Myer

Comparando, um *parâmetro opcional* é exatamente o que o nome significa: o parâmetro não precisa ser digitado para o cmdlet ser executado. Por exemplo, Remove-CsUserAcp tem um parâmetro opcional Name. Se o parâmetro Name for incluído no comando, então, apenas o provedor de audioconferência especificado será removido. Esse comando remove o provedor de audioconferência com o nome Fabrikam ACP, mas não remove nenhum outro provedor de audioconferência atribuído a Ken Myer:

    Remove-CsUserAcp -Identity "Ken Myer" -Name "Fabrikam ACP"

Se você omitir esse parâmetro opcional, o comando ainda será executado. Neste caso, contudo, Remove-CsUserAcp apagará todos os provedores de audioconferência atribuidos a Ken Myer:

    Remove-CsUserAcp -Identity "Ken Myer"

## Consulte Também

#### Conceitos

[Uma introdução ao Windows PowerShell e ao Lync Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

