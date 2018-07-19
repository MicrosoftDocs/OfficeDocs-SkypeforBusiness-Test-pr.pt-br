---
title: Exibir Informações de Configuração do Lync Phone Edition
TOCTitle: Exibir Informações de Configuração do Lync Phone Edition
ms:assetid: 15f94478-651f-4063-9918-6a059f98df16
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ687976(v=OCS.15)
ms:contentKeyID: 49886112
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exibir Informações de Configuração do Lync Phone Edition

 

_**Tópico modificado em:** 2013-02-23_

Você pode visualizar informações de configuração de dispositivos executando o Lync Phone Edition. As informações são organizadas em conjuntos. Ao instalar o Lync Server, você obtém um conjunto de configurações do Lync Phone Edition que se aplicam a todos os dispositivos executando o Lync Phone Edition em sua implantação. Você também pode criar novos conjuntos de configurações para um site específico. As configurações de site tem precedência sobre configurações globais. Cada conjunto de configurações consiste em um nome, o escopo (global ou site), configuração de segurança SIP, nível de log, nível do QoS (Qualidade de Serviço) de voz, configuração de bloqueio de telefone e detalhes de bloqueio de telefone, isto é, o comprimento mínimo do PIN (número de identificação pessoal) de desbloqueio e o tempo para que o telefone se bloqueie sozinho.

## Para visualizar informações de configuração de dispositivos executando o Lync Phone Edition

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes**, e então clique no botão de navegação **Configuração de Dispositivo**.

4.  Na página **Configuração de Dispositivo**, clique no conjunto de configurações sobre o qual deseja visualizar informações. O nome, escopo, configuração de segurança SIP, nível de qualidade de voz e a configuração de bloqueio de telefone são listados na página principal. Para visualizar o nível de log e os detalhes de bloqueio de telefone, clique no menu **Editar**, e então clique em **Exibir detalhes**.

## Para visualizar informações de configuração do Lync Phone Edition usando cmdlets do Shell de Gerenciamento do Lync Server

Você também pode visualizar definições de configuração do Lync Phone Edition usando o Shell de Gerenciamento do Lync Server e o cmdlet **Get-CsUCPhoneConfiguration**. Você pode usar este cmdlet a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para visualizar informações de configuração do Lync Phone Edition

  - Para visualizar informações sobre todas as suas definições de configuração do Lync Phone Edition, digite o comando a seguir no Shell de Gerenciamento do Lync Server e então pressione ENTER:
    
        Get-CsUCPhoneConfiguration
    
    O comando retorna informações parecidas com as seguintes:
    
        Identity             : Global
        CalendarPollInterval : 00:03:00
        EnforcePhoneLock     : True
        PhoneLockTimeout     : 00:10:00
        MinPhonePinLength    : 6
        SIPSecurityMode      : High
        VoiceDiffServTag     : 40
        Voice8021p           : 0
        LoggingLevel         : Off

Para obter detalhes, consulte [Get-CsUCPhoneConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsUCPhoneConfiguration).

## Consulte Também

#### Tarefas

[Criar ou Modificar um Conjunto de Configurações de Lync Phone Edition](lync-server-2013-create-or-modify-a-collection-of-lync-phone-edition-configuration-settings.md)  
[Excluir um conjunto existente das configurações do Lync Phone Edition](lync-server-2013-delete-an-existing-collection-of-lync-phone-edition-configuration-settings.md)  
[Configurações de segurança para o Lync Phone Edition](lync-server-2013-configure-security-settings-for-lync-phone-edition.md)  
[Aplicar Bloqueio de Telefone](lync-server-2013-enforce-phone-locking.md)

