---
title: Instalando os arquivos do agente do Operation Manager
TOCTitle: Installing the Operation Manager Agent Files
ms:assetid: e2246c44-0c75-43fc-8b04-26e53c5dd572
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205345(v=OCS.15)
ms:contentKeyID: 49308382
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando os arquivos do agente do Operation Manager

 

_**Tópico modificado em:** 2012-10-20_

Para instalar os arquivos de agente do Gerenciador de Operações no computador, conclua as seguintes etapas.

1.  Na sua mídia de configuração do System Center, clique duas vezes em **SetupOM.exe**.

2.  Na configuração do Gerenciador de Operações do System Center, clique em **Instalar o agente do Gerente de operações**.

3.  No assistente Instalação do System Center, na página do assistente **Bem-vindo à Instalação do Gerenciador de operações do System Center**, clique em **Avançar**.

4.  Na página **Pasta de destino**, selecione a pasta onde os arquivos do Agente do Gerenciador de operações serão instalados e clique em **Avançar**.

5.  Na página **Configuração do grupo de gerenciamento**, selecione **Especificar a informação do grupo de gerenciamento** e clique em **Avançar**.

6.  Na página **Configuração do grupo de gerenciamento**, digite o nome do seu grupo de gerenciamento do Gerente de operações na caixa **Nome do grupo de gerenciamento** e digite o nome do host do seu servidor do Gerente de operações (por exemplo, atl-scom-001) na caixa **Servidor de gerenciamento**. Se você alterou o número da porta usado pelo Gerente de operações, digite o novo número da porta na caixa Porta do servidor de gerenciamento. Caso contrário, deixe a porta no valor padrão de 5723 e clique em **Avançar**.

7.  Na página **Conta de ação do agente**, selecione **Sistema local** e clique em **Avançar**.

8.  Na página **Microsoft Update**, selecione **Eu não desejo usar o Microsoft Update** e clique em **Avançar**.

9.  Na página **Pronto para instalar**, clique em **Instalar**.

10. Na página **Concluir o assistente de Instalação do gerente de operações do System Center**, clique em **Concluir**.

11. Clique em **Sair**.

Se você estiver usando o System Center 2007 R2, é possível verificar se o agente foi criado clicando em **Iniciar**, **Todos os programas**, **System Center Operations Manager 2007 R2** e em **Shell do gerente de operações**. No Shell do gerente de operações, digite o seguinte comando do Windows PowerShell e pressione ENTER:

    Get-Agent 

Uma lista de todos os seus agentes do Gerente de operações aparecerá na tela.

Se você estiver usando o System Center 2012, execute este comando no Shell do gerente do Operations 2012:

    Get-SCOMAgent

