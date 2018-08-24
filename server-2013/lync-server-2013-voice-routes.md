---
title: 'Lync Server 2013: Rotas de voz'
TOCTitle: Rotas de voz
ms:assetid: a2ddf327-2ec4-407b-af0f-276f2b13eefd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412757(v=OCS.15)
ms:contentKeyID: 49307660
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Rotas de voz no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-22_

Rotas de chamada especificam como o  Lync Server manipula chamadas feitas por usuários do Enterprise Voice. Quando um usuário disca um número, o Servidor Front-End normaliza a cadeia de caracteres de discagem para o formato E.164, se necessário, e tenta fazê-la corresponder a um URI do SIP. Se o servidor não conseguir fazer a correspondência, aplicará a lógica de encaminhamento de chamadas realizadas com base no número. A etapa final na definição dessa lógica é a criação de uma rota de chamada nomeada separada para cada conjunto de números de telefone listados em cada plano de discagem.

Antes de definir as rotas de chamadas de saída, você deve concluir as seguintes etapas:

  - Implantar um ou mais troncos.

  - Criar planos de discagem conforme a necessidade para sites, indivíduos e objetos de Contato.

  - Criar registros de uso de rede telefônica pública comutada (PSTN).

Além disso, para habilitar o roteamento de chamadas de saída, você deve criar e atribuir uma ou mais políticas de voz. Você pode fazer isso antes ou depois de definir as rotas das chamadas de saída.

Para cada rota, você deve especificar:

  - Um nome pelo qual a rota possa ser facilmente identificada.

  - Uma descrição opcional, caso apenas o nome não seja suficiente para descrevê-la.

  - O padrão de correspondência da expressão regular que identifica os números de telefone de destino aos quais a rota será aplicada, junto com as exceções às quais o padrão de correspondência não será aplicado.

  - Um ou mais troncos que você desejar atribuir à rota.

  - Os registros de uso do PSTN que os usuários devem ter para fazer chamadas para números que correspondam à expressão regular do número de telefone de destino.

Você pode especificar rotas de chamadas no Painel de Controle do Lync Server. Estas rotas alimentam a tabela de roteamento do servidor, que o Lync Server usa para rotear chamadas destinadas para o PSTN.

## Suporte de Tronco M:N

O Lync Server fornece flexibilidade na maneira que as chamadas são roteadas ao PSTN. Uma rota de voz especifica um conjunto de troncos ao PSTN que pode ser usado para uma chamada de voz específica. Um tronco associa um Servidor de Mediação e um número de porta com um gateway PSTN e número de porta de escuta. Essa associação lógica permite que um Servidor de Mediação seja associado com vários gateways e tenha várias conexões ao mesmo gateway. Ao definir uma rota de chamada, você especifica os troncos associados àquela rota, mas não quais Servidor de Mediação estão associados à rota. Para criar troncos definindo as relações entre os Servidor de Mediação e os gateways PSTN,IP-PBXs e Controladores de Borda de Sessão (SBCs), use o Construtor de Topologias.

## Roteamento de Custo Mínimo

A capacidade de especificar os troncos para os quais os diversos números são roteados permite determinar as rotas de menor custo e implementá-las adequadamente. A regra geral para selecionar troncos é escolher o tronco com o gateway mais próximo da localidade do número de destino para reduzir as tarifas de interurbano. Por exemplo, caso você esteja em Nova York telefonando para um número em Roma, a chamada seguiria pela rede IP até o tronco com o gateway no escritório de Roma e os custos seriam os de uma chamada local.

Para um exemplo de como o roteamento de custo mínimo poderia ser usado, considere o seguinte: a Fabrikam decide permitir que os usuários alemães façam chamadas para os números dos EUA usando o tronco norte-americano. A Fabrikam também deseja configurar o sistema para que as chamadas dos usuários do Lync Server dos EUA para a Alemanha e países/regiões adjacentes terminem tronco com o gateway na Alemanha. Este roteamento economizará dinheiro porque uma chamada da Alemanha para a Áustria, por exemplo, é mais barata do que uma chamada dos EUA para a Áustria.

## Como traduzir cadeias de caracteres de discagem de saída

O Lync Server 2013, como seus predecessores imediatos, exige que todas as cadeias de caracteres de chamada sejam normalizadas para o formato E.164 com a finalidade de realizar RNL (pesquisa de número reversa). Para troncos com gateways ou PBXs (private branch exchanges) que exigem números convertidos em formatos de discagem local, o Lync Server 2013 permite criar uma ou mais regras que ajudam na manipulação do número chamado (ou seja, URI de Solicitação), antes de roteá-lo ao tronco. Por exemplo, você pode escrever uma regra para remover +44 do início da cadeia de caracteres de discagem e subsituí-lo por 0144.

Com o Lync Server 2013, é possível criar uma ou mais regras que ajudam na manipulação do número chamado, antes de roteá-lo ao tronco.

Ao planejar seus troncos que se associam com gateways:pares de porta com Servidor de Mediação:pares de porta, pode ser útil agrupar troncos com exigências de discagem local similares, e desta forma reduzir o número de regras de conversões necessárias e o tempo que leva para escrevê-las.

## Como configurar o ID de chamador

Lync Server oferece uma forma de manipular o ID de chamador para chamadas de saída. Por exemplo, se uma organização deseja mascarar os ramais de discagem direta dos funcionários e substituí-los pelo número corporativo ou departamental genérico, um administrador agora pode fazer isso agora usando o Painel de Controle do Lync Server para suprimir o ID de chamador e substituí-lo com um ID de chamador alternativo especificado. Ao planejar a lógica do seu roteamento, considere para quais indivíduos, grupos e sites você deseja essa opção - talvez, mesmo, para todos os funcionários.

> [!NOTE]  
> Para chamadas que são roteadas novamente através do PSTN, o ID de chamador genérico será apresentado em vez do ID de chamador original. Isso pode fazer com que a chamada ignore configurações de Não Incomodar ou de privacidade que o receptor possa ter configurado.

## Lógica de roteamento adicional

Ao criar rotas de chamadas de saída, você deve estar ciente dos seguintes fatores que podem afetar a lógica de roteamento:

  - Onde uma chamada passa por uma fronteira federada, a parte do domínio do URI é usada para rotear a chamada até a empresa responsável por aplicar a lógica de roteamento de saída.

  - Se a parte do domínio do URI de solicitação não contiver um domínio suportado para a empresa, o componente de roteamento de saída no servidor não processa a chamada.

  - Se um usuário não estiver habilitado para o Enterprise Voice, o servidor aplicará outra lógica de roteamento apropriada.

  - Se uma chamada for roteada para um gateway que está completamente ocupado (todas as linhas do tronco estão ocupadas), o gateway rejeita a chamada e a lógica de roteamento de saída a redireciona para a próxima rota de menor custo. Considere isso cuidadosamente, porque um gateway dimensionado para um escritório pequeno no exterior (por exemplo, em Zurique) pode na verdade carregar um volume significativo de tráfego não-local para chamadas internacionais para a Suíça. Se o gateway não for dimensionado corretamente para esse tráfego adicional, as chamadas para a Suíça poderão ser roteadas por um gateway na Alemanha, resultando em tarifas maiores.

