---
title: 'Lync Server 2013: Requisitos de resiliência do site da filial'
TOCTitle: Requisitos de resiliência do site da filial
ms:assetid: a570922c-52bd-42d7-bd64-226578b3d110
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412772(v=OCS.15)
ms:contentKeyID: 49307694
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de resiliência do site da filial para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Este tópico ajudará a você preparar usuários para resiliência de site de filial e persistência da caixa postal, e também especifica os requisitos de hardware e software importantes.

## Preparação de usuários da filial para resiliência de site de filial

Prepare os usuários para resiliência de site de filial configurando o pool de registradores deles como o Aparelho de Filial Persistente (SBA) ou Servidor de Filial Persistente.

## Atribuições do registrador avançado para usuários da filial

Independentemente da solução de resiliência de site de filial escolhida, será necessário atribuir um Registrador principal a cada usuário. Usuários do site de filial sempre devem se registrar nele com o Registrador Avançado, independente de o Registrador estar hospedado no Aparelho de Filial Persistente, Servidor de Filial Persistente, ou Lync Server 2013 Standard autônomo ou Servidor Enterprise Edition. Um registro de recurso de serviço (SRV) de sistema de nome de domínio (DNS) é necessário para que o cliente possa descobrir seu pool de Registrador. Se o Aparelho de Filial Persistente se tornar indisponível, esta é a maneira com que os clientes de filial descobrirão automaticamente o Registrador de backup.

Se um site de filial não possuir um servidor DNS, existem duas formas alternativas para configurar a descoberta do Aparelho de Filial Persistente ou Servidor de Filial Persistente:

  - Configure a opção 120 do DHCP no servidor DHCP (Dynamic Host Configuration Protocol) para apontar para o nome de domínio totalmente qualificado (FQDN) do Aparelho de Filial Persistente ou Servidor de Filial Persistente.

  - Configure o Aparelho de Filial Persistente ou Servidor de Filial Persistente para responder às consultas do DHCP 120.

## Roteamento de voz para usuários de filial

É recomendável criar uma política separada de VoIP (Voice over Internet Protocol) no nível do usuário para usuários em um site de filial. Esta política deve incluir uma rota principal que use o Aparelho de Filial Persistente ou o gateway do servidor de filial e uma ou mais rotas de backup que usem um tronco com um gateway de rede de telefonia comutada pública (PSTN) no site central. Se a rota principal estiver indisponível, a rota de backup que usa um ou mais gateways do site central será utilizada. Desta forma, independentemente de onde o usuário estiver registrado—seja no Registrador Avançado do site de filial ou no pool de registradores de backup no site central—the user’s VoIP policy is always in effect. This is an important consideration for failover scenarios. a política de VoIP do usuário sempre estará em vigor. Esta é uma consideração importante para cenários de failover. Por exemplo, se for necessário renomear o Aparelho de Filial Persistente ou reconfigurar o Aparelho de Filial Persistente para se conectar a um pool de registradores de backup no site central, então você deverá mover os usuários do site de filial para o site central enquanto isso. (Para detalhes sobre como renomear ou reconfigurar um Aparelho de Filial Persistente, consulte [Anexo B: Gerenciando um Aplicativo de Filial Persistente no Lync Server 2013](lync-server-2013-appendix-b-managing-a-survivable-branch-appliance.md) na documentação de Implantação.) Se estes usuários não possuírem políticas de VoIP ou planos de discagem no nível de usuário, quando forem movidos para outro site, as políticas de VoIP e os planos de discagem de nível de site do site central serão aplicados aos usuários como padrão, em vez das políticas de VoIP e planos de discagem de nível de site do site de filial. Neste cenário, a menos que as políticas de VoIP e planos de discagem de nível de site usados pelo pool de registradores de backup também possam ser aplicadas aos usuários do site de filial, suas chamadas falharão. Por exemplo, se os usuários de um site de filial localizado no Japão forem movidos para um site central em Redmund, um plano de discagem com regras de normalização que precedam +1425 a todas as chamadas de 7 dígitos provavelmente não traduzirá chamadas de forma apropriada para estes usuários.

> [!IMPORTANT]  
> Ao criar uma rota de backup do escritório da filial, é recomendável adicionar dois registros de utilização de telefone do PSTN à política do usuário do escritório da filial e atribuir rotas separadas para cada uma. A primeira rota, ou rota principal, direcionaria chamadas para o gateway associado ao Aparelho de Filial Persistente (SBA) ou servidor da filial; a segunda rota, ou rota de backup, direcionaria chamadas para o gateway no site central. Ao direcionar chamadas, o SBA ou servidor da filial tentará todas as rotas atribuídas ao primeiro registro de uso do PSTN antes de tentar o segundo registro de uso.

