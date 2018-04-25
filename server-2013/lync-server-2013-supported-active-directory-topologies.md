---
title: 'Lync Server 2013: Topologias do Active Directory suportadas'
TOCTitle: Topologias do Active Directory suportadas
ms:assetid: 0c76b778-7652-4eb0-b161-86f2d4a94ccf
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398173(v=OCS.15)
ms:contentKeyID: 49305863
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Topologias do Active Directory suportadas no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server 2013 oferece suporte às mesmas topologias Serviços de Domínio Active Directory de Microsoft Lync Server 2010 e Microsoft Office Communications Server 2007 R2. s topologias abaixo têm suporte:

  - Floresta única com domínio único

  - Floresta única com uma única árvore e vários domínios

  - Floresta única com várias árvores e namespaces não contíguos

  - Várias florestas em uma topologia de floresta central

  - Várias florestas em uma topologia de floresta de recursos

  - Várias florestas em uma topologia de floresta de recursos do Lync com Exchange Online

A figura a seguir identifica os ícones usados nas ilustrações desta seção.

**Chave para as ilustrações de topologia**

![Chave para as ilustrações de topologia](images/Gg398173.0c3cc89f-6c43-4bc8-b2ec-61d89e391ee9(OCS.15).jpg "Chave para as ilustrações de topologia")

## Floresta única, domínio único

A topologia mais simples do Active Directory suportada pelo Lync Server, uma floresta de domínio único, é uma topologia comum.

A figura a seguir ilustra uma implantação do Lync Server em uma topologia do Active Directory de domínio único.

**Topologia de domínio único**

![Topologia de domínio único](images/Gg398173.258b3b3f-0558-4a36-a4c2-031be7299668(OCS.15).jpg "Topologia de domínio único")

## Floresta única, vários domínios

Outra topologia do Active Directory suportada pelo Lync Server é uma floresta única que consiste em um domínio raiz e um ou mais domínios filho. Nesse tipo de topologia do Active Directory, o domínio no qual você cria usuários pode ser diferente do domínio no qual você implanta o Lync Server. Porém, se você implantar um pool de Front-Ends, você deve implantar todos os Servidores de Front-Ends no pool com um único domínio. O suporte do Lync Server para grupos de administradores universais do Windows habilita a administração entre domínios.

A figura a seguir ilustra uma implantação em uma floresta única com vários domínios. Nessa figura, um ícone de usuário mostra o domínio em que a conta do usuário está hospedada, e a seta aponta para o domínio em que está o pool Lync Server. As contas de usuário incluem:

  - Contas de usuário no mesmo domínio que o pool do Lync Server

  - Contas de usuário em um domínio diferente do pool do Lync Server

  - Contas de usuário em um domínio filho do domínio com o pool do Lync Server

**Floresta única com vários domínios**

![Floresta única com vários domínios](images/Gg398173.2b809c72-c3cd-4fad-afe6-8c2dae779750(OCS.15).jpg "Floresta única com vários domínios")

## Floresta única, várias árvores

Uma topologia de floresta com várias árvores consiste em dois ou mais domínios que definem estruturas de árvore independentes e namespaces do Active Directory separados.

A figura a seguir ilustra uma floresta única com várias árvores. Nessa figura, um ícone de usuário mostra o domínio em que a conta do usuário está hospedada, uma linha sólida aponta para um pool do Lync Server que está no mesmo domínio ou em um domínio diferente, e uma linha tracejada aponta para o pool do Lync Server que está em uma árvore diferente. As contas de usuário incluem:

  - Contas de usuário no mesmo domínio que o pool do Lync Server

  - Contas de usuário em um domínio diferente do pool do Lync Server (mas na mesma árvore)

  - Contas de usuário em uma árvore diferente do pool do Lync Server

**Floresta única com várias árvores**

![Floresta única com várias árvores](images/Gg398173.db30fa49-174a-4974-8695-41dd78e39432(OCS.15).jpg "Floresta única com várias árvores")

## Várias florestas, floresta central

O Lync Server dá suporte a várias florestas configuradas em uma topologia de floresta central. Topologias de floresta central usam objetos de contato na floresta central para representar os usuários nas outras florestas. A floresta central também hospeda contas de usuário para os usuários dessa floresta. Um produto da sincronização do diretório, como um Microsoft Identity Integration Server (MIIS), um Microsoft Forefront Identity Manager (FIM) 2010 ou um Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1), gerencia o ciclo de vida das contas de usuário dentro da organização: quando um novo usuário é criado em uma das florestas ou quando uma conta de usuário é excluída de uma floresta, o produto de sincronização do diretório sincroniza o contato correspondente na floresta central.

