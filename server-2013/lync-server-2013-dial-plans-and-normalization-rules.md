---
title: 'Lync Server 2013: Planos de discagem e regras de normalização'
TOCTitle: Planos de discagem e regras de normalização
ms:assetid: fde45195-6eb4-403c-9094-57df7fc0bd2a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413082(v=OCS.15)
ms:contentKeyID: 49308714
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Planos de discagem e regras de normalização no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Um plano de discagem é um conjunto nomeado de regras de normalização que converte números de telefone de um local nomeado, usuário individual ou objeto de contato em um formato padrão único (E.164) para fins de roteamento de chamadas e autorização.

As regras de normalização definem como os números de telefone expressos em vários formatos devem ser roteados para cada local, usuário ou objeto de contato especificado. A mesma sequência de discagem pode ser interpretada e convertida de forma diferente dependendo do local do qual ele é discado e a pessoa ou o objeto de Contato fazendo a chamada.

## Escopo do plano de discagem

Um *escopo* do plano de discagem determina o nível hierárquico no qual o plano de discagem pode ser aplicado. No Lync Server, um usuário pode ser atribuído a um plano de discagem por usuário específico. Se um plano de discagem do usuário não for atribuído, o plano de discagem do pool do Registrador é aplicado. Se não houver nenhum plano de discagem do pool do Registrador, o plano de discagem local é aplicado. Finalmente, se nenhum plano de discagem é aplicável para o usuário, o plano de discagem global é aplicado.

Os clientes obtêm níveis de escopo do plano discagem através das configurações de provisionamento em banda que são fornecidas quando os usuários fazem o login no Lync Server. Como administrador, você pode gerenciar e atribuir os níveis de escopo do plano de discagem usando o Painel de Controle do Lync Server.

> [!NOTE]  
> O plano de discagem de gateway PSTN (Rede Telefônica Pública Comutada) a nível de serviço é aplicado às chamadas recebidas por um gateway específico.

Os níveis de escopo do plano de discagem são definidos como a seguir:

  - **Plano de discagem do usuário :** pode ser atribuído a usuários individuais, grupos ou objetos de contato. Os aplicativos de voz podem procurar um plano de discagem por usuário quando uma chamada com o valor de contexto de telefone do usuário padrão é recebida. Para atribuir um plano de discagem, um objeto de contato é tratado como um usuário individual.

  - **Plano de discagem do pool :** pode ser criado no nível de serviço para qualquer gateway PSTN ou Registrador na sua topologia. Para definir um plano de discagem do pool, você deve especificar o serviço (gateway PSTN ou pool do Registrador) ao qual o plano de discagem se aplica.

  - **Plano de discagem local :** pode ser criado para todo um local, exceto para qualquer usuário, grupo ou objeto de contato que são atribuídos com um plano de discagem do pool ou plano de discagem do usuário. Para definir um plano de discagem local, você deve especificar o local ao qual o plano de discagem é aplicado.

  - **Plano de discagem global :** é o plano de discagem padrão instalado com o produto. É possível editar o plano de discagem global, mas não exclui-lo. Este plano de discagem se aplica a todos os usuários, grupos e objetos de contato do do Enterprise Voice na sua implantação, a menos que você configure e atribua um plano de discagem com um escopo mais específico.

## Planejamento de planos de discagem

Para planejar uma discagem, siga estas instruções:

  - Liste todas as localidades nas quais a organização tem escritórios.
    
    A lista deve estar atualizada e ser completa. Precisará ser revisada conforme a organização da empresa evolui. Em uma grande empresa multinacional com várias filiais pequenas, isso pode ser uma tarefa demorada.

  - Identifique padrões de números válidos para cada local.
    
    A parte mais demorada do planejamento de seus planos de discagem é identificar os padrões de números válidos para cada local. Em alguns casos, será possível copiar as regras de normalização gravadas para um plano de discagem a outros planos de discagem, especialmente se os locais correspondentes estão dentro do mesmo país/região ou continente. Em outros casos, as pequenas alterações em números em um plano de discagem podem ser suficientes para usá-los em outros planos de discagem.

  - Desenvolva um esquema de toda a organização para nomeação de planos de discagem.
    
    Adotar um esquema de nomeação padrão garante a consistência em toda a organização e facilita a manutenção e as atualizações.

  - Decida se vários planos de discagem são necessários para um único local.
    
    Se sua organização mantém um único plano de discagem em vários locais, talvez ainda seja necessário criar um plano de discagem separado para usuários do Enterprise Voice que estão migrando de um PBX e que precisam de suas extensões existentes retidas.

  - Decida se os planos de discagem por usuário são necessários. Por exemplo, se você tiver usuários de uma filial que são registrados com o local central ou se você tiver usuários registrados em um Aparelho de Filial Persistente, é possível considerar cenários de discagem especiais com planos de discagem por tais usuário e regras de normalização. Para obter detalhes, consulte [Requisitos de resiliência do site da filial para Lync Server 2013](lync-server-2013-branch-site-resiliency-requirements.md).

  - Determine o escopo do plano de discagem (como descrito anteriormente neste tópico).

