---
title: Excluir configurações da qualidade de experiência
TOCTitle: Excluir configurações da qualidade de experiência
ms:assetid: fd0c4c2f-3bfb-42cb-9b6a-f0f8d5aa9e81
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182613(v=OCS.15)
ms:contentKeyID: 49308707
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir configurações da qualidade de experiência

 

_**Tópico modificado em:** 2013-02-23_

Os atributos métricos de Qualidade de Experiência (QoE) rastreiam a qualidade das chamadas de áudio e vídeo feitas na organização, inclusive o número de pacotes de rede perdidos, o ruído de fundo e a quantidade de "jitter" (diferenças no atraso de pacotes). Esses atributos métricos são armazenados em um banco de dados separado de outros dados (como registros de detalhes das chamadas), permitindo a habilitação e desabilitação do QoE, independentemente de outros registros de dados.

Ao instalar Microsoft Lync Server 2013, um conjunto único e global de definições de configuração de QoE é criado. Os administradores também têm a opção de criar conjuntos personalizados de definições que podem ser aplicados a sites individuais. Por design, as configurações no escopo do site têm precedência sobre configurações no escopo global. Se você excluir definições no escopo do site, o QoE será gerenciado naquele site usando as configurações globais.

Observe que você também pode “excluir” as definições globais. Contudo, elas não serão realmente removidas. Em vez disso, todas as propriedades naquele conjunto serão redefinidas de acordo com os valores padrão. Por exemplo, por padrão, a exclusão é habilitada em um conjunto de configurações de QoE. Digamos que você modifique o conjunto global para que a exclusão seja desabilitada. Se depois você resolver apagar as definições globais, todas as propriedades serão redefinidas para os valores padrão. Nesse caso, isso significa que a exclusão será habilitada novamente.

Você pode remover as definições de configuração de QoE usando Painel de Controle do Lync Server ou o cmdlet [Remove-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsQoEConfiguration).

## Para excluir as definições de configuração de QoE usando Painel de Controle do Lync Server

1.  Faça logon no computador como um membro do grupo RTCUniversalServerAdmins ou como um membro da função CsVoiceAdministrator, CsServerAdministrator ou CsAdministrator. Para obter detalhes, consulte [Delegar permissões de configuração no Lync Server 2013](lync-server-2013-delegate-setup-permissions.md).

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Monitoramento e arquivamento** e em **Dados de Qualidade da Experiência**.

4.  Na página **Dados de Qualidade de Experiência**, clique na política que quiser, clique em **Editar** e em **Excluir**.

5.  Clique em **OK**.

## Para remover as definições de configuração de QoE usando os cmdlets Shell de Gerenciamento do Lync Server

Você também pode excluir as definições de configuração de QoE usando os cmdlets Shell de Gerenciamento do Lync Server e the **Remove-CsQoEConfiguration**. Execute esse cmdlet no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Para remover um conjunto especificado de definições de configuração de QoE

  - Esse comando remove as definições de configuração de QoE aplicadas ao site de Redmond:
    
        Remove-CsQoEConfiguration -Identity "site:Redmond"

## Para remover todas as definições de configuração de QoE aplicadas no escopo do site

  - Esse comando remove todas as definições de configuração de QoE aplicadas ao escopo do site:
    
        Get-CsQoEConfiguration -Filter "site:*" | Remove-CsQoEConfiguration

## Para remover todas as definições de configuração de QoE onde o monitoramento de QoE for desabilitado

  - Este comando remove todas as definições de configuração de QoE onde o monitoramento de QoE foi desabilitado:
    
        Get-CsQoEConfiguration | Where-Object {$_.EnableQoE -eq $False} | Remove-CsQoEConfiguration

Para detalhes, consulte [Remove-CsQoEConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsQoEConfiguration).

