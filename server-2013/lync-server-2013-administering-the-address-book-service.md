---
title: Administrando o serviço de catálogo de endereços no Lync Server 2013
TOCTitle: Administrando o serviço de catálogo de endereços no Lync Server 2013
ms:assetid: 801e4243-9670-4477-aa2f-88b61ecf5351
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg429711(v=OCS.15)
ms:contentKeyID: 49307267
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Administrando o serviço de catálogo de endereços no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Como parte da implantação do Lync Server, Enterprise Edition ou Servidor Standard Edition, o Serviço de Catálogo de Endereços é instalado por padrão. Os bancos de dados usados pelo Serviço de Catálogo de Endereços – RTCab – é criado no SQL Server (para o Enterprise Edition, é o SQL Server de Back-End, para o Servidor Standard Edition, o SQL Server colocado).

> [!NOTE]  
> Para obter informações sobre como usar o <strong>Editor ADSI</strong> para editar atributos do objeto do Serviços de Domínio Active Directory, consulte <a href="http://go.microsoft.com/fwlink/?linkid=330427">ADSI Edit</a>. Para obter mais informações sobre uma ferramenta no Resource Kit, especificamente o serviço de Catálogo de Endereços, consulte <a href="http://go.microsoft.com/fwlink/?linkid=330429">Microsoft Lync Server 2013 Resource Kit Tools</a>.

## Normalização de Número de Telefone do Servidor de Catálogo de Endereços

Lync Server requer números de telefone RFC 3966/E.164 padronizados. Para usar os números de telefone que não estão estruturados ou estão formatados de forma inconsistente, o Lync Server depende do servidor de catálogo de endereços para pré-processar os números de telefone antes de serem entregues para as regras de normalização. Quando um número de telefone do catálogo de endereços é usado e a regra de normalização é aplicada, os clientes, como Lync Phone Edition e Lync Mobile, podem usar esses números normalizados.

As regras de normalização que foram usadas nas versões anteriores podem não funcionar corretamente sem alguns ajustes. Como o espaço em branco e os caracteres não obrigatórios são removidos antes das regras de normalização, se sua expressão regex estiver procurando especificamente por um traço ou outro caractere que foi removido, a regra de normalização pode falhar. Você deve examinar as regras de normalização para verificar se elas não estão procurando por esses caracteres não obrigatórios, ou se a regra pode falhar normalmente e continuar com o evento onde a regra prevê que o caractere estaria presente mas não está.

## Replicador de Usuários e Servidor de Catálogo de Endereços

O servidor de catálogo de endereços usa os dados fornecidos pelo Replicator de usuários para atualizar as informações que ele obtém inicialmente da lista de endereços global (GAL). O Replicador de usuários grava os atributos Serviços de Domínio Active Directory para cada usuário, contato e grupo na tabela AbUserEntry no banco de dados; o servidor de catálogo de endereços sincroniza os dados de usuário do banco de dados em arquivos no repositório de arquivos do servidor do catálogo de endereços e no banco de dados RTCab do catálogo de endereços. O esquema da tabela de AbUserEntry usa duas colunas, **UserGuid** e **UserData**. A **UserGuid** é a coluna de índice e contém o GUID de 16 bytes do objeto do Active Directory. A **UserData** é uma coluna de imagem que contém todos os atributos Serviços de Domínio Active Directory anteriormente mencionados desse contato.

O Replicador de usuários determina quais atributos do Active Directory gravar ao ler uma tabela de configuração localizada na mesma instância com base em SQL Server que a tabela AbUserEntry. A tabela AbAttribute tem três colunas, **ID**, **Nome**, **Sinalizadores** e **Habilitar**. A tabela é criada durante a instalação do banco de dados. Se a tabela AbAttribute está vazia, o Replicador de usuários ignora a lógica de processamento da tabela AbUserEntry. Os atributos do servidor de catálogo de endereços são dinâmicos e recuperados da tabela AbAttribute, que inicialmente é gravada pelo servidor de catálogo de endereços quando o servidor de catálogo de endereços é ativado.

