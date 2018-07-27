---
title: 'Lync Server 2013: Notas de versão'
TOCTitle: Notas de versão
ms:assetid: 9f9e864c-3365-4800-803c-5289bd8fd363
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205120(v=OCS.15)
ms:contentKeyID: 49307620
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Notas de versão para Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Bem-vindo às notas de versão do Lync Server 2013. Consulte esse arquivo para obter informações sobre problemas conhecidos do Lync Server 2013.

## Sobre este documento

Este documento contém informações importantes que você deve conhecer antes de implantar e usar o Lync Server 2013. Para obter detalhes sobre o Lync Server 2013, consulte a documentação do [Microsoft Lync Server 2013](microsoft-lync-server-2013.md).

Este documento contém as seguintes seções:

   Cliente Lync 2013

   Lync Server

   Instalação

   Mobilidade

   Conferência

   Enterprise Voice

   Presença

   Aplicativo Grupo de Resposta, Aplicativo de Estacionamento de Chamada e Recebimento de Chamadas de Grupo

   Painel de Controle do Lync Server, Construtor de Topologias e Ferramenta de Planejamento

   Localização

   Direitos autorais

## Cliente Lync 2013

## A transferência de um arquivo em uma mensagem instantânea falhará se o arquivo for aberto em outro aplicativo (1920369)

**Problema:**

Se você tentar transferir um arquivo, como um documento do Word, incluindo-o em uma mensagem instantânea para outro usuário do Lync, a transferência aparentemente será bem-sucedida, mas, na verdade, poderá não ocorrer a transferência do arquivo. Um ícone para o tipo de arquivo será exibido no cliente Lync, mas o arquivo não poderá ser aberto pelo receptor desejado. Nenhuma mensagem de erro será exibida para informar que a transferência não foi bem-sucedida.

**Solução alternativa:**

Para solucionar esse problema, feche o arquivo aberto ou o aplicativo que foi aberto antes da tentativa de transferência do arquivo em uma mensagem instantânea.

## Lync Server

## Se a replicação de dados do Serviço de Armazenamento do Lync Server falhar, os administradores precisarão verificar os contadores de desempenho dos itens obsoletos na fila do serviço de armazenamento (3225121)

**Problema:**

O Serviço de Armazenamento do Lync Serverusa o Windows Fabric para replicação. Se os dados são excluídos em um Servidor Front-End principal, mas a exclusão em um Servidor Front-End secundário falhar (por exemplo, se houver um desligamento inesperado ou erro no Servidor Front-End), os dados podem ficar para trás e "órfãos". Os dados órfãos podem degradar o desempenho e desperdiçar espaço em disco.UNRESOLVED\_TOKEN\_VAL()UNRESOLVED\_TOKEN\_VAL()UNRESOLVED\_TOKEN\_VAL()UNRESOLVED\_TOKEN\_VAL()

**Solução alternativa:**

Para resolver este problema, se os eventos LYSS\_DB\_SPACE\_USED\_ERROR (Id=32058) e LYSS\_DB\_SPACE\_USED\_CRITICAL (Id=32059) forem gerados no log do evento, os administradores deverão verificar os contadores de desempenho no Servidor Front-End em **LS:LYSS - API do Serviço de Armazenamento** com um nome de **LYSS - Número atual de itens obsoletos da fila de Serviço de Armazenamento**. Se este contador de desempenho tiver um valor alto, por exemplo, maior que 50.000, o administrador deve executar a ferramenta CleanuUpStorageServiceData.exe no Resource Kit do Lync Server 2013, que excluirá todos os dados órfãos do pool. Para obter detalhes sobre a ferramenta, consulte a documentação do Resource Kit do Lync Server 2013.

## Sempre que a configuração de endereço IP for alterada para um servidor ou pool, os serviços do Lync Server devem ser reiniciados (3212447)

**Problema:**

Quando a configuração de endereço IP for alterada para uma implantação do Lync Server 2013, como alterar de IPv4 para Dual Stack ou de Dual Stack para IPv6, nem todos os componentes do servidor pegarão as alterações de configuração até que os serviços sejam reiniciados.

**Solução alternativa:**

Para solucionar esse problema, reinicie os serviços do Lync Server após alterar a configuração dos endereços de IP da implantação. Para isso, execute os cmdlets a seguir no Shell de Gerenciamento do Lync Server:

```
    Stop-CsWindowsService -graceful
```
```
    Start-CsWindowsService
```

## O cmdlet de transação sintética de conferência discada não está mais disponível no Pacote de Gerenciamento do Lync Server 2013 (3212342)

**Problema:**

O cmdlet de transação sintética de conferência discada **Test-CsDialInConferencing** não está mais disponível no Pacote de Gerenciamento do Lync Server 2013.

**Solução alternativa:**

O uso do cmdlet de transação sintética de conferência discada **Test-CsDialInConferencing** é suportado apenas internamente para uma empresa.

Os administradores podem continuar usando o cmdlet no Shell de Gerenciamento do Lync Server para solução de problemas. Se necessário, uma empresa também pode desenvolver um pacote de gerenciamento privado para executar o cmdlet internamente.

## O Serviço de log centralizado para se o tráfego de rede é interrompido quando os arquivos de log são copiados para compartilhamento de rede (3212464)

**Problema:**

Quando o Serviço de log centralizado é configurado para usar um caminho de rede (o valor do parâmetro CacheFileNetworkFolder do cmdlet **Get-CsClsConfiguration** é um caminho UNC válido), os arquivos de log em cache são copiados ao compartilhamento de rede. Se houver interrupção de tráfego de rede enquanto os arquivos são copiados, uma exceção ocorrerá causando a interrupção do serviço de log centralizado.

Esse serviço está configurado para reiniciar automaticamente até três vezes, assim o serviço se recuperará das três primeiras exceções.

**Solução alternativa:**

Não há solução para esse problema. Para identificar o problema, monitore o log de eventos do ID de Evento 7031 do "Gerenciador de Controle de Serviço" que registra quando o "Agente de Serviço de Log Centralizado do Lync Server" termina inesperadamente. Se isso acontecer mais que três vezes, reinicie manualmente o serviço usando o cmdlet **Start-CsWindowService**.

## Itens de fila de serviço de armazenamento que precisam ser importados manualmente (3211368)

**Problema:**

O Lync Server 2013 armazena dados sobre conferência e mensagens instantâneas, como mensagens arquivadas e registro de detalhes das chamadas (CDR), em um banco de dados em cada Servidor Front-End. Os dados são armazenados no banco de dados enquanto são processados, antes de serem entregues no destino planejado. Para melhorar o desempenho, o Lync Server 2013 exporta periodicamente os itens de fila do banco de dados local que não são processados por um período grande de tempo e os grava no armazenamento de arquivos. Se o armazenamento de arquivos estiver indisponível, os itens serão armazenados em cada Servidor Front-End. A mesma operação ocorre para evitar perda de dados durante o failover do pool.

