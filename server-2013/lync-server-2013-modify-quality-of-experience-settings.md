---
title: Modificas as configurações da qualidade da experiência
TOCTitle: Modificas as configurações da qualidade da experiência
ms:assetid: a6b41de2-1466-4240-8a70-14ce6f0f3ddc
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182563(v=OCS.15)
ms:contentKeyID: 49307701
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificas as configurações da qualidade da experiência

 

_**Tópico modificado em:** 2013-02-23_

Por padrão, os dados de QoE (Qualidade de Experiência) são limpos após 60 dias. Você pode usar as configurações da página **Dados de Qualidade de Experiência** para manter os dados por um período maior ou menor. Se você desabilitar a QoE, os dados capturados antes da habilitação da QoE também ficarão sujeitos à limpeza.

> [!NOTE]  
> Você deve configurar o registro de detalhes de chamadas (CDR) e a QoE para manter dados durante o mesmo número de dias. Cada chamada nos relatórios de detalhes de chamadas (CDRs), disponíveis na página inicial de relatórios do Monitoring Reports, inclui informações de CDR e QoE. Se o momento da limpeza para o CDR e a QoE for diferente, algumas chamadas podem incluir somente dados de CDR, enquanto outros podem incluir somente dados de QoE.

O procedimento a seguir descreve como definir as configurações de limpeza para dados de QoE.

## Para especificar a retenção de dados de QoE usando o Painel de Controle do Lync Server

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação à esquerda, clique em **Monitoramento e Arquivamento** e clique em **Dados de Qualidade de Experiência**.

4.  Na página **Dados de Qualidade de Experiência**, clique no site adequado na tabela, clique em **Editar** e em **Exibir Detalhes**.

5.  Para ativar a limpeza, selecione **Habilitar a Limpeza do QoE**.

6.  Em **Manter QoE por um período máximo de (dias)** selecione o número máximo de dias durante os quais dados de QoE devem ser mantidos.

7.  Clique em **Confirmar**.

## Para especificar a retenção de QoE usando os cmdlets do Windows PowerShell

Você pode criar configurações de retenção de QoE usando o Windows PowerShell e o cmdlet do **Set-CsQoEConfiguration**. Você pode executar esse cmdlet do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para especificar a retenção de QoE de um local específico

  - Esse comando permite limpar os dados de QoE do site da Redmond e configura o site para manter os dados de QoE por 20 dias.
    
        Set-CsQoeConfiguration -Identity "site:Redmond" -EnablePurging -KeepQoEDataForDays 20

## Para especificar a retenção de QoE de vários locais

  - Esse comando configura a retenção de QoE para todos as configurações de QoE em uso em uma organização.
    
        Get-CsQoEConfiguration | Set-CsQoEConfiguration-EnablePurging -KeepQoEDataForDays 20 

Para obter mais informações, consulte o tópico de ajuda do cmdlet [Set-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsQoEConfiguration).

## Consulte Também

#### Outros Recursos

[Implantando o monitoramento no Lync Server 2013](lync-server-2013-deploying-monitoring.md)

