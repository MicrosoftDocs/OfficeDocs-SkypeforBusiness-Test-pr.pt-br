---
title: 'Lync Server 2013: Gerenciando locais para fornecedores de serviço de tronco SIP'
TOCTitle: Gerenciando locais para fornecedores de serviço de tronco SIP
ms:assetid: d9b33b56-66c2-4dee-b056-faaf98925bf2
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398959(v=OCS.15)
ms:contentKeyID: 49308296
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciando locais para fornecedores de serviço de tronco SIP no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para configurar o Lync Server a fim de localizar automaticamente os clientes dentro de uma rede, é necessário preencher o banco de dados Serviço de Informações de Local com um mapeamento de cabos de rede e publicar os locais, ou vincular com um banco de dados externo que já contém os mapeamentos corretos. Como parte desse processo, é necessário validar os endereços cívicos dos locais com seu provedor de serviço de E9-1-1. Para obter detalhes, consulte [Configurar o banco de dados de localização no Lync Server 2013](lync-server-2013-configure-the-location-database.md) na documentação Implantação.

Você preenche o banco de dados de serviço de Informação de Local com um Local de Resposta de Emergência (ERL), que consiste de um endereço civil e o endereço específico dentro de uma construção. O campo Serviço de Informações de Local**Location**, que é o local específico dentro de uma construção, possui um comprimento máximo de 20 caracteres (incluindo espaços). Dentro deste comprimento limitado, tente incluir o seguinte:

  - Um nome fácil de entender que identifica o local do chamador de 911 para ajudar a garantir que os respondentes de emergência encontrem o local correto quando chegarem ao endereço cívico. Esse nome de local pode incluir um número de edifício, número do andar, designador de ala, número do quarto, etc. Evite apelidos conhecidos apenas pelos funcionários, que pode fazer com que os respondentes de emergência cheguem ao local errado.

  - Um identificador de local que ajuda os usuários a ver facilmente que seu cliente do Lync obteve o local correto. O cliente Lync concatena e exibe automaticamente os campos **Location** e **City** descobertos em seu cabeçalho. Uma prática recomendada é adicionar o endereço da rua do edifício a cada entrada de local, (por exemplo, 1º andar \<número da rua\>). Sem o endereço físico, um identificador de local genérico como "1° andar" pode ser aplicado a qualquer construção na cidade.

  - Se o local for aproximado por ser determinado por um ponto de acesso sem fio, convém adicionar a palavra Near (por exemplo, "próximo ao 1º andar, 1234").

> [!NOTE]  
> Os locais adicionados ao banco de dados central de local não ficam disponíveis para o cliente até que tenham sido publicados usando um comando Shell de Gerenciamento do Lync Server e tenham replicado para os repositórios de local do pool. Para obter detalhes, consulte <a href="lync-server-2013-publish-the-location-database.md">Publicar o banco de dados de localização</a> na documentação Implantação.

As seções a seguir discutem as considerações que devem ser analisadas ao preencher e manter o banco de dados de local.

## Preenchendo o banco de dados Local

As seguintes perguntas podem ajudar a determinar como você preencherá o banco de dados de local.

  - **Qual processo você usará para preencher o banco de dados de local?**  
    Onde os dados existem e quais etapas você precisa executar para converter os dados para o formato necessário pelo banco de dados de local? Você adicionará locais individualmente ou em lote usando um arquivo CSV?

<!-- end list -->

  - **Você tem um banco de dados de terceiro que já contém um mapeamento de locais?**  
    Ao usar a opção secundária Serviço de Informações de Local do Lync Server para se conectar a um banco de dados de terceiros, é possível agrupar e gerenciar os locais usando uma plataforma offline. Um benefício dessa abordagem é que além de associar locais aos identificadores de rede, é possível associar locais a um usuário. Isso significa que o Serviço de Informações de Local pode retornar múltiplos endereços, a partir do Serviço de Informações de Local secundário até um cliente do Lync Server 2010. Em seguida, o usuário pode escolher o local mais apropriado.
    
    Para integrar com o Serviço de Informações de Local, o banco de dados de terceiros deve seguir o esquema de Resposta/Solicitação de local do Lync Server. Para obter detalhes, consulte "\[MS-E911WS\]: Web Service para Especificação de protocolo de suporte E911" em <http://go.microsoft.com/fwlink/p/?linkid=213819>. Para obter detalhes sobre a implantação de um Serviço de Informações de Local secundário, consulte [Configurar um serviço de informações de localização secundário no Lync Server 2013](lync-server-2013-configure-a-secondary-location-information-service.md) na documentação de Implantação.

Para obter detalhes sobre como preencher o banco de dados de local, consulte [Configurar o banco de dados de localização no Lync Server 2013](lync-server-2013-configure-the-location-database.md) na documentação Implantação.

## Manutenção do banco de dados Local

Depois de preencher o banco de dados de local, é necessário desenvolver uma estratégia para atualização do banco de dados à medida que a configuração de rede muda. As seguintes perguntas ajudarão a determinar como você manterá o banco de dados de local.

  - **Como você atualizará o banco de dados de local?**  
    Há diversos cenários que exigem uma atualização para o banco de dados de local, incluindo a adição de WAPs, recabeamento do escritório (resultando em atribuições de comutação diferentes) e expansão da subrede. Você atualizará diretamente cada local individual ou realizará uma atualização em massa de todos os locais usando um arquivo CSV?

<!-- end list -->

  - **Você usará um aplicativo SNMP para corresponder a endereços do MAC do cliente do Lync a identificadores de porta e de comutador?**  
    Se você usar um aplicativo SNMP, precisará desenvolver um processo manual para manter as informações de chassi de comutador e de porta consistentes entre o aplicativo SNMP e o banco de dados de local. Se o aplicativo SNMP retornar um endereço IP de chassi ou ID de porta que não esteja incluído no banco de dados, o Serviço de Informações de Local não poderá retornar um local para o cliente.

