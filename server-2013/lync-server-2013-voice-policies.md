---
title: 'Lync Server 2013: Políticas de voz'
TOCTitle: Políticas de voz
ms:assetid: b7433c62-9d8c-48af-89a0-19f0d34806ec
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412891(v=OCS.15)
ms:contentKeyID: 49307882
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Políticas de voz no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-21_

Lync Server As *políticas de voz* definem o seguinte para cada usuário, site ou organização que recebeu a política:

  - Um conjunto de recursos de chamadas que pode ser habilitado ou desabilitado para disponibilizar a funcionalidade Enterprise Voice aos usuários

  - Um conjunto de registros de uso de PSTN (Rede telefônica comutada pública) que define quais tipos de chamadas são autorizadas.

## Planejando as políticas de voz

As seguintes etapas ajudam você a planejar as políticas de voz necessárias à sua implantação do Enterprise Voice:

  - Determine como você configurará sua política de voz global (a política de voz padrão instalada com o produto). Essa política será aplicada a todos os usuários do Enterprise Voice que não receberam explicitamente uma política de nível de local ou por usuário.

  - Identifique as políticas de voz de nível de local que você possa precisar.

  - Identifique as políticas de voz por usuário que você possa precisar.

  - Decida quais recursos de chamada serão habilitados para cada política de voz.

  - Determine quais registros de uso de PSTN configurar para cada política de voz.

## Escopo da política de voz

*Escopo da política de voz* determina o nível hierárquico no qual a política pode ser aplicada. No Lync Server, é possível configurar políticas de voz com os seguintes níveis de escopo (listados a partir do mais específico até o mais geral).

  - A **Política de voz de usuário** pode ser atribuída a usuários individuais, grupos ou objetos de contato. Essa á política de nível mais baixo. As políticas de voz de usuário podem ser implantadas a fim de habilitar recursos para determinados usuários ou grupos em um site, mas não para outros no mesmo site. Por exemplo, talvez você queira desabilitar a discagem de longa distância para alguns funcionários. Para o objetivo de atribuir uma política de voz, um objeto de contato é tratado como um usuário individual.
    
    > [!NOTE]  
    > Recomendamos que você implante uma política de voz do usuário para os usuários do Enterprise Voice do site de filial, registrados com a implantação do site central ou para usuários registrados em um Aparelho de Filial Persistente.

  - **Política de voz de site** se aplica a todo um site, exceto para quaisquer usuários, grupos ou objetos de contato que recebam uma política de voz de usuário. Para definir uma política de voz de site, você precisa especificar o site ao qual a política será aplicada. Se uma política de voz de usuário não tiver sido atribuída, a política de voz de site será usada.

  - **Política de voz global** é a política de voz padrão, instalada com o produto. É possível editar a política de voz global a fim de atender às necessidades específicas de sua organização, mas não é possível renomear ou excluí-la. Essa política de voz se aplica a todos os usuários, grupos e objetos de contato do Enterprise Voice em sua implantação, a menos que você configure e atribua uma política de voz com um escopo mais específico. Se você quiser desabilitar totalmente essa política, certifique-se de que todos os sites e usuários tenham políticas personalizadas.

## Recursos de chamada

É possível habilitar ou desabilitar os recursos de chamada a seguir para cada política de voz:

  - **Encaminhamento de chamada** permite que os usuários encaminhem chamadas a outros telefones e dispositivos clientes. Habilitado por padrão.

  - **Delegação** permite que o usuário especifique outros usuários para enviar e receber chamadas em seu nome. Habilitado por padrão.

  - **Transferência de chamada** permite a transferência de chamadas para outros usuários. Habilitado por padrão.

  - **Estacionamento de chamada** permite que os usuários estacionem chamadas e atendam à chamada de um telefone ou cliente diferente. Desabilitado por padrão.

  - **Toque simultâneo** permite que as chamadas recebidas toquem em um telefone adicional (por exemplo, um celular) ou outros dispositivos. Habilitado por padrão.

  - **Chamada de equipe** permite que os usuários de uma equipe definida respondam às chamadas de outros membros da equipe. Habilitado por padrão.

  - **Redirecionamento de PSTN** permite que as chamadas realizadas por usuários que receberam essa política para outros usuários empresariais sejam redirecionadas na PSTN (Rede Telefônica Pública Comutada) se a WAN estiver congestionada ou indisponível. Habilitado por padrão.

  - **Substituição da política de largura de banda** permite que os administradores substituam as decisões da política de controle de admissão de chamada para um usuário específico. Desabilitada por padrão.

  - **Rastreamento de chamadas mal-intencionadas** permite que os usuários denunciem chamadas mal-intencionadas usando o cliente Lync e sinaliza essas chamadas nos registros de detalhes de chamada. Desabilitado por padrão.

  - O **Escape do correio de voz** impede que as chamadas sejam roteadas imediatamente para o sistema de correio de voz do telefone móvel do usuário quando a chamada simultânea está configurada e o telefone está desligado, sem bateria ou fora de área, tendo por base um valor de temporizador. Esta configuração habilita e desabilita o temporizador e define o valor dele. Pode ser configurada somente usando o Shell de Gerenciamento do Lync Server. Desabilitado por padrão.

  - **Usos de PSTN de encaminhamento de chamadas e toque simultâneo** permite que os administradores especifiquem o mesmo uso de PSTN que a política de voz para encaminhamento de chamadas e toque simultâneo, restrinjam o encaminhamento de chamadas e o toque simultâneo somente a usuários internos do Lync ou especificar um uso personalizado de PSTN diferente do uso de PSTN da política de voz. O padrão é usar o mesmo uso de PSTN que a política de voz para encaminhamento de chamadas e toque simultâneo.

## Registros de uso de PSTN

Cada política de voz deve ter um ou mais registros de uso de PSTN associados. Os usos de PSTN podem ser associados a uma política de voz somente para toque simultâneo e encaminhamento de chamadas. Para obter detalhes sobre como planejar os registros de uso de PSTN, consulte [Registros de uso de PSTN no Lync Server 2013](lync-server-2013-pstn-usage-records.md).

> [!NOTE]  
> A ordem de uso de PSTN é fundamental, pois ao se comparar usuários a rotas, a funcionalidade de roteamento de saída compara as utilizações de PSTN do início ao fim. Se o primeiro uso corresponder à rota da chamada, essa rota será usada. Caso contrário, a funcionalidade de roteamento de saída analisa o próximo uso de PSTN na lista e continua até que uma correspondência seja encontrada. De fato, os usos de PSTN subsequentes fornecem um backup se o primeiro da lista não estiver disponível.
