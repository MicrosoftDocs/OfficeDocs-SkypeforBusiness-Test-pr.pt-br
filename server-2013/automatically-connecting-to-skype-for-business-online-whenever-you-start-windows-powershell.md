---
title: Conectando Automaticamente ao Lync Online Quando Você Iniciar o Windows PowerShell
TOCTitle: Conectando Automaticamente ao Lync Online Quando Você Iniciar o Windows PowerShell
ms:assetid: 68f76c36-5dd6-48ea-b19a-d65593199e4c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn362799(v=OCS.15)
ms:contentKeyID: 56270421
ms.date: 06/02/2017
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Conectando Automaticamente ao Lync Online Quando Você Iniciar o Windows PowerShell

 

_**Tópico modificado em:** 2015-06-22_

Se você não consegue lembrar de todos os comandos necessários para conectar-se ao Skype for Business Online, você pode configurá-los e tudo o que você precisa fazer é dar dois cliques no arquivo de atalho, insira sua senha de Skype for Business Online, e simples assim, conecte-se ao Skype for Business Online.

Para fazer isso, comece abrindo o Notepad (ou qualquer editor de texto) e cole os seguintes comandos, substituindo seu nome de conta do Skype for Business Online para kenmyer@litwareinc.com:

    $credential = Get-Credential "kenmyer@litwareinc.com"
    $session = New-CsOnlineSession -Credential $credential 
    Import-PSSession $session

Salve o arquivo com uma extensão de arquivo .PS1 (por exemplo, C:\\Scripts\\LyncOnline.ps1).

Depois de ter salvado o arquivo, complete o seguinte procedimento para criar um atalho na área de trabalho que inicia Windows PowerShell e executa o script no startup:

1.  Clique com o botão direito na área de trabalho, clique em **Novo** e depois clique em **Atalho**.

2.  No assistente **Criar Atalho**, escreva o seguinte no **Escreva o local da caixa do item** e clique em **Próximo** (lembre-se de usar o caminho para o arquivo de script que você acabou de criar):
    
        powershell.exe -noexit C:\Scripts\LyncOnline.ps1

3.  Em **Escreva um nome para esta caixa de atalho**, ecreva um nome para o atalho (por exemplo, **Skype for Business Online**) e clique em **Concluir**.

4.  A próxima vez que você quiser usar Windows PowerShell para gerenciar Skype for Business Online, apenas dê dois cliques no novo ataho e insira sua senha.O script cuidará de fazer a conexão e de definir a nova sessão remota.

Essa nova sessão, tipicamente, não será armazenada na variável $session. Em vez disso, normalmente, será dada a ID da sessão 1. Isso não afetará sua sessão de nenhuma forma, até que chegue a hora de fechar a sessão. Para fazer isso, você precisa se referir à ID da sessão quando chamar o cmdlet **Remove-PSSession**:

    Remove-PSSession 1

Você pode verificar a ID dada para sua sessão Skype for Business Online executando esse comando do prompt Windows PowerShell :

    Get-PSSession

## Consulte Também

#### Conceitos

[Configurando o Computador Gerenciamento do Lync Online](configuring-your-computer-for-skype-for-business-online-management.md)

