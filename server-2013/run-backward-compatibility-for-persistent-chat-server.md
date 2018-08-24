---
title: "Executar compatibilidade c/ versões anteriores p/ Servidor de Chat Persistente"
TOCTitle: "Executar compatibilidade c/ versões anteriores p/ Servidor de Chat Persistente"
ms:assetid: 53f1a706-3104-4a94-8b4e-8badd9a066d6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204901(v=OCS.15)
ms:contentKeyID: 49306724
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Executar compatibilidade com versões anteriores para Servidor de Chat Persistente

 

_**Tópico modificado em:** 2013-02-21_

O ponto de extremidade do Lync Server 2013, Servidor de Chat Persistente fornece uma maneira de criar uma URL simples que aponte para um Pool de Servidor de Chat Persistente. Isso é útil para clientes herdados ( Microsoft Office Communications Server 2007 R2Servidor de Chat de Grupo ou Lync Server 2010, Chat de Grupo), pois os usuários podem inserir uma URL simples na configuração manual quando estiverem tentando direcionar o cliente herdado a um computador executando o Lync 2013, Chat Persistente. Esse ponto de extremidade do não é utilizado pelo Chat Persistente e é necessário somente para os clientes herdados. Isso é útil para o período intermediário no qual as salas podem ser migradas, mas os clientes do Lync 2013 não precisam ser implantados por toda a organização. Os usuários executando o Lync 2010Chat de Grupo (cliente) podem ainda se conectar ao Servidor de Chat PersistenteServidor Back-End.

Não é necessário criar vários pontos de extremidade do Servidor de Chat Persistente, é necessário apenas um para cada Pool de Servidor de Chat Persistente. Os administradores podem criar vários pontos de extremidade (um por pool), mas os clientes herdados podem estar configurados para conectar-se somente a um pool por vez. No cenário habitual ou importante, a implantação herdade é somente um pool. Uma nova implantação, geralmente, migra esse pool para um novo Lync Server 2013 e pode adicionar alguns novos Pools de Servidor de Chat Persistente adicionais.

Esse cenário indispensável, geralmente, segue esse padrão:

  - Você pode administrar os usuários com um pool do Lync Server 2010, Chat de Grupo e seus clientes do Chat de Grupo do Lync 2010 se conectam a esse pool utilizando algum usuário conhecido (SIP padrão:ocschat@ *\<domainName\>* .com ou um semelhante). Os usuários são Serviços de Domínio Active Directory habilitados para SIP e o Serviço de Pesquisa neles registrados para receber solicitações de entrada.

  - Subsequentemente, você instala um Lync Server 2013Servidor de Chat Persistente e o Pool de Servidor de Chat Persistente.

  - Durante um período no qual os usuários, geralmente, estão offline (por exemplo, um fim de semana):
    
      - Desative o Lync Server 2010, Chat de Grupo.
    
      - Migre os dados do pool do Lync Server 2010, Chat de Grupo para o Lync Server 2013Pool de Servidor de Chat Persistente.
    
      - Exclua o usuário conhecido do Serviços de Domínio Active Directory.
    
      - Crie um novo *ponto de extremidade herdado* com o mesmo URI do SIP do usuário conhecido excluído anteriormente.
    
      - Inicie o Lync Server 2013, Servidores de Chat Persistente.

  - Os usuários fazem logoff e, em seguida, logon novamente utilizando o Chat de Grupo do Lync 2010 (cliente) e se conectam aos dados sem precisar alterar qualquer configuração.

  - Futuramente, você pode desprogramar o Lync Server 2010, Chat de Grupo. Posteriormente, é possível implantar o Lync Server 2013, Servidor de Chat Persistente e instalar o novo Lync Server 2013Pools de Servidor de Chat Persistente.

Para obter detalhes sobre a migração do Lync Server 2010, Chat de Grupo para o Lync Server 2013, Servidor de Chat Persistente, consulte [Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md).

Para executar a compatibilidade com versões anteriores (para criar um ponto de extremidade do Servidor de Chat Persistente que aponta para um Pool de Servidor de Chat Persistente, que pode ser utilizado por clientes de pool do Chat de Grupo herdados):

    New-CsPersistentChatEndpoint -SipAddress <CO name, ex. persistentchat@contoso.com> -PersistentChatPoolFqdn <pool FQDN, like pcpool.contoso.com>

Em seguida, configure os clientes do Chat Persistente para utilizar esse endereço SIP como seu objeto de contato. O endereço SIP foi criado com o cmdlet **New-CsPersistentChatEndpoint** para um Pool de Servidor de Chat Persistente específico.

Para adicionar o ponto de extremidade do Servidor de Chat Persistente utilizando o Interface da linha de comando do Windows PowerShell, considere o seguinte exemplo. Neste caso, você está configurando o objeto de contato para ser chamado de "persistentchat" na topologia "contoso.com", no qual o nome de domínio totalmente qualificado (FQDN) do pool é "pcpool.contoso.com":

    New-CsPersistentChatEndpoint -SipAddress sip:persistentchat@contoso.com -PersistentChatPoolFqdn pcpool.contoso.com

## Consulte Também

#### Conceitos

[Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md)

