---
title: Cmdlets, parâmetros e valores de parâmetro do Windows PowerShell
TOCTitle: Cmdlets, parâmetros e valores de parâmetro do Windows PowerShell
ms:assetid: 04615700-099f-4ac5-a801-ddeffccb9e4f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362765(v=OCS.15)
ms:contentKeyID: 56270364
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Cmdlets, parâmetros e valores de parâmetro do Windows PowerShell

 

_**Tópico modificado em:** 2015-06-22_

Se você estiver familiarizado com a janela de comando encontrada em todas as versões do Windows (ou se estiver familiarizado com o MS-DOS), então já terá uma vantagem para aprender a usar o Windows PowerShell. Na janela de comando, você digita um comando e pressiona ENTER. Em resposta, o computador executa um comando ou um arquivo executável. Por exemplo, para retornar informações sobre todos os arquivos e pastas no diretório atual, você digitaria este comando no prompt de comando e então pressionaria ENTER:

    dir

Em troca, você obtém informações sobre todos os arquivos e pastas no diretório atual:

``` 
    Directory: C:\

03/21/2013  03:39 PM    <DIR>          Deploy
03/21/2013  02:55 PM    <DIR>          Intel
07/26/2012  12:33 AM    <DIR>          PerfLogs
04/10/2013  10:29 AM    <DIR>          Program Files
04/08/2013  10:28 AM    <DIR>          Program Files (x86)
03/22/2013  08:44 AM    <DIR>          Users
04/11/2013  03:00 PM    <DIR>              Windows
03/13/2013  02:53 PM                 117   pldok.log
03/21/2013  03:35 PM                 769   RHDSetup.exe
03/21/2013  03:37 PM            207   setup.doc
              3 File(s)        1,093 bytes
              7 Dir(s)21,386,002,432 bytes free
```

Este é um exemplo de um resultado quando você digita somente o nome de um comando ou arquivo executável. Entretanto, vários dos comandos também são executados da janela de comando, exceto *argumentos*. Os argumentos são informações adicionais passadas ao comando, que modificam o comportamento do comando. Por exemplo, se você só quisesse ver os nomes dos arquivos e da pasta no diretório atual — sem outras informações, como o tamanho do arquivo ou da pasta, ou a data e a hora em que o arquivo ou a pasta foi criado. Nesse caso, você anexaria o argumento **/b** ao executar o comando dir:

    dir /b

Quando você inclui o argumento **/b**, o comando **dir** relata de volta somente os nomes das pastas e dos arquivos encontrados no diretório atual:

    Deploy
    Intel
    PerfLogs
    Program Files
    Program Files (x86)
    Users
    Windows
    pldok.log
    RHDSetup.exe
    setup.doc

No comando anterior, o argumento **/b** é a única informação obrigatória para limitar os dados retornados a nomes de arquivo e de pasta. Com frequência esse será o caso de comandos de linha de comando: a mera presença de um argumento é todo o necessário para alterar o comportamento do comando (ou seja, você inclui o argumento **/b** para ocultar informações adicionais ou exclui o argumento **/b** para mostrar as informações extras). Em outras ocasiões, no entanto, você deve especificar um *valor de argumento*. Um valor de argumento é uma informação adicional passada ao próprio argumento. Por exemplo, o argumento **/o** permite que você especifique como gostaria que o comando dir classificasse os dados retornados. Entre outras opções, você pode usar o valor de argumento **e** para classificar a extensão de arquivo ou o valor de argumento **s** para classificar o tamanho do arquivo. Por exemplo, este comando classifica os dados retornados por extensão do arquivo. Observe como o valor de argumento **e** é incluído imediatamente após o argumento **/o**:

    dir /oe

Usando nossa pasta de exemplo, os dados retornados terão esta aparência, com os arquivos classificados alfabeticamente por extensão do arquivo:

