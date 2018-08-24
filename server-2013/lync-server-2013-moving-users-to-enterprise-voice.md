---
title: 'Lync Server 2013: Movendo usuários para o Enterprise Voice'
TOCTitle: Movendo usuários para o Enterprise Voice
ms:assetid: a2df6d51-5cf2-4d3e-8f97-496af5fd5e5e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412758(v=OCS.15)
ms:contentKeyID: 49307668
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Movendo usuários para o Enterprise Voice no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Se você estiver movendo usuários de uma infraestrutura de telefonia PBX para o Enterprise Voice, o processo de implantação inclui algumas etapas que não fazem parte do processo de planejamento já descrito em [Planejamento para Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice.md). Para informações sobre a migração de usuários de uma implantação anterior do Enterprise Voice, consulte os documentos de migração incluídos na sua mídia de instalação.

O processo de migração dos usuários de uma infraestrutura de telefonia existente para o Enterprise Voice consiste nas seguintes etapas:

1.  Designar números de telefone principais.

2.  Habilitar usuários para o Enterprise Voice.

3.  Preparar planos de discagem para os usuários.

4.  Planejar as políticas de voz dos usuários.

5.  Planejar rotas de chamadas.

6.  Configurar o PBX ou Tronco SIP para rerotear chamadas para usuários habilitados para o Enterprise Voice.

7.  Mover usuários para Unificação de Mensagens (UM) do Exchange (recomendado).

Este tópico descreve o planejamento necessário em cada uma dessas etapas.

## Etapa 1. Designar números de telefone principais

O Enterprise Voice integra voz a outras mídias de mensagens de forma que, quando uma chamada recebida chega ao servidor, o servidor mapeia o número para o SIP-URI do usuário e, em seguida, bifurca a chamada para todos os pontos de extremidade do cliente associados a esse SIP-URI. Esse processo exige que cada usuário esteja associado a um número de telefone principal.

Um número de telefone principal deve ser:

  - Globalmente exclusivo ou, no caso de ramais internos, exclusivo na empresa.

  - Próprio da empresa e roteável. Números pessoais não devem ser usados.

Os usuários corporativos podem ter dois ou mais números de telefone listados no Serviços de Domínio Active Directory. Todos os números de telefone associados a um usuário específico podem ser exibidos ou alterados na respectiva folha de propriedades no snap-in Usuários e Computadores do Active Directory.

A caixa **Número de telefone** na guia **Geral** da caixa de diálogo **Propriedades do Usuário** deve conter o número de trabalho principal do usuário. Normalmente, esse número é designado como o número de telefone principal do usuário.

Alguns usuários podem ter requisitos especiais (como um executivo que deseja que as chamadas recebidas sejam roteadas por um assistente administrativo), mas essas exceções devem ser limitadas somente àquelas nas quais a necessidade seja clara e crítica.

Após a escolha do número principal, ele deverá ser:

  - Normalizado no formato E.164, sempre que possível.

  - Copiado para o atributo **msRTCSIP-line** do Active Directory.
    
    > [!NOTE]  
    > <strong>Coexistência com o RCC (controle de chamada remota).</strong><br />    RCC é a habilidade de usar o Lync Server para monitorar e controlar um telefone PBX de mesa. O controle é roteado pelo servidor, que atua como um gateway para o PBX. Embora você não possa configurar um usuário para ambos, RCC e Enterprise Voice, a configuração do URI de Linha designa o número de telefone principal do usuário em ambos os casos.<br />    Se você tem uma infraestrutura de PBX existente que deseja que usuários selecionados continuem usando, pode introduzir o Enterprise Voice de forma incremental na sua organização. Para detalhes sobre este cenário de implantação, consulte <a href="lync-server-2013-direct-sip-deployment-options.md">Opções de implantação de SIP Direto no Lync Server 2013</a> na documentação de Planejamento.<br />    Em versões anteriores, era possível habilitar ambos, RCC e o Enterprise Voice para um usuário, mas somente se você configurasse o usuário também para bifurcação dupla, um recurso em que uma chamada de entrada toca no telefone PBX de um usuário e no Communicator simultaneamente. No Lync Server 2010, a bifurcação dupla não é suportada.

Há três métodos para popular o atributo **msRTCSIP-line**:

  - Microsoft Identity Integration Server (recomendado)

  - A página **Usuários** no Painel de Controle do Lync Server