Durante a operação de exportação, o Serviço de Armazenamento do Lync Server registra cada estágio no log de eventos com os IDs de evento 32075 (operação de liberação total iniciada), 32076 (operação de liberação total concluída), 32082 (liberação no nível de manutenção iniciada), 32083 (liberação no nível de manutenção concluída), 32089 (liberação ocorreu devido ao preenchimento do banco de dados). Esses dados não serão importados de volta automaticamente ao sistema para serem processados e entregues ao destino final ( SQL Server ou Exchange Server).

**Solução alternativa:**

Para importar os dados no sistema, os administradores precisarão usar a ferramenta ImportStorageServiceData no Kit de Recursos do Lync Server, que adiciona os dados de volta ao sistema para serem processados e entregues em seu destino final.

## As pesquisas de Consulta à web do Catálogo de Endereços falharão se o valor padrão de UseNormalizationRules for alterado para Falso (3175514)

**Problema:**

Se o valor padrão de UseNormalizationRules for alterado para Falso, as pesquisas de Consulta à web do Catálogo de Endereços falharão. Depois de alterar o valor, os usuários do Lync Client não conseguirão usar a consulta web do Catálogo de Endereços do Lync para pesquisar usuários.

**Solução alternativa:**

Se o valor padrão de UseNormalizationRules for definido como Falso, de forma que os usuários possam usar números de telefone como definido no Serviços de Domínio Active Directory sem que o Lync Server 2013 aplique regras de normalização, resolva esse problema fazendo o seguinte:

1.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

2.  Siga um destes procedimentos:
    
      - Se sua implantação contiver apenas servidores do Lync Server 2013, execute o cmdlet a seguir em nível global para alterar os valores de UseNormalizationRules e IgnoreGenericRules para verdadeiro:
        
            Set-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true
    
      - Se sua implantação incluir uma combinação de Lync Server 2013 e Lync Server 2010 ou Office Communications Server 2007 R2, execute o cmdlet a seguir e atribua-o a cada pool do Lync Server 2013 na topologia:
        
            New-CsAddressBookConfiguration -identity <XdsIdentity> -UseNormalizationRules=$true -IgnoreGenericRules=$true

3.  Espere para que a replicação de CMS ocorra em todos os pools.

4.  Modifique o arquivo de regras de normalização de telefone para sua implantação apagar o conteúdo. O arquivo está no compartilhamento de arquivo de cada pool do Lync Server 2013. Se o arquivo não estiver presente, crie então um arquivo vazio chamado "Company\_Phone\_Number\_Normalization\_Rules.txt".

5.  Espere alguns minutos para que todos os pools de Front End leiam os novos arquivos.

6.  Execute o cmdlet a seguir em cada pool do Lync Server 2013 em sua implantação.
    
        Update-csAddressBook

## O evento 21054 de erro no Servidor do Catálogo de Endereços é gerado uma vez por dia em cada pool do Lync 2013 (3195918)

**Problema:**

O Servidor do Catálogo de Endereços Lync Server 2013 gerará o evento 21054 de erro todos os dias ao realizar a manutenção diária. O erro é também gerado todas as vezes que um administrador executa o cmdlet **Update-csAddressBook**, mesmo quando uma atualização é bem sucedida. No entanto, esse evento de erro pode ser ignorado com segurança, quando a atualização é bem sucedida.

**Solução alternativa:**

Ao encontrar esse erro, execute o cmdlet a seguir:

    Debug-csAddressBookReplication -Poolfqdn <Pool FQDN for which the event was generated>

Se o cmdlet relatar que não há objetos não indexados ou abandonados, o evento de erro 21054 pode ser ignorado com segurança.

Além disso, o KHI (Key Health Indicator) "Usuários do catálogo de endereços indexados com sucesso" deverá estar desativado no System Center Operations Manager.

## As solicitações podem falhar quando IPv6 está configurado no pool de borda (3205810)

**Problema:**

Quando IPv6 está configurado no pool de borda, algumas solicitações pool de borda podem falhar.

**Solução alternativa:**

Para contornar esse problema, não configure um pool de borda com IPv6.

## O cmdlet invoke-csPoolFailback pode falhar durante o failback do pool (3206153)

**Problema:**

Ao tentar fazer o fail back de um pool, o cmdlet **invoke-csPoolFailback** pode falhar com o erro "Falha em completar o processo de hidratação após repetidas tentativas".

**Solução alternativa:**

Para solucionar esse problema, execute o cmdlet novamente e espere até que o cmdlet seja bem sucedido. Observe que o processo de failback pode levar vários minutos para ser concluído. Pode levar até 60 minutos para um pool com 20.000 usuários.

## Pode ocorrer perda de dados ao adicionar um Servidor Front-End para um pool já estabelecido (3015990) - Híbrido, Skype for Business Online

**Problema:**

Esse problema pode ocorrer em um ambiente onde um pool tenha mais que um Servidor Front-End, e você reiniciar um dos Servidores Front-End ou adicionar um novo Servidor Front-End que já fazia parte do pool.

Os usuários cujos os dados estão sendo arquivados podem enfrentar perda de dados até que um arquivamento de distribuição de dados estável seja estabelecido para o pool. Esse período de perda potencial de dados é limitada a 15 minutos para conversas entre duas pessoas e 30 minutos para conferências.

**Solução alternativa:**

Ao executar a manutenção, em vez de iniciar os Servidores Front-End no pool, um de cada vez, você deverá fazer o fail over do pool para outro pool, e então executar as tarefas de manutenção nos servidores. Você pode também tornar o serviço indisponível ao executar as tarefas de manutenção, e depois restaurar a disponibilidade quando a manutenção for concluída.

## Os administradores não conseguem obter contagem de licenciados usando o cmdlet Get-CsClientAccessLicense (3012255)

**Problema:**

Os administradores não conseguem obter uma contagem precisa de licenças usando o **Get-CsClientAccessLicense** cmdlet.

**Solução alternativa:**

Para verificar o tipo de licença de servidor, é possível executar o cmdlet **Get-CsService** para recuperar FQDN (Nomes de Domínio Completamente Qualificados) de todos os bancos de dados. Se o FQDN do Servidor Front-End for o mesmo do FQDN do banco de dados de back-end, a licença é uma licença para Standard Edition. Caso contrário, a licença é para Enterprise Edition.

## A contagem de licenciados do cliente não é informada com exatidão (3010175)

**Problema:**

Ao determinar as contagens de licença do cliente, você poderá enfrentar uma das seguintes condições:

1.  **Contagem de licenças de usuários móveis imprecisa**
    
    A contagem de licenças é baseada no número de endereços IP exclusivos de usuários baseados em dispositivos. A contagem de licenças será limitada das seguintes maneiras:
    
      - As licenças serão superestimadas se o endereço IP de um usuário for alterado durante sessões do Lync. Isso pode ocorrer quando um usuário se conectar ao Lync Server de mais de um local com um cliente desktop.
    
      - As licenças serão subestimadas se um usuário se conectar com um cliente móvel, pois o endereço IP do dispositivo não pode ser determinado.