Uma floresta central tem as seguintes vantagens:

  - Os servidores executando o Lync Server ficam centralizados dentro de uma única floresta.

  - Os usuários podem procurar outros usuários em qualquer floresta e se comunicar com eles.

  - Os usuários podem visualizar a presença de outros usuários em qualquer floresta.

  - O produto da sincronização do diretório automatiza a adição e a exclusão de objetos de contato na floresta central à medida que as contas de usuários são criadas ou removidas.

A figura a seguir ilustra a topologia de floresta central. Nessa figura, existem relações de confiança bidirecionais entre o domínio que hospeda o Lync Server, que está na floresta central, e cada domínio somente de usuário, que está em uma floresta separada. O esquema nas florestas de usuários separadas não precisa ser estendido.

**Topologia de floresta central**

![Topologia de floresta central](images/Gg398173.7feb049a-453b-4134-9128-873b83ee1755(OCS.15).jpg "Topologia de floresta central")

## Várias florestas, floresta de recursos

Em uma topologia de floresta de recursos, uma floresta é dedicada a executar aplicativos de servidor, como um Microsoft Exchange Server e um Lync Server. A floresta de recursos hospeda os aplicativos de servidor e uma representação sincronizada do objeto de usuário ativo, mas não inclui contas de usuário habilitadas para logon. A floresta de recursos atua como um ambiente de serviços compartilhado para as outras florestas em que os objetos de usuário residem. As florestas de usuários têm uma relação de confiança no nível de floresta com a floresta de recursos. Quando você implanta o Lync Server nesse tipo de topologia, você cria um objeto de usuário desativado na floresta de recurso para cada conta de usuário nas florestas de usuário. Se o Microsoft Exchange já estiver implantado na floresta de recurso, as contas de usuários desativadas já devem existir. Um produto de sincronização do diretório, como o MIIS, o Microsoft Forefront Identity Manager (FIM) 2010 ou o Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1), gerencia o ciclo de vida das contas de usuário. Quando uma nova conta de usuário é criada em uma das florestas do usuário ou quando uma conta de usuário é excluída de uma floresta, o produto de sincronização do diretório sincroniza a representação do usuário correspondente na floresta de recurso.

Essa topologia pode ser usada para fornecer uma infraestrutura compartilhada para os serviços nas organizações que gerenciam várias florestas ou para separar a administração de objetos do Active Directory de outros tipos de administração. As empresas que precisam isolar a administração do Active Directory por motivos de segurança escolhem essa topologia com frequência.

Essa topologia proporciona a vantagem de limitar a necessidade de estender o esquema do Active Directory a uma única floresta (a saber, a floresta de recursos).

O diagrama a seguir ilustra uma topologia de floresta de recursos.

**Topologia de floresta de recursos**

![Topologia de Floresta de Recursos do Active Directory](images/Gg398173.54ab82f1-e9e5-40f0-a54e-86e340b65c2a(OCS.15).jpg "Topologia de Floresta de Recursos do Active Directory")

## Várias florestas em uma topologia de floresta de recursos do Lync com Exchange Online

Nesta topologia, uma ou mais florestas se encontram no local e são dedicadas à hospedagem de contas de usuário do Active Directory. A floresta de recursos se encontra fora do local e é mantida por um provedor de hospedagem de terceiros. A floresta de recursos contém somente a implantação de Lync Server e uma replicação sincronizada das contas de usuário das florestas de contas de usuário do local. Ela não contém contas de usuário ativadas por logon. O Exchange é implantado nas florestas integradas de contas de usuário do local com o Exchange Online (Híbrido), ou os serviços de email para as contas de usuário do local são fornecidas exclusivamente por Exchange Online.

A floresta de recursos atua como um ambiente de serviços compartilhado para as florestas do Active Directory do local em que os objetos de usuário residem. As florestas da conta de usuário têm um relacionamento de confiança com o nível da floresta unidirecional com a floresta de recursos. Quando você implanta o Lync Server neste tipo de topologia, você cria um objeto de usuário desativado na floresta de recurso para cada conta de usuário nas florestas de usuário. Um produto de sincronização do diretório, como o MIIS, o Microsoft Forefront Identity Manager (FIM) 2010 ou o Microsoft Identity Lifecycle Manager (ILM) 2007 Feature Pack 1 (FP1), gerencia o ciclo de vida das contas de usuário. Quando uma nova conta de usuário é criada em uma das florestas do usuário ou quando uma conta de usuário é excluída de uma floresta, o produto de sincronização do diretório sincroniza a representação do usuário correspondente na floresta de recurso. Para obter mais informações sobre a configuração da implantação de várias florestas, consulte [Deploying Lync in a Multi-Forest Architecture (Partner Hosted Lync with Exchange Hybrid)](http://go.microsoft.com/fwlink/p/?linkid=513216).