A ativação do Servidor do Catálogo de Endereços popula a tabela AbAttribute com os valores mostrados na tabela a seguir.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>ID</th>
<th>Nome</th>
<th>Sinalizadores</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>givenName</p></td>
<td><p>0x01400000</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Sn</p></td>
<td><p>0x02400000</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Nome para exibição</p></td>
<td><p>0x03420000</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Título</p></td>
<td><p>0x04000000</p></td>
</tr>
<tr class="odd">
<td><p>5</p></td>
<td><p>mailNickname</p></td>
<td><p>0x05400000</p></td>
</tr>
<tr class="even">
<td><p>6</p></td>
<td><p>Empresa</p></td>
<td><p>0x06000000</p></td>
</tr>
<tr class="odd">
<td><p>7</p></td>
<td><p>physicalDeliveryOfficeName</p></td>
<td><p>0x07000000</p></td>
</tr>
<tr class="even">
<td><p>8</p></td>
<td><p>msRTCSIP-PrimaryUserAddress</p></td>
<td><p>0x08520C00</p></td>
</tr>
<tr class="odd">
<td><p>9</p></td>
<td><p>telefone</p></td>
<td><p>0x09022800</p></td>
</tr>
<tr class="even">
<td><p>10</p></td>
<td><p>homePhone</p></td>
<td><p>0x0A302800</p></td>
</tr>
<tr class="odd">
<td><p>11</p></td>
<td><p>Mobile</p></td>
<td><p>0x0B622800</p></td>
</tr>
<tr class="even">
<td><p>12</p></td>
<td><p>otherTelephone</p></td>
<td><p>0x0C302000</p></td>
</tr>
<tr class="odd">
<td><p>13</p></td>
<td><p>ipPhone</p></td>
<td><p>0x0D302000</p></td>
</tr>
<tr class="even">
<td><p>14</p></td>
<td><p>Correio</p></td>
<td><p>0x0E500000</p></td>
</tr>
<tr class="odd">
<td><p>15</p></td>
<td><p>groupType</p></td>
<td><p>0x0F010800</p></td>
</tr>
<tr class="even">
<td><p>16</p></td>
<td><p>Departamento</p></td>
<td><p>0x10000000</p></td>
</tr>
<tr class="odd">
<td><p>17</p></td>
<td><p>Descrição</p></td>
<td><p>0x11000100</p></td>
</tr>
<tr class="even">
<td><p>18</p></td>
<td><p>Gerente</p></td>
<td><p>0x12040001</p></td>
</tr>
<tr class="odd">
<td><p>19</p></td>
<td><p>proxyAddress</p></td>
<td><p>0x00500105</p></td>
</tr>
<tr class="even">
<td><p>20</p></td>
<td><p>msExchHideFromAddressLists</p></td>
<td><p>0xFF000003</p></td>
</tr>
<tr class="odd">
<td><p>99</p></td>
<td><p>entryID</p></td>
<td><p>0x99000000</p></td>
</tr>
</tbody>
</table>


