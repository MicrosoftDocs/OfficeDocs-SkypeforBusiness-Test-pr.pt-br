---
title: Processo de migração - detalhes
TOCTitle: Processo de migração - detalhes
ms:assetid: ca7e352c-9bde-47d9-8273-5cf2fdfdfe7e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205264(v=OCS.15)
ms:contentKeyID: 49308105
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de migração - detalhes

 

_**Tópico modificado em:** 2016-12-08_

Use os seguintes pré-requisitos e etapas detalhadas para migrar o Lync Server 2010, Chat de Grupo ou o Office Communications Server 2007 R2  Chat de Grupo para o Lync Server 2013, Servidor de Chat Persistente.

## Pré-requisitos de Migração

Certifique-se de cumprir os seguintes pré-requisitos antes de migrar o Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2  Chat de Grupo para o Lync Server 2013,  Servidor de Chat Persistente.

1.  Implemente pelo menos um pool do Lync Server 2013. Se você possui vários pools do Lync Server 2013, decida qual pool do Lync Server 2013 será o pool inicial para o novo Lync Server 2013  Pool de Servidor de Chat Persistente.

2.  Instale o Lync Server 2013, Pool de Servidor de Chat Persistente. Ele estará vazio (sem categorias, salas ou complementos). Antes de migrar suas categorias herdadas, salas ou complementos, é possível criar salas, categorias ou complementos em sua implantação do Lync Server 2013, Servidor de Chat Persistente.
    
    > [!IMPORTANT]  
    > Tenha cuidado pois estes itens recentemente criados podem entrar em conflito com itens herdados migrados. Evite qualquer conflito de nome; caso contrário, eles serão substituídos com o dado herdado quando migrado.

## Preparando os dados de origem para migração

Realize as seguintes etapas para preparar adequadamente seus dados de origem para migração.

1.  Faça o backup dos bancos de dados de origem para o Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2 Chat de Grupo. Para obter detalhes sobre o backup do SQL Server, consulte "Visão geral do backup (SQL Server)" em <http://go.microsoft.com/fwlink/p/?linkid=254851>.
    
    > [!IMPORTANT]  
    > O Serviços de Domínio Active Directory deve usar o mesmo. Como uma condição de migração, não é possível migrar para um pool em uma implantação diferente (especificamente, em uma floresta do Active Directory diferente).

2.  Inspecione suas salas de bate-papo e configuração de categoria do Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2  Chat de Grupo. Qualquer mudança nas categorias, salas ou complementos em sua implantação herdada existente será realizada pelo Ferramenta de Administração do Chat de Grupo.
    

    > [!TIP]
    > Qualquer mudança nas categorias, salas ou complementos do Lync Server 2013, as implantações do Servidor de Chat Persistente são realizadas pelos cmdlets do Painel de Controle do Lync Server ou Windows PowerShell.

    
    Siga estas etapas para preparar seu sistema herdado para migração.
    
    1.  O Servidor de Chat Persistente suporta um único nível de categorias, diferente de um conjunto de categorias hierárquico profundo. Após a migração, as subcategorias são inseridas com nomes de categorias pai completos. Você pode desejar simplificar a reduzir sua estrutura de categoria existente para que a estrutura resultante atenda seus requisitos.
    
    2.  Verifique os **Gerentes** na raiz Categoria. Se existir qualquer Gerente neste nível, estes usuários serão adicionados como **Gerentes de todas as salas** após a migração. Se este não é um requisito para sua migração, você precisa remover estes Gerentes da raiz Categoria.
    
    3.  Verifique o comprimento dos nomes das salas. Após a migração, devido às estruturas de categoria simplificadas, se as salas existirem em uma categoria filho, elas são inseridas com nomes de categoria pai completos. O limite de nomeação é de 256 caracteres, incluindo os nomes da categoria pai. Você deve verificar o comprimento dos nomes das salas e possivelmente reduzi-lo, se estiverem muito longos.
    
    4.  No Lync Server 2013, se a categoria de configurações **convites** está definida para verdadeiro, é possível escolher verdadeiro ou falso para convites de salas nesta categoria. No entanto, se as configurações de convites da categoria forem definidas para falso, as salas nesta categoria estão com os convites desativados. Antes da migração, você deve reiniciar as configurações de convite em sua versão do Lync Server  Servidor de Chat de Grupo herdado, se desejar que as salas existam em uma categoria específica. Caso contrário, durante a migração, o Lync Server 2013 exibe avisos e define as salas para o valor padrão de falso.
    
    5.  Se você usou arquivos em salas de bate-papo, deve XCOPIAR os arquivos manualmente para o novo repositório de arquivos do Chat Persistente após a migração. As ferramentas não fazem isso.
    
    6.  Se você tem usuários e salas federados com usuários federados, tenha cuidado que o Servidor de Chat Persistente não suporta federação. As salas com usuários federados serão migradas; no entanto, os próprios usuários não poderão acessar o conteúdo, porque o acesso federado não é suportado.
    
    7.  Identifique estas salas que não deseja migrar e marque-as como desabilitado.
    
    8.  Identifique os dados além daqueles que deseja migrar o conteúdo da sala de bate-papo. Por exemplo, você pode não desejar migrar mensagens antes do dia 1° de janeiro de 2010, porque estas mensagens podem estar obsoletas ou não serem relevantes para a migração.

## Realizando a Migração

Realize as seguintes etapas para migrar seu Servidor de Chat de Grupo herdado.

1.  Desligue os serviços do Lync Server 2010, Chat de Grupo, Office Communications Server 2007 R2  Chat de Grupo ou do Lync Server 2013, Servidor de Chat Persistente. Todos os serviços devem ser parados. Portanto, planeje fazer isso em um momento onde há inatividade suficiente. Como descrito anteriormente, certifique-se de fazer o backup do seu banco de dados do Chat de Grupo atual.

