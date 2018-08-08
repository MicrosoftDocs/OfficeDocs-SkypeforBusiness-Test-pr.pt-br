---
title: "Instal. os Arquivos de Núcleo de Lync Server 2013 e o Banco de Dados RTCLocal"
TOCTitle: "Instal. os Arquivos de Núcleo de Lync Server 2013 e o Banco de Dados RTCLocal"
ms:assetid: 206f0c1d-40f7-45b6-aa62-88aaef6cf7f6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204734(v=OCS.15)
ms:contentKeyID: 49306116
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando os Arquivos de Núcleo de Lync Server 2013 e o Banco de Dados RTCLocal

 

_**Tópico modificado em:** 2012-10-20_

Para instalar os principais arquivos do Lync Server 2013 em um computador, conclua o seguinte procedimento. O banco de dados RTCLocal é instalado automaticamente ao instalar os principais arquivos. Observe que você não precisará instalar o SQL Server em nós do observador. Ao invés disso, o SQL Server Express é instalado automaticamente para você.

Para instalar os principais arquivos do Lync Server 2013 e o banco de dados RTCLocal:

1.  No computador do nó do observador, clique em **Iniciar**, em **Todos os programas**, em **Acessórios**, clique com o botão direito no **Prompt de comando** e clique em **Executar como administrador**.

2.  Na janela de console, digite o seguinte comando e pressione ENTER, usando o caminho adequado para seus arquivos de instalação do Lync Server:
    
        D:\Setup.exe /BootstrapLocalMgmt

Para verificar se os principais componentes do Lync Server foram instalados com sucesso, clique em **Iniciar**, em **Todos os programas**, em **Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**. No Shell de Gerenciamento do Lync Server 2013, digite o seguinte comando do Windows PowerShell e pressione ENTER:

    Get-CsWatcherNodeConfiguration

A primeira vez que você executar este comando, nenhum dado é retornado porque você não configurou qualquer computador do nó do observador. Enquanto o comando executar sem retornar um erro, é possível assumir que a instalação do Lync Server foi concluída com sucesso.

Se seu computador do nó do observador estiver localizada dentro da sua rede de perímetro, é possível executar o seguinte comando para verificar a instalação do Lync Server 2013:

    Get-CsPinPolicy

Você irá receber informações semelhantes ao seguinte, dependendo do número de políticas de PIN configuradas para uso em sua organização:

    Identity             : Global
    Description          :
    MinPasswordLength    : 5
    PINHistoryCount      : 0
    AllowCommonPatterns  : False
    PINLifetime          : 0
    MaximumLogonAttempts :

Se você ver informações sobre suas políticas de PIN, significa que você instalou com sucesso os principais componentes.

