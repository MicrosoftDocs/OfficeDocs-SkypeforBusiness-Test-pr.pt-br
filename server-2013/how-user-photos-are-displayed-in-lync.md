---
title: Como as fotos do usuário são exibidas no Lync
TOCTitle: Como as fotos do usuário são exibidas no Lync
ms:assetid: b44a364d-a1d2-4d45-b27a-b5f77775e233
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn783119(v=OCS.15)
ms:contentKeyID: 62833689
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Como as fotos do usuário são exibidas no Lync

 

_**Tópico modificado em:** 2016-12-08_

**Resumo:** as fotos de usuário exibidas no cliente Lync podem ser diferentes, dependendo do recurso do Lync que você está usando; por exemplo, quando está em uma conferência ou em um chat de mensagens instantâneas.

O Lync 2010 incorporou a capacidade de incluir uma foto com o perfil do Lync exibido para outros usuários do Lync. Você também pode decidir se exibirá ou não fotos para seus contatos no cliente Lync. No Lync 2013, há suporte para fotos de alta resolução dos usuários. Este tópico descreve como o cliente Lync obterá e exibirá as fotos do usuário, onde as imagens serão armazenadas, as limitações de cada fonte de imagens e como as fotos do usuário serão utilizadas por diferentes serviços do Lync.

## Considerações sobre planejamento

Considere o seguinte ao planejar a implementação do suporte para fotos do usuário.

  - O suporte para foto de alta resolução do usuário requer que a caixa de correio do usuário esteja localizada no Exchange 2013 e que a conta de usuário do Lync esteja no pool do Lync 2013.

  - Somente um ambiente em que o Lync Server 2013 e o Exchange 2013 sejam utilizados oferece suporte a fotos de alta resolução do usuário.

  - Os usuários com caixas de correio no Exchange 2010 sempre utilizarão o atributo **thumbnailPhoto** do AD DS como fonte de suas fotos de usuário.

  - Uma foto de usuário armazenada como atributo **thumbnailPhoto** no AD DS não será exibida para contatos externos/federados.

  - Se as fotos para os contatos do usuário forem armazenadas no AD DS, o arquivo de imagem será limitado a 96×96 pixels e não terá mais de 100 KB.

  - Se a conectividade entre o Lync Server e o Exchange Server for perdida, o atributo **thumbnailPhoto** de baixa resolução do usuário no AD DS será exibido, e somente para os usuários internos.

  - As fotos de alta resolução do usuário são exibidas nas reuniões do Lync 2013 quando um palestrante ativo não está com vídeo habilitado. Mover o mouse sobre a foto em miniatura na galeria também exibirá a foto de alta resolução.

## Foto do usuário no Lync 2010

No cliente Lync 2010, você pode escolher entre duas opções para exibir uma foto para seu perfil: **Imagem corporativa padrão** e **Mostrar uma imagem de um endereço web**.

## Imagem corporativa padrão

Quando você escolhe a opção **Imagem corporativa padrão**, o Lync exibe a foto para você do Serviços de Domínio Active Directory. A imagem usada é a imagem definida como valor para o atributo **thumbnailPhoto** no Serviços de Domínio Active Directory. Esse é o mesmo arquivo usado pelo Exchange para exibir imagens no Outlook.

Considerações sobre o uso de imagens do Serviços de Domínio Active Directory:

  - Há suporte somente para as imagens com dimensões até 96 x 96 pixels. O arquivo da imagem pode ter até 100 KB.

  - Por padrão, os usuários podem alterar a imagem usada no atributo **thumbnailPhoto**, porém, não diretamente através do cliente Lync. Você pode desabilitar isso no Serviços de Domínio Active Directory.

  - As imagens armazenadas no Serviços de Domínio Active Directory não são exibidas para contatos externos da sua organização, mesmo se forem contatos federados.

  - Nas organizações de grande porte, o armazenamento e a recuperação das imagens para um grande número de usuários podem impactar o tamanho e o desempenho do banco de dados do Serviços de Domínio Active Directory.

  - A limitação das dimensões de imagem e do tamanho de arquivo significa que somente as imagens de baixa resolução podem ser usadas.

## Como os usuários gerenciam as fotos de usuário no Serviços de Domínio Active Directory

