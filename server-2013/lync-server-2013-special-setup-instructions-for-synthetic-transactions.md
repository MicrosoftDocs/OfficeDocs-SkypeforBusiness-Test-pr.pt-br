---
title: Instruções Especiais de Configuração para Transações Sintéticas
TOCTitle: Instruções Especiais de Configuração para Transações Sintéticas
ms:assetid: 694cbe05-5dba-4035-a01c-c87ebfb0478b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688080(v=OCS.15)
ms:contentKeyID: 49886249
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instruções Especiais de Configuração para Transações Sintéticas

 

_**Tópico modificado em:** 2015-11-16_

A maioria das transações sintéticas pode ser executada em um nó do inspetor no estado em que se encontram, ou seja, assim que uma transação sintética é adicionada às configurações do nó do inspetor, ele pode começar a usá-la durante as fases de teste. No entanto, isso não ocorre para todas as transações sintéticas. As exceções (transações que exigem instruções de configuração especiais) são abordadas nas seções a seguir.

## Transações sintéticas de conferência de dados

Se o computador de nó do inspetor estiver localizado fora da sua rede de perímetro, você provavelmente não poderá executar a transação sintética de conferência de dados, a menos que primeiro desabilite as configurações de proxy do Internet Explorer para a conta Serviço de Rede. Para desabilitar as configurações de proxy para esse serviço, execute o procedimento a seguir:

1.  No computador de nó do inspetor, clique em **Iniciar**, em **Todos os Programas**, em **Acessórios**, clique com o botão direito do mouse em **Prompt de Comando** e clique em **Executar como administrador**.

2.  Na janela do console, digite o seguinte comando e pressione ENTER:
    
        bitsadmin /util /SetIEProxy NetworkService NO_PROXY

A seguinte mensagem será exibida na janela de comando:

    BITSAdmin is deprecated and is not guaranteed to be available in future versions of Windows. Administration tools for the BITS service are now provided by BITS PowerShell cmdlets.
    
    Internet proxy settings for account NetworkService set to NO_PROXY. 
    (connection = default)

Essa mensagem significa que você desabilitou as configurações de proxy do Internet Explorer para a conta Serviço de Rede.

## Transações sintéticas de Unificação de Mensagens do Exchange

A transação sintética de Unificação de Mensagens (UM) do Exchange verifica se usuários de teste podem se conectar a contas de caixa postal hospedadas no Exchange. Esses usuários de teste precisarão ser pré-configurados com contas de caixa postal para poderem usar os testes de UM do Exchange.

## Transações sintéticas do Chat Persistente

Para usar a transação sintética do Chat Persistente, os administradores primeiro devem criar um canal e conceder aos usuários de teste permissões para usá-lo. O cmdlet [Test-CsPersistentChatMessage](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsPersistentChatMessage) pode ser usado para configurar adequadamente esses usuários de teste.

    $cred1 = Get-Credential "litwareinc\kenmyer"
    $cred2 = Get-Credential "litwareinc\pilar"
    
    Test-CsPersistentChatMessage -TargetFqdn atl-cs-001.litwareinc.com -SenderSipAddress sip:kenmyer@litwareinc.com -SenderCredential $cred1 -ReceiverSipAddress sip:pilar@litwareinc.com -ReceiverCredential $cred2 -TestUser1SipAddress sip:kenmyer@litwareinc.com -TestUser2SipAddress sip:pilar@litwareinc.com -Setup $True

Esta tarefa de configuração deve ser realizada de dentro da empresa:

  - Se ela for realizada de uma máquina que não é um servidor, o usuário que executar o cmdlet deverá ser um membro da função PersistentChatAdministrators do RBAC (Controle de Acesso Baseado em Função).

  - Se ela for realizada a partir do próprio servidor, o usuário que executar o cmdlet deverá ser um membro do grupo RTCUniversalServerAdmins.

No comando anterior, o parâmetro Setup foi incluído e definido como True ($True). Se você incluir o parâmetro Setup, Test-CsPersistentChatMessage criará uma sala de Chat Persistente especial e a preencherá com os usuários de teste. Isso ajudará a garantir que haja uma sala de chat real disponível para fins de teste. O parâmetro só deve ser executado a partir de um Servidor Front-End.

A sala de chat criada por Test-CsPersistentChatMessage só pode ser excluída por um administrador.

## Transações sintéticas de chamada ponto a ponto PSTN

A transação sintética de [Test-CsPstnPeerToPeerCall](https://docs.microsoft.com/en-us/powershell/module/skype/Test-CsPstnPeerToPeerCall) verifica a capacidade de realizar e receber chamadas através de uma PSTN (rede telefônica pública comutada).

Para executar essa transação sintética, os administradores devem configurar:

  - Dois usuários de teste (um chamador e um receptor) habilitados para o Enterprise Voice.

  - Números DID (Discagem Interna Direta) para cada conta de usuário.

  - Políticas e rotas de voz que permitem que chamadas para o número do receptor cheguem ao gateway PSTN.

  - Um gateway PSTN que aceita chamadas e mídia que encaminha os retornos de chamada para o pool primário de um receptor com base no número discado.

## Transações sintéticas do repositório unificado de contatos

A transação sintética do repositório unificado de contatos verifica se o Lync Server 2013 é capaz de recuperar contatos em nome de um usuário do Microsoft Exchange Server 2013.

Para usar essa transação sintética, as seguintes condições devem ser atendidas:

  - É necessário configurar [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) entre o Lync Server 2013 e o Exchange 2013.

  - Os usuários de teste devem ter uma caixa de correio válida do Exchange 2013.

Depois que essas condições forem atendidas, os administradores poderão executar o seguinte comando para verificar se o usuário com o endereço SIP kenmyer@litwareinc.com pode recuperar seus contatos do repositório unificado de contatos:

    Test-CsUnifiedContactStore -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -RegistrarPort 5061 -Authentication TrustedServer -Setup

Observe o uso do parâmetro Setup no comando anterior. Se o parâmetro Setup estiver incluído durante a execução de Test-CsUnifiedContactStore, os contatos do usuário especificado (neste caso, sip:kenmyer@litwareinc.com) serão transferidos para o repositório unificado de contatos (evidentemente, se os contatos do usuário já estiverem no repositório unificado de contatos, eles não precisarão ser transferidos). O parâmetro Setup geralmente só é usado uma vez (na primeira execução de Test-CsUnifiedContactStore) e só deve ser usado com usuários de teste, ou seja, com contas de usuário que nunca se conectarão de fato ao Lync Server. Depois que o usuário de teste for migrado para o repositório unificado de contatos, você poderá verificar se os contatos do usuário podem ser recuperados chamando Test-CsUnifiedContactStore sem o parâmetro Setup:

    Test-CsUnifiedContactStore -TargetFqdn atl-cs-001.litwareinc.com -UserSipAddress "sip:kenmyer@litwareinc.com" -RegistrarPort 5061 -Authentication TrustedServer

## Transações sintéticas XMPP

A transação sintética de IM do protocolo XMPP exige que o recurso XMPP seja configurado com um ou mais domínios federados.

Para habilitar a transação sintética XMPP, um parâmetro XmppTestReceiverMailAddress deve ser fornecido com uma conta de usuário em um domínio XMPP roteável. Por exemplo:

    Set-CsWatcherNodeConfiguration -Identity pool0.contoso.com -Tests @{Add="XmppIM"} -XmppTestReceiverMailAddress user1@litwareinc.com

No exemplo, uma regra do Lync Server 2013 precisará existir para encaminhar mensagens de litwareinc.com para um gateway XMPP.