Para ajudar a garantir que chamadas de entrada para usuários do site da filial cheguem a eles quando o gateway da filial ou o componente Windows do site do Aparelho de Filial Persistente estiver indisponível (que aconteceria, por exemplo, se o Aparelho de Filial Persistente ou o gateway da filial estivesse fora do ar para manutenção), crie uma rota de failover no gateway (ou trabalhe com seu provedor de Número Fixo Virtual - DID) para redirecionar chamadas de entrada para o pool de registradores de backup no site central. Daí, as chamadas serão roteadas sobre o link WAN para os usuários da filial. Garanta que a rota traduza os números para estar de acordo com o gateway PSTN ou outros formatos de número de telefone aceitos pelo ponto do tronco. Para detalhes sobre a criação de uma rota de failover, consulte [Configurando uma rota de failover no Lync Server 2013](lync-server-2013-configuring-a-failover-route.md). Crie também planos de discagem de nível de serviço para o tronco associado ao gateway no site de filial para normalizar chamadas de entrada. Se houver dois Aparelho de Filial Persistente em um site de filial, você pode criar um plano de discagem de nível de site para ambos, a menos que um plano de nível de serviço separado para cada um seja necessário.

> [!NOTE]  
> Para suportar o consumo dos recursos do site central pelos usuários de qualquer site de filial que se apoiem no site central para presença, conferência ou failover, é recomendável considerar cada usuário de site de filial como se estivesse registrado no site central. Atualmente não existem limites para o número de usuários de site de filial, incluindo usuários registrados em um Aparelho de Filial Persistente.

Também é recomendável criar um plano de discagem de nível de usuário e uma política de voz e atribuí-los a usuários do site de filial. Para detalhes, consulte [Criar um plano de discagem no Lync Server 2013](lync-server-2013-create-a-dial-plan.md) e [Criar a política de roteamento VoIP para usuários de filiais no Lync Server 2013](lync-server-2013-create-the-voip-routing-policy-for-branch-users.md) na documentação de Implantação.

## Números de extensão de roteamento

Ao preparar planos de discagem e políticas de Voz para usuários do site de filial, certifique-se de incluir regras de normalização e de conversão que correspondam às cadeias de caracteres e formato de número usados no atributo msRTCSIP-line (ou URI da Linha), de forma que as chamadas do Lync 2013 permitidas entre usuários do site de filial e usuários do site central sejam roteadas corretamente—especialmente quando as chamadas devam ser re-roteadas através do PSTN porque o link WAN está indisponível. Existem considerações especiais adicionais para números discados que contêm números de ramal, em vez de apenas números de telefone.

Regras de normalização e de tradução que correspondam a URIs de Linha que contêm um número de extensão, seja de forma exclusiva ou além de um número de telefone totalmente E.164, possuem requisitos adicionais. Esta seção descreve vários cenários de exemplo para rotear chamadas para URIs de Linha com um número de extensão.

Se sua organização não possui Números Fixos Virtuais (DID) configurados para usuários individuais e a URI de Linha de cada usuário está configurada *apenas* com um número de extensão, usuários internos podem ligar uns para os outros discando apenas um número de extensão. No entanto, é necessário configurar regras de normalização que possam se aplicar a chamadas a partir de um site de filial para um usuário do site central que correspondam a números de extensão.

Em um cenário onde o link WAN entre um site de filial e um site central esteja disponível, chamadas de usuários do site de filial para usuários do site central não exigem que a regra de normalização correspondente traduza o número porque a chamada não é roteada sobre o PSTN. Por exemplo:


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome da regra</th>
<th>Descrição</th>
<th>Padrão do número</th>
<th>Tradução</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5digitExtensions</p></td>
<td><p>Não traduz números de 5 dígitos</p></td>
<td><p>^(\d{5})$</p></td>
<td><p>$1</p></td>
<td><p>10001 não é traduzido</p></td>
</tr>
</tbody>
</table>