Quando é necessário processar vários números de telefone, um script personalizado desenvolvido por sua organização é a melhor opção. Dependendo de como a organização representa os números de telefone nos Serviços de Domínio do Active Directory, o script talvez precise normalizar números de telefone principais no formato E.164 antes de copiá-los para o atributo **msRTCSIP-line**.

  - Se a sua organização mantém todos os números de telefone dos Serviços de Domínio Active Directory em um único formato, e se esse formato é o E.164, então o script só precisará gravar cada número de telefone principal no atributo **msRTCSIP-line**.

  - Se a sua organização mantém todos os números de telefone dos Serviços de Domínio Active Directory em um único formato, mas esse formato não é o E.164, o script deverá definir uma regra de normalização apropriada para converter os números de telefone principais do formato existente no formato E.164, antes de gravá-los no atributo **msRTCSIP-line**.

  - Se a sua organização não impõe um formato padrão aos números de telefone dos Serviços de Domínio Active Directory, o script deverá definir regras de normalização apropriadas para converter os números de telefone principais dos vários formatos existentes no formato E.164, antes de gravá-los no atributo **msRTCSIP-line**.

Seu script também deverá inserir o prefixo **Tel:** antes de cada número principal antes de gravá-lo no atributo **msRTCSIP-line**.

O formato esperado do número especificado nesse atributo é:

  - Tel:+14255550100;ext=50100.

  - Tel:5550100 (para ramais exclusivos na empresa toda).
    
    > [!IMPORTANT]  
    > A normalização realizada pelo ABS (Serviço de Catálogo de Endereços) não substitui nem elimina a necessidade de normalizar o número de telefone principal de cada usuário nos Serviços de Domínio Active Directory, pois o ABS não tem acesso aos Serviços de Domínio Active Directory e, portanto, não pode copiar números de telefone principais para o atributo <strong>msRTCSIP-line</strong>.

## Etapa 2. Habilitar usuários para o Enterprise Voice

Além de identificar os usuários que devem ser habilitados, nenhum outro planejamento especial é necessário para concluir esta etapa.

## Etapa 3. Preparar planos de discagem para os usuários.

Usuários que estão habilitados para o Enterprise Voice não conseguirão fazer chamadas para o PSTN sem planos de discagem. Um plano de discagem é um conjunto nomeado de regras de normalização que converte números de telefone de um local nomeado, usuário individual ou objeto de contato em um formato padrão único (E.164) para fins de roteamento de chamadas e autorização. Regras de normalização definem como números de telefone expressos em vários formatos serão roteados para cada local, usuário ou objeto de contato especificado

Para informações sobre como preparar planos de discagem, consulte [Planos de discagem e regras de normalização no Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md).

## Etapa 4. Planejar as políticas de voz dos usuários

Configurações de serviço de classe do usuário em um PBX herdado, como o direito de fazer chamadas de longa distância ou internacionais a partir dos telefones da empresa, devem ser reconfigurados como políticas de VoIP para usuários movidos para o Enterprise Voice. Para detalhes sobre como planejar e criar políticas para o Enterprise Voice, consulte [Políticas de voz no Lync Server 2013](lync-server-2013-voice-policies.md).

## Etapa 5. Planejar rotas de chamadas de saída

Rotas de chamada especificam como o Lync Server trata chamadas de saída realizadas por usuários do Enterprise Voice. Quando um usuário disca para um número, o servidor, se necessário, normaliza a cadeia de caracteres de discagem para o formato E.164 e tenta compará-lo com um URI de SIP. Se o servidor não conseguir a correspondência, aplica o roteamento de chamada de saída com base no número. A etapa final em definir a lógica é criar uma rota de chamada nomeada separada para cada conjunto de números de telefone de destino que esteja listado em cada plano de discagem.

Para detalhes sobre como planejar rotas de chamada, consulte [Rotas de voz no Lync Server 2013](lync-server-2013-voice-routes.md).

## Etapa 6. Configurar o PBX ou Tronco SIP para rerotear chamadas para usuários do Enterprise Voice

Usuários que anteriormente eram hospedados em uma conexão PBX ou Tronco SIP tradicional com um Provedor de Serviços de Telefonia de Internet (ITSP) mantêm seus números de telefone depois da mudança. O único requisito é que, após a mudança, o PBX ou Tronco SIP deve ser reconfigurado para rotear chamadas de entrada para usuários do Servidor de Mediação.

## Etapa 7. Mover usuários para a Unificação de Mensagens do Exchange (recomendado)

Mover usuários para a Unificação de Mensagens do Exchange consiste das seguintes tarefas:

  - Configurar a Unificação de Mensagens do Exchange e o Lync Server para trabalharem juntos.

  - Habilitar os usuários para atender chamadas pela Unificação de Mensagens do Exchange e para o Outlook Voice Access. Esta tarefa é executada no servidor de Unificação de Mensagens do Exchange. Para obter detalhes, consulte Biblioteca do Technet do Exchange Server 2010 em [http://go.microsoft.com/fwlink/p/?linkID=139372](http://go.microsoft.com/fwlink/p/?linkid=139372).