2.  **As licenças são contadas duas vezes para chamadas da rede telefônica comutada pública (PSTN) para o cliente Lync, chamadas do cliente Lync para linhas PSTN e chamadas Lync transferidas para linhas PSTN**
    
    Nos seguintes cenários, duas licenças adicionais serão contadas ao invés de uma, pois o número de telefone e o usuário Lync são contados para determinar o número de licenças usadas. Para obter dados precisos sobre licenças, remova manualmente as licenças geradas por um número de telefone.
    
      - Uma chamada telefônica PSTN para Lync
    
      - Uma chamada Lync para uma linha PSTN
    
      - Uma chamada PSTN para Lync, e depois o Lync transfere a chamada para uma linha PSTN. Uma das linhas PSTN será contada.

3.  **Uma licença para telefone Lync logado não será contada**
    
    Quando um usuário usa um telefone certificado pelo Lync, se o telefone fizer logon e permanecer conectado, retendo seu status de logon, o telefone não será contado como usando uma licença, se a consulta de licenças ocorrer após o logon do telefone.

4.  **São contadas licenças para telefones PSTN que participam de conferências**
    
    Quando um usuário participa de uma conferência com um telefone PSTN, uma licença será contada incorretamente para a participação na conferência, No entanto, nenhuma licença é necessária para participar de uma conferência com um telefone PSTN.

**Solução alternativa:**

1.  **Contagem de licenças de usuários móveis imprecisa**
    
      - Você pode identificar manualmente os endereços IP que pertencem ao mesmo dispositivo e depois remover um deles na contagem da licença.
    
      - Não há solução para esse problema com dispositivos móveis se conectado ao cliente Lync.

2.  **As licenças são contadas duas vezes para chamadas PSTN para o cliente Lync, chamadas do cliente Lync para linhas PSTN, e chamadas Lync transferidas para linhas PSTN**
    
    Você precisa identificar manualmente o número de telefone PSTN e remover a contagem de licença gerada para ele.

3.  **Uma licença não pode ser contada para um telefone do Lync logado**
    
    É possível configurar para que o telefone Lynch fala logoff e depois logon novamente, em intervalos regulares, como a cada 3 meses.

4.  **São contadas licenças para telefones PSTN que participam de conferências**
    
    Você pode identificar manualmente o número de telefone PSTN que é usado para participar da conferência e remover a licença gerada pelo número de telefone.

## O Painel de Controle do Lync Server para de funcionar em um ambiente VMware após atualização para Silverlight 5 (3010077)

**Problema:**

Se você usar o Painel de Controle do Lync Server em um ambiente VMware, o Painel de Controle do Lync Server pode parar de funcionar após a atualização do Microsoft Silverlight para versão 5.

**Solução alternativa:**