Você também deve acomodar números de extensão para cenários específicos, como quando o link WAN entre um site de filial e o site central está indisponível e um chamada de um site de filial deve ser roteada através do PSTN. Durante uma interrupção da WAN, se um usuário do site de filial ligar para um usuário do site central discando apenas sua extensão, você deverá ter uma regra de conversão de saída que adicione o número de telefone completo do usuário do site central. Se a URI de Linha contiver o número de telefone completo da sua empresa e o número de extensão único do usuário em vez de um número de telefone completo que seja único para o usuário, você deverá ter uma regra de conversão de saída que adicione o número de telefone completo da empresa no lugar. Por exemplo:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Padrão de correspondência</th>
<th>Tradução</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Traduz números de 5 dígitos para o número de telefone e extensão de um usuário</p></td>
<td><p>^(\d{5})$</p></td>
<td><p>+14255550123;ext=$1</p></td>
<td><p>10001 é traduzido como +14255550123;ext=10001</p></td>
</tr>
<tr class="even">
<td><p>Traduz números de 5 dígitos para o número de telefone da sua empresa e a extensão de um usuário</p></td>
<td><p>^(\d{5})$</p></td>
<td><p>+14255550100;ext=$1</p></td>
<td><p>10001 é traduzido como +14255550100;ext=10001</p></td>
</tr>
</tbody>
</table>


Neste cenário, se o ponto do tronco que trata o re-roteamento para o PSTN não suportar os números de extensão, a regra de tradução de saída também deve remover o número de extensão. Por exemplo:


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Descrição</th>
<th>Padrão de correspondência</th>
<th>Tradução</th>
<th>Exemplo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Remove a extensão dos números de telefone com extensões</p></td>
<td><p>^\+(\d*);ext=(\d*)$</p></td>
<td><p>+$1</p></td>
<td><p>+14255550123;ext=10001 é traduzido como +14255550123</p></td>
</tr>
</tbody>
</table>


Independente da disponibilidade de um link WAN, se sua organização não possuir números DID configurados para usuários individuais e a URI de Linha para um usuário contiver o número de telefone da sua empresa e o número de extensão único do usuário, você deve configurar a URI de Linha do número de telefone da sua empresa com um número que seja alcançável pelo ponto do tronco ou gateway PSTN no site da filial. Você também deve configurar a URI de Linha do número de telefone da sua empresa para incluir sua própria extensão única para chamadas a serem roteadas para este número.

Para obter detalhes sobre chamadas de um usuário do site central para um usuário do site de filial quando o link WAN entre os sites está indisponível, consulte Preparação para Persistência de Caixa Postal, posteriormente neste tópico. Para detalhes sobre planos de discagem e regras de normalização, incluindo outras regras de exemplo, consulte [Planos de discagem e regras de normalização no Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md) na documentação de Planejamento e [Configurando planos de discagem no Lync Server 2013](lync-server-2013-configuring-dial-plans.md) na documentação de Implantação. Para detalhes sobre regras de tradução de saída, consulte [Regras de tradução no Lync Server 2013](lync-server-2013-translation-rules.md) na documentação de Planejamento e [Definindo regras de tradução no Lync Server 2013](lync-server-2013-defining-translation-rules.md) na documentação de Implantação.

## Preparação para persistência de caixa postal

O Unificação de Mensagens (UM) do Exchange normalmente é instalado apenas em uma central e não em filiais. Um chamador deve ser capaz de deixar uma mensagem de caixa postal, mesmo se o link WAN entre o site da filial e o site central estiver indisponível. Como resultado, configurar a URI de Linha para o número de telefone do Atendedor Automático da UM do Exchange que fornece a caixa postal para usuários do site da filial requer considerações especiais, além de política de Voz, o plano de discagem e as regras de normalização aplicáveis àquele número de caixa postal.

O Aparelho de Filial Persistente (SBAs) e os Servidor de Filial Persistente fornecem persistência de caixa postal para usuários da filial durante a interrupção da WAN. Especificamente, se você estiver usando um Aparelho de Filial Persistente ou Servidor de Filial Persistente e a WAN se tornar indisponível, o SBA ou Servidor de Filial Persistente roteia novamente chamadas não atendidas sobre o PSTN para o UM do Exchange na central. Com um SBA ou Servidor de Filial Persistente, os usuários também podem recuperar mensagens de caixa postal através do PSTN durante uma interrupção da WAN. Finalmente, durante uma interrupção da WAN, o Aparelho de Filial Persistente ou Servidor de Filial Persistente enfileira notificações de chamadas perdidas e as carrega no servidor do UM do Exchange quando a WAN for restaurada. Para garantir que o re-roteamento da caixa postal seja resiliente, certifique-se de adicionar uma entrada para o FQDN do pool do site central e uma entrada para o FQDN do Servidor de Borda para o arquivo de hosts no Servidor de Filial Persistente. Do contrário, a resolução do DNS pode ultrapassar o tempo se não houver um servidor DNS no site da filial.

