---
title: Criar ou Modificar uma Política de Mobilidade
TOCTitle: Criar ou Modificar uma Política de Mobilidade
ms:assetid: fc2dfea0-2215-440d-9f4b-7c985da29211
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721946(v=OCS.15)
ms:contentKeyID: 49886497
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Criar ou Modificar uma Política de Mobilidade

 

_**Tópico modificado em:** 2013-02-23_

Você pode criar ou modificar a política de mobilidade para permitir que usuários móveis usem os dispositivos móveis suportados para a funcionalidade Lync, como mensagens instântaneas (IM), presença e contatos. Você pode criar ou modificar políticas de mobilidade de Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server 2013

## Para criar uma política de mobilidade em Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e no botão de navegação **Política de Mobilidade**.

4.  Na página **Política de Mobilidade**, clique em **Novo** e execute uma das seguintes ações:
    
    1.  Para criar uma política de mobilidade do site, clique em **Política do Site**, clique em um site e en **OK**; reveja as configurações e faça as mudanças desejadas, se aplicável.
    
    2.  Para criar uma política de mobilidade do usuário, clique em **Política do Usuário**, digite um nome, reveja as configurações e faça as mudanças desejadas, se aplicável.

5.  Clique em **Confirmar**.

## Para modificar uma política de mobilidade em Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Clientes** e no botão de navegação **Política de Mobilidade**.

4.  Na página **Política de Mobilidade**, clique em uma das políticas de mobilidade existentes.

5.  No menu **Editar**, clique em **Exibir detalhes**.

6.  Edite as configurações.

7.  Clique em **Confirmar**.

## Remover Políticas de Acesso Externo Usando Windows PowerShell e Cmdlets

As políticas de mobilidade também podem ser criadas (no escopo do site ou do usuário) usando Windows PowerShell e o cmdlet **New-CsMobilityPolicy**. Ademais, você pode usar o cmdlet **Set-CsMobilityPolicy** para modificar qualquer política existente, incluindo a política global. Esses cmdlets podem ser executados no Shell de Gerenciamento do Lync Server 2013 ou em uma sessão remota de Windows PowerShell. Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" em [http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)](http://go.microsoft.com/fwlink/p/?linkid=255876).

## Criar uma política de mobilidade no escopo do site

  - Esse comando cria uma nova política de mobilidade para o site de Redmond:
    
        New-CsMobilityPolicy -Identity "site:Redmond"
    
    Já que nenhum parâmetro (além do parâmetro obrigatório Identity) foi especificado no comando precedente, as políticas usarão os valores padrão para todas as suas propriedades.

## Criar uma política de mobilidade no escopo do usuário

  - Para criar uma política de mobilidade no escopo por usuário, especifique uma Identidade exclusiva para a política:
    
        New-CsMobilityPolicy -Identity "RedmondMobilityPolicy"

## Modificar um valor único de propriedade ao criar uma política de mobilidade

  - Para criar políticas que usam diferentes valores de propriedade, inclua o parâmetro e o valor de parâmetro adequados. Por exemplo, esse comando cria a política de mobilidade que desabilita Chamada via Trabalho:
    
        New-CsMobilityPolicy -Identity "site:Redmond" -EnableOutsideVoice $False

## Modificar valores múltiplos de propriedade ao criar uma política de mobilidade

  - Valores múltiplos de propriedade podem ser modificados incluindo parâmetros múltiplos. Por exemplo, esse comando cria uma política que desabilita mobilidade e Chamada via Trabalho:
    
        New-CsMobilityPolicy "site:Redmond" -EnableMobility $False -EnableOutsideVoice $False

Para detalhes, consulte o tópico de ajuda para os cmdlets [New-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsMobilityPolicy) e [Set-CsMobilityPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsMobilityPolicy).

## Consulte Também

#### Tarefas

[Configurando a política de mobilidade no Lync Server 2013](lync-server-2013-configuring-mobility-policy.md)

