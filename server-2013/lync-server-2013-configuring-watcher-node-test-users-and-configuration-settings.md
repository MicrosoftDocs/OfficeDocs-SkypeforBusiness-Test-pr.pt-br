---
title: Configurando Usuários de Teste do Nó Inspetor e Definições de Configuração
TOCTitle: Configurando Usuários de Teste do Nó Inspetor e Definições de Configuração
ms:assetid: ab00e9cb-f539-4aa6-bcb4-5533fbe7bc44
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205152(v=OCS.15)
ms:contentKeyID: 49307766
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando Usuários de Teste do Nó Inspetor e Definições de Configuração

 

_**Tópico modificado em:** 2013-07-29_

Depois de configurar o computador que atuará como um nó do inspetor, você deve:

1.  Criar as contas de teste que serão usadas por esses nós de inspetor. Se estiver usando o método de autenticação Negociar, você também deve usar o cmdlet [Set-CsTestUserCredential](https://docs.microsoft.com/en-us/powershell/module/skype/) para permitir o uso dessas contas de teste no nó do inspetor.

2.  Atualizar as definições de configuração do nó do inspetor.

Esta seção cobre:

  - Configurando contas de usuário de teste

  - Configurando uma Nó do inspetor básico com as Transações sintéticas padrão

  - Configurando Tests estendidos

  - Adicionando e removendo Transações sintéticas

  - Exibindo e testando a configuração do nó inspetor

## Configurando contas de usuário de teste

Os usuários de teste não precisam representar pessoas reais, mas devem ser contas válidas do Serviços de Domínio Active Directory; além disso, essas contas devem estar ativadas para Lync Server 2013, devem ter endereços SIP válidos, além de serem ativadas para Enterprise Voice (para usar a transação sintética Test-CsPstnPeerToPeerCall). Se você usar o método de autenticação TrustedServer, então será necessário certificar-se de que essas contas existem e foram configuradas como especificado aqui. É necessário atribuir pelo menos três usuários de teste a cada pool que deseja testar.

Se estiver usando o método de autenticação Negociar, você deve usar o cmdlet **Set-CsTestUserCredential** e o Shell de Gerenciamento do Lync Server para permitir que essas contas de teste funcionem com transações sintéticas. Isso pode ser feito executando um comando semelhante a este. (Esses comandos consideram que as três contas do usuário do Active Directory já foram criadas e estão ativadas para o Lync Server 2013.):

    Set-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com" -UserName "litwareinc\watcher1" -Password "P@ssw0rd"
    Set-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com" -UserName "litwareinc\watcher2" -Password "P@ssw0rd"
    Set-CsTestUserCredential -SipAddress "sip:watcher3@litwareinc.com" -UserName "litwareinc\watcher3" -Password "P@ssw0rd"

Observe que é necessário incluir não apenas o endereço SIP, mas também o nome e a senha do usuário. Se não incluir a senha, Set-CsTestUserCredential solicitará que você insira essas informações. O nome do usuário pode ser especificado usando o formato nome do domínio\\nome do usuário mostrado acima ou usando o formato nome do usuário@nome do domínio; por exemplo:

    -UserName "watcher3@litwareinc.com"

Para verificar se as credenciais do usuário de teste foram criadas, execute estes comandos no Shell de Gerenciamento do Lync Server:

    Get-CsTestUserCredential -SipAddress "sip:watcher1@litwareinc.com"
    Get-CsTestUserCredential -SipAddress "sip:watcher2@litwareinc.com"
    Get-CsTestUserCredential -SipAddress "sip:watcher3@litwareinc.com"

Informações semelhantes a estas devem ser retornadas para cada usuário:

    NomeUsuário                        Senha
    --------                        --------
    Litwareinc\watcher1              System.Security.SecureString

## Configurando uma Nó do inspetor básico com as Transações sintéticas padrão

Depois que os usuários de teste são criados, você pode criar um nó do inspetor usando um comando semelhante a este:

    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"}

Esse comando cria um novo nó do inspetor que usa as configurações padrão e executa o conjunto padrão de transações sintéticas. O novo nó do inspetor também usa watcher1@litwareinc.com, watcher2@litwareinc.com e watcher3@litwareinc.com dos usuários de teste. Se o nó do inspetor está usando a autenticação TrustedServer, as três contas de teste podem ser quaisquer contas de usuário válidas ativadas habilitadas para Active Directory e Lync Server. Se o nó do inspetor está usando o método de autenticação Negociar, você também deve ativar essas contas do usuário para o nó do inspetor usando o cmdlet **Set-CsTestUserCredential**.

## Configurando testes estendidos

Se você desejar ativar a rede telefônica pública comutada (teste da PSTN), que verifica a conectividade com a rede telefônica comutada, será necessário efetuar configurações adicionais ao configurar o nó do inspetor. Primeiro, é necessário associar seus usuários de teste ao tipo de teste da PSTN. Para isso, execute um comando semelhante a este no Shell de Gerenciamento do Lync Server:

    $pstnTest = New-CsExtendedTest -TestUsers "sip:watcher1@litwareinc.com", "sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"  -Name "Contoso Provider Test" -TestType PSTN

Observe que os resultados desse comando devem ser armazenados em uma variável. Neste exemplo, é uma variável chamada de $pstnTest.

Nesse ponto, você pode usar o cmdlet **New-CsWatcherNodeConfiguration** para associar o tipo de teste (armazenado na variável $pstnTest) a um pool do Lync Server 2013. Por exemplo, o seguinte comando cria uma nova configuração de nó do inspetor para o pool atl-cs-001.litwareinc.com, adicionando os três usuários de teste que foram criados anteriormente e também adicionando o tipo de teste de PSTN:

    New-CsWatcherNodeConfiguration -TargetFqdn "atl-cs-001.litwareinc.com" -PortNumber 5061 -TestUsers @{Add= "sip:watcher1@litwareinc.com","sip:watcher2@litwareinc.com", "sip:watcher3@litwareinc.com"} -ExtendedTests @{Add=$pstnTest}

Observe que o comando anterior falhará se não tiver instalado os arquivos de núcleo do Lync Server e o banco de dados RTCLocal no computador do nó do inspetor.

Para testar várias políticas de voz, é necessário criar um teste estendido para cada política usando o cmdlet **New-CsExtendedTest**. Os usuários atribuídos ao teste devem ser configurados com as políticas de voz desejadas. Os testes estendidos são passados para o cmdlet **New-CsWatcherNodeConfiguration** usando um comando semelhante a este:

    -ExtendedTests @{Add=$pstnTest1,$pstnTest2,$pstnTest3}

Se New-CsWatcherNodeConfiguration é chamado sem usar o parâmetro Tests, isso significa que somente as transações sintéticas Padrão (e a transação sintética estendida especificada) serão ativadas no novo nó do inspetor. Isso significa que o nó do inspetor testará os seguintes componentes:

  - Registro

  - IM

  - GroupIM

  - P2PAV (sessões de áudio/vídeo ponto a ponto)

  - AvConference (áudio/conferência)

  - Presença

  - ABS (serviço do Catálogo de Endereços)

  - ABWQ (serviço Web do Catálogo de Endereços)

  - PSTN (chamadas de gateway PSTN, especificadas como um teste estendido. Por padrão, a PSTN está desativada. O teste está ativado somente nesse caso, pois o comando ativou a PSTN usando o parâmetro ExtendedTests).

Isso também significa que os seguintes componentes não serão testados por padrão:

  - AVEdgeConnectivity

  - MCXP2PIM (mensagens instantâneas de dispositivo móvel)

  - ExumConnectivity (Unificação de Mensagens do Exchange)

  - JoinLauncher

  - PersistentChatMessage

  - DataConference

  - XmppIM

  - UnifiedContactStore

## Adicionando e removendo Transações sintéticas

Depois que um nó do inspetor é configurado, é possível usar o cmdlet **Set-CsWatcherNodeConfiguration** para adicionar ou remover transações sintéticas do nó. Por exemplo, para adicionar o teste PersistentChatMessage ao nó do inspetor, use o método Add e um comando semelhante a este:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage"}

É possível adicionar vários testes separando os nomes de teste com vírgulas. Por exemplo:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Add="PersistentChatMessage","DataConference","UnifiedContactStore"}

