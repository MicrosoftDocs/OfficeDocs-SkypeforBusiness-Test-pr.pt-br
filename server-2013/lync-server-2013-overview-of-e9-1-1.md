---
title: 'Lync Server 2013: Visão geral de E9-1-1'
TOCTitle: Visão geral de E9-1-1
ms:assetid: c01e6774-bc9f-4c5b-a60b-478b7317b2b7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412936(v=OCS.15)
ms:contentKeyID: 49307982
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de E9-1-1 no Lync Server 2013

 

_**Tópico modificado em:** 2012-10-29_

O Microsoft Lync Server 2013 suporta chamadas E9-1-1 (9-1-1 Avançado) de clientes do Lync e dispositivos com Lync Phone Edition. Quando você configura o Lync Server para E9-1-1, as chamadas de emergência feitas de Lync 2013 ou de Lync Phone Edition incluem informações de ERL (Local da resposta de emergência) do banco de dados do Serviço de Informações de Local. ERLs são compostos por endereços cívicos (rua) e outras informações que ajudam a identificar um local mais preciso em escritórios em edifícios e em outras instalações com vários locatários. Quando um usuário faz uma chamada de emergência, o Lync Server encaminha o áudio da chamada junto com o local e as informações de retorno de chamada por meio de um Servidor de Mediação para um provedor de serviço E9-1-1. O provedor de serviço E9-1-1 usa o endereço cívico do chamador para encaminhar a chamada ao PSAP (Ponto de atendimento público seguro) que atende ao local do chamador e envia também uma ESQK (Chave de consulta de serviço de emergência) que o PSAP usa para procurar o ERL do chamador.

O Lync Server suporta dois métodos de roteamento de chamadas de emergência a um provedor de serviço E9-1-1:

  - Uma conexão de tronco SIP com um provedor de serviço qualificado E9-1-1

  - Um gateway ELIN (para um provedor de serviço E9-1-1 baseado em PSTN (Rede Telefônica Pública Comutada)

Ao usar um provedor de serviço E9-1-1 de tronco SIP, é possível adicionar ERLs ao banco de dados do Serviço de Informações de Local e validar os locais com base em um MSAG (Catálogo de Endereços Principal) mantido pelo provedor de serviço E9-1-1. Se um provedor de serviço E9-1-1 recebe uma chamada sem informações sobre o local ou com um local que não foi validado com o MSAG, o provedor de serviço E9-1-1 encaminha a chamada a um ECRC (Centro de resposta à chamada de emergência) nacional/regional, equipado com pessoas especialmente treinadas que obtém verbalmente o local do chamador, se for possível, e encaminha manualmente a chamada ao PSAP apropriado. (Alguns provedores de serviço E9-1-1 de tronco SIP também fornecem aos clientes um DID (discagem direta interna) de PSTN ao ECRC, o que proporciona um meio alternativo de encaminhar as chamadas de 9-1-1, se um tronco SIP falhar por qualquer motivo).

Ao contrário dos telefones TDM (Multiplexação de divisão do tempo) e PBX (Central privada de comutação telefônica) com base em IP que possuem locais fixos, um ponto de extremidade do Lync pode ser bastante móvel. Quando você implanta o recurso E9-1-1, o Lync Server garante que não importa onde um chamador esteja localizado, a chamada de emergência pode ser encaminhada ao PSAP que atende ao local do chamador. Por exemplo, se a sede de um usuário fica localizada em Redmond, Washington, mas o usuário faz uma chamada de emergência de um computador em uma filial em Wichita, Kansas, o tronco SIP ou o provedor de serviço E9-1-1 com base em PSTN encaminhará a chamada ao PSAP em Wichita, não ao PSAP em Redmond.

Ao usar um gateway ELIN, você também adiciona ERLs ao banco de dados do Serviço de Informações de Local, mas também inclui um número ELIN para cada local. O número ELIN se torna o número de discagem de emergência durante a chamada de emergência. Em seguida, é necessário certificar-se de que a operadora PSTN carrega os ELINs no banco de dados de ALI (Identificação automática de local).


> [!NOTE]  
> Dispositivos analógicos conectados ao Lync não podem receber informações sobre o local do Serviço de Informações de Local ou transmitir o local ao provedor de serviço E9-1-1. Se você usar a opção do provedor de serviço E9-1-1 do tronco SIP e precisar oferecer suporte ao E9-1-1 a partir de telefones analógicos, terá duas opções:<ul><li><p><strong>Opção PS-ALI tradicional</strong>   Se você tiver gateways PSTN locais em cada site nos quais os telefones analógicos foram implantados e cada telefone analógico tiver um DID, você poderá fornecer o local do dispositivo analógico diretamente com um provedor de serviço PS-ALI (Comutador particular/Identificação de local automática). Nesse caso, você configura políticas de voz do Lync criadas especialmente e as atribui aos objetos de contato com o dispositivo analógico, de modo que as chamadas E9-1-1 desses telefones sejam encaminhadas diretamente pelo gateway local para o provedor de PSTN que atende ao site (em vez de encaminhá-las ao tronco SIP de um provedor de serviço E9-1-1). Quando uma chamada de emergência é feita, um banco de dados em um provedor PS-ALI associado ao tronco do PSTN mapeia o DID de cada telefone analógico para um local físico e fornece esse local ao PSAP. Esses registros precisam ser atualizados com o provedor de serviço PS-ALI sempre que os telefones são movidos para ERLs diferentes.</p></li><li><p><strong>Opção do provedor de serviço E9-1-1</strong>   Você pode registrar os DIDs do telefone analógico e seus ERLs correspondentes com o provedor de serviço E9-1-1, se isso for suportado pelo provedor de serviço E9-1-1. Se o provedor receber uma chamada do Lync Server que não inclua dados de PIDF-LO, o provedor poderá ver se há uma correspondência no banco de dados para o número DID da parte chamadora. Usando o ERL recuperado de seu banco de dados, o provedor pode rotear automaticamente a chamada de emergência para o PSAP correto, e o PSAP receberá o DID do dispositivo analógico e um registro ESQK que permite ao despachante procurar o local do chamador.</p></li></ul>
> Se você usar a opção de gateway ELIN e precisar oferecer suporte a E9-1-1 de telefones analógicos, é possível prover o local do dispositivo analógico diretamente com o provedor de serviços PS-ALI, como descrito na primeira opção acima.


A partir de uma perspectiva do Lync Server, o processo E9-1-1 pode ser separado em dois estágios:

  - Estágio 1: adquirindo um local

  - Estágio 2: roteando a chamada de emergência para um provedor de serviço E9-1-1

Esta seção descreve como esses estágios funcionam.

Se você planeja configurar sua infraestrutura para detectar automaticamente o local do cliente, primeiro você precisa decidir quais elementos de rede serão usados para mapear os chamadores aos locais. Para obter detalhes sobre as opções possíveis, consulte [Definindo os elementos de rede usados para determinar local no Lync Server 2013](lync-server-2013-defining-the-network-elements-used-to-determine-location.md).

## Nesta seção

  - [Adquirindo um local no Lync Server 2013](lync-server-2013-acquiring-a-location.md)

  - [Roteamento de chamadas E9-1-1 usando tronco SIP no Lync Server 2013](lync-server-2013-routing-e9-1-1-calls-by-using-a-sip-trunk.md)

  - [Roteamento de chamadas E9-1-1 usando um gateway ELIN no Lync Server 2013](lync-server-2013-routing-e9-1-1-calls-by-using-an-elin-gateway.md)