Os números da coluna **ID** devem ser exclusivos e nunca devem ser reutilizados. O máximo valor de ID é 65535, mas para economizar espaço nos arquivos de saída gravados pelo servidor de catálogo de endereços, use valores de ID abaixo de 256, se possível. A coluna **Nome** corresponde ao nome de atributo do Active Directory que o Replicador de usuário deve colocar na tabela AbUserEntry para cada contato. O valor na coluna **Sinalizadores** é usado para definir o tipo de atributo. Os tipos de atributos do servidor de catálogo de endereços a seguir são reconhecidos pelo Replicador de usuário, indicado pelo baixo byte do valor na coluna **Sinalizadores**.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Atributo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0x0</p></td>
<td><p>Um atributo de seqüência de caracteres. O Replicador de usuário converte esse tipo em UTF-8 antes de armazená-lo na tabela AbUserEntry.</p></td>
</tr>
<tr class="even">
<td><p>0x1</p></td>
<td><p>Um atributo binário. O Replicador de usuário armazena esse blob sem qualquer conversão.</p></td>
</tr>
<tr class="odd">
<td><p>0x2</p></td>
<td><p>Um atributo de seqüência de caracteres, mas é incluído apenas se o valor do atributo começa com &quot;tel:&quot;. Isso é principalmente para atributos com valores múltiplos, especificamente <strong>proxyAddresses</strong>. Nesse caso, o servidor de catálogo de endereços está interessado somente nas entradas de <strong>proxyAddresses</strong> que começam com &quot;tel:&quot;. Portanto, com o intuito de economizar espaço, o Replicador de uuário armazena apenas as entradas que começam com &quot;tel:&quot;.</p></td>
</tr>
<tr class="even">
<td><p>0x3</p></td>
<td><p>Um atributo de sequência de caracteres booliano, que se for VERDADEIRO faz com que o Replicador de usuário não inclua esse contato na tabela AbUserEntry. Se for FALSO, faz com que o Replicador de usuário inclua os atributos desse contato na tabela AbUserEntry, mas não o atributo específico com esse sinalizador. Este é outro tipo de caso especial que é principalmente para o atributo de <strong>msExchHideFromAddressLists</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>0x4</p></td>
<td><p>Um atributo de seqüência de caracteres, mas é incluído apenas se o valor do atributo começa com &quot;smtp:&quot; e inclui o símbolo &quot;@&quot;.</p></td>
</tr>
<tr class="even">
<td><p>0x5</p></td>
<td><p>Um atributo de seqüência de caracteres, mas é incluído apenas se o valor do atributo começa com &quot;tel:&quot; ou &quot;smtp:&quot; e inclui o símbolo &quot;@&quot;.</p></td>
</tr>
<tr class="odd">
<td><p>0x100</p></td>
<td><p>Se definido, é um atributo de valores múltiplos que pode aparecer mais de uma vez para cada contato.</p></td>
</tr>
<tr class="even">
<td><p>0x400</p></td>
<td><p>Se definido, identifica o atributo de nome de conta de usuário do email de um contato. O servidor de catálogo de endereços usa esse sinalizador para identificar que valor de atributo mostrar na entrada do log de eventos de normalização do telefone.</p></td>
</tr>
<tr class="odd">
<td><p>0x800</p></td>
<td><p>Se definido, identifica um atributo necessário para um contato. O servidor de catálogo de endereços inclui um usuário na tabela AbUserEntry somente se houver um valor para este atributo em Active Directory. Se houver mais de um atributo obrigatório, somente é necessário que um deles tenha que incluir o usuário em um valor na tabela AbUserEntry.</p></td>
</tr>
<tr class="even">
<td><p>0x1000</p></td>
<td><p>Se definido, o servidor de catálogo de endereços sempre normaliza o valor desse atributo.</p></td>
</tr>
<tr class="odd">
<td><p>0x2000</p></td>
<td><p>Se definido, o servidor de catálogo de endereços usa o número normalizado de <strong>proxyAddresses</strong>, se a configuração de CMS do <strong>UseNormalizationRules</strong> é FALSO; caso contrário, ele se comporta igual a quando o bit de sinalizador é 0x1000.</p></td>
</tr>
<tr class="even">
<td><p>0x4000</p></td>
<td><p>Se definido, o servidor de catálogo de endereços não inclui os objetos que têm esse valor para o atributo especificado na tabela AbUserEntry. Por exemplo, se o atributo <strong>msRTCSIP-PrimaryUserAddress</strong> tem esse bit de sinalizador definido, os contatos que tenham esse atributo não são gravados no banco de dados.</p></td>
</tr>
<tr class="odd">
<td><p>0x8000</p></td>
<td><p>Se definido, o servidor de catálogo de endereços não inclui objetos na tabela AbUserEntry que não possuam esse valor para o atributo especificado. Se os bits de sinalizador 0x4000 e 0x8000 são definidos em um objeto, o atributo com o valor de bit de sinalizador definido como 0x4000 terá precedência e o objeto é excluído da tabela AbUserEntry.</p></td>
</tr>
<tr class="even">
<td><p>0x10000</p></td>
<td><p>Se definido, representa um objeto de grupo. O Replicador de usuário usa esse bit de sinalizador para incluir os contatos com o atributo de <strong>groupType</strong> cuja presença indica um grupo (por exemplo, uma lista de distribuição ou um grupo de segurança).</p></td>
</tr>
<tr class="odd">
<td><p>0x20000</p></td>
<td><p>Se definido, o Replicador de usuário usa esse bit de sinalizador para incluir este atributo em arquivos de servidor de catálogo de endereços específicos de dispositivo (ou seja, arquivos com uma extensão .dabs).</p></td>
</tr>
</tbody>
</table>


