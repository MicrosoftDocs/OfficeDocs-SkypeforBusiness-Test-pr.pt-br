---
title: Atributos e descrições de esquema no Lync Server 2013
TOCTitle: Atributos e descrições de esquema no Lync Server 2013
ms:assetid: b009df76-9c22-471d-b57a-bda009a98261
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412841(v=OCS.15)
ms:contentKeyID: 49307796
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Atributos e descrições de esquema no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Esta seção descreve todos os atributos de esquema usados pelo Lync Server 2013. Para as classes associadas a atributos, consulte [Atributos de esquema por classe no Lync Server 2013](lync-server-2013-schema-attributes-by-class.md). Para uma lista de classes e atributos que são novos no Lync Server 2013, consulte [Alterações de esquema no Lync Server 2013](lync-server-2013-schema-changes-in-lync-server-2013.md).

Atributos que são pares vinculados são especificados como vínculos sequenciais ou vínculos inversos. Um atributo que faz referência a outro objeto é um vínculo sequencial; o atributo do outro objeto que faz referência de volta ao primeiro objeto é um vínculo inverso. Vínculos sequenciais são atualizáveis, enquanto vínculos inversos são somente leitura.

Alguns atributos possuem um valor de máscara de bit. Para estes atributos, cada configuração é representada por um bit e o valor decimal exibido representa a posição do bit. Posições de bit começam com o bit 0. Por exemplo, 1 (binário) é o bit 0 definido e 10000 (binário) é o bit 4 definido. Cada bit representa uma propriedade. A seguir, alguns exemplos:

  - 10000 (binário) tem o valor decimal igual a 16 (ou seja, o bit 4 está definido).

  - 100000000 (binário) tem o valor decimal igual a 256 (ou seja, o bit 8 está definido).

  - 1100 (binário) tem o valor decimal igual a 12 (ou seja, os bits 2 e 3 estão definidos; as propriedades representadas por ambos estão habilitadas).

  - 1111000001 (binário) tem o valor decimal igual a 961 (ou seja, os bits 0, 6, 7, 8 e 9 estão definidos; as propriedades para cada um deles estão habilitadas).