Para contornar esse problema, siga um destes procedimentos:

  - Desinstale o Silverlight 5 e instale o Silverlight 4 de [http://go.microsoft.com/fwlink/p/?LinkID=149156](http://go.microsoft.com/fwlink/p/?linkid=149156).

  - Acessar o Painel de Controle do Lync Server de um computador que não é um computador virtual VMware.
    
    Para isso, você pode iniciar o Painel de Controle do Lync Server a partir do menu **Iniciar** do Windows no servidor, se as ferramentas de administração do Lync Server estiverem instaladas no computador.
    
    Você pode também acessar o Painel de Controle do Lync Server usando um navegador web. O URL será parecido com https://\<frontend\_pool\_fqdn\>/cscp.

## As informações do usuário no Serviço de Catálogo de Endereços não são atualizadas depois que um nome distinto de usuário foi modificado no Active Directory (3211549)

**Problema:**

Se um um nome distinto de usuário (conhecido também como DN) for alterado no Serviços de Domínio Active Directory, todas as alterações adicionais não serão atualizadas no Serviço de Catálogo de Endereços (ABS). Isso não afeta a entrada ou presença do usuário, mas impedirá a comunicação do usuário, se o endereço SIP for também alterado, pois as pesquisas retornarão um endereço SIP desatualizado.

**Solução alternativa:**

Para solucionar esse problema, não mude o DN de um usuário. Se você reverter o DN do usuário para o valor anterior, as atualizações se refletirão no Serviço de Catálogo de Endereços.

## Instalação

## O uso de caracteres não ASCII pode resultar na falha de inicialização do Lync Server

**Problema:**

Haverá falha na instalação se o nome da pasta de destino incluir caracteres não ASCII (incluindo UNICODE, conjunto de caracteres de dois bytes (DBCS), UTF-8 e UTF-16). Além disso, a instalação pode ser executada com sucesso, mas o servidor não será iniciado se caracteres não ASCII estiverem contidos em qualquer um dos seguintes:

  - Nome do computador

  - Nome do domínio

  - Nome do usuário

  - URI do SIP do usuário

  - Nome da conta do serviço

**Solução alternativa:**

Use somente caracteres ASCII no nome da pasta de destino, nome do computador, nome do domínio, nome do usuário, URI do SIP do usuário e nomes de conta do serviço.

## O hotfix para "Corrupção de pilha ocorre quando um módulo chama o método InsertEntityBody no IIS 7.5" deve ser instalado antes de instalar o Lync Server 2013

**Problema:**

O hotfix para "Muitas corrupções ocorrem quando um módulo chama o método InsertEntityBody no IIS 7.5" ( [http://go.microsoft.com/fwlink/?linkid=268602\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268602%26clcid=0x416)) descrito no artigo 264886 da Base de Dados de Conhecimento Microsoft ( [http://go.microsoft.com/fwlink/?linkid=268603\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268603%26clcid=0x416)), deve estar instalado antes de instalar o Lync Server 2013.

**Solução alternativa:**

Baixe e instale o hotfix pelo Centro de Download da Microsoft em [http://go.microsoft.com/fwlink/?linkid=268602\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=268602%26clcid=0x416).

## O Lync Server 2013 falha ao instalar a versão OS RTM do ITA Windows Server 2012 (3179467)

**Problema:**

A instalação do Lync Server 2013 falha no ITA Windows Server 2012 devido à falha na instalação do Windows Fabric.

A instalação do Windows Fabric falha, pois os traços de estrutura são criados com o formato de hora HH:MM:SS. No entanto, no ITA Windows Server, o formato é HH.MM.SS.

**Solução alternativa:**

Para solucionar esse problema, atualize o registro do sistema antes de instalar o Lync Server 2013. A chave do registro que precisa ser atualizada é: HKEY\_USERS\\.DEFAULT\\Control Panel\\International\\sTimeFormat. Altere o valor de sTimeFormat para HH:mm:ss usando o Interface da linha de comando do Windows PowerShell, da seguinte maneira:

1.  Execute o Windows PowerShell e os seguintes cmdlets:
    
    ```
        New-PSDrive -Name HKU -PSProvider Registry -Root HKEY_USERS
    ```
    ```    
        $a="HKU:\.Default\Control Panel\International"
    ```

2.  Para exibir o valor atual, execute o seguinte cmdlet:
    
        Get-itemproperty $a -Name sTimeFormat
    
    Anote o valor atual do sTimeFormat para que ele possa ser restaurado após a conclusão da instalação.

3.  Para definir o novo valor, execute o seguinte cmdlet:
    
        Set-ItemProperty $a -Name sTimeFormat -Value "HH:mm:ss"

4.  Depois da instalação bem sucedida do Lync Server 2013, restaure o valor original do sTimeFormat, executando o seguinte cmdlet:
    
        - Set-ItemProperty $a -Name sTimeFormat -Value "<Value noted down in Step 3. above>"

## Mobilidade

## Problemas para clientes móveis durante o processo de failover do servidor (3345992)

**Problema:**

Quando um Servidor Lync falha e o processo de failover começa, os problemas a seguir podem afetar usuários de cliente móvel:

  - Nenhuma chamada do Lync de entrada ou sinal por até 10 minutos após o início do failover.

  - Não é possível aceitar solicitações de Chat de entrada

  - Não será possível ingressar em reuniões caso o servidor com falha seja o servidor inicial do usuário

**Solução alternativa:**

Não há solução alternativa para este problema. A funcionalidade normal será restaurada assim que o processo de failover estiver concluído.

## Se um usuário móvel recusar uma chamada de entrada de outro ponto de extremidade do Lync, a chamada será exibida como uma conversão perdida em clientes do Lync Mobile (3346251)

**Problema:**

Se um usuário móvel recusar uma chamada de entrada, e se a chamada tiver sido originada de outro ponto de extremidade do Lync, a chamada será exibida como uma conversa perdida no cliente do Lync Mobile em de como uma chamada na lista de chamadas do dispositivo.

**Solução alternativa:**

Não há solução alternativa para este problema.

## O cliente móvel pode não exibir um nome para exibição do contato federado ao pesquisar contatos (3346256)

**Problema:**

O nome para exibição de contatos federados pode não ser exibido em alguns cenários, como durante uma pesquisa de um contato federado na lista de contatos. Isso poderá ocorrer quando não houver assinatura de presença ativa para o contato do cliente móvel do Lync.

**Solução alternativa:**

Não há solução alternativa para este problema.

## No cliente móvel, as informações do convidado e do carimbo de data/hora estão ausentes de uma conversa perdida que é um convite para uma conferência (3346265)

**Problema:**

No cliente móvel, quando uma conversa perdida for um convite para uma conferência, as informações sobre o convidado e o carimbo de data/hora estarão ausentes da mensagem de conversa perdida.

**Solução alternativa:**

Não há solução alternativa para este problema.

## Usuários de cliente móvel que fazem chamadas usando VoIP não conseguem deixar uma mensagem na caixa postal para usuários cujas caixas postais tiverem sido configuradas no Exchange 2010 ou em versões anteriores (3346260)

**Problema:**

Se um usuário de cliente móvel estiver usando VoIP para fazer chamadas, o usuário não conseguirá deixar mensagens de caixa postal para usuários configurados para usar a caixa postal no Microsoft Exchange Server 2007 ou no Microsoft Exchange Server 2010.

**Solução alternativa:**

Para contornar o problema, use o Exchange 2010 com SP1 ou versão posterior do Microsoft Exchange Server.

## Ao usar Bloquear com URL para a Configuração de Versão de Cliente em clientes móveis, uma mensagem de erro incorreta poderá ser exibida (3346258)

**Problema:**

A usar **Bloquear com URL** para a Configuração de Versão de Cliente em clientes móveis, uma mensagem de erro incorreta poderá ser exibida quando a versão do cliente não tiver suporte.

**Solução alternativa:**

Para contornar o problema, defina a Configuração de Versão de Cliente para usar **Bloquear** em vez de **Bloquear com URL**.

## Conferência

## Software antivírus executando no Lync Server 2013Servidores Front-End pode ocasionar reciclagem do Domínio de Aplicativos, que interrompe temporariamente os serviços dos clientes do Lync Web App 2013, Lync Mobile 2010, e Lync Mobile 2013 (3212531)

**Problema:**

O software antivírus pode disparar a reinicialização de domínios do aplicativo, fazendo com que o Lync Mobility Service 2013 e os aplicativos clientes da PAI de comunicações unificadas (UC) ( Lync Web App 2013, Lync Mobile 2010 e Lync Mobile 2013) percam seu estado.

**Solução alternativa:**

Para solucionar esse problema, exclua as pastas que contêm os componentes web e .NET framework da verificação do antivírus. Para obter detalhes, consulte o artigo 312592 da Base de Dados de Conhecimento Microsoft, "PRB: Reinicializações aleatórias de aplicativo com o erro "O aplicativo está reinicializando" no ASP.NET," em [http://go.microsoft.com/fwlink/?linkid=3052\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=3052%26clcid=0x416).

As seguintes pastas devem ser excluídas:

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Mcx\\Ext

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Mcx\\Int

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Ucwa\\Int

  - %ProgramFiles%\\Microsoft Lync Server 2013\\Web Components\\Ucwa\\Ext

  - %Windir%\\Microsoft.NET\\Framework64\\v4.0.30319\\Config

## ActiveX Controls ou suporte XMLHTTP nativo deve ser ativado no Windows Internet Explorer para participar com sucesso de conferências (2798163)

**Problema:**

Se um usuário desativar o ActiveX Controls e o suporte XMLHTTP nativo nas configurações do navegador de Internet Windows Internet Explorer, ele não poderá participar de uma reunião se o Internet Explorer for selecionado como navegador padrão.

**Solução alternativa:**

Ative o ActiveX Controls ou "suporte XMLHTTP nativo" no Internet Explorer.

## O serviço de Conferência Web do Lync Server não consegue se recuperar de um modo crítico (2788663)

**Problema:**

Se o modo crítico estiver voltado para arquivamento, em caso de falhas do sistema, o modo crítico irá iniciar e as conferências não funcionarão mais para os participantes. Após as correções do administrador nas falhas do sistema (como corrigir um problema de banco de dados), o serviço de conferência de dados não se recuperará automaticamente, e o administrador deverá reiniciar manualmente o serviço de conferência para que a conferência seja retomada.

**Solução alternativa:**

Um administrador precisa reiniciar manualmente o serviço de conferência após a correção de uma falha do sistema.

## O serviço de webconferência ignora o proxy HTTP de servidores externos do Office Web App (2602182)

**Problema:**

Se você implantou um Servidor Office Web Apps externo ao serviço de Webconferência (isto é, um servidor que não seja interno à rede corporativa) na Internet, rede de perímetro e o serviço de Webconferência exigir um proxy HTTP para se conectar, o descobrimento do Servidor Office Web Apps falhará. O serviço de Webconferência ignora a configuração do proxy HTTP, como definido em Construtor de Topologias para configuração do Servidor Office Web Apps. Como resultado, o cliente Lync não conseguirá compartilhar Microsoft PowerPoint 2010 outros participantes da conferência. Se você estiver instalando o Lync Server no local e também configurar o Servidor Office Web Apps no local na rede interna, não será necessário configurar o proxy.

**Solução alternativa:**

A única solução é não ter uma configuração e implantação que exija o uso de proxy HTTP para se comunicar com um Servidor Office Web Apps externo.

## Adicionar vídeo a uma conferência de provedor de conferência de áudio não é suportado (2603861)

**Problema:**

Adicionar um vídeo não é suportado se o usuário ingressar por uma conferência de áudio de um provedor de conferência de áudio.

**Solução alternativa:**

Não há solução alternativa para este problema.

## As topologias com IPv6 ativado forçam o plug-in Lync Web App Silverlight a se atualizar automaticamente para garantir que a funcionalidade de compartilhamento de tela possa funcionar do Lync Web App (2604634)

**Problema:**

Quando uma topologia é configurada com IPv6 ativado, os usuários não podem compartilhar sua tela com o cliente do Lync Web App, se uma versão anterior do plug-in de compartilhamento de tela estiver já instalado.

**Solução alternativa:**

Para forçar uma atualização para a versão mais recente do plug-in de compartilhamento de tela ao ingressar na reunião através do Lync Web App, modifique o valor de **MinSupportedBuildVersion** de "4.0.7457.0" para "4.0.7577.380" nos dois arquivos a seguir:

  - %ProgramFiles%\\Microsoft Lync Server 15\\Web Components\\Reach\\Int\\Client\\Plugins\\ReachAppShPluginProperties.xml

  - %ProgramFiles%\\Microsoft Lync Server 15\\Web Components\\Reach\\Ext\\Client\\Plugins\\ReachAppShPluginProperties.xml

## Enterprise Voice

## Em alguns casos, um cliente do Lync em execução em um computador configurado para usar uma pilha dupla de IPv4 e IPv6 poderá não ter suporte a recursos baseados na sub-rede IP do computador, como E911, Desvio de Mídia, Controle de Admissão de Chamadas e Roteamento com Base no Local (3335508)

> [!NOTE]  
> A informação nesta seção está relacionada às Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

**Problema:**

Quando um cliente do Lync estiver em execução em um computador habilitado para a pilha dupla de IPv4 e IPv6 e for baseado na resolução de DNS do servidor proxy, poderá usar o endereço IPv6 do computador para entrar. Depois de fazer isso, o Cliente do Lync só dará suporte aos recursos com suporte do IPv6, o que exclui E911, Desvio de Mídia, Controle de Admissão de Chamadas e Roteamento com Base no Local.

**Solução alternativa:**

Para contornar esse problema, desabilite o suporte a IPv6 no computador cliente.

## Se o Enterprise Voice não estiver configurado para um usuário, o usuário precisará usar o formato E164 para fazer uma discagem a partir de uma conferência (3215342)

**Problema:**

Se o Enterprise Voice não estiver configurado para um usuário, o usuário precisará usar o formato E164 para fazer uma discagem com sucesso a partir de uma conferência, Se o formato E164 não for usado, o usuário não poderá fazer uma discagem a partir de uma conferência.

**Solução alternativa:**

Para solucionar esse problema, os usuários que não estão habilitados para Enterprise Voice deverão discar a partir de uma conferência usando números no formato E164.

## Presença

## Se um usuário selecionar "Bloquear todos os convites e comunicações" enquanto o armazenamento de contato unificado estiver ligado para o usuário, o status de Presença não será rejeitado quando deveria (3204526)

**Problema:**

Se um usuário selecionar "Bloquear todos os convites e comunicações" enquanto o armazenamento de contato unificado estiver ligado para o usuário, o status de Presença não será rejeitado quando deveria.

**Solução alternativa:**

Para solucionar esse problema, você pode desligar o armazenamento de contato unificado do usuário. Para isso, execute os seguintes cmdlets:

    Set-CsUserServicesPolicy -Identity "<user display name>" -UcsAllowed $False

Por exemplo:

    Set-CsUserServicesPolicy -Identity "Ken Myer" -UcsAllowed $False

## Os usuários do Office Communications Server 2007 R2 hospedados no local não poderão ver o status de Presença de usuários do Skype for Business Online em implantações híbridas (3014624) - Híbrida

**Problema:**

Esse problema pode ocorrer em uma implantação híbrida quando você estiver usando um Diretor do Lync Server 2013.

O status de presença de usuários hospedados para Skype for Business Online é exibido como Presença Desconhecida para usuários no local. Além disso, os usuários hospedados para Skype for Business Online não podem ver os status de presença de usuários do Office Communications Server R2 no local.

**Solução alternativa:**

Para solucionar parcialmente esse problema, altere o servidor primário (msrtcsip-presencehomeserver) dos usuários do Skype for Business Online para apontar para o pool Lync Server 2013 no local, em vez do Diretor do Lync Server 2013. Você pode modificar essa configuração no Servidor Front-End no local.

Essa solução exibirá corretamente o status de Presença dos usuários hospedados para Office Communications Server 2007 R2 para usuários do Skype for Business Online.

## Aplicativo Grupo de Resposta, Aplicativo de Estacionamento de Chamada e Recebimento de Chamadas de Grupo

## Um chamador pode ouvir um segundo de música em espera durante o estabelecimento de uma chamada com a parte de recuperação (3334097)

> [!NOTE]  
> A informação nesta seção está relacionada às Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

**Problema:**

Quando uma chamada é recuperada via Recebimento de Chamadas de Grupo, o chamador poderá ouvir um segundo de música em espera durante o estabelecimento da chamada com a parte do recuperador.

**Solução alternativa:**

Não há solução alternativa para este problema.

## Um agente do Grupo de Resposta pode entrar e sair no sistema através de um Console de Agente do Lync Server 2010 apenas para Grupos de Agente Lync Server 2010 formais (2773455)

**Problema:**

Um agente do Lync Server 2013Grupo de Resposta pode entrar e sair no sistema através de um Console de Agente do Lync Server 2010 apenas para Grupos de Agente Lync Server 2010 formais. No Console de Agente do Lync Server 2010, os usuários podem ver apenas o Lync Server 2010Grupo de Resposta ao qual eles pertencem. Eles não podem ver nenhum dos Grupos de Resposta do Lync Server 2013 aos quais eles pertencem.

**Solução alternativa:**

Se o agente do Grupo de Resposta é um usuário do Lync Server 2013 e parte de um Grupo de Agente formal do Lync Server 2013, o usuário deverá acessar o Console do Agente do Lync Server 2013 diretamente através de um link da web em um navegador para entrar e sair do sistema a partir dos Grupos de Agente do Lync Server 2013.

## Um agente do Lync Server 2010Grupo de Resposta não pode fazer chamadas em nome de um Lync Server 2013Grupo de Resposta (2773471)

**Problema:**

Um usuário do Lync Server 2010 que é agente de um Lync Server 2013Grupo de Resposta não pode fazer chamadas em nome do Grupo de Resposta. O Lync Server 2013Grupo de Resposta não estará disponível no cliente do Lync para fazer uma chamada.

**Solução alternativa:**

Para solucionar esse problema, é necessário mover o usuário do Lync Server 2010 para Lync Server 2013.

## Remover um Grupo de Resposta do Lync Server 2010 após ele ter sido migrado para o Lync Server 2013 evitará que o Grupo de Resposta aceite qualquer chamada (3016227)

**Problema:**

Se um Grupo de Resposta que foi migrado do Lync Server 2010 para Lync Server 2013 for removido do Lync Server 2010 através do Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server, o Grupo de Resposta no Lync Server 2013 parará de receber chamadas.

**Solução alternativa:**

Para solucionar esse problema, não remova nenhum Grupo de Resposta do Lync Server 2010 que tenha sido migrado do Lync Server 2010 para o Lync Server 2013.

Se o Grupo de Resposta já tiver sido removido, você deverá reinstalá-lo no Lync Server 2013.

## Quando um novo fluxo de trabalho gerenciado for definido como inativo ao ser criado, a implantação do fluxo de trabalho falhará (3207527)

**Problema:**

Quando um novo fluxo de trabalho gerenciado for definido como inativo ao ser criado, a implantação do fluxo de trabalho falhará. Esse problema é encontrado quando o fluxo de trabalho é definido como inativo ao ser criado, mas não afeta um fluxo de trabalho que é editado para defini-lo como inativo após ter sido implantado.

**Solução alternativa:**

Ao criar e implantar um fluxo de trabalho, defina o fluxo de trabalho como ativo e depois implante-o. Após ele ter sido implantado com sucesso, o fluxo de trabalho pode ser editado e definido como inativo.

## Remover um Grupo de Resposta do pool Proprietário impedirá que o Grupo de Resposta do pool de Backup aceite qualquer chamada durante o failover, se o Grupo de Resposta foi importado para o pool de back up (3016214)

**Problema:**

Se um Grupo de Resposta de propriedade do pool primário for importado ao pool de back up sem sobrescrever o proprietário, e o Grupo de Resposta for removido do pool do proprietário, o Grupo de Resposta no pool de backup não aceitará chamadas durante o failover.

**Solução alternativa:**

Você vai precisar implantar novamente o Grupo de Resposta no pool primário. Você então precisará exportar a configuração do Grupo de Resposta do pool primário e importá-la no pool de backup novamente.

Você também pode recriar o Grupo de Resposta no pool de backup. Neste caso, o pool de backup será o pool proprietário do Grupo de Resposta

## Uma chamada estacionada não pode ser recuperada do Aplicativo de Estacionamento de Chamada se a solicitação de recuperação for feita em nome de um Grupo de Resposta (3211798)

**Problema:**

Quando as seguintes condições forem verdadeiras, uma solicitação de recuperação para chamada estacionada falhará:

  - Um agente é parte de um Grupo de Resposta anônimo

  - O agente tenta recuperar uma chamada estacionada do Aplicativo de Estacionamento de Chamada através do Grupo de Resposta anônimo

  - O agente tenta recuperar a chamada discando o número de órbita através da opção Chama em Nome ou através da mesma opção no cliente atendedor do Lync

**Solução alternativa:**

Não há nenhuma solução alternativa para este problema. A chamada estacionada deve ser recuperada sem fazer isso em nome de um Grupo de Resposta.

## Painel de Controle do Lync Server, Construtor de Topologias e Ferramenta de Planejamento

## Limitações da Ferramenta de Planejamento (3331056 e 3331059)

> [!NOTE]  
> A informação nesta seção está relacionada às Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

**Problema:**

A Ferramenta de Planejamento tem as seguintes limitações durante o planejamento da sua implantação:

  - Há um máximo de 10 sites centrais com suporte

  - Cada site central pode ter até 14 sites de ramificação

  - Cada site central pode ter, no máximo, 240.000 usuários

Além disso, a Ferramenta de Planejamento não inclui valores para o seguinte durante o cálculo da topologia recomendada:

  - O número de usuários online iniciais

  - A porcentagem de usuários habilitados para a federação XMPP

  - A porcentagem de usuários usando o Lync Web App

**Solução alternativa:**

Não há solução alternativa para estes problemas. Para obter mais informações sobre a Ferramenta de Planejamento, consulte [Projetando a topologia para Lync Server 2013 usando a Ferramenta de Planejamento](lync-server-2013-designing-the-topology-by-using-the-planning-tool.md).

## A Ferramenta de Planejamento não pode usar endereços IP definidos anteriormente para a rede Edge ao atualizar opções

**Problema:**

Depois de concluir seu design usando a Ferramenta de Planejamento, se você fizer alterações nas opções da Rede Edge, endereços IP adicionais poderão ser adicionados ao design em vez da atualização dos endereços IP existentes. Isso poderá ocorrer quando você estiver exibindo os detalhes do Diagrama de Rede Edge, selecionar **Clique aqui para atualizar suas opções** e, então, na caixa de diálogo Opções de Configuração, selecionar Rede Edge e selecionar **Eu quero usar os mesmos FQDNs e endereços IP, mas portas diferentes para os serviços edge em meu Servidor Edge**. A aplicação de qualquer alteração poderá resultar em novos endereços IP e servidores Edge adicionados ao design.

**Solução alternativa:**

Não há solução alternativa para este problema no momento.

## No Painel de Controle do Lync Server, "Mover todos os usuários para o pool" pode não funcionar como o esperado (3199270)

**Problema:**

Ao usar o Painel de Controle do Lync Server para mover todos os usuários de um pool para outro em um ambiente do Active Directory complexo, como um com vários Controladores de Domínio e domínios pai/filhos, uma mensagem de erro pode retornar dizendo "O usuário especificado não é um usuário herdado, em vez disso, use o cmdlet Move-CsUser". Isso é resultado de um tempo de replicação maior em ambientes complexos do Active Directory.

**Solução alternativa:**

Para contornar esse problema, siga um destes procedimentos:

  - Use filtros no Painel de Controle do Lync Server para procurar usuários herdados, selecione esses usuários, e depois use o **comando Mover usuários selecionados para o pool**, em vez de **Mover todos os usuários para o pool**.

  - Use o Shell de Gerenciamento do Lync Server para mover usuários herdados batches usando os cmdlets Lync Server.

## O Painel de Controle do Lync Server para de funcionar em um ambiente VMware depois que o Plug-in do navegador do Microsoft Silverlight é atualizado para a versão 5 (3199270)

**Problema:**

Se você usar o Painel de Controle do Lync Server em um ambiente VMware, o Painel de Controle do Lync Server pode parar de funcionar após a atualização do Silverlight para versão 5.

**Solução alternativa:**

Para contornar esse problema, siga um destes procedimentos:

  - Desinstale o Silverlight 5 e depois instale o Silverlight 4 de [http://go.microsoft.com/fwlink/?linkid=149156\&clcid=0x416](http://go.microsoft.com/fwlink/?linkid=149156%26clcid=0x416).

  - Abra o Painel de Controle do Lync Server de um computador que não é um computador virtual VMware.
    
    Para abrir o Painel de Controle do Lync Server a partir de um computado remoto, instale as ferramentas Administrativas do Lync Server no computador e depois inicie o Painel de Controle do Lync Server do menu **Iniciar** do Windows.
    
    Você pode também abrir o Painel de Controle do Lync Server inserindo o URL em um navegador web. O URL será similar a https://\<frontend\_pool\_fqdn\>/cscp.

## Um administrador não consegue executar o cmdlet Uninstall-csMirrorDB após remover o banco de dados de espelhamento no Construtor de Topologias (3199266)

**Problema:**

Quando um administrador desativa um banco de dados de espelhamento no Construtor de Topologias, e depois exclui o banco de dados de espelhamento no Construtor de Topologias, uma mensagem é exibida na lista de tarefas do administrador para executar o cmdlet **Uninstall-csMirrorDatabase** para remover o espelhamento do SQL Server. Quando o administrador tenta executar o cmdlet, ele falha.

**Solução alternativa:**

Para remover o espelhamento SQL de um pool no Construtor de Topologias, é necessário primeiro usar um cmdlet para remover o espelho no SQL Server. Você pode então usar o Construtor de Topologias para remover o espelho da topologia. Para remover o espelhamento no SQL Server, use o seguinte cmdlet:

    Uninstall-CsMirrorDatabase -SqlServerFqdn <SQLServer FQDN> [-SqlInstanceName <SQLServer instance name>] -DatabaseType <Application | Archiving | CentralMgmt | Monitoring | User | BIStaging | PersistentChat | PersistentChatCompliance> [-DropExistingDatabasesOnMirror] [-Verbose]

Por exemplo, para remover o espelhamento e soltar os bancos de dados para os banco de dados do usuário, digite o seguinte:

    Uninstall-CsMirrorDatabase -SqlServerFqdn primaryBE.contoso.com -SqlInstanceName rtc -Verbose -DatabaseType User -DropExistingDatabasesOnMirror

O parâmetro *DropExistingDatabasesOnMirror* faz com que os banco de dados afetados sejam excluídos do espelho. Depois, para remover o espelho da topologia, faça o seguinte:

1.  Em Construtor de Topologias, clique com o botão direito no pool e clique em **Editar Propriedades**.

2.  Desmarque **Habilitar espelhamento de armazenamento SQL** e clique em **OK**.

3.  Publique a topologia.

> [!IMPORTANT]  
> Sempre que você fizer uma alteração em uma relação de espelhamento de banco de dados de backend, será necessário reiniciar todos os Servidores Front-End no pool.

## Erros de validação são retornados no Construtor de Topologias quando um administrador tenta remover uma implantação com um pool de front end que tenha um armazenamento testemunha associado (3199266)

**Problema:**

Se um administrador tenta usar o comando **Remover Implantação** no Construtor de Topologias para remover uma implantação que inclui um pool de front end com um armazenamento testemunha associado, um erro de validação é exibido no Construtor de Topologias e ação não prossegue.

**Solução alternativa:**

Para contornar esse problema, siga um destes procedimentos:

  - Remova o armazenamento testemunha antes de tentar remover a implantação.

  - Adicione um armazenamento testemunha para o pool de front end e depois remova-o.

## As informações de implantação do Servidor de Chat Persistente são inconsistentes entre a Ferramenta de Planejamento e o Construtor de Topologias (3012228)

**Problema:**

Quando o Lync Server 2013, Ferramenta de Planejamento produz o diagrama da topologia do site de uma implantação do Servidor de Chat Persistente com recuperação de desastres ativada, o diagrama da topologia do site inclui vários sites (físicos), com Servidores de Chat Persistente atribuídos uniformemente em cada site. No Construtor de Topologias, todos os Servidores de Chat Persistente são representados como pertencentes a um único site (lógico) e estão listados sob o mesmo nó do Pool de Servidor de Chat Persistente.

**Solução alternativa:**

Atualmente, não há solução para esse problema. O usuário deve analisar o resultado do Ferramenta de Planejamento para a implantação do Servidor de Chat Persistente e modificar o plano para atender suas necessidades específicas.

## Localização

## Monitoramento

## O assistente Implantar relatórios de monitoramento exibe caracteres incorretos sob certas circunstâncias ao usar a versão do leste da Ásia do Lync Server (3113565)

**Problema:**

Ao usar uma versão do leste da Ásia do Lync Server 2013, por exemplo, chinês (simplificado), chinês (tradicional), japonês ou coreano, em um sistema operacional que tenha o local do sistema não definido para um idioma do leste da Ásia, o assistente Implantar relatórios de monitoramento exibe pontos de interrogação ou outros caracteres em vez das mensagens localizadas.

**Solução alternativa:**

Para corrigir esse problema, defina o local do sistema operacional e Lync Server 2013 para o mesmo idioma, que todas as mensagens serão exibidas corretamente.

## Painel de Controle do Lync Server

## Em certos casos, o primeiro item da barra de navegação superior em uma página do Painel de Controle do Lync Server desaparece quando o último item na barra de navegação superior é clicado (3158118)

**Problema:**

Há três casos conhecidos onde clicar no último item na barra de navegação superior em uma página do Painel de Controle do Lync Server faz com que o primeiro item da barra de navegação superior desapareça:

  - Na versão francesa, na página "Féderation et accès externe", o item "Stratégie d'accès externe" desaparecerá quando o item "Partenaires fédérés XMPP" for clicado.

  - Na versão em alemão, na página "Clients", o item "Clientversionskonfiguration" desaparecerá quando "Pushbenachrichtigungskonfiguration" for clicado.

  - Na versão russa, na página "Конфигурация сети", o item "Глобально" desaparecerá quando "Маршрут региона" for clicado.

**Solução alternativa:**

Para solucionar esse problema, atualize a página do Painel de Controle do Lync Server em seu navegador. A página será carregada no navegador com todos os itens na barra de navegação superior sendo exibidos.

## Catálogo de Endereços

## A indexação no Catálogo de Endereços não funciona como esperado em alguns idiomas (3336047)

> [!NOTE]  
> A informação nesta seção está relacionada às Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

Se as propriedades de um usuário contiverem um campo indexado, e se esse campo contiver somente caracteres que não possam ser indexados, então o usuário não aparecerá em pesquisas realizadas no Catálogo de Endereços.

Os caracteres e as localidades a seguir não podem ser indexados:

  - Caracteres maiúsculos de cirílico, grego e armênio

  - Caracteres maiúsculos acentuados

  - Tailandês

  - Laosiano

  - Birmanês

  - Devanágari

  - Etíope

  - Tibetano

  - Bengalês

  - Guzerate

  - Télugu

  - Todos os outros scripts índicos

## Lync Web App, Agendador Web e componentes Web

## O fallback de idioma para determinados idiomas no Programador do Lync Web, Discagem, Iniciador de Ingresso, Gerenciamento de Sala de Chat Persistente e OCTab pode não funcionar como esperado (3079700)

**Problema:**

Ao selecionar um local neutro em um navegador da Web (no Internet Explorer, por exemplo, o nome do idioma sem maiores especificações, como "Norueguês \[no\]"), em vez de um idioma que especifica o local (como "Norueguês, Bokmål (Noruega) \[nb-NO\]") pode levar a um comportamento de exibição inesperado para certos idiomas no Programador do Lync Web, Discagem, Iniciador de Ingresso, Gerenciamento de Sala de Chat Persistente e OCTab. Para obter exemplos, os usuários podem consultar a página em inglês quando um dos seguintes idiomas é selecionado:

  - Norueguês

  - Português

  - Sérvio

**Solução alternativa:**

Se desejar selecionar um idioma com um local neutro, certifique-se sempre de adicionar também o idioma com um local específico (com script e/ou código do país) como um idioma adicional na lista de preferências de idioma do seu navegador.

## Há um suporte limitado para localidades Azeri e Uzbeque ao usar o Programador do Lync Web, a Discagem, o Iniciador de Ingresso, o Gerenciamento de Sala de Chat Persistente e OCTab em alguns navegadores da Web (3336748)

> [!NOTE]  
> A informação nesta seção está relacionada às Atualizações Cumulativas para Lync Server 2013: Fevereiro de 2013.

**Problema:**

Ao usar o Internet Explorer 8 ou o Internet Explorer 9 e definir o idioma do navegador como Azeri (latino) ou Uzbeque (latino), as páginas Discagem e Iniciador de Ingresso serão exibidas em inglês ou no idioma preferencial definido no navegador.

Quando você usar os navegadores Firefox ou Chrome, e definir o idioma do navegador como Azeri (latino) ou Uzbeque (latino), o Lync Web App, Programador do Lync Web e o RGS OCTab serão mostrados em inglês ou no idioma preferencial definido para o navegador.

A localidade Uzbeque (latino) não tem suporte no navegador Safari.

**Solução alternativa:**

Não há solução alternativa para estes problemas.

## Falta a seta de menu suspenso na lista "Ingressar na Reunião" na versão em romeno do Lync Web App (3154899)

**Problema:**

Quando um usuário que estiver usando a versão em romeno do Lync Web App realizar as seguintes etapas, a seta de menu suspenso não é exibida na lista suspensa **Ingressar na Reunião**:

1.  Selecione **Lembrar de mim neste computador** na guia **Geral**.

2.  Selecione a guia **Telefone**.

3.  Clique na lista suspensa de **Ingressar na reunião de**.
    
    Os usuários não verão uma seta indicando que eles têm mais opções que o **Lync Web App** padrão, que inclui: **Não participar do áudio** (em romeno, "Nu se asociaža la componenta audio") e **Novo número** (em romeno, "Numar nou").

**Solução alternativa:**

Apesar a seta dessa lista suspensa não ser exibida, os usuários podem ainda selecionar as configurações adicionais na lista clicando no valor padrão.

## Ao usar a versão em turco do Programador do Lync Web, uma reunião não pode ser salva usando a opção "Pessoas que eu escolher" em "Quem é um apresentador" (3169483)

**Problema:**

Ao criar ou editar uma reunião na versão em turco do Programador do Lync Web, a opção "Pessoas que eu escolher" em "Quem é um apresentador" não é suportada. Quando essa opção é selecionada, a reunião não pode ser salva. Em vez disso, uma mensagem de erro é exibida, indicando que uma ou mais pessoas não podem se tornar apresentadores.

**Solução alternativa:**

Para contornar esse problema, os usuários podem usar a opção padrão de "Pessoas na minha empresa" ou qualquer outra opção, como "Apenas organizador" ou "Todos, incluindo pessoas de fora da minha empresa". O organizador pode promover ou rebaixar pessoas a suas funções corretas mais tarde, após elas terem entrado na reunião.

Como alternativa, os usuários que entenderem outro idioma podem escolher um dos outros 43 idiomas em seu navegador e tentar usar a opção "Pessoas que eu escolher".

## Direitos autorais

Este documento serve de apoio a uma versão preliminar de um software que pode ser alterado substancialmente antes da versão comercial final e contém informações confidenciais e proprietárias da Microsoft Corporation. A sua divulgação é feita conforme acordo de não divulgação entre o destinatário e a Microsoft. Este documento é fornecido apenas para fins informativos. A Microsoft não oferece quaisquer garantias, expressas ou implícitas, neste documento. As informações neste documento, incluindo URLs e outras referências a sites na Internet, estão sujeitas a alteração sem aviso prévio. O risco da utilização ou dos resultados da utilização deste documento é exclusivamente do usuário. A menos que especificado o contrário, empresas, organizações, produtos, nomes de domínio, endereços de email, logotipos, pessoas, lugares e eventos descritos nos exemplos aqui incluídos são fictícios. Nenhuma associação com empresas, organizações, produtos, nomes de domínio, endereços de email, logotipos, pessoas, lugares ou eventos reais é intencional ou deve ser inferida. O cumprimento de todas as leis de direitos autorais aplicáveis é responsabilidade do usuário. Sem limitar os direitos autorais, nenhuma parte deste documento pode ser reproduzida, armazenada ou introduzida em um sistema de recuperação, ou transmitida de qualquer forma ou por qualquer meio (eletrônico, mecânico, fotocópia, gravação ou outro), ou com qualquer finalidade, sem a permissão expressa por escrito da Microsoft Corporation.

A Microsoft pode ter patentes, pedidos de patentes, marcas comerciais, direitos autorais ou outros direitos de propriedade intelectual abrangendo o assunto deste documento. Exceto quando estabelecido expressamente em qualquer contrato de licença por escrito da Microsoft, o fornecimento deste documento não concede a você nenhuma licença sobre essas patentes, marcas comerciais, direitos autorais ou outra propriedade intelectual.

© 2012 Microsoft Corporation. Todos os direitos reservados.

Microsoft, Windows, Windows Live, Active Directory, Internet Explorer, MSN, Outlook e SQL Server são marcas registradas ou comerciais da Microsoft Corporation nos Estados Unidos e/ou em outros países.

Todas as outras marcas comerciais são propriedade dos respectivos donos.