``` 
    Directory: C:\

03/21/2013  03:39 PM    <DIR>          Deploy
03/21/2013  02:55 PM    <DIR>          Intel
07/26/2012  12:33 AM    <DIR>          PerfLogs
04/10/2013  10:29 AM    <DIR>          Program Files
04/08/2013  10:28 AM    <DIR>          Program Files (x86)
03/22/2013  08:44 AM    <DIR>          Users
04/11/2013  03:00 PM    <DIR>              Windows
03/21/2013  03:37 PM            207   setup.doc
03/21/2013  03:35 PM                 769   RHDSetup.exe
03/13/2013  02:53 PM                 117   pldok.log
              3 File(s)        1,093 bytes
              7 Dir(s)21,386,002,432 bytes free
```

Ou, para ajudar você a saber exatamente do que estamos falando:

setup. **doc**  
RHDSetup. **exe**  
pldok. **log**

Embora o Windows PowerShell use uma terminologia diferente, a abordagem básica ao trabalho com o Windows PowerShell é igual ao trabalho com a janela de comando: você digita comandos, inclui argumentos e valores de argumento como necessário e então pressiona ENTER para executar esses comandos. Como observado, no entanto, o Windows PowerShell usa uma terminologia diferente do shell de comando. No Windows PowerShell, os comandos executados são conhecidos como *cmdlets*. Por sua vez, os argumentos passados para um cmdlet são conhecidos como *parâmetros* e os valores passados para um parâmetro são conhecidos como *valores de parâmetro*.

As definições anteriores estão, de alguma forma, simplificadas. Os cmdlets são essencialmente miniaplicativos que podem ser executados somente no ambiente do Windows PowerShell. Entretanto, você também pode executar outros comandos e aplicativos do Windows PowerShell, incluindo a maioria dos comandos e aplicativos que podem ser executados de uma janela de comando. Por exemplo, se você quiser iniciar o Bloco de Notas do Windows PowerShell, tudo o que precisará fazer é digitar o seguinte e pressionar ENTER:

    notepad.exe

Quando se trata de gerenciar o Skype for Business Online, no entanto, a maioria dos administradores se baseará nos cmdlets do Windows PowerShell para realizarem tarefas administrativas. No momento, existem muito poucos tipos diferentes de comandos e aplicativos que possam ser usados para gerenciar o Skype for Business Online. Algumas vezes, os cmdlets do Skype for Business Online pode ser usados sem qualquer argumento adicional (como observado, os argumentos são conhecidos como parâmetros no Windows PowerShell). Por exemplo, o comando a seguir chama o cmdlet [Get-CsOnlineUser](get-csonlineuser.md) sem qualquer parâmetro adicional. Sozinho, o comando retorna informações sobre todos os seus usuários do Skype for Business Online:

    Get-CsOnlineUser

Entretanto, a maioria dos cmdlets do Skype for Business Online também aceita parâmetros (e valores de parâmetro). Considere o seguinte comando:

    Get-CsOnlineUser -Identity "kenmyer@litwareinc.com"

Este comando consiste em três partes:

  - O cmdlet **Get-CsOnlineUser**.

  - O parâmetro Identidade. Observe que, no Windows PowerShell, os parâmetros são sempre prefixados por um traço (-). Isso significa que, para esse mesmo cmdlet, o parâmetro UnassignedUser seria indicado usando esta sintaxe:
    
        -UnassignedUser
    
    É útil saber disso, não só porque os parâmetros devem ser prefixados com um traço, como também porque isso difere da janela de comando, onde argumentos são prefixados usando uma barra (/):
    
    ``` 
    /b
    ```

  - O valor de parâmetro **pauloneves@litwareinc.com**.

Esse comando, incidentalmente, retorna informações sobre um usuário específico: o usuário com a identidade, pauloneves@litwareinc.com.

## Consulte Também

#### Conceitos

[Uma introdução ao Windows PowerShell e ao Lync Online](an-introduction-to-windows-powershell-and-skype-for-business-online.md)

