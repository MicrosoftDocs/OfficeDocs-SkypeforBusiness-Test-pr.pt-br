---
title: 'Lync Server 2013: Gerenciando locais para gateways ELIN'
TOCTitle: Gerenciando locais para gateways ELIN
ms:assetid: ced79c13-4e7e-4034-95cd-6fc913f4f222
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205288(v=OCS.15)
ms:contentKeyID: 49308148
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando locais para gateways ELIN no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para que o Lync Server ofereça automaticamente locais para clientes dentro de uma rede, é necessário realizar as seguintes tarefas:

  - Preencha o banco de dados do Serviço de Informações de Local com um mapa de rede e inclua Números de Identificação do Local de Emergência (ELINs) no campo CompanyName.

  - Publique os locais para que estejam disponíveis para clientes em sua rede.

  - Carregue os ELINs no banco de dados de Identificação de Localização Automática (ALI) da transportadora PSTN.

Para obter detalhes sobre como realizar estas tarefas, consulte [Configurar o banco de dados de localização no Lync Server 2013](lync-server-2013-configure-the-location-database.md) na documentação de Implantação;

> [!NOTE]  
> Os locais adicionados ao banco de dados central Local não ficam disponíveis para o cliente até que tenham sido publicados usando um comando Shell de Gerenciamento do Lync Server e tenham replicado para os repositórios de local do pool. Para obter detalhes, consulte <a href="lync-server-2013-publish-the-location-database.md">Publicar o banco de dados de localização</a> na documentação Implantação.

Esta seção descreve coisas a considerar conforme você planeja atualizar e manter o banco de dados de localização.

## Planejamento de locais de emergência

Ao usar gateways ELIN, você preenche o banco de dados do Serviço de Informações de Local com o endereço civil, um local específico ao construir e pelo menos um ELIN para cada local. Durante a fase de planejamento, é uma boa ideia decidir como deseja nomear os locais e como você deseja atribuir os ELINs.

## Planejamento dos nomes de local

O campo Serviço de Informações de Local**Location**, que mantém o local específico dentro de uma construção, possui um comprimento máximo de 20 caracteres (incluindo espaços). Dentro deste comprimento limitado, tente incluir o seguinte:

  - Um nome fácil de compreender que identifica o local do chamador 911 para ajudar a garantir que os respondedores da emergência encontrem o local específico rapidamente quando chegarem ao endereço civil. Este nome de local pode incluir um número de construção, número do piso, designador de asa, número da sala e assim por diante. Evite apelidos que são conhecidos apenas pelos funcionários, que pode fazer com que os respondedores de emergência vão para o local incorreto.

  - Um identificador de local que ajuda os usuários a ver facilmente que seu cliente do Lync obteve o local correto. O cliente Lync concatena e exibe automaticamente os campos **Location** e **City** descobertos em seu cabeçalho. Uma prática recomendada é adicionar o endereço da rua do edifício a cada entrada de local, (por exemplo, 1º andar \<número da rua\>). Sem o endereço físico, um identificador de local genérico como "1° andar" pode ser aplicado a qualquer construção na cidade.

  - Se o local for aproximado por ser determinado por um ponto de acesso sem fio, convém adicionar a palavra Near (por exemplo, próximo ao 1º andar, 1234).

## Planejamento de ELINs

Após decidir como você deseja dividir o espaço da construção em locais, é necessário decidir quantos ELINs atribuir em cada local. Por exemplo, em uma construção de vários locais ou pisos, diferentes áreas na construção podem ser atribuídas com zonas de emergência diferentes. Geralmente, cada piso na construção é designado como um local. Cada local é atribuído com um ou mais ELINs, que são usados como números de chamada durante uma chamada de emergência. Entre em contato com sua transportadora PSTN para obter os números de telefone que você pode usar para ELINs. A tabela a seguir oferece um exemplo de locais para um endereço específico.

### Local de amostra e Atribuições de ELIN

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Área de construção</th>
<th>Local</th>
<th>ELIN</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Primeiro andar</p></td>
<td><p>1</p></td>
<td><p>425-555-0100</p></td>
</tr>
<tr class="even">
<td><p>Segundo andar</p></td>
<td><p>2</p></td>
<td><p>425-555-0111</p></td>
</tr>
<tr class="odd">
<td><p>Terceiro andar</p></td>
<td><p>3</p></td>
<td><p>425-555-0123</p></td>
</tr>
</tbody>
</table>


Os locais definidos devem atender os seguintes requisitos:

  - Cumpre os regulamentos locais e nacionais/regionais em termos de área máxima por local e número de locais por endereço.

  - São específicos o suficiente para tornar fácil localizar o chamador de emergência.

## Preenchendo o banco de dados Local

As seguintes perguntas ajudarão a determinar como preencher o banco de dados de local.

  - **Qual processo você usará para preencher o banco de dados de local?**  
    Onde os dados existem e quais etapas você precisa executar para converter os dados para o formato necessário pelo banco de dados de local? Você adicionará locais individualmente ou em lote usando um arquivo CSV?

<!-- end list -->

  - **Você tem um banco de dados de terceiro que já contém um mapeamento de locais?**  
    Ao usar a opção secundária Serviço de Informações de Local do Lync Server para se conectar a um banco de dados de terceiros, é possível agrupar e gerenciar os locais usando uma plataforma offline. Um benefício dessa abordagem é que além de associar locais aos identificadores de rede, é possível associar locais a um usuário. Isso significa que o Serviço de Informações de Local pode retornar múltiplos endereços, a partir do Serviço de Informações de Local secundário até um cliente do Lync Server 2010. Em seguida, o usuário pode escolher o local mais apropriado.
    
    Para integrar com o Serviço de Informações de Local, o banco de dados de terceiros deve servir o esquema de Resposta/Solicitação de Local do Lync Server. Para obter detalhes, consulte <http://go.microsoft.com/fwlink/p/?linkid=213819>. Para obter detalhes sobre a implantação de um Serviço de Informações de Local secundário, consulte [Configurar um serviço de informações de localização secundário no Lync Server 2013](lync-server-2013-configure-a-secondary-location-information-service.md) na documentação de Implantação.

Para obter detalhes sobre como preencher o banco de dados de local, consulte [Configurar o banco de dados de localização no Lync Server 2013](lync-server-2013-configure-the-location-database.md) na documentação Implantação.

## Manutenção do banco de dados Local

Depois de preencher o banco de dados de local, é necessário desenvolver uma estratégia para atualização do banco de dados à medida que a configuração de rede muda. As seguintes perguntas ajudarão a determinar como você manterá o banco de dados de local.

  - **Como você atualizará o banco de dados de local?**  
    Há diversos cenários que exigem uma atualização para o banco de dados de local, incluindo a adição de WAPs (pontos de acesso sem fio), recabeamento do escritório (resultando em atribuições de comutação diferentes) e expansão da subrede. Você atualizará diretamente cada local individual ou realizará uma atualização em massa de todos os locais usando um arquivo CSV?

<!-- end list -->

  - **Você usará um aplicativo SNMP para corresponder a endereços do MAC do cliente do Lync a identificadores de porta e de comutador?**  
    Se você usar um aplicativo SNMP, precisará desenvolver um processo manual para manter as informações de chassi de comutador e de porta consistentes entre o aplicativo SNMP e o banco de dados de local. Se o aplicativo SNMP retornar um endereço IP de chassi ou ID de porta que não esteja incluído no banco de dados, o Serviço de Informações de Local não poderá retornar um local para o cliente.

