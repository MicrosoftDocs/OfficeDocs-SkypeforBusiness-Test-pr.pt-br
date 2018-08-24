---
title: Exigências da conferência discada no Lync Server 2013
TOCTitle: Exigências da conferência discada no Lync Server 2013
ms:assetid: 9aff949e-3dac-481a-be46-a180c72e8066
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398802(v=OCS.15)
ms:contentKeyID: 49307576
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Exigências da conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Antes de iniciar o processo de implantação do Lync Server 2013, você precisa planejar o seguinte:

  - A configuração a ser usada para conectar a rede telefônica pública comutada (PSTN)

  - Sua estratégia para atribuir regiões de conferência discada a números de acesso de discagem

  - Sua estratégia para criar diretórios de conferência

## Como planejar a conectividade PSTN de discagem

A conferência discada exige no mínimo um Servidor de Mediação e um gateway PSTN.

Você pode implantar um Servidor de Mediação em um site central ou em um site de filial. No site central, você pode colocar um Servidor de Mediação em um Pool de Front-Ends ou Servidor Standard Edition, ou pode implantá-lo em um servidor ou pool autônomo. Em um site de filial, você pode implantar um Servidor de Mediação em um servidor autônomo ou como um componente do Aparelho de Filial Persistente.

Você pode implantar um gateway PSTN em um site central ou em um site de filial. Em um site de filial, o gateway PSTN pode ser autônomo ou um componente do Aparelho de Filial Persistente.

> [!NOTE]  
> A conferência discada não usa bypass de mídia porque os Servidor de Conferência A/V não suportam bypass de mídia.

Para obter detalhes sobre como planejar sua configuração para Servidor de Mediação e gateways PSTN para conferência discada, consulte [Componentes e topologias para o Servidor de Mediação no Lync Server 2013](lync-server-2013-components-and-topologies-for-mediation-server.md) na documentação de Planejamento.

## Como planejar regiões de conferência discada

Durante a configuração discada, crie planos de discagem e números de acesso de conferência discada. Planos de discagem são conjuntos de regras de normalização que especificam o número e o padrão de dígitos em um número de telefone e traduzem o número de telefone para o padrão E.164 para o roteamento de chamadas. Números de acesso de conferência discada são os números para os quais os participantes ligam para entrar em uma conferência.

Todo número de acesso de conferência discada deve ser associado a no mínimo um plano de discagem. Regiões de conferência discada associam um número de acesso de conferência discada a seus planos de discagem. Ao definir um plano de discagem, especifique a região de conferência discada que se aplica ao plano de discagem. Ao criar o número de acesso de discagem, selecione as regiões que associam o número de acesso aos planos de discagem apropriados.

Ao criar um plano de discagem, especifique o escopo do plano de discagem: escopo de usuário, escopo de pool ou escopo de site. Todo usuário é atribuído ao plano de discagem do escopo mais estreito que se aplicar a ele. Por exemplo, um usuário é atribuído a um plano de discagem de nível de usuário, caso um se aplique. Se um plano de discagem de nível de usuário não se aplicar, o usuário é atribuído a um plano de discagem de nível de pool. Se um plano de discagem de nível de pool não se aplicar, o usuário é atribuído a um plano de discagem de nível de site. Se um plano de discagem de nível de site não se aplicar, o usuário é atribuído ao plano de discagem global.

Antes de configurar os planos de discagem, é importante planejar como você deseja nomear e usar regiões. As considerações a seguir aplicam-se a regiões de conferência discada:

  - Uma região normalmente é uma área geográfica associada a um escritório ou grupo de escritórios.

  - Idiomas são associados a números de acesso de discagem. Se você oferecer suporte a áreas geográficas que possuam vários idiomas, deve decidir como deseja definir regiões para oferecer suporte a vários idiomas. Por exemplo, você pode definir várias regiões com base em uma combinação de geografia e idioma ou pode definir uma única região com base em geografia e ter diferentes números de acesso de discagem para cada idioma.

  - Quando um usuário agenda uma reunião, por padrão a reunião usa a região especificada pelo plano de discagem do usuário.

  - Por padrão, a totalidade dos números de acesso de discagem para a região são incluídos no convite da região.

  - É importante nomear regiões para que sejam claramente reconhecíveis. O usuário pode usar estes nomes das regiões para alterar a região de uma reunião, para que diferentes números de acesso sejam incluídos no convite. (Quando os usuários usam o Outlook para agendar uma reunião, o usuário usa o Suplemento de Reunião Online para Lync 2013 para alterar a região).

  - Regiões devem ser criadas para que qualquer convidado que deseje discar para uma conferência possa ver um número de acesso local no convite da conferência.

  - Você pode configurar a ordem em que os números de acesso dentro de uma região aparecem no Página Configurações de Conferência Discada (e, portanto, a ordem em que aparecem no convite da conferência) usando cmdlets Shell de Gerenciamento do Lync Server.

  - Qualquer usuário de qualquer localização pode ligar para qualquer número de acesso de discagem para entrar em uma conferência.

## Como planejar diretórios de conferência

Diretórios de conferência mantêm um mapeamento entre o ID alfanumérico da reunião que o participante usa para entrar em uma conferência quando estiver usando o Lync 2013 e o ID exclusivamente numérico da conferência que o participante da conferência discada usa para entrar nela. O formato do ID de conferência é como segue:

    <housekeeping digit (1 digit)><conference directory (usually 1-2 digits)><conference number (variable number of digits><check digit (1 digit)>

Criar vários diretórios de conferência garantirá que os IDs de conferência sejam curtos até que uma quantidade significativa de conferências seja criada. Em uma organização com um número comum de conferências por usuário, é recomendável criar um diretório de conferência para cada 999 usuários no pool. Usando essa diretriz, os IDs podem ser geralmente mantidos pequenos. No entanto, assim que o número de diretórios de conferência (em todos os pools) ultrapassar 9, o número do ID de conferência aumentará para suportar conferências adicionais.

## Consulte Também

#### Conceitos

[Componente do Servidor de Mediação no Lync Server 2013](lync-server-2013-mediation-server-component.md)  
[Planos de discagem e regras de normalização no Lync Server 2013](lync-server-2013-dial-plans-and-normalization-rules.md)