2.  Execute o cmdlet Windows PowerShell**Export-CsPersistentChatData** como membro da função RBAC do administrador do Chat Persistente (CsPersistentChatAdministrator). Para obter detalhes sobre os cmdlets de exportação/importação, consulte [Configuração de solução de problemas do Servidor de Chat Persistente usando cmdlets do Windows PowerShell no Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md).
    
    Inspecione o conteúdo exportado.

3.  Antes de estar pronto para importar, desative os serviços do Lync Server 2013, Servidor de Chat Persistente.Todos os serviços precisam ser parados. Portanto, planeje fazer isso quando há tempo de inatividade suficiente.

4.  Realize um backup do banco de dados do Chat Persistente se criou qualquer categoria, sala ou complemento em sua implantação do Lync Server 2013 antes da migração. O processo de exportação/importação poderá mesclar os dados herdados na implantação do Lync Server 2013, mas você precisará fazer o backup do banco de dados caso este conteúdo seja substituído inadvertidamente (por exemplo, se existir um conflito de nomenclatura).

5.  Execute o cmdlet Windows PowerShell**Import-CsPersistentChatData** (ferramenta importar), com um comando **WhatIf** para preencher o Servidor Back-End do Pool de Servidor de Chat Persistente com dados migrados. Algumas conversas ocorrem no processo para acomodar o modelo de administração simplificado. Corrija qualquer erro ou aviso que aparece.

6.  Execute o cmdlet Servidor de Chat PersistenteWindows PowerShell**Import-CsPersistentChatData** como membro da função RBAC do administrador do Chat Persistente (CsPersistentChatAdministrator). Para obter detalhes sobre os cmdlets de exportação/importação, consulte [Configuração de solução de problemas do Servidor de Chat Persistente usando cmdlets do Windows PowerShell no Lync Server 2013](lync-server-2013-troubleshooting-persistent-chat-server-configuration-using-windows-powershell-cmdlets.md).

7.  Você deve XCOPIAR todos os arquivos carregados (toda a pasta) para o novo repositório de arquivos do Lync Server 2013, Chat Persistente.
    
    > [!IMPORTANT]  
    > O Lync 2013 (cliente) não suporta carregar e exibir arquivos em salas de bate-papo. Ainda é possível usar o cliente herdado para publicar e exibir arquivos na sala.

8.  Insira a URI do Servidor de Pesquisa do Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2  Chat de Grupo no objeto de contato do Lync Server 2013, Servidor de Chat Persistente. As etapas a seguir são necessárias se seus clientes do Chat de Grupo do Lync 2010 ou Office Communicator 2007 R2  Chat de Grupo precisam se conectar ao Lync 2013, Chat Persistente (cliente) mais atual após a migração sem qualquer mudança na configuração do lado do cliente:
    
      - Exclua a conta de usuário do Servidor de Pesquisa ocschat@ *\<nomedodomínio\>* .com. Isto foi usado para apontar para o Serviço de Pesquisa no Lync Server 2010, Chat de Grupo. É possível desinstalar o pool e remover as entradas confiáveis posteriormente.
    
      - Criar um ponto de extremidade herdado (objeto de contato do Servidor de Chat Persistente) executando o cmdlet Windows PowerShell, **New-CsPersistentChatEndpoint**, com uma URI SIP idêntica para que o cliente herdado funcione efetivamente quando o serviço seja reiniciado.
    
    O processo de migração obrigatório está concluído neste ponto. O Chat de Grupo do Lync 2010 (clientes) ou Office Communicator 2007 R2Chat de Grupo (clientes) pode se conectar ao novo Pool de Servidor de Chat Persistente agora, de forma transparente.
    
    Siga estas etapas de descomissionamento adicionais para o Lync Server 2010, Chat de Grupo ou Office Communications Server 2007 R2Chat de Grupo.

9.  Inicie o serviço Servidor de Chat Persistente ligando todos os computadores no novo Pool de Servidor de Chat Persistente.

10. Use os cmdlets do Painel de Controle do Lync Server e Windows PowerShell para verificar se os dados foram migrados com êxito.

11. Desinstale o Chat de Grupo do Lync 2010 ou o Office Communicator 2007 R2Chat de Grupo dos computadores no pool do Servidor de Chat de Grupo.

12. Exclua o aplicativo confiável e o pool de aplicativo confiável usando cmdlets do Windows PowerShell. Isto exclui estes itens do Repositório de Gerenciamento Central e as Entradas de Serviço Confiável (TSEs) associadas do Active Directory. Em alternativa, esta etapa funciona usando o Construtor de Topologias (o aplicativo/pools confiável também possui um nó exclusivo).

13. Agora é possível começar a habilitar a funcionalidade do Servidor de Chat Persistente através de novos clientes. Para obter detalhes sobre a habilitação do Servidor de Chat Persistente, consulte [Implantando Servidor de Chat Persistente no Lync Server 2013](lync-server-2013-deploying-persistent-chat-server.md).
    
    > [!IMPORTANT]  
    > O Lync Server 2013 suporta vários Pools de Servidor de Chat Persistente. No entanto, suportamos a migração de um pool do Chat de Grupo do Lync 2010 ou Office Communications Server 2007 R2  Chat de Grupo para um único Lync Server 2013, Pool de Servidor de Chat Persistente. É possível adicionar novos Pools de Servidor de Chat Persistente em sua implantação para atender as necessidades regulatórias (por exemplo, manter os dados dentro de uma determinada geografia).