Observe que um erro ocorrerá se um ou mais desses testes (por exemplo, DataConference) já estiverem ativados no nó do inspetor. Nesse caso, você receberá uma mensagem de erro semelhante a esta:

    Set-CsWatcherNodeConfiguration : There is a duplicate key sequence 'DataConference' for the 'urn:schema:Microsoft.Rtc.Management.Settings.WatcherNode.2010:TestName' key or unique identity constraint.

Quando esse erro ocorre, nenhuma alteração será aplicada. O comando deve ser executado novamente com o teste duplicado removido.

Para remover uma transação sintética do nó do inspetor, use o método Remove em vez de Add. Por exemplo, esse comando remove o teste ABWQ do nó do inspetor:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Remove="ABWQ"}

É possível usar o método Replace para substituir todos os testes ativados no momento por um ou mais testes novos. Por exemplo, se desejar que apenas um nó do inspetor execute o teste IM, você pode configurar isso usando este comando:

    Set-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" -Tests @{Replace="IM"}

Quando você executa o comando anterior, todas as transações sintéticas no nó do inspetor especificado serão desativadas exceto para IM.

## Exibindo e testando a configuração do nó inspetor

Se quiser exibir os testes que foram atribuídos ao nó do inspetor, use um comando semelhante a este:

    Get-CsWatcherNodeConfiguration -Identity "atl-cs-001.litwareinc.com" | Select-Object -ExpandProperty Tests

O comando anterior retornará informações semelhantes a essa, dependendo das transações sintéticas atribuídas ao nó:

    Registration
    IM
    GroupIM
    P2PAV
    AvConference
    Presence
    PersistentChatMessage
    DataConference


> [!TIP]
> Para exibir as transações sintéticas em ordem alfabética, use este comando:<BR>Get-CsWatcherNodeConfiguration –Identity "atl-cs-001.litwareinc.com" | Select-Object –ExpandProperty Tests | Sort-Object



Para verificar se um nó do inspetor foi criado, digite o seguinte comando no Shell de Gerenciamento do Lync Server:

    Get-CsWatcherNodeConfiguration

Você receberá informações semelhantes a estas:

    Identidade      : atl-cs-001.litwareinc.com
    TestUsers     : {sip:watcher1@litwareinc.com, sip:watcher2@litwareinc.com ...}
    ExtendedTests : {TestUsers=IList<System.String>;Name=PSTN Test; Te...}
    TargetFqdn    : atl-cs-001.litwareinc.com
    PortNumber    : 5061

Para verificar que o nó do inspetor foi configurado corretamente, digite o seguinte comando no Shell de Gerenciamento do Lync Server:

    Test-CsWatcherNodeConfiguration

O comando anterior testará o nó do inspetor em sua implantação e informará se:

  - A função Registrador necessária foi instalada.

  - A chave de registro necessária foi criada por você ao executar Set-CsWatcherNodeConfiguration.

  - Seus servidores estão executando com uma versão correta do Lync Server.

  - Suas portas foram configuradas corretamente.

  - Seus usuários de teste atribuídos têm as credenciais necessárias.