O usuário não pode alterar a imagem usada no perfil do Serviços de Domínio Active Directory diretamente no cliente Lync 2010. Ele pode usar uma destas opções para fazer isso, caso estejam disponíveis:

  - **SharePoint Server**   Os usuários podem carregar uma foto para ‘Meu Site’ em um SharePoint Server e, em seguida, [configurar a sincronização do perfil no SharePoint](http://go.microsoft.com/fwlink/p/?linkid=507466) para sincronizar a foto com o atributo **thumbnailPhoto** no Serviços de Domínio Active Directory.

  - **Foto armazenada na URL acessível publicamente**   Os usuários podem configurar a foto de usuário especificando uma URL acessível publicamente para a imagem que desejam usar. A imagem precisa ser acessada publicamente sem uma senha. A imagem armazenada no endereço web especificado é transferida para outros usuários através da categoria de cartão de visita nas informações de presença. Quando o cliente Lync precisa exibir uma foto de usuário, ele recupera a imagem no endereço web especificado.

  - **cmdlets para Windows PowerShell do Exchange 2010**   Os administradores podem executar o cmdlet [Import-RecipientDataProperty](http://go.microsoft.com/fwlink/p/?linkid=507468) no Shell de Gerenciamento do Exchange 2010 para gerenciar o atributo **thumbnailPhoto**. Quando as imagens forem importadas com cmdlets Exchange 2010, o tamanho de arquivo estará limitado a 10 KB.

  - **Ferramentas de terceiros**   Os usuários podem carregar apenas sua própria foto para o atributo **thumbnailPhoto**.

## Mostrar uma imagem de um endereço web

Quando você escolher a opção **Mostrar uma imagem de um endereço web**, o Lync obterá a imagem no endereço que você inseriu e a exibirá como sua foto de usuário no Lync.

Considerações sobre o uso de imagens de um endereço web:

  - Os limites de tamanho de arquivo são determinados pelo atributo **MaxPhotoSizeKB** da política de cliente, definidos com o cmdlet [New-CsClientPolicy](http://go.microsoft.com/fwlink/p/?linkid=507463). O limite de tamanho padrão é 30 KB. O valor máximo é 100 KB. Não há restrição de resolução da imagem, mas se você tentar usar um arquivo de imagem que exceda o limite de tamanho, ele não será baixado para os clientes Lync. Você pode definir o valor como 0 para desabilitar todas as fotos de usuário no Lync.

  - As fotos de usuário de um endereço web podem ser visualizadas por contatos federados externos.

## Gerenciando a foto do usuário com cmdlets da política de cliente

No Lync Server 2010, as configurações de política de cliente são configuradas com os cmdlets CsClientPolicy. As configurações de política definidas são enviadas aos clientes através do provisionamento em banda. Os dois parâmetros dos cmdlets CsClientPolicy que determinam a experiência com foto de usuário são o **DisplayPhoto** e o **MaxPhotoSizeKB**. O parâmetro de provisionamento em banda correspondente para **DisplayPhoto** e **MaxPhotoSizeKB** recebe o nome **PhotoUsage**. Os valores do parâmetro **PhotoUsage** são enviados aos clientes através do **endpointConfigurationprovisionGroup**. Consulte [Visão geral das configurações e políticas de cliente](http://go.microsoft.com/fwlink/?linkid=507470) para obter mais informações.

O valor do parâmetro **DisplayPhoto** determina a fonte da imagem da foto do usuário. Os valores com suporte foram incluídos na tabela a seguir.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Valor do parâmetro DisplayPhoto</th>
<th>Fonte da imagem</th>
<th>Configurações do cliente Lync 2010</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>NoPhoto</p></td>
<td><p>nenhuma</p></td>
<td><p><strong>Não mostrar minha imagem</strong></p></td>
</tr>
<tr class="even">
<td><p>PhotoFromADOnly</p></td>
<td><p>Active Directory</p></td>
<td><p><strong>Imagem corporativa padrão</strong></p></td>
</tr>
<tr class="odd">
<td><p>AllPhotos</p></td>
<td><p>Endereço web</p></td>
<td><p><strong>Mostrar uma imagem de um endereço web</strong></p></td>
</tr>
</tbody>
</table>


## Como o cliente Lync 2010 obtém fotos

No Lync 2010, as fotos de usuário são gerenciadas no servidor pelo Serviço de Catálogo de Endereços. O cliente Lync obtém as fotos de usuário consultando primeiro o serviço Consulta à Web do Catálogo de Endereços (ABWQ) no servidor, que é exposto através do serviço web Expansão da Lista de Distribuição. O cliente recebe o arquivo de imagem e o copia para o cache do usuário para que não precise baixar a imagem cada vez que for necessário exibi-la. Os valores de atributo retornados pela consulta também são armazenados para o usuário na entrada do Serviço de Catálogo de Endereços armazenada em cache. O Serviço de Catálogo de Endereços exclui todas as imagens armazenadas em cache a cada 24 horas, o que significa que pode levar até 24 horas para que as novas imagens do usuário sejam atualizadas no cache do servidor. Você pode forçar uma atualização no cache usando o cmdlet [Update-CsAddressBook](https://docs.microsoft.com/en-us/powershell/module/skype/Update-CsAddressBook).

As fotos de usuário incluídas no status Presença também têm um valor de hash associado que o cliente Lync usa para determinar se há uma imagem mais recente disponível. O cliente é notificado automaticamente das alterações feitas no arquivo de imagem usado no status Presença.

> [!NOTE]  
> Como as fotos não são armazenadas no banco de dados GalContacts.db, o download das fotos de usuário não depende da configuração <strong>AddressBookAvailability</strong> na política de cliente (<a href="http://go.microsoft.com/fwlink/p/?linkid=507508">Set-CsClientPolicy</a>).

A consulta ao serviço ABWQ inclui os seguintes atributos:

  - **PhotoHash**   O valor de hash dos dados binários da foto; é usado para determinar se a foto atual foi alterada.

  - **PhotoRelPath**   O caminho relativo para o arquivo de imagem armazenado no servidor.

  - **PhotoSize**   O tamanho do arquivo de imagem, em bytes.

  - **TimeStamp**   A data e a hora em que o arquivo de imagem foi baixado pela última vez no servidor e copiado para o cache do cliente.

Em seguida, após recuperar o arquivo de imagem, o cliente Lync 2010 compara os valores de atributo retornados pela consulta com base nos valores de atributo recebidos pelo cliente no provisionamento em banda para verificar se são diferentes. Se eles forem diferentes, o cliente recuperará o arquivo de imagem do usuário conectado com uma solicitação HTTP GET.

Além disso, o cliente verifica o servidor a cada 24 horas, a partir do momento em que a versão armazenada em cache do arquivo de imagem foi criada, para comparar o valor do atributo **PhotoHash** no servidor com o valor existente no cliente. Se os valores forem diferentes, o cliente saberá que o arquivo de imagem foi alterado. Para obter o arquivo de imagem atualizado, o cliente consultará mais uma vez o serviço ABWQ para atualizar o arquivo de imagem no cache do cliente com o arquivo de imagem que está no servidor, o que também redefinirá o **TimeStamp** no arquivo contido no cache do cliente.

Este é um exemplo de resposta para uma consulta feita ao serviço ABWQ:

    <Attribute>
              <Name>PhotoRelPath</Name>
              <Value>efa6096aed2746cb9ab2037f7dbdde9d.f2eeeb5946db54a7aa607ecd3ae09d
              95.photo</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
              <Name>PhotoHash</Name>
              <Value>f2eeeb5946db54a7aa607ecd3ae09d95</Value>
              <Values xmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays" i:nil="true" />
    </Attribute>
    <Attribute>
         <Name>PhotoSize</Name>
         <Value>4620</Value>
         <Valuesxmlns:d6p1="http://schemas.microsoft.com/2003/10/Serialization/Arrays"
    i:nil="true" />
    </Attribute>

## Fotos do usuário no Lync 2013

O Lync 2013 incorporou o suporte a imagens de alta resolução das fotos do usuário. O Lync 2013 também oferece suporte ao armazenamento de fotos do usuário na caixa de correio do usuário no Exchange 2013, o que eliminará as limitações de tamanho e resolução de imagem presentes no Lync 2010. As fotos do usuário no Lync 2013 podem ter até 648 x 648 pixels, com um tamanho de arquivo de, no máximo, 20 MB. As fotos de alta resolução no Lync 2013 devem estar localizadas na caixa de correio do usuário no Exchange 2013; há suporte para elas somente no cliente Lync 2013. Esta integração com o Exchange aproveita a nova estrutura de autorização incluída nas versões 2013 do Lync, do Exchange e do SharePoint, denominadas Oauth.

Se o Exchange 2013 não for usado na sua implantação, o suporte às fotos do usuário será o mesmo que o oferecido no Lync 2010. No entanto, as opções do usuário para escolher a foto a ser usada serão diferentes no cliente Lync 2013. No cliente Lync 2013, os usuários podem selecionar **Ocultar minha imagem** ou **Mostrar minha imagem**. Por padrão, a opção **Mostrar uma imagem de um site** não está disponível, mas pode ser habilitada através da atribuição de uma política de cliente.

## Ocultar minha imagem

As configurações das fotos do usuário estão na caixa de diálogo **Opções** no Lync 2013. Quando você escolher **Ocultar minha imagem**, nenhuma foto de usuário será exibida para você no cliente Lync, mas sua foto ainda será exibida no seu cartão de visita e fora do Lync.

## Mostrar minha imagem

Quando você escolher a opção **Mostrar minha imagem**, sua foto de usuário será exibida no cliente Lync e para outros usuários nas conversas do Lync. A imagem usada é a armazenada no AD DS.

## Mostrar uma imagem de um site

A opção **Mostrar imagem de um site** é disponibilizada no Lync 2013 depois que uma política de cliente é definida para habilitá-la. A versão do cliente deve ser mais recente do que 15.0.4535.1002, que é a versão instalada com as [Atualizações cumulativas do Lync: novembro de 2013](http://go.microsoft.com/fwlink/p/?linkid=509908). Talvez, os usuários precisem fazer logout e fazer login novamente para ver as alterações no cliente.

Você pode definir a política do cliente para habilitar a configuração **Mostrar imagem de um site** executando a política [Set-CsClientPolicy](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClientPolicy) no Shell de Gerenciamento do Lync Server. Os cmdlets de exemplo a seguir demonstram como definir a política globalmente para todos os usuários na sua implantação:

```
    $pe=New-CsClientPolicyEntry -Name EnablePresencePhotoOptions -Value True
```
```
    $po=Get-CsClientPolicy -Identity Global
```
```
    $po.PolicyEntry.Add($pe)
```
```
    Set-CsClientPolicy -Instance $po
```

Quando uma imagem é carregada para a caixa de correio do usuário, o Exchange cria automaticamente uma versão de resolução mais baixa da imagem, que pode ser usada nos aplicativos cliente. A foto de usuário também é atualizada no AD DS.

> [!NOTE]  
> Quando um arquivo de imagem é atualizado no AD DS, uma imagem de 48 x 48 pixels é criada e utilizada para o thumbnailPhoto no AD DS. Qualquer imagem existente será substituída. Portanto, se você adicionou uma imagem de 96 x 96 pixels ao AD DS, ela será substituída pela nova imagem de 48 x 48 pixels. Isso só será importante se houver usuários no seu ambiente que usem os clientes Lync 2010, pois esses clientes obterão fotos de usuário no AD DS. Você poderá importar imagens de 96 x 96 pixels para substituir as criadas pelo AD DS, caso tenha clientes Lync 2010 na sua organização.

## Suporte a foto de usuário no Lync 2013

No Lync 2013, há suporte para três resoluções de imagem nas fotos de usuário, conforme descrito na tabela a seguir. A imagem a ser usada é determinada pela configuração de política de cliente atribuída aos usuários do Lync. Consulte “Gerenciando a foto do usuário com os cmdlets de política de cliente” neste tópico para obter mais informações.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Resolução de imagem (pixels)</th>
<th>Aplicativo</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>48 x 48</p></td>
<td><p>Usada se não houver imagem de resolução superior selecionada</p></td>
</tr>
<tr class="even">
<td><p>96 x 96</p></td>
<td><p>Usada no Outlook Web App e no Outlook 2013</p></td>
</tr>
<tr class="odd">
<td><p>648 x 648</p></td>
<td><p>Usada no cliente de desktop Lync 2013 e no Lync 2013 Web App</p></td>
</tr>
</tbody>
</table>


Qualquer usuário com uma caixa de correio habilitada no Exchange 2013 pode carregar uma imagem diferente, inclusive fotos de alta resolução, através das opções do Outlook Web Access ou do cliente Lync 2013. Estas são as configurações recomendadas para as imagens usadas:

  - **Resolução de Imagem**   648 x 648 pixels

  - **Intensidade de Cor**   24 bits

  - **Tamanho do arquivo de imagem**   até 20 MB

  - **Formato do arquivo**   JPEG

Uma imagem JPEG de 24 bits típica, com 648 x 648 pixels, tem aproximadamente 240 KB; portanto, 1 MB de espaço de armazenamento é necessário para cada quatro fotos de usuário.