Para criar um plano de discagem, especifique os valores nos seguintes campos, conforme necessário, usando o Painel de Controle do Lync Server ou o Shell de Gerenciamento do Lync Server.

## Nome e o nome simples

Para planos de discagem do usuário, você deve especificar um nome descritivo que identifica os usuários, grupos ou objetos de contato para os quais o plano de discagem será atribuído. Para planos de discagem local, o campo Nome é preenchido com o nome do local e não pode ser alterado. Para planos de discagem do pool, o campo Nome é pré-preenchido com o gateway PSTN ou nome de domínio totalmente qualificado (FQDN) do pool de front-end e não pode ser alterado.

O *Nome simples* do plano de discagem é preenchido com uma sequência derivada do nome do plano de discagem. O campo Nome simples é editável, o que permite criar uma convenção de nomenclatura mais descritiva para os planos de discagem. O valor *Nome simples* não pode estar vazio e deve ser exclusivo. Uma prática recomendada é desenvolver uma convenção de nomeação para toda a empresa e usar esta convenção consistentemente em todos os locais e usuários.

## Descrição

Recomendamos digitar o nome comum reconhecível da localização geográfica à qual se aplica o plano de discagem correspondente. Por exemplo, se o nome do plano de discagem for Londres.Contoso.com, a descrição recomendada seria Londres.

## Região da conferência discada

Se você estiver implantando a conferência discada, precisará especificar uma região de conferência de discagem para associar os números de acesso da conferência discada com um plano de discagem.

## Prefixo de acesso externo