Nas versões anteriores de Lync Server, ao aplicar uma mudança no Active Directory, o administrador deveria executar os cmdlets **Update -CSUserDatabase** e **Update –CSAddressBook**Windows PowerShell para realizar a mudança no banco de dados Lync Server e no banco de dados RTCab imediatamente. Em Lync Server 2013, Lync Server o Replicador de Usuários usará as mudanças no Active Directory e atualizará o banco de dados do Lync Server com base em um intervalo configurado. Lync Server O Replicador de Usuários também propagará as mudanças ao banco de dados RTCab rapidamente sem que o administrador tenha que executar o Update-CSAddressBook. Se a consulta web ao Catálogo de Endereços estiver habilitada, as mudanças serão refletidas nos resultados de busca por clientes Lync. Os administradores precisarão executar o Atualizar -CSAddressBook somente se o download de arquivo do Catálogo de Endereços estiver habilitado.

> [!NOTE]  
> Por padrão, Lync Server o Replicador de Usuários é executado automaticamente a cada 5 minutos. Você pode configurar esse intervalo usando Set -CSUserReplicatorConfiguration -ReplicationCycleInterval &lt;&gt;.

## Filtrando o catálogo de endereços

Os usuários preenchidos nos arquivos do servidor de catálogo de endereços podem ser controlados com base em determinados atributos do Serviços de Domínio Active Directory listados na tabela AbAttribute. Um desses atributos que é usado para a filtragem é o atributo do **msExchangeHideFromAddressBook**. Este é um atributo de usuário adicionado pelo esquema do Exchange. Se o valor desse atributo é VERDADEIRO, o Exchange Server usa esse atributo para ocultar o contato da lista de endereços global do Outlook (GAL). Da mesma forma, se o valor desse atributo é VERDADEIRO, o Replicador de usuário não inclui o usuário na tabela AbUserEntry e esse usuário não estará nos arquivos do servidor de catálogo de endereços.

Você pode usar alguns bits de sinalizadores para definir um filtro a ser usado nos atributos do servidor de catálogo de endereços. Por exemplo, a presença de determinados bits de sinalizador pode identificar um atributo como um atributo de inclusão ou exclusão. O Replicador de usuários filtra os contactos que contêm um atributo de exclusão e filtra conteúdos que não têm um atributo de inclusão.


> [!WARNING]
> Para obter informações sobre como filtrar o Catálogo de Endereços, consulte <A href="https://technet.microsoft.com/en-us/library/gg415643(v=ocs.15)">Cmdlets do servidor de catálogo de endereços</A> e <A href="http://go.microsoft.com/fwlink/?linkid=330430">Filter Lync 2013 address book</A>



