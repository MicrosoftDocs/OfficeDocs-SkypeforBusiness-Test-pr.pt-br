---
title: 'Lync Server 2013: Habilitar usuários do Lync para controle de chamada remotas'
TOCTitle: Habilitar usuários do Lync para controle de chamada remota
ms:assetid: f39bc10d-034c-4875-a0b8-554e1109e7e6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg615048(v=OCS.15)
ms:contentKeyID: 49308599
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar usuários do Lync para controle de chamada remota no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

É possível configurar os usuários do Lync para o controle de chamada remota usando as políticas de provisionamento em banda que são baseados em servidor. É possível gerenciar as configurações de provisionamento em banda usando o Painel de Controle do Lync Server ou a interface de linha de comando do Shell de Gerenciamento do Lync Server. Estas ferramentas substituem o snap-in Windows Management Instrumentation (WMI) usado para gerenciar as configurações da Política de Grupo em versões anteriores.

Se você prefere permitir que os usuários definam suas próprias configurações de controle de chamada remota no Lync, é possível definir as configurações do controle de chamada remota para usuários no servidor sem especificar os valores de **URI do Servidor de Linha** e de **URI da Linha**. Certifique-se de comunicar os valores de **URI do Servidor de Linha** e **URI da Linha** adequados aos seus usuários e oferecer a eles as instruções para definir estas configurações. Para o procedimento de configurar manualmente o controle de chamada remota no Lync Server, consulte "Definir opções e números do telefone" em <http://go.microsoft.com/fwlink/p/?linkid=210132> na documentação do cliente do Lync no site do Microsoft Office.

Se você possui uma implantação do Communications Server 2007 R2 ou Communications Server 2007 existente, e os clientes do Communicator 2007 R2 e Communicator 2007continuarão a usar a Política de Grupo durante a migração lado a lado. No entanto, se você deseja que as configurações de política sejam transportadas para os clientes do Lync, é necessário definir a configuração de provisionamento em banda do Lync Server equivalente.

> [!NOTE]  
> Para habilitar um usuário para o controle de chamada remota, um usuário deve ter um URI de linha e um URI do servidor de linha. Conforme descrito em <a href="lync-server-2013-deployment-tasks-for-remote-call-control.md">Tarefas de implantação de controle de chamada remota no Lync Server 2013</a>, certifique-se de usar a sintaxe exigida pelo gateway para estas configurações.<br />Certifique-se de que o domínio no URI do servidor de linha é igual ao domínio de destino especificado no parâmetro MatchUri ao configurar um roteamento estático para o gateway.<br />O URI da linha especifica o número de telefone atribuído ao usuário no formato E.164, com o prefixo “TEL:” (por exemplo, tel:+14255550150). Se você deseja configurar um número de ramal, o formato é tel:+14255550150;ramal=111. Se você configurou anteriormente o URI da Linha do usuário e o valor não foi alterado, não é necessário especificar o URI da Linha ao habilitar o usuário para controle de chamada remota.

## Para habilitar o controle de chamada remota para usuários habilitados em Lync utilizando o Shell de Gerenciamento

1.  Faça login no computador onde o Shell de Gerenciamento do Lync Server está instalado como membro do grupo RTCUniversalServerAdmins ou uma função de controle de acesso baseada em função para a qual você atribuiu o cmdlet **Set-CsUser**.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Para usar o cmdlet **Set-CsUser** para configurar o controle de chamada remota para um usuário habilitado em Lync existente, faça o seguinte:
    
        Set-CsUser -Identity <User ID> -EnterpriseVoiceEnabled $false -LineServerUri <SIP URI of the SIP/CSTA gateway> -LineUri <TEL URI of the user> -RemoteCallControlTelephonyEnabled $true
    
    Por exemplo:
    
        Set-CsUser -Identity "Katie Jordan" -EnterpriseVoiceEnabled $false -LineServerUri sip:rccgateway@contoso.net -LineUri tel:+14255550150 -RemoteCallControlTelephonyEnabled $true

## Para configurar os usuários para o controle de chamada remota usando o Painel de Controle do Lync Server

1.  Usando uma conta de usuário atribuída à função CsUserAdministrator ou CsAdministrator, faça logon em qualquer computador de sua implantação interna.

2.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

3.  Na barra de navegação esquerda, clique em **Usuários**.

4.  Na caixa **Pesquisar usuários**, digite todo ou a primeira parte do nome de exibição, nome, sobrenome, nome da conta SAM (Security Accounts Manager), endereço SIP ou URI de linha da conta que deseja e clique em **Localizar**.

5.  Na tabela, clique na conta de usuário que deseja modificar.

6.  No menu **Editar**, clique em **Modificar**.

7.  Em **Telefonia**, faça um dos seguintes:
    
      - Para habilitar o controle de chamada remota para permitir que o usuário controle este telefone PBX pelo Lync 2013 para realizar chamadas de áudio de computador para computador e chamadas de computador para telefone, clique em **Controle de chamada remota**. Em **URI de linha**, especifique o número de telefone do usuário. Em **URI do servidor de linha**, especifique o URI SIP do gateway SIP/CSTA.
    
      - Para habilitar o controle de chamada remota, mas desabilitar as chamadas de áudio de computador para computador e permitir que apenas o usuário controle seu telefone PBX pelo Lync 2013 para realizar chamadas de computador para telefone, clique em **Apenas controle de chamada remota**. Em **URI de linha**, especifique o número de telefone do usuário. Em **URI do servidor de linha**, especifique o URI SIP do gateway SIP/CSTA.

8.  Ao concluir, clique em **Confirmar**.

