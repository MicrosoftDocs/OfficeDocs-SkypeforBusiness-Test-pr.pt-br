---
title: Combinar cmdlets do Lync Online com outros cmdlets do Windows PowerShell
TOCTitle: Combinar cmdlets do Lync Online com outros cmdlets do Windows PowerShell
ms:assetid: 8bb8800a-f966-4570-8c8b-db87a91ad783
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362816(v=OCS.15)
ms:contentKeyID: 56270444
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Combinar cmdlets do Lync Online com outros cmdlets do Windows PowerShell

 

_**Tópico modificado em:** 2015-06-22_

Quando você se conectar ao Skype for Business Online usando o Windows PowerShell, aproximadamente 40 Skype for Business Online cmdlets estarão disponíveis para uso. No entanto, você não está limitado a usar apenas 40 cmdlets ao gerenciar o Skype for Business Online. Além dos cmdlets Skype for Business Online, você também pode usar outros cmdlets Windows PowerShell que estão instalado no computador. (Quando você instalar o Windows PowerShell 3.0, centenas de cmdlets fundamentais Windows PowerShell também são instalados.) Seus comandos podem misturar e combinar cmdlets Skype for Business Online e quaisquer outros cmdlets disponíveis no computador.

Embora um curso completo no Windows PowerShell 3.0 englobe além do escopo deste artigo, veja aqui alguns exemplos que mostram por que convém misturar e combinar cmdlets. Em primeiro lugar, nenhum dos cmdlets Skype for Business Online incluem um comando Imprimir e também não se encontra este tipo de comando no console Windows PowerShell. Então, como você obter uma cópia impressa das informações recuperadas por um cmdlet? É uma maneira de recuperar as informações, e em seguida enviar essas informações para o cmdlet **Out-Printer**:

    Get-CsTenant | Out-Printer

Como não há parâmetros adicionais incluídos, todas as informações retornadas pelo cmdlet **the Out-Printer** serão impressas na impressora padrão.

Da mesma forma, nenhum dos cmdlets Skype for Business Online inclui um parâmetro que permite que você salve os dados em um arquivo. Mas tudo bem: esse comando usa o cmdlet **Out-File** para salvar as informações retornadas para o arquivo de texto C:\\Logs\\Inquilinos.txt:

    Get-Tenant | Out-File -FilePath "C:\Logs\Tenants.txt"

E esse comando usa o cmdlet **Select-Object** limitar os dados retornados e exibidos na tela. Neste exemplo, cmdlet [Get-CsOnlineUser](get-csonlineuser.md) recupera as informações de todos os usuários Skype for Business Online , e em seguida o cmdlet **Select-Object** é usado para limitar os dados apresentados ao valor de identidade do usuário e sua política de arquivamento:

    Get-CsOnlineUser | Select-Object Identity, ArchivingPolicy

Como haverá centenas de cmdlets disponíveis para uso em seu computador, você pode ter dificuldade em determinar quais cmdlets são Skype for Business Online cmdlets e quais não são. Para retornar uma lista dos cmdlets Skype for Business Online (e não apenas cmdlets Skype for Business Online ), primeiro você deve determinar o nome do módulo temporário Windows PowerShell que contém todos os cmdlets Skype for Business Online. Para isso, execute este comando a partir do prompt Windows PowerShell:

    Get-Module

Informação semelhante às seguintes serão exibidas na tela:

    ModuleType Name                 ExportedCommands
    ---------- ----                 ----------------
    Manifest   Microsoft.PowerS...  {Add-Computer, Add-Content, A...}
    Script     tmp_5astd3uh.m5v     {Disable-CsMeetingRoom, Enabl...}

O módulo com o Script ModuleType é o módulo que contém os cmdlets Skype for Business Online. Para retornar uma lista dos cmdlets, execute o cmdlet **Get-Command**, usando o nome do módulo Script como o nome do módulo:

    Get-Command -Module tmp_5astd3uh.m5v

É possível que você pode ter vários módulos com um ModuleType igual a Script. Nesse caso, você pode executar o seguinte comando para descobrir qual módulo inclui o cmdlet **Get-CsTenant**:

    Get-Command Get-CsTenant

O módulo retornado para o cmdlet **Get-CsTenant** será o módulo que contém todos os cmdlets Skype for Business Online:

    CommandType     Name                                               ModuleName
    -----------     ----                                               ----------
    Function        Get-CsTenant                                       tmp_5astd3uh.m5v

## Consulte Também

#### Conceitos

[Uma introdução ao Windows PowerShell e ao Lync Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