Atualmente existem três filtros diferentes. A tabela a seguir lista esses filtros.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Atributo</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0x800</p></td>
<td><p>Se definido, identifica um atributo necessário para um contato. O Replicador de usuário usa esse bit de sinalizador para filtrar os contatos que não contêm pelo menos um atributo necessário. O OuPathId é um atributo obrigatório, que sempre é definido. Portanto, pelo menos um dos outros necessários atributos devem ser definidos. Caso contrário, o contato (isto é, com valor do atributo OuPathId necessário) ainda não será gravado no banco de dados. Por exemplo, se <strong>telephoneNumber</strong> e <strong>TelefoneResidencial</strong> são definidos como atributos necessários, somente os contatos que têm pelo menos um desses atributos são gravados no banco de dados.</p></td>
</tr>
<tr class="even">
<td><p>0x4000</p></td>
<td><p>Se definido, identifica um atributo de exclusão. O Replicador de usuário usa esse bit de sinalizador para filtrar os contactos que contêm esse atributo. Por exemplo, se <strong>msRTCSIP-PrimaryUserAddress</strong> é definido como um atributo de exclusão, contatos que têm este atributo não são gravados no banco de dados.</p></td>
</tr>
<tr class="odd">
<td><p>0x8000</p></td>
<td><p>Se definido, identifica um atributo de inclusão. O Replicador de usuário usa esse bit de sinalizador para filtrar os contactos que não contêm esse atributo. Por exemplo, se <strong>msRTCSIP-PrimaryUserAddress</strong> é definido como um atributo de inclusão, somente os contatos que têm este atributo são gravados no banco de dados.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Se os bits de sinalizador 0x4000 (excluir atributo) e 0x8000 (incluir atributo) estão definidos, o bit 0x4000 substitui o bit 0x8000 e o contato é excluído.

Embora você possa filtrar o catálogo de endereços para incluir somente certos usuários, limitar as entradas não limita a capacidade de outros usuários para entrar em contato com os usuários filtrados ou para ver seu status de presença. Os usuários sempre podem enviar manualmente mensagens instantâneas, iniciar chamadas ou encontrar os usuários que não estão no catálogo de endereços, digitando o nome completo de entrada de um usuário. Além disso, as informações de contato para um usuário também podem ser encontradas no Outlook.

Embora a existência de registros completos de contatos nos arquivos do catálogo de endereços permita que você use o Lync Server para iniciar chamadas de telefone, email ou do Enterprise Voice (isto é, se Enterprise Voice estiver habilitado no servidor) a usuários que não estejam configurados para o protocolo SIP (Session Initiation Protocol), algumas empresas preferem incluir somente os usuários habilitados para o SIP nas entradas de servidor de catálogo de endereços. Você pode filtrar o catálogo de endereços para incluir somente os usuários habilitados para o SIP limpando o bit 0x800 na coluna **Sinalizadores** dos seguintes atributos obrigatórios: **mailNickname**, **telephoneNumber**, **homePhone** e **celular**. Você também pode filtrar o catálogo de endereços para incluir somente os usuários habilitados para SIP, definindo o 0x8000 (inclua o atributo) na coluna **Sinalizadores** do atributo **msRTCSIP-PrimaryUserAddress** . Isso também ajuda a excluir as contas de serviço de arquivos de catálogo de endereços.

Depois de modificar a tabela AbAttribute, você pode atualizar os dados na tabela AbUserEntry executando o comando do cmdlet **Update-CsUserDatabase**. Após a conclusão da replicação UR, é possível atualizar o arquivo no repositório de arquivos do servidor de catálogo de endereços manualmente, executando o comando cmdlet **UpdateCsAddressBook**.

> [!NOTE]  
> O Servidor Front-End no qual o servidor de catálogo de endereços é colocado não é configurável administrativamente. Um deles é escolhido durante a implantação; normalmente o primeiro Servidor Front-End implantado. Em caso de falha, o serviço de catálogo de endereços será movido para outro Servidor Front-End e não requer nenhuma atenção administrativa.

> [!IMPORTANT]  
> Se você consolidou ou modificou de alguma forma a infra-estrutura da implantação de várias florestas ou uma implantação de pai e filho (por exemplo, consolidar a infra-estrutura antes de mover ao Lync Server), é possível encontrar o download do serviço de catálogo de endereços e as falhas de consulta à Web do catálogo de endereços para alguns usuários. Quando em uma implantação que tinha vários domínios ou florestas, o atributo <strong>MsRTCSIP-OriginatorSid</strong> é preenchido nos objetos de usuário que estão apresentando o problema. O atributo <strong>MsRTCSIP-OriginatorSid</strong> deve ser definido como NULO nesses objetos para solucionar o problema.
