---
title: 'Lync Server 2013: Definindo os elementos de rede usados para determinar local'
TOCTitle: Definindo os elementos de rede usados para determinar local
ms:assetid: 7538779d-055d-44ed-8dd7-11c45fc1b9f5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398567(v=OCS.15)
ms:contentKeyID: 49307134
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo os elementos de rede usados para determinar local no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

Se estiver configurando a infraestrutura do Lync Server para oferecer suporte à detecção automática de cliente local, primeiro você precisará decidir que elementos da rede você pretende usar para mapear os chamadores nos locais. No Lync Server 2013, você pode associar os seguintes elementos de rede de Camada 2 e Camada 3 locais:

  - Endereços de BSSID (Identificação de Conjunto de Serviço Básico) do ponto de acesso sem fio (WAP) (Camada 2)

  - Porta de comutador LLDP (Camada 2)

  - IDs de chassi do comutador LLDP (Camada 2)

  - Sub-redes IP (Camada 3)

  - Endereços MAC do cliente (Camada 2)

Os elementos de rede estão listados em ordem de precedência. Se um cliente pode ser localizado ao usar mais de um elemento de rede, o Lync Server usa a ordem de precedência para determinar qual mecanismo deve ser usado.

As seções a seguir fornecem mais detalhes de uso de cada elemento da rede.

> [!IMPORTANT]  
> Quando você usa elementos de rede para mapear chamadores a locais, é extremamente importante manter o banco de dados do Serviço de Informações de Local atualizado. Por exemplo, se você adicionar ou alterar um elemento de rede (como adicionar um WAP), será necessário excluir a entrada antiga e adicionar a nova no banco de dados de local.

## Ponto de acesso sem fio

Quando um cliente se conecta à rede sem fio, a solicitação de local usa o endereço BSSID do WAP para determinar a sua localização. Se o cliente estiver em roaming, o WAP indicado pode não ser o mais próximo, e é até possível obter um WAP que esteja em outro andar do edifício. Para indicar que o local é aproximado, você pode colocar o valor do local com um descritor Near ou Close to.

Este método local supõe que o BSSID de cada WAP é estático. Entretanto, se o seu fornecedor WAP usa BSSIDs atribuídos dinamicamente, o BSSID obtido de um WAP poderia ser alterado (isso pode acontecer após a alteração de uma configuração WAP) e clientes sem fio podem ser deixados em uma situação onde não recebem um local. Para evitar essa possibilidade, você precisa preencher o banco de dados do Serviço de Informações de Local com ERLs com todos os possíveis endereços BSSID usados por cada WAP.

## Comutadores e portas LLDP

Os comutadores Ethernet gerenciados que oferecem suporte ao protocolo LLDP-MED podem anunciar suas informações de identidade e a porta a clientes compatíveis com LLDP-MED, que podem ser consultados em relação ao banco de dados de local para fornecer o local do dispositivo. Você pode associar ERLs exclusivamente na identificação de chassi de comutador ou pode mapeá-los ao nível de porta.

> [!NOTE]  
> O Lync Server 2013 oferece suporte ao uso de LLDP-MED para determinar somente locais de dispositivos do Lync Phone Edition e Lync 2013 em execução no Windows 8. Se você precisa usar dados em nível de comutador de Camada 2 para determinar o local de outros clientes do Lync com base em computadores com fio, será necessário usar o método de endereço MAC do cliente.

## Sub-rede

As sub-redes IP da Camada 3 fornecem um mecanismo suportado por todos os clientes do Lync Server que pode ser usado para detectar automaticamente o local do cliente. O uso de sub-redes IP é o método de localização mais fácil de configurar e gerenciar os clientes com fio. Porém, antes de decidir usar as sub-redes, você deve usar as seguintes perguntas para ajudar a determinar se a especificidade do local da sub-rede é boa o suficiente para localizar com precisão um cliente:

  - Uma ou mais sub-redes de cliente abrangem vários andares?

  - Uma ou mais sub-redes abrangem mais de um edifício?

  - Quanto espaço é coberto por cada sub-rede do cliente?

Se a sub-rede abrange uma área muito ampla, talvez seja necessário usar outro mecanismo para localizar clientes. No entanto, se for prático, recomendamos que os clientes reorganizem suas sub-redes IP para atender aos requisitos de especificidade de local ERL, em vez de assumir os custos e a complexidade de soluções de terceiros baseadas em SNMP.

## Endereço MAC do cliente

Para usar o endereço MAC do computador cliente para localizar um chamador, você precisa de comutadores Ethernet gerenciados e deve implantar uma solução SNMP de terceiros que possa descobrir os endereços MAC de clientes Lync conectados a (ou através de) esses comutadores. A solução SNMP continuamente controla os comutadores gerenciados para obter mapeamentos atuais dos endereços MAC de extremidade conectados a cada porta e obtém os IDs de porta correspondentes. Durante a solicitação do cliente Lync para o Serviço de Informações de Local, o Serviço de Informações de Local consulta o aplicativo de terceiros usando o endereço MAC do cliente e retorna qualquer correspondência de endereços IP do comutador e IDs de porta. O Serviço de Informações de Local usa essas informações para consultar sua wiremap da Camada 2 publicada um registro coincidente e retorna o local para o cliente. Se você usar esta opção, verifique se os identificadores de porta do comutador são consistentes entre o aplicativo SNMP e os registros publicados do banco de dados de local.

> [!NOTE]  
> Algumas soluções SNMP de terceiros podem oferecer suporte a comutadores de acesso não gerenciados; se a opção de atendimento ao cliente Lync não for gerenciada, mas tem um uplink a um comutador de distribuição gerenciado, o comutador gerenciado pode relatar os endereços MAC dos clientes conectados ao comutador de acesso ao aplicativo SNMP. Essas informações permitem que o Serviço de Informações de Local identifique o local do usuário. No entanto, só é possível atribuir um único ERL a todas as portas no comutador não gerenciado, para que a especificidade do local só esteja disponível a nível do chassi do comutador de acesso, não a nível de porta.
