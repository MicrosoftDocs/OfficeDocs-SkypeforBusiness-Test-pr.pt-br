---
title: 'Lync Server 2013: Habilitar usuários para Enterprise Voice'
TOCTitle: Habilitar usuários para Enterprise Voice
ms:assetid: f252b23b-9641-4160-aa81-bf06dc2eced3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413011(v=OCS.15)
ms:contentKeyID: 49308584
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar usuários para Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2012-11-01_

Após instalar arquivos em um ou mais Servidores de Mediação, configurar o roteamento de chamadas de saída e, opcionalmente, implantar um ou mais recursos avançados do Enterprise Voice, use os seguintes procedimentos para permitir um usuário realizar chamadas usando o Enterprise Voice:

> [!NOTE]  
> Dos seguintes procedimentos, apenas o primeiro pode ser realizado usando o Painel de Controle do Lync Server. Para os procedimentos restantes, é possível usar apenas o Shell de Gerenciamento do Lync Server.

  - Habilitar a conta do usuário para o Enterprise Voice.

  - (Opcional) Atribuir a conta de usuário com uma política de voz específica do usuário.

  - (Opcional) Atribuir a conta do usuário com um plano de discagem específico do usuário.

## Para habilitar uma conta do usuário para o Enterprise Voice

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários** .

4.  Na caixa **Pesquisar usuários** , digite todo ou parte do nome de exibição, nome, sobrenome, nome da conta SAM, endereço SIP ou URI de linha da conta do usuário que deseja habilitar e clique em **Localizar** .

5.  Na tabela, clique na conta de usuário que deseja habilitar para o Enterprise Voice.

6.  No menu **Editar** , clique em **Exibir detalhes** .

7.  Na página **Editar Lync Server** , em **Telefonia** , clique em **Enterprise Voice** .

8.  Clique em **URI de linha** e digite um número de telefone único e normalizado (por exemplo, tel:+14255550200).

9.  Clique em **Confirmar** .

Para finalizar a habilitação de um usuário para o Enterprise Voice, certifique-se de que o usuário é atribuído com uma política de voz e um plano de discagem, global (atribuído por padrão) ou específico do usuário.

Por padrão, todos os usuários são atribuídos com uma política de voz global e plano de discagem. Se uma política de voz ou plano de discagem existe no nível do site para o site na qual a conta do usuário está hospedada, estas políticas de site serão aplicadas automaticamente ao usuário. Para aplicar uma política de voz por usuário ou plano de discagem para um usuário, você deve executar os cmdlets **Grant-CsVoicePolicy** e **Grant-CsDialPlan**. Para obter detalhes, consulte a documentação do [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Atribuição da política de voz

As políticas de voz a nível global e do site são atribuídas automaticamente para todas as contas do usuário habilitadas para o Enterprise Voice. Também é possível criar políticas de voz que são aplicadas a usuários ou grupos específicos. Estas políticas por usuário devem ser atribuídas explicitamente aos usuários ou grupos. Se você deseja usar a política de voz global ou de site em todos os usuários habilitados para o Enterprise Voice, é possível pular esta seção e continuar com a seção Atribuição do plano de discagem posteriormente neste tópico.

## Para atribuir uma política de voz específica do usuário

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para atribuir uma política de voz do usuário existente para um usuário, execute o seguinte no prompt de comando:
    
        Grant-CsVoicePolicy -Identity <UserIdParameter> -PolicyName <String>
    
    Por exemplo:
    
        Grant-CsVoicePolicy -Identity "Bob Kelly" -PolicyName VoicePolicyJapan
    
    Neste exemplo, o usuário com o nome de exibição Bob Kelly é atribuído com a política de voz chamada **VoicePolicyJapan**.

Para obter detalhes sobre a atribuição de uma política de voz específica do usuário ou sobre a execução do cmdlet **Grant-CsVoicePolicy**, consulte a documentação do [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Atribuição do plano de discagem

Para concluir a configuração da conta do usuário para usuários do Enterprise Voice ou usuários da conferência discada, o usuário deve estar atribuído com um plano de discagem. As contas do usuário usarão automaticamente o plano de discagem global ou, se existir, o plano de discagem a nível do site quando você não atribuir explicitamente um plano de discagem por usuário existente. Se você deseja usar o plano de discagem global ou de site para todos os usuários habilitados para o Enterprise Voice, é possível pular esta seção.

## Para atribuir um plano de discagem

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para atribuir um plano de discagem específico do usuário, execute o seguinte no prompt de comando:
    
        Grant-CsDialPlan -Identity <UserIdParameter> -PolicyName <String>
    
    Por exemplo:
    
        Grant-CsDialPlan -Identity "Bob Kelly" -PolicyName DialPlanJapan
    
    Neste exemplo, o usuário com o nome de exibição Bob Kelly é atribuído com o plano de discagem do usuário chamado **DialPlanJapan**.

Para obter detalhes sobre a atribuição de um plano de discagem do usuário ou sobre a execução do cmdlet **Grant-CsDialPlan**, consulte a documentação do [Shell de gerenciamento do Lync Server](lync-server-2013-lync-server-management-shell.md).

## Consulte Também

#### Tarefas

[Desabilitar um usuário para o Enterprise Voice](lync-server-2013-disable-a-user-for-enterprise-voice.md)