### Atributos de esquema para o Lync Server 2013

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Atributo</th>
<th>Descrição</th>
<th>Comentários</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>dnsHostName</p></td>
<td><p>Um atributo existente no Serviços de Domínio Active Directory que agora está associado às classes <strong>msRTCSIP-Pool</strong> e <strong>msRTCSIP-MonitoringServer</strong>. Este atributo especifica o nome de domínio totalmente qualificado (FQDN) de um pool ou Servidor de Monitoramento.</p>
<p>O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Microsoft Office Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msDS-SourceObjectDN</p></td>
<td><p>Este atributo contém a representação de cadeia de caracteres do nome diferenciado (DN) do objeto em outra floresta que corresponde a este objeto. Este atributo é usado para a expansão do grupo de distribuição e auto atendimento e é definido no esquema padrão do Active Directory para o Windows Server 2003 R2.</p>
<p>Para evitar a solicitação de uma atualização do AD DS para o Windows Server 2003 R2, a preparação do esquema do Active Directory estende o esquema do Windows Server 2003 com esta definição de atributo.</p></td>
<td><p>Novo no Microsoft Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msExchUCVoiceMailSettings</p></td>
<td><p>Este atributo multivalorado armazena as configurações da caixa postal. Este atributo é compartilhado com o Unificação de Mensagens (UM) do Exchange.</p></td>
<td><p>Novo no Microsoft Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msExchUserHoldPolicies</p></td>
<td><p>Esse atributo de vários valores mantém identificadores para políticas de espera que se aplicam ao usuário. As políticas de espera preservam itens da caixa de correio para o usuário durante o período. Este atributo é compartilhado com o Exchange 2013.</p></td>
<td><p>Novo no Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-AcpInfo</p></td>
<td><p>Este atributo armazena informações do provedor de serviços de audioconferência para um usuário.</p></td>
<td><p>Novo no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationDestination</p></td>
<td><p>Este atributo aponta para a entrada de serviço confiável para o contato de aplicativo.</p></td>
<td><p>Novo no Microsoft Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationList</p></td>
<td><p>Este atributo contém uma lista de aplicativos hospedados no servidor de aplicativos.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationOptions</p></td>
<td><p>Este atributo especifica as opções para o contato de aplicativo.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationPrimaryLanguage</p></td>
<td><p>Este atributo contém o idioma principal para o contato de aplicativo.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationSecondaryLanguages</p></td>
<td><p>Este atributo de vários valores contém os idiomas secundários para o contato de aplicativo.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ApplicationServerBL</p></td>
<td><p>Este atributo contém uma lista de servidores de aplicativos que pertencem a este pool. O vínculo sequencial correspondente a este atributo de vínculo inverso é <strong>msRTCSIP-ApplicationServerPoolLink</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ApplicationServerPoolLink</p></td>
<td><p>Este atributo aponta para o pool ao qual este servidor de aplicativos pertence. Este é o vínculo sequencial. O vínculo inverso correspondente é <strong>msRTCSIP-ApplicationServerBL</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchiveDefault (obsolete)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchiveDefaultFlags (obsoleto)</p></td>
<td><p>Este atributo especifica o padrão global dentro dos limites da floresta para o arquivamento de todas as comunicações do usuário. É imposto pela camada do agente de arquivamento. O intervalo de valores para este atributo é:</p>
<ul>
<li><p><strong>TRUE</strong>: Arquivar todos os usuários</p></li>
<li><p><strong>FALSE</strong>: Não arquivar todos os usuários</p></li>
</ul>
<p>Este atributo controla globalmente, dentro dos limites da floresta, como as comunicações do usuário dentro de uma rede interna são arquivadas.</p>
<p><strong>Comportamento do Live Communications Server 2005 (agora desativado)</strong></p>
<p>O intervalo de valores para este atributo é da seguinte forma:</p>
<ul>
<li><p>0: Arquiva o corpo da mensagem [bit 0]</p></li>
<li><p>1: Não arquiva o corpo da mensagem [bit 0]</p></li>
</ul>
<p><strong>Comportamento do Office Communications Server 2007</strong></p>
<p>O intervalo de valores para este atributo é da seguinte forma:</p>
<ul>
<li><p>0: ArchiveFederationDefaultWithoutBody (desativado)</p></li>
<li><p>1-2: ArchiveInternalCommunications</p></li>
<li><p>3-4: ArchiveFederatedCommunications</p></li>
<li><p>5: RecordPresenceRegistrations</p></li>
<li><p>6: RecordIMCallDetails</p></li>
<li><p>7: RecordGroupIMCallDetails</p></li>
<li><p>8: RecordFileTransferInstances</p></li>
<li><p>9: RecordAudioCallDetails</p></li>
<li><p>10: RecordVideoCallDetails</p></li>
<li><p>11: RecordRemoteAssistanceCallDetails</p></li>
<li><p>12: RecordApplicationSharingDetails</p></li>
<li><p>13: RecordMeetingInstantiations</p></li>
<li><p>14: RecordMeetingJoins</p></li>
<li><p>15: RecordDataJoins</p></li>
<li><p>16: RecordAVJoins</p></li>
</ul></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchiveFederationDefault (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchiveFederationDefaultFlags (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingEnabled</p></td>
<td><p>Este atributo é um inteiro usado como um campo de bit para controlar se as comunicações de um único usuário estão prestes a ser arquivadas. Este controle é imposto pela camada do agente de arquivamento. Ele é marcado para replicação do catálogo global.</p>
<p>O escopo deste atributo é específico a um único usuário ou contato. Os valores válidos (e posições de bit associadas) no Lync Server são:</p>
<ul>
<li><p>0: Não arquiva (nenhum bit definido)</p></li>
<li><p>1: Desativado (posição de bit 0)</p></li>
<li><p>2: Desativado (posição de bit 1)</p></li>
<li><p>4: Arquiva comunicações internas (posição de bit 2)</p></li>
<li><p>8: Arquiva comunicações federadas (posição de bit 3)</p></li>
</ul>
<p>Valores válidos anteriormente no Live Communications Server 2005 são:</p>
<ul>
<li><p>0:Usa o valor padrão definido pelo <strong>msRTCSIP-ArchiveDefault</strong> e <strong>msRTCSIP-ArchiveFederation</strong> nesta ordem de precedência:</p>
<ul>
<li><p>1: Arquiva</p></li>
<li><p>2: Não arquiva</p></li>
<li><p>3: Arquiva sem o corpo da mensagem</p></li>
</ul></li>
</ul></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ArchivingServerData (obsoleto)</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ArchivingServerVersion (obsoleto)</p></td>
<td><p>Este atributo define a versão do serviço de Arquivamento. Este atributo é um tipo de inteiro lentamente crescente que aumenta a cada lançamento de produto oficial. Os valores válidos possíveis são:</p>
<ul>
<li><p>Indefinido: Live Communications Server 2003</p>
<p>                 Live Communications Server 2005</p>
<p>                 Live Communications Server 2005 com SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-BackEndServer</p></td>
<td><p>Este atributo especifica o FQDN do Servidor Back End do pool. Como só pode haver um único Servidor Back End por pool, este é um atributo de valor único.</p>
<p>O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectoryHomePool</p></td>
<td><p>Este atributo contém o identificador do pool que hospeda o diretório de conferências.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ConferenceDirectoryId</p></td>
<td><p>Este atributo contém o identificador de um diretório de conferências.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ConferenceDirectoryTargetPool</p></td>
<td><p>Este atributo contém o identificador do pool para o qual o diretório de conferências está sendo movido.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Default</p></td>
<td><p>Este atributo booleano define se o uso do telefone é padrão. Se estiver definido como <strong>TRUE</strong>, o uso do telefone é padrão e não pode ser excluído pelo administrador. Se estiver definido como <strong>FALSE</strong>, o uso pode ser excluído.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultCWAExternalURL</p></td>
<td><p>Este atributo identifica a URL do Communicator Web Access para usuários que estão fora da organização.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultCWAInternalURL</p></td>
<td><p>Este atributo identifica a URL do Communicator Web Access para usuários que estão dentro da organização.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultLocationProfileLink (obsoleto)</p></td>
<td><p>Este atributo de valor único contém o nome diferenciado (DN) de um objeto de classe de perfil de local associado a ele.</p>
<p>Vínculo sequencial: <strong>Link ID 11036</strong></p>
<p>O vínculo inverso correspondente é <strong>msRTCSIP-ServerReferenceBL</strong>.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultPolicy (obsoleto)</p></td>
<td><p>Este atributo booleano especifica se a política é padrão. A política é padrão quando o atributo está definido como <strong>TRUE</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefaultRouteToEdgeProxy (obsoleto)</p></td>
<td><p>Este atributo especifica o FQDN do Servidor de Borda que está executando o Serviço de Borda de Acesso, se puder ser acessado diretamente, ou do balanceador de carga do hardware para um pool de servidores executando o Serviço de Borda de Acesso. Se for possível acessar os servidores que estão executando o Serviço de Borda de Acesso somente através de um ou mais Diretores, este atributo especifica o FQDN e, opcionalmente, o número da porta do Diretor ou do balanceador de carga do hardware que está atendendo um pool de Diretores.</p>
<p>O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefaultRouteToEdgeProxyPort (obsoleto)</p></td>
<td><p>Este atributo representa o número da porta que deve ser usada para estabelecer conexão com o servidor que está executando o Serviço de Borda de Acesso.</p>
<p>O valor válido é um inteiro especificando a porta a ser usada. O valor padrão é 5061.</p></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefPresenceSubscriptionTimeout (obsoleto)</p></td>
<td><p>Este atributo representa o tempo limite da assinatura de presença padrão.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DefRegistrationTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite do registro padrão.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DefRoamingDataSubscriptionTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite da assinatura de dados de roaming padrão.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DeploymentLocator</p></td>
<td><p>Este atributo é usado em uma topologia de domínio dividida e contém um nome de domínio totalmente qualificado (FQDN).</p></td>
<td><p>Novo no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Description (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres UNICODE de valor único contém uma descrição amigável desta rota de telefone ou regra de normalização.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-DomainData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-DomainName</p></td>
<td><p>Este atributo representa um domínio configurado para o Registrador Avançado.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EdgeProxyData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EdgeProxyFQDN</p></td>
<td><p>Este atributo especifica o FQDN do servidor que está executando o serviço de Borda de Acesso.</p>
<p>O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnableBestEffortNotify (obsoleto)</p></td>
<td><p>Este atributo controla se um servidor gera uma solicitação Best Effort NOTIFY (BENOTIFY), em vez de uma solicitação NOTIFY, em resposta a uma solicitação SUBSCRIBE de um cliente. BENOTIFY é uma extensão de aprimoramento de desempenho para o handshake da notificação de assinatura onde o servidor gera solicitações BENOTIFY, em vez de solicitações NOTIFY regulares. O benefício no desempenho é que uma solicitação BENOTIFY não requer uma resposta 200 OK do cliente, como a solicitação NOTIFY.</p>
<p>Os valores válidos são <strong>TRUE</strong> ou <strong>FALSE</strong>.</p>

> [!NOTE]  
> O Live Communications Server 2003 não é compatível com solicitações BENOTIFY. Para interoperar com aplicativos de servidor escritas com a API de servidor do Live Communications Server 2003 que está em execução no Live Communications Server 2005 e servidores de terceiros, solicitações BENOTIFY podem ser desabilitadas configurando seu valor como <strong>FALSE</strong>. BENOTIFY atualmente não é parte do processo de padronização SIP IETF (Internet Engineering Task Force).

</td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-EnableFederation (obsoleto)</p></td>
<td><p>Este atributo é um comutador global que administradores de TI usam para configurar se usuários têm permissão para se comunicar com usuários de outras organizações. Ele permite que um administrador sobrescreva o atributo <strong>FederationEnabled</strong> de um usuário individual. Este atributo pode ser útil para ajudar a proteger a rede interna de ataques provenientes da Internet que podem ser causados por worms, vírus ou ataques direcionados à empresa.</p>
<p>Os valores válidos (e posições de bit associadas) são:</p>
<ul>
<li><p>1: Habilitado para conectividade de IM pública (posição de bit 0)</p></li>
<li><p>2: Reservado (posição de bit 1)</p></li>
<li><p>4: Reservado (posição de bit 2)</p></li>
<li><p>8: Reservado (posição de bit 3)</p></li>
<li><p>16: Controle de chamada remota habilitado [Telefonia] (posição de bit 4)</p></li>
<li><p>64: AllowOrganizeMeetingWithAnonymousParticipants (permite que usuários convidem usuários anônimos para reuniões (posição de bit 6)</p></li>
<li><p>128: UCEnabled (habilita usuários para comunicações unificadas) (posição de bit 7)</p></li>
<li><p>256: EnabledForEnhancedPresence (habilita o usuário para conectividade de IM pública) (posição de bit 8)</p></li>
<li><p>512: RemoteCallControlDualMode (posição de bit 9)</p></li>
</ul></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-EnterpriseServices</p></td>
<td><p>Este atributo indica se Enterprise Services estão carregados em determinado servidor.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ExtensionData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ExternalAccessCode</p></td>
<td><p>Este atributo contém o código de discagem para acesso externo.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-FederationEnabled</p></td>
<td><p>Este atributo controla se um único usuário está habilitado para federação. É imposto pela camada do Enterprise Services e está marcado para replicação do catálogo global.</p>
<p>Os valores válidos são <strong>TRUE</strong> ou <strong>FALSE</strong>.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-FrontEndServers</p></td>
<td><p>Este atributo é uma lista multivalorada dos nomes de domínio de todos os servidores Enterprise Edition associados a um pool.</p>
<p>Vínculo inverso: <strong>Link ID 11023</strong></p>
<p>O vínculo sequencial correspondente a este vínculo inverso é <strong>msRTCSIP-PoolAddress</strong>.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Gateways (obsoleto)</p></td>
<td><p>Este atributo multivalorado de cadeia de caracteres contém uma lista de gateways e portas (por gateway).</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-GlobalSettingsData (obsoleto)</p></td>
<td><p>Este atributo armazena pares nome:valor. Os par nome:valor já definido é para a configuração <strong>permitir sondagem de presença</strong>.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-GroupingID</p></td>
<td><p>Este atributo é um identificador único de um grupo usado para agrupar entradas do catálogo de endereços.</p></td>
<td><p>Novo no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-HomeServer (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2003 (não utilizado).</p>
<p>Obsoleto no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-HomeServerString (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2003.</p>
<p>Obsoleto no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-HomeUsers (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2003 (não utilizado).</p>
<p>Obsoleto no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-InternetAccessEnabled</p></td>
<td><p>Este atributo controla se um único usuário está habilitado para acesso externo de usuário. É imposto pela camada do Enterprise Services e está marcado para replicação do catálogo global.</p>
<p>Os valores válidos são <strong>TRUE</strong> ou <strong>FALSE</strong>.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-IsMaster (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2003</p>
<p>Obsoleto no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Line</p></td>
<td><p>Este atributo de valor único contém o ID do dispositivo (o URI do SIP ou o URI do TEL do telefone controlado pelo usuário) usado pelo Lync para telefonia. Este atributo está marcado para replicação do Catálogo Global e é indexado. Se o usuário estiver habilitado para o Enterprise Voice, este atributo armazena a versão normalizada E.164 do número do telefone do usuário.</p></td>
<td><p>Novo no Microsoft Office Live Communications Server 2005 com SP1</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LineServer</p></td>
<td><p>Este atributo de valor único contém o URI do SIP do servidor de gateway CSTA-SIP. Este atributo está marcado para replicação do Catálogo Global mas não é indexado.</p></td>
<td><p>Novo no Microsoft Office Live Communications Server 2005 com SP1</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizationData (obsoleto)</p></td>
<td><p>Este atributo está marcado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocalNormalizationLinks (obsoleto)</p></td>
<td><p>Este atributo multivalorado contém uma lista de nomes diferenciados (DN) de normalização local associados a este perfil de localidade. O tipo deste atributo é binário de DN. Existe um relacionamento de um-para-muitos entre o perfil de localidade e regras de normalização local. A ordenação da lista de DNs de normalização local deve ser mantida na ordem especificada pelo administrador. A preservação da ordem é mantida pela parte binária do binário de DN, que especifica o índice da ordem.</p>
<p>Vínculo sequencial: <strong>Link ID 11034</strong></p>
<p>O vínculo inverso correspondente a este atributo de vínculo sequencial é <strong>msRTCSIP-LocationProfileBL</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocalNormalizationOptions</p></td>
<td><p>Este atributo contém uma lista de opções para a regra de normalização.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationName (obsoleto)</p></td>
<td><p>Este atributo de valor único contém um nome amigável para o perfil de localidade que indica o local representado por este perfil. Como podem existir vários perfis de localidade, o administrador precisa de uma forma de distinção entre os perfis.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-locationProfileBL (obsoleto)</p></td>
<td><p>Este atributo multivalorado contém uma lista de nomes diferenciados de perfis de localidade. Este atributo especifica o vínculo inverso para um ou mais perfis de localidade.</p>
<p>Vínculo inverso: <strong>Link ID 11035</strong></p>
<p>Este atributo corresponde ao vínculo sequencial <strong>msRTCSIP-LocalNormalizationLinks</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-LocationProfileData (obsoleto)</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-LocationProfileOptions</p></td>
<td><p>Este atributo contém as opções para o perfil de localidade.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MappingContact</p></td>
<td><p>Este atributo multivalorado hospeda uma lista de contatos de aplicativo.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MappingLocation</p></td>
<td><p>Este atributo multivalorado hospeda uma lista de perfis de localidade.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxNumOutstandingSearchPerServer (obsoleto)</p></td>
<td><p>Este atributo representa o número máximo de solicitações de pesquisa pendentes por servidor.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MaxNumSubscriptionsPerUser (obsoleto)</p></td>
<td><p>O atributo representa o número máximo de assinaturas por usuário.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxPresenceSubscriptionTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite máximo da assinatura.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MaxRegistrationsTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite máximo de registros.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MaxRoamingDataSubscriptionTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite máximo de assinaturas de dados de roaming.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactoryAddress</p></td>
<td><p>Este atributo é um atributo de ponto de controle de serviço sob a classe de computador que especifica um vínculo inverso para o alocador de unidade de controle de multipontos (MCU) à qual ele pertence. Este ponto de controle de serviço e atributo é criado para cada MCU Microsoft. Cada MCU Microsoft deve encontrar o Servidor Back End do pool ao qual pertence, para recuperar configurações de nível de pool dele.</p>
<p>O valor deste atributo é o nome diferenciado (DN) do Alocador de MCU. Este é um atributo de valor único, marcado para replicação do catálogo global.</p>
<p>Vínculo sequencial: <strong>Link ID 11026</strong></p>
<p>O vínculo inverso correspondente a este atributo de vínculo sequencial é <strong>msRTCSIP-MCUServers</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryData</p></td>
<td><p>Este é um atributo reservado de várias cadeias de caracteres. As configurações armazenadas neste atributo são representadas como pares nome=valor. Os pares nome=valor atualmente definidos são:</p>
<ul>
<li><p>FactoryURL = &lt;URL&gt;</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUFactoryPath</p></td>
<td><p>Este é um atributo de valor único que contém o nome diferenciado (DN) de um único alocador de MCU associado ao pool.</p>
<p>Vínculo sequencial: <strong>Link ID 11024</strong></p>
<p>O vínculo inverso correspondente a este atributo de vínculo sequencial é <strong>msRTCSIP-PoolAddresses</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUFactoryProviderID</p></td>
<td><p>Este atributo é uma cadeia de caracteres de valor único que especifica o GUID do provedor do alocador de MCU. Com base no valor GUID, o processo do alocador de MCU determina se atenderá este tipo de MCU. Se o valor GUID for <strong>{F0810510-424F-46ef-84FE-6CC720DF1791}</strong>, o processo do alocador de MCU (disponível por padrão no Lync Server) o processará. Para qualquer outro valor GUID, o processo do alocador de MCU não atenderá o tipo de MCU.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUServers</p></td>
<td><p>Este atributo é uma lista multivalorada de nomes diferenciados (DN). Este atributo contém uma lista de todos os servidores MCU do mesmo tipo e fornecedor associado a este alocador de MCU. O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p>
<p>Vínculo inverso: Link ID 11027</p>
<p>O vínculo sequencial correspondente a este vínculo inverso é <strong>msRTCSIP-MCUFactoryAddress</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MCUType</p></td>
<td><p>Este atributo é uma cadeia de caracteres de valor único que especifica o meio que o MCU pode tratar.</p>
<p>Os tipos válidos suportados são:</p>
<ul>
<li><p>meeting</p></li>
<li><p>audio-video</p></li>
<li><p>chat</p></li>
<li><p>phone-conf</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MCUVendor</p></td>
<td><p>Este atributo é uma cadeia de caracteres de valor único que especifica um nome de fornecedor de MCU. Todos os MCUs Microsoft especificarão este atributo como <strong>Microsoft Corporation</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MeetingFlags (obsoleto)</p></td>
<td><p>Este atributo define diferentes opções de reunião habilitadas globalmente para todos os usuários ou objetos de contato. Este atributo é um valor de máscara de bit do tipo inteiro.</p>
<p>Os valores válidos (e posições de bit associadas) são:</p>
<ul>
<li><p>0: AllowOrganizeMeetingWithAnonymousParticipants is None (não permite que usuários convidem usuários anônimos para reuniões) (nenhum bit definido)</p></li>
<li><p>4: AllowOrganizeMeetingWithAnonymousParticipants is Everyone (permite que todos os usuários convidem usuários anônimos para reuniões) (posição de bit 2)</p></li>
<li><p>8: AllowOrganizeMeetingWithAnonymousParticipants is UsePerUserSetting (permite que usuários convidem usuários anônimos para reuniões com base na configuração por usuário) (posição de bit 3)</p></li>
<li><p>16: UserPerUserMeetingPolicy (política de reunião definida por usuário) (posição de bit 4)</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MeetingPolicy (obsoleto)</p></td>
<td><p>Este atributo especifica o nome diferenciado (DN) da política que o administrador atribuiu a este usuário como um atributo de valor único.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MinPresenceSubscriptionTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite mínimo de assinatura de presença.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MinRegistrationTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela de tempo limite mínimo do registro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MinRoamingDataSubscriptionTimeout (obsoleto)</p></td>
<td><p>Este atributo representa a janela do tempo limite mínimo da assinatura de dados de roaming.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MirrorBackEndServer</p></td>
<td><p>Este atributo é usado para armazenar o back-end espelhado do SQL Server usado pelo Pool de Front-Ends.</p></td>
<td><p>Novo no Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-MobilityFlags</p></td>
<td><p>Este atributo contém opções e sinalizadores que definem configurações de mobilidade.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-MobilityPolicy</p></td>
<td><p>Este atributo contém o DN de um objeto de política de mobilidade.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-NumDevicesPerUser (obsoleto)</p></td>
<td><p>Este atributo representa o número permitido de dispositivos em que um usuário pode se registrar para comunicações SIP e assinar presença.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-OptionFlags</p></td>
<td><p>Este atributo especifica as opções que estão habilitadas para o usuário ou objeto de contato. Este atributo é um valor de máscara de bit do tipo inteiro. Cada opção é representada por um bit. Este atributo está marcado para a replicação do catálogo global.</p>
<p>Os valores válidos (e posições de bit associadas) são:</p>
<ul>
<li><p>1: Habilitado para conectividade com sistemas públicos de mensagens instantâneas (IM) (posição de bit 0).</p></li>
<li><p>2: Reservado (posição de bit 1)</p></li>
<li><p>4: Reservado (posição de bit 2)</p></li>
<li><p>8: Reservado (posição de bit 3)</p></li>
<li><p>16: Controle de chamadas remotas Habilitado [Telefonia] (posição de bit 4)</p></li>
<li><p>64: AllowOrganizeMeetingWithAnonymousParticipants (permite que usuários convidem usuários anônimos para reuniões (posição de bit 6)</p></li>
<li><p>128: UCEnabled (habilita usuários para UC) (posição de bit 7)</p></li>
<li><p>256: EnabledForEnhancedPresence (habilita o usuários para conectividade pública com IM) (posição de bit 8)</p></li>
<li><p>512: RemoteCallControlDualMode (posição de bit 9)</p></li>
</ul></td>
<td><p>Novo no Live Communications Server 2005 com SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-OriginatorSID</p></td>
<td><p>Este atributo é usado em topologias de floresta de recursos e centrais para habilitar o logon único quando um ObjectSID de um usuário da conta principal do Windows NT Server é copiado para este atributo do usuário correspondente ou objeto de contato na floresta de recursos ou central. O Communicator Web Access procura um usuário no AD DS usando este atributo ou o ObjectSID do usuário. Este atributo está marcado para replicação do catálogo global.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-OwnerUrn</p></td>
<td><p>Este atributo é o Uniform Resource Name (URN) do proprietário de um contato de aplicativo.</p></td>
<td><p>Novo no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-Pattern (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres de valor único contém um padrão usado para comparar números de discagem no formato E.164. Se o número de discagem corresponder a este padrão, a tradução é aplicada ao número discado.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRouteBL (obsoleto)</p></td>
<td><p>Este atributo multivalorado contém uma lista de nomes diferenciados (DN) de rota de telefone. Este atributo especifica o vínculo inverso para uma ou mais rotas de telefone.</p>
<p>Vínculo inverso: <strong>Link ID 11033</strong></p>
<p>Este atributo corresponde ao vínculo sequencial <strong>msRTCSIP-RouteUsageLinks</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneRouteData (obsoleto)</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PhoneRouteName (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres UNICODE de valor único especifica o nome amigável da rota de telefone, para que possa ser facilmente referenciado pelo administrador.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PhoneUsageData (obsoleto)</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PolicyContent (obsoleto)</p></td>
<td><p>Este atributo é uma cadeia de caracteres Unicode de valor único. Esta cadeia de caracteres contém a definição da política no formato XML. A definição de esquema XML é comum entre diferentes tipos de política, apenas as configurações são diferentes para cada um deles.</p>
<p>A definição de esquema XML (XSD) é definida da seguinte forma:</p>
<pre><code>&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;
&lt;xs:schema id=&quot;instance&quot;  xmlns:xs=&quot;http://www.w3.org/2001/XMLSchema&quot; xmlns:msdata=&quot;urn:schemas-microsoft-com:xml-msdata&quot;&gt;
  &lt;xs:element name=&quot;instance&quot; msdata:IsDataSet=&quot;true&quot;&gt;
    &lt;xs:complexType&gt;
      &lt;xs:choice maxOccurs=&quot;unbounded&quot;&gt;
        &lt;xs:element name=&quot;property&quot; nillable=&quot;true&quot;&gt;
          &lt;xs:complexType&gt;
            &lt;xs:simpleContent msdata:ColumnName=&quot;property_Text&quot; msdata:Ordinal=&quot;1&quot;&gt;
              &lt;xs:extension base=&quot;xs:string&quot;&gt;
                &lt;xs:attribute name=&quot;name&quot; type=&quot;xs:string&quot; /&gt;
              &lt;/xs:extension&gt;
            &lt;/xs:simpleContent&gt;
          &lt;/xs:complexType&gt;
        &lt;/xs:element&gt;
      &lt;/xs:choice&gt;
    &lt;/xs:complexType&gt;
  &lt;/xs:element&gt;
&lt;/xs:schema&gt;</code></pre></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PolicyData (obsoleto)</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PolicyType (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres Unicode de valor único contém o tipo de política. Tipos de política válidos são:</p>
<ul>
<li><p>reunião</p></li>
<li><p>telefonia</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolAddress</p></td>
<td><p>Este atributo especifica um link de volta ao pool ao qual um computador pertence. Este atributo é definido independente de o computador estar executando a Standard Edition ou a Enterprise Edition do Lync Server. Este atributo está marcado para replicação do catálogo global.</p>
<p>O valor válido é o nome do domínio do pool.</p>
<p>Vínculo sequencial: <strong>Link ID 11022</strong></p>
<p>O vínculo inverso correspondente a este atributo de vínculo sequencial é <strong>msRTCSIP-FrontEndServers</strong>.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolAddresses</p></td>
<td><p>Este é um atributo multivalorado que contém uma lista dos nomes diferenciados (DN) de pools com os quais o alocador de MCU está associado.</p>
<p>Vínculo inverso: <strong>Link ID 11025</strong></p>
<p>O vínculo sequencial correspondente a este vínculo inverso é <strong>msRTCSIP-MCUFactoryPath</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Live Communications Server 2005 com SP1.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolDisplayName</p></td>
<td><p>Este atributo especifica um nome arbitrário para um pool que é exibido no console de gerenciamento. Este nome pode ser alterado pelo administrador.</p>
<p>O valor válido é uma cadeia de caracteres que representa o nome de um pool.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolDomainFQDN</p></td>
<td><p>Este atributo é um valor de cadeia de caracteres de valor único. O valor deste atributo, quando presente, representa o FQDN do domínio do pool, se o administrador quiser criar um pool de Front End com um FQDN que não esteja de acordo com a estrutura de domínio do Active Directory em que o pool de Front End foi criado (por exemplo, um namespace SIP retirado do namespace do Sistema de Nomes de Domínio (DNS)).</p>
<p>É recomendável que você mapeie o FQDN do domínio do pool de Front End para a parte do nome de domínio como o domínio do Active Directory em que o pool está hospedado. Portanto, quando nenhum valor estiver presente neste atributo, o FQDN do pool de Front End terá, por padrão, a estrutura de nome de domínio do Active Directory, conforme representado pelo atributo <strong>dnsHostName</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolFunctionality</p></td>
<td><p>Uma lista multivalorada de nomes de domínio de todos os servidores Lync Server Enterprise Edition associados a um pool. Este atributo do tipo inteiro define se o pool está habilitado para sistemas de mensagem instantânea (IM), presença e reuniões.</p>
<p>Os tipos de valores válidos possíveis são:</p>
<ul>
<li><p>Indefinido: IM e Serviço de Presença (Live Communications Server 2005 e 2003)</p></li>
<li><p>1: IM e Serviço de Presença (Lync Server)</p></li>
<li><p>2: IM, Serviço de Presença e Serviço de Reunião (Lync Server)</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PoolType</p></td>
<td><p>Este atributo especifica se um pool de servidores está executando o servidor Standard Edition ou o Enterprise Edition. Este atributo é um valor de máscara de bit do tipo inteiro. Cada opção é representada por um bit.</p>
<p>Os valores válidos (e posições de bit associadas) são:</p>
<ul>
<li><p>1: Servidor Standard Edition, hospeda usuários (posição de bit 0)</p></li>
<li><p>2: Servidor Enterprise Edition, hospeda usuários (posição de bit 1)</p></li>
<li><p>4: Servidor Standard Edition, hospeda aplicativos (posição de bit 2)</p></li>
<li><p>8: Servidor Enterprise Edition, hospeda aplicativos (posição de bit 3)</p></li>
</ul>
<p>Como o Lync Server não suporta pools que armazenam apenas aplicativos, os únicos valores válidos são:</p>
<ul>
<li><p>5: Servidor Standard Edition, hospeda usuários e aplicativos (posições de bit 0 e 2)</p></li>
<li><p>10: Servidor Enterprise Edition, hospeda usuários e aplicativos (posições de bit 1 e 3)</p></li>
</ul></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PoolVersion</p></td>
<td><p>Este atributo define a versão do pool. É um tipo inteiro incrementado de acordo com cada lançamento de produto principal.</p>
<p>Os tipos de valores válidos possíveis são:</p>
<ul>
<li><p>0: Live Communications Server 2003</p></li>
<li><p>1: Live Communications Server 2005</p></li>
<li><p>2: Live Communications Server 2005 com SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
</ul></td>
<td><p>Live Communications Server 2005 com SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PresenceFlags</p></td>
<td><p>Este atributo contém opções e sinalizadores que definem configurações de presença.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PresencePolicy</p></td>
<td><p>Este atributo contém o DN para um objeto de política de presença.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PrimaryHomeServer</p></td>
<td><p>Este atributo habilita um usuário ou contato para o sistema de mensagens SIP. Ele é adicionado à classe de contato porque na topologia de floresta central, objetos de contato, não objetos de usuário, são habilitados para SIP.</p>
<p>O valor válido é o DN do servidor Standard Edition ou pool de Front End do Enterprise Edition onde um usuário está hospedado.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-PrimaryUserAddress</p></td>
<td><p>Este atributo contém o endereço SIP de um determinado usuário.</p></td>
<td><p>-</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-PrivateLine</p></td>
<td><p>Este atributo contém o ID do dispositivo de linha privada.</p></td>
<td><p>Novo no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Routable</p></td>
<td><p>Este é um atributo booleano usado para determinar se o Lync Server está autorizado a rotear para este serviço usando seu endereço GRUU. Se este valor estiver definido como <strong>TRUE</strong>, o Lync Server está autorizado a rotear para este serviço. Se estiver definido como <strong>FALSE</strong>, o Lync Server não está autorizado.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RouteUsageAttribute (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres UNICODE de valor único define um atributo que qualifica a utilização para uma rota de telefone. A seleção de uma rota de telefone é determinada com base em dois elementos: o atributo de uso atribuído à rota de telefone e os atributos de uso da política permitida ao chamador. A primeira rota de telefone com um atributo de uso que corresponde à utilização permitida ao chamador é selecionada.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RouteUsageLinks (obsoleto)</p></td>
<td><p>Este atributo de nome diferenciado (DN) multivalorado contém uma lista de nomes diferenciados de uso de rota.</p>
<p>Vínculo sequencial: <strong>Link ID 11032</strong></p>
<p>Este atributo é um vínculo sequencial para o vínculo inverso correspondente <strong>msRTCSIP-PhoneRouteBL</strong>.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-RoutingPoolDN</p></td>
<td><p>Este atributo contém o DN que aponta para o pool através do qual todo o tráfego SIP endereçado a este MCU ou Serviço Confiável deve passar.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-RuleName (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres UNICODE de valor único especifica o nome amigável da regra de normalização, para que possa ser facilmente referenciada por um administrador.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SchemaVersion</p></td>
<td><p>Este atributo representa a versão do esquema atualmente implantada na organização.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-SearchMaxRequests (obsoleto)</p></td>
<td><p>Este atributo limita o número de resultados de pesquisa retornados a partir de uma pesquisa de diretório, quando um usuário busca um contato usando o Communicator. Este atributo substituirá o valor fornecido pelo cliente.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SearchMaxResults (obsoleto)</p></td>
<td><p>Este atributo limita o número de solicitações de pesquisa retornadas.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ServerBL</p></td>
<td><p>Este atributo multivalorado é um vínculo inverso que contém uma lista de nomes diferenciados (DN). Estes DNs apontam para um pool ou objeto <strong>TrustedService</strong>.</p>
<p>Este atributo corresponde ao vínculo sequencial <strong>msRTCSIP-TrustedServiceLinks</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ServerData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-ServerReferenceBL (obsoleto)</p></td>
<td><p>Este atributo multivalorado contém uma lista de nomes diferenciados. Estes nomes são vínculos inversos que referenciam outros objetos de servidor que podem ser atribuídos a um perfil de localidade padrão.</p>
<p>Vínculo inverso: <strong>Link ID 11037</strong></p>
<p>O vínculo sequencial correspondente a este vínculo inverso é <strong>msRTCSIP-DefaultLocationProfileLink</strong>.</p>
<p>Este atributo de vínculo inverso referencia somente pools e Servidores de Mediação.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-ServerVersion</p></td>
<td><p>Este atributo define as informações de versão do servidor. Este número de versão aplica-se a todas as funções de servidor. É um inteiro de crescimento lento que aumenta a cada lançamento de produto oficial.</p>
<p>Os valores válidos possíveis são:</p>
<ul>
<li><p>Indefinido: Live Communications Server 2003</p>
<p>                 Live Communications Server 2005</p>
<p>                 Live Communications Server 2005 com SP1</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
<li><p>6: Lync Server 2013</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-SourceObjectType</p></td>
<td><p>Este atributo de valor único do tipo inteiro especifica o tipo de objeto para o qual o <strong>msDS-SourceObjectDN</strong> aponta, da seguinte forma:</p>
<ul>
<li><p>null | 0x00000001: Representa um objeto de usuário principal do Windows NT Server de uma floresta diferente</p></li>
<li><p>Os atributos a seguir representam um tipo de grupo de uma floresta diferente para a expansão do grupo de distribuição:</p>
<ul>
<li><p>0x00000002: ADS_GROUP_TYPE_GLOBAL_GROUP</p></li>
<li><p>0x00000004: ADS_GROUP_TYPE_DOMAIN_LOCAL_GROUP</p></li>
<li><p>0x00000004: ADS_GROUP_TYPE_LOCAL_GROUP</p></li>
<li><p>0x00000008: ADS_GROUP_TYPE_UNIVERSAL_GROUP</p></li>
<li><p>0x80000000: ADS_GROUP_TYPE_SECURITY_ENABLED</p></li>
<li><p>0x90000000: Representa um Atendedor Automático ou objeto de acesso do assinante da mesma floresta ou de uma floresta diferente</p></li>
</ul></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-SubscriptionAuthRequired (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2003.</p>
<p>Obsoleto no Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TargetHomeServer</p></td>
<td><p>Este atributo permite mover um usuário ou objeto contato de um servidor ou pool do Lync Server para outro. Esse atributo é adicionado à classe de contato, pois na topologia da floresta, os objetos de contato e não objetos do usuário, estão habilitados para SIP.</p>
<p>O valor válido é o DN do servidor Standard Edition de destino ou pool de Front End para o qual o usuário será movido.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TargetPhoneNumber (obsoleto)</p></td>
<td><p>Este atributo de cadeia de caracteres de valor único contém um padrão de número de telefone ou intervalo para rotear para os gateways específicos definidos no <strong>msRTCSIP-Gateways</strong>.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TargetUserPolicies</p></td>
<td><p>Este atributo armazena pares nome-valor para políticas de destino para usuários do Lync Server.</p></td>
<td><p>Novo no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TenantId</p></td>
<td><p>Este atributo armazena o identificador único para um locatário.</p></td>
<td><p>Novo no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-Translation (obsoleto)</p></td>
<td><p>Este atributo é usado pelo recurso de voz do Lync Server e contém a cadeia de caracteres de tradução a serem aplicados no número discado, se uma correspondência for encontrada.</p></td>
<td><p>Novo no Office Communications Server 2007.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedMCUData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedMCUFQDN</p></td>
<td><p>Este atributo é um valor de cadeia de caracteres que contém o FQDN do MCU. Este é um atributo de valor único. O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedProxyData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedProxyFQDN</p></td>
<td><p>Este atributo é um valor de cadeia de caracteres que contém o FQDN do servidor que está executando o Proxy Server. Este é um atributo de valor único. O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServerData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServerFQDN</p></td>
<td><p>Este é um atributo de valor único que representa o FQDN de um servidor confiável.</p></td>
<td><p>Novo no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServerVersion</p></td>
<td><p>Este atributo especifica o número de versão de um servidor na lista de servidores confiáveis.</p>
<p>Os valores válidos possíveis são:</p>
<ul>
<li><p>NULL: Live Communications Server 2003</p></li>
<li><p>2: Live Communications Server 2005</p></li>
<li><p>3: Office Communications Server 2007</p></li>
<li><p>4: Office Communications Server 2007 R2</p></li>
<li><p>5: Lync Server 2010</p></li>
<li><p>6: Lync Server 2013</p></li>
</ul></td>
<td><p>New in Live Communications Server 2005.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServiceFlags</p></td>
<td><p>Este atributo define as opções habilitadas para o serviço confiável.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServiceLinks</p></td>
<td><p>Este atributo multivalorado contém uma lista de nomes diferenciados (DN) que referenciam um objeto de serviço confiável, como um Serviço de Autenticação de Media Relay. Um Serviço de Autenticação de Media Relay (fisicamente colocado no Servidor de Borda que está executando o Serviço de Conferência A/V) deve estar associado a um pool para suportar cenários de áudio para usuários remotos.</p>
<p>O vínculo inverso correspondente a este atributo de vínculo sequencial é <strong>msRTCSIP-ServerBL</strong>.</p></td>
<td><p>UC</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedServicePort</p></td>
<td><p>Este atributo é um inteiro que define o número de porta usado para estabelecer conexão com este serviço GRUU.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedServiceType</p></td>
<td><p>Este é um atributo de valor de cadeia de caracteres que define o tipo de serviço GRUU que representa.</p>
<p>Os tipos de serviço GRUU válidos são:</p>
<ul>
<li><p>MediationServer</p></li>
<li><p>Gateway</p></li>
<li><p>Serviço de Autenticação de Media Relay (MRAS)</p></li>
<li><p>QoSM</p></li>
<li><p>msRTCSIP-UserExtension CWA</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-TrustedWebComponentsServerData</p></td>
<td><p>Este atributo está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-TrustedWebComponentsServerFQDN</p></td>
<td><p>Este é um atributo de valor de cadeia de caracteres que contém o FQDN do IIS que está executando o Lync Server Web Services. Este á um atributo de valor único. O valor válido para cada segmento pode ter até 63 caracteres; o valor válido para todo o FQDN pode ter até 255 caracteres.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UCFlags (obsoleto)</p></td>
<td><p>Este atributo define diferentes opções de UC que são habilitadas globalmente para todos os objetos de usuário ou de contato. Este atributo é um valor de máscara de bit do tipo inteiro. Cada opção é representada pela presença de um bit.</p>
<p>Os valores válidos possíveis (e posição de bit associada) são:</p>
<ul>
<li><p>4: UsePerUserUCPolicy (posição de bit 2)</p></li>
</ul>
<p>Quando este bit está definido, a política de UC está definida por usuário.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UCPolicy (obsoleto)</p></td>
<td><p>Este atributo de valor único contém o nome diferenciado (DN) da política de UC atribuída a este usuário pelo administrador.</p></td>
<td><p>Obsoleto no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserDomainList (obsoleto)</p></td>
<td><p>Este atributo fornece uma lista de todos os domínios em uma floresta que hospeda usuários habilitados para SIP. O padrão é uma lista vazia, indicando que todos os domínios na floresta estão habilitados para SIP.</p>
<p>Os valores válidos são várias cadeias de caracteres representando os nomes de domínio de domínios individuais.</p></td>
<td><p>Novo no Live Communications Server 2005.</p>
<p>Obsoleto no Lync Server 2010.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserEnabled</p></td>
<td><p>Este atributo determina se o usuário está habilitado para o Lync Server atualmente.</p></td>
<td><p>-</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserExtension</p></td>
<td><p>Este atributo multivalorado contém uma lista de pares nome-valor no formato &quot;nome=valor&quot;. Este atributo está marcado para replicação do catálogo global.</p></td>
<td><p>Novo no Live Communications Server 2005 com SP1.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserLocationProfile</p></td>
<td><p>Este atributo contém o nome diferenciado (DN) que aponta para um objeto de perfil de localidade.</p></td>
<td><p>Novo no Office Communications Server 2007 R2.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserPolicies</p></td>
<td><p>Este atributo armazena pares nome-valor para políticas de usuário.</p></td>
<td><p>Novo no Lync Server 2010.</p>
<p></p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-UserPolicy</p></td>
<td><p>Este é um atributo multivalorado que contém uma lista de nomes diferenciados com binários (DN_WITH_BINARY) apontando para políticas de usuário globais de diferentes tipos. A parte binária indica o tipo de política para o qual a parte DN aponta.</p>
<p>Os valores binários válidos são:</p>
<ul>
<li><p>0x00000001: Política de reunião</p></li>
<li><p>0x00000002: Política de UC</p></li>
<li><p>0x00000005: Política de presença</p></li>
</ul></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-UserRoutingGroupId</p></td>
<td><p>Esta é a ID do grupo de roteamento SIP. Os usuário no mesmo grupo registrarão no mesmo servidor Front-End.</p></td>
<td><p>Novo no Lync Server 2013.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentsData</p></td>
<td><p>Este é um atributo multivalorado que está reservado para uso futuro.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WebComponentsPoolAddress</p></td>
<td><p>Este atributo de valor único aponta para o pool ou servidor Standard Edition ao qual os componentes web pertencem.</p>
<p>Vínculo sequencial: <strong>Link ID 11028</strong></p>
<p>O vínculo inverso correspondente a este atributo de vínculo sequencial é <strong>msRTCSIP-WebComponentsServers</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="odd">
<td><p>msRTCSIP-WebComponentsServers</p></td>
<td><p>Este atributo é uma lista multivalorada de nomes diferenciados. Ele contém uma lista de todos os servidores Web associados a este pool.</p>
<p>Vínculo inverso: <strong>Link ID 11029</strong></p>
<p>O vínculo sequencial correspondente a este vínculo inverso é <strong>msRTCSIP-WebComponentsPoolAddress</strong>.</p></td>
<td><p>Novo no Office Communications Server 2007.</p></td>
</tr>
<tr class="even">
<td><p>msRTCSIP-WMIInstanceId (obsoleto)</p></td>
<td><p>-</p></td>
<td><p>Novo no Live Communications Server 2003.</p>
<p>Obsoleto no Live Communications Server 2005.</p></td>
</tr>
<tr class="odd">
<td><p>OtherIPPhone</p></td>
<td><p>Este atributo existente do Active Directory é usado pela telefonia para especificar a lista de endereços TCP/IP alternativos para um telefone.</p></td>
<td><p>Novo no sistema operacional Windows Server 2008.</p></td>
</tr>
<tr class="even">
<td><p>PhoneOfficeOther</p></td>
<td><p>Este atributo existente do Active Directory é usado pelos componentes de voz no Lync Server somente para objetos de contato, com o objetivo de rotear chamadas para os números do atendedor automático da unificação de mensagens e do acesso do assinante. O endereço de encaminhamento da chamada incondicional é armazenado neste atributo multivalorado. Esta conta é criada para o uso específico do atendedor automático e acesso do assinante. Os atributos desta conta não devem ser modificados pelos administradores.</p></td>
<td><p>Novo no sistema operacional Windows 2000.</p></td>
</tr>
<tr class="odd">
<td><p>ProxyAddresses</p></td>
<td><p>Este atributo multivalorado existente do Active Directory é parte do esquema do Active Directory base apresentado no Windows 2000. Este atributo contém os vários endereços X400, X500 e SMTP do e-mail de um usuário. No Live Communications Server 2003 e posteriores, o URI do SIP do usuário é adicionado a esta lista usando a marca &quot;sip:&quot;.</p>
<p>Os aplicativos a seguir pesquisam o URI do SIP do usuário a partir deste atributo:</p>
<ul>
<li><p>Sistema de mensagens e cliente de colaboração do Microsoft Office Outlook 2003</p></li>
<li><p>Microsoft Office SharePoint Server 2007</p></li>
</ul></td>
<td><p>Novo no sistema operacional Windows 2000.</p></td>
</tr>
<tr class="even">
<td><p>TelephoneNumber</p></td>
<td><p>Este atributo existente do Active Directory contém o número de telefone do usuário.</p></td>
<td><p>Novo no sistema operacional Windows 2000.</p></td>
</tr>
</tbody>
</table>