Recomendamos seguir as configurações a seguir para a persistência de caixa postal para usuários de filiais:

  - Um administrador do Microsoft Exchange deve configurar o Atendedor Automático (AA) do UM do Exchange para aceitar apenas mensagens. Esta configuração desabilita todas as outras funcionalidades genéricas, como transferência para um usuário ou transferência para um operador e limita o AA a aceitar apenas mensagens. Como alternativa, o administrador do Exchange pode usar um AA genérico ou um AA personalizado para rotear a chamada para um operador.

  - O administrador do Lync Server deve usar o número de telefone do AA como o número do **atendedor automático da um do exchange** nas configurações de re-roteamento da caixa postal para o Aparelho de Filial Persistente ou servidor da filial.

  - O administrador do Lync Server deve usar o número de telefone de acesso do assinante ao UM do Exchange como número de **acesso do assinante** nas configurações de re-roteamento da caixa postal para o Aparelho de Filial Persistente ou o Servidor de Filial Persistente.

  - O administrador do Lync Server deve configurar o UM do Exchange para que apenas um plano de discagem seja associado a todos os usuários da filial que precisam acessar a caixa postal durante uma interrupção da WAN.

  - Quando o link WAN está indisponível, as chamadas para usuários do site da filial podem ser roteadas para a caixa postal da UM (Unified Messaging) do Exchange, mas somente se a política de Voz aplicada à chamada especificar um número de telefone de caixa postal que seja único e não inclua um número de extensão.

## Requisitos de hardware e software para resiliência de site de filial

Os requisitos de hardware e software variam, dependendo da sua solução de resiliência.

## Requisitos para Aparelhos de Filial Persistente

O hardware e software necessários são incorporados ao Aparelho de Filial Persistente. No entanto, também recomendamos que cada site de filial implante um servidor DHCP para obter endereços IP clientes; do contrário, quando a concessão do DHCP expirar, os clientes não terão conectividade IP.

Se os servidores DNS da empresa estiverem localizados apenas em sites centrais, usuários do site de filial não conseguirão se conectar a eles durante uma interrupção da WAN e, portanto, a descoberta do Lync Server que usa o servidor DNS SRV (registro de recurso de serviço) falhará. Para garantir o re-roteamento imediato durante uma interrupção da WAN, registros DNS devem ser armazenados em cache no site da filial. Se o roteador da filial for compatível, ative o cache do DNS. Ou você pode implantar um servidor DNS na filial. Pode ser um servidor autônomo ou uma versão do Aparelho de Filial Persistenteque seja compatível com as funcionalidades do DNS. Para detalhes, entre em contato com seu provedor do Aparelho de Filial Persistente.

> [!NOTE]  
> Não é necessário ter um controlador de domínio no site da filial. O Aparelho de Filial Persistente autentica clientes usando um certificado especial que envia ao cliente em resposta à solicitação de certificado do cliente ao entrar.

Clientes do Lync podem descobrir o Lync Server usando a Opção 120 do DHCP (Opção Registrador SIP). Ela pode ser configurada em uma de duas formas:

  - Configure o servidor DHCP no site da filial para responder a consultas do DHCP 120, que retornam o FQDN do Registrador Avançado do Aparelho de Filial Persistente ou Servidor de Filial Persistente.

  - Ative o DHCP do Lync Server. Quando ele está ativado, o Registrador Avançado do Lync Server responde às consultas da Opção 120 do DHCP. Observe que o Registrador Avançado não responde a nenhuma consulta do DHCP diferente da Opção 120 do DHCP.

Além disso, para sites de filial maiores, que possuem várias sub-redes, agentes de retransmissão DHCP devem estar habilitados para encaminhar consultas da Opção 120 do DHCP para o Servidor DHCP (configuração 1) ou para o Registrador Avançado (configuração 2).

Finalmente, usuários do site de filial devem estar configurados para o Enterprise Voice e provisionados com um ponto de extremidade de comunicações unificadas apropriado.

## Requisitos para Servidores de Filial Persistente

Os requisitos de Servidor de Filial Persistente são iguais aos requisitos de um Servidor Front-End. Para obter detalhes, consulte [Plataformas de hardware de servidor para Lync Server 2013](lync-server-2013-server-hardware-platforms.md) na documentação de planejamento.

## Requisitos para implantações de site de filial do Lync Server em larga escala

Para obter detalhes, consulte [Determinando seus requisitos de infraestrutura para Lync Server 2013](lync-server-2013-determining-your-infrastructure-requirements.md) na documentação de Planejamento.