É possível especificar um prefixo de acesso externo de até quatro caracteres (\#, \* e 0-9) se os usuários precisam discar um ou mais dígitos adicionais (por exemplo, 9) para obter uma linha externa.

> [!NOTE]  
> Se você especificar um prefixo de acesso externo, não é necessário criar uma regra de normalização adicional para acomodar o prefixo.

## Regras de normalização

As regras de normalização definem como os números de telefone expressos em vários formatos devem ser roteados para o local nomeado. A mesma sequência numérica pode ser interpretada e convertida de forma diferente dependendo do local no qual ela é discada. As regras de normalização são necessárias para o roteamento de chamada porque os usuários podem, e devem, usar vários formatos ao inserir números de telefone em suas listas de contatos.

A normalização de números de telefone fornecidos pelo usuário oferece um formato consistente facilita as tarefas a seguir:

  - Fazer corresponder um número discado com o URI do SIP do destinatário pretendido.

  - Aplicar regras de autorização de discagem ao chamador.

Estes são alguns dos campos numéricos que as regras de normalização talvez precisem considerar:

  - Plano de discagem

  - Código do país

  - Código de área

  - Tamanho da extensão

  - Prefixo do local

## Criando regras de normalização

As regras de normalização usam expressões regulares do .NET Framework para especificar padrões de correspondência numérica que o servidor usa para converter sequências de discagem para o formato E.164 para fins de pesquisa de número inverso. Crie regras de normalização no Painel de Controle do Lync Server inserindo as expressões manualmente ou digitando os dígitos iniciais e o comprimento das sequências de discagem a ser correspondido e permitindo que o Painel de Controle do Lync Server gere a expressão regular correspondente para você. De qualquer forma, ao terminar, você pode inserir um número de teste para verificar se a regra de normalização funciona como esperado.

Para obter detalhes sobre o uso de expressões regulares do .NET Framework, consulte "Expressões regulares do .NET Framework" em [http://go.microsoft.com/fwlink/p/?linkId=140927](http://go.microsoft.com/fwlink/p/?linkid=140927).

## Exemplos de regras de normalização

A tabela a seguir mostra exemplos de regras de normalização que são gravadas como expressões reguladores do .NET Framework. São apenas exemplos e não deve ser uma referência prescritiva para a criação de regras de normalização.

### Tabela 1. Regras de normalização usando expressões regulares do .NET Framework

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
<td><p>4digitExtension</p></td>
<td><p>Converte extensões de 4 dígitos</p></td>
<td><p>^(\d{4})$</p></td>
<td><p>+1425555$1</p></td>
<td><p>0100 é convertido em +14255550100</p></td>
</tr>
<tr class="even">
<td><p>5digitExtension</p></td>
<td><p>Converte extensões de 5 dígitos</p></td>
<td><p>^5(\d{4})$</p></td>
<td><p>+1425555$1</p></td>
<td><p>50100 é convertido em +14255550100</p></td>
</tr>
<tr class="odd">
<td><p>7digitcallingRedmond</p></td>
<td><p>Converte números de 7 dígitos para números locais de Redmond</p></td>
<td><p>^(\d{7})$</p></td>
<td><p>+1425$1</p></td>
<td><p>5550100 é convertido em +14255550100</p></td>
</tr>
<tr class="even">
<td><p>7digitcallingDallas</p></td>
<td><p>Converte números de 7 dígitos para números locais de Dallas</p></td>
<td><p>^(\d{7})$</p></td>
<td><p>+1972$1</p></td>
<td><p>5550100 é convertido em +19725550100</p></td>
</tr>
<tr class="odd">
<td><p>10digitcallingUS</p></td>
<td><p>Converte números de 10 dígitos nos Estados Unidos</p></td>
<td><p>^(\d{10})$</p></td>
<td><p>+1$1</p></td>
<td><p>2065550100 é convertido em +12065550100</p></td>
</tr>
<tr class="even">
<td><p>LDCallingUS</p></td>
<td><p>Converte números com prefixos de longa distância nos Estados Unidos</p></td>
<td><p>^1(\d{10})$</p></td>
<td><p>+$1</p></td>
<td><p>12145550100 é convertido em +2145550100</p></td>
</tr>
<tr class="odd">
<td><p>IntlCallingUS</p></td>
<td><p>Converte números com prefixos internacionais nos Estados Unidos</p></td>
<td><p>^011(\d*)$</p></td>
<td><p>+$1</p></td>
<td><p>01191445550100 é convertido em +91445550100</p></td>
</tr>
<tr class="even">
<td><p>RedmondOperator</p></td>
<td><p>Converte 0 no operador de Redmond</p></td>
<td><p>^0$</p></td>
<td><p>+14255550100</p></td>
<td><p>0 é convertido em +14255550100</p></td>
</tr>
<tr class="odd">
<td><p>RedmondSitePrefix</p></td>
<td><p>Converte números com o prefixo dentro da rede (6) e o código de área de Redmond (222)</p></td>
<td><p>^6222(\d{4})$</p></td>
<td><p>+1425555$1</p></td>
<td><p>62220100 é convertido em +14255550100</p></td>
</tr>
<tr class="even">
<td><p>NYSitePrefix</p></td>
<td><p>Converte números com o prefixo dentro da rede (6) e o código de área de Nova York (333)</p></td>
<td><p>^6333(\d{4})$</p></td>
<td><p>+1202555$1</p></td>
<td><p>63330100 é convertido em +12025550100</p></td>
</tr>
<tr class="odd">
<td><p>DallasSitePrefix</p></td>
<td><p>Converte números com o prefixo dentro da rede (6) e o código de área de Dallas (444)</p></td>
<td><p>^6444(\d{4})$</p></td>
<td><p>+1972555$1</p></td>
<td><p>64440100 é convertido em +19725550100</p></td>
</tr>
</tbody>
</table>


A tabela a seguir ilustra um exemplo de plano de discagem para Redmond, Washington, Estados Unidos, baseado nas regras de normalização mostradas na tabela anterior.

### Tabela 2. Plano de discagem de Redmond com base em regras de normalização mostradas na Tabela 1

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th>Redmond.forestFQDN</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>5digitExtension</p></td>
</tr>
<tr class="even">
<td><p>7digitcallingRedmond</p></td>
</tr>
<tr class="odd">
<td><p>10digitcallingUS</p></td>
</tr>
<tr class="even">
<td><p>IntlCallingUS</p></td>
</tr>
<tr class="odd">
<td><p>RedmondSitePrefix</p></td>
</tr>
<tr class="even">
<td><p>NYSitePrefix</p></td>
</tr>
<tr class="odd">
<td><p>DallasSitePrefix</p></td>
</tr>
<tr class="even">
<td><p>RedmondOperator</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Os nomes das regras de normalização mostrados na tabela anterior não incluem espaços, mas é uma questão de escolha. O primeiro nome da tabela, por exemplo, poderia ter sido escrito &quot;extensão de 5 dígitos&quot; ou &quot;extensão de 5-dígitos&quot; e ainda ser válido.
