---
title: 'Lync Server 2013: Roteamento de chamadas E9-1-1 usando um gateway ELIN'
TOCTitle: Roteamento de chamadas E9-1-1 usando um gateway ELIN
ms:assetid: 5a3997e3-898d-49cb-922a-4184c3373350
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204919(v=OCS.15)
ms:contentKeyID: 49306804
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Roteamento de chamadas E9-1-1 usando um gateway ELIN no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Alguns parceiros do Programa de Interoperabilidade Aberta de Comunicações Unificadas fornecem gateways compatíveis com ELIN (número de identificação de local de emergência) qualificados, que podem servir como uma alternativa a uma conexão de tronco SIP com um provedor de serviços E9-1-1 qualificado. Os gateways ELIN oferecem suporte à conectividade CAMA (Contabilidade de Mensagem Automática Centralizada) ou ISDN com serviços E9-1-1 baseados em PSTN (Rede Telefônica Pública Comutada). Para obter detalhes sobre os parceiros que fornecem gateways ELIN e links para sua documentação, consulte [http://go.microsoft.com/fwlink/p/?LinkId=248425](http://go.microsoft.com/fwlink/p/?linkid=248425).

Assim como as conexões de tronco SIP com provedores de serviços E9-1-1, os gateways ELIN também fornecem um meio de encaminhar uma chamada de emergência para o PSAP (ponto de atendimento público seguro) mais apropriado do chamador, mas esses gateways usam um ELIN como identificador do local. Você define ELINs para cada ERL (Local de Resposta de Emergência) em sua organização (para obter detalhes, consulte [Gerenciando locais para gateways ELIN no Lync Server 2013](lync-server-2013-managing-locations-for-elin-gateways.md)).

Quando você usa um gateway ELIN para chamadas de emergência, usa a mesma infraestrutura de E9-1-1 do Lync Server que usaria para uma conexão de tronco SIP. Ou seja, o banco de dados do Serviço de Informações de Local fornece o local para o cliente do Lync Server e a política de local habilita o recurso e define o encaminhamento. Com um gateway ELIN, por sua vez, é necessário adicionar os ELINs ao banco de dados do Serviço de Informações de Local e solicitar que sua operadora de PSTN os carregue no banco de dados ALI (Identificação de Local Automática).

Quando um cliente do Lync obtém seu local do Serviço de Informações de Local, o local inclui o ELIN. Durante uma chamada de emergência, o ELIN é incluído no local enviado para o gateway ELIN. O gateway ELIN identifica a chamada como uma chamada de emergência e troca o número do chamador pelo ELIN. Em seguida, o gateway de ELIN encaminha a chamada para a PSTN com o ELIN como número chamador. O provedor de E9-1-1 da PSTN pesquisa o ELIN no banco de dados ALI, que é um banco de dados complementar ao banco de dados MSAG (Guia principal de endereços de ruas). A PSTN então envia a chamada para o PSAP mais apropriado com base na pesquisa do ALI, e o PSAP envia os primeiros atendentes para o local do chamador com base na pesquisa do ALI. O número chamador é armazenado em cache no gateway ELIN por um tempo predefinido para retornos de chamada. Durante um retorno de chamada, o PSAP chega ao gateway ELIN, que troca o ELIN pelo número DID (discagem direta interna) do chamador.

Os gateways ELIN oferecem suporte a chamadas de emergência somente de dentro da rede da sua organização. Eles não oferecem suporte a chamadas de emergência realizadas fora da sua rede.

> [!NOTE]  
> Para obter detalhes sobre o uso de uma conexão de tronco SIP para chamadas de emergência, consulte <a href="lync-server-2013-routing-e9-1-1-calls-by-using-a-sip-trunk.md">Roteamento de chamadas E9-1-1 usando tronco SIP no Lync Server 2013</a>.

O diagrama a seguir mostra como uma chamada de emergência é encaminhada do Lync Server para o PSAP quando um gateway ELIN é usado.

**Encaminhando chamadas de E9-1-1 com um gateway ELIN**

![Roteamento de chamada ELIN](images/JJ204919.ea68f88a-0fc4-43d4-9660-79a7e8936df1(OCS.15).jpg "Roteamento de chamada ELIN")

1.  Um SIP INVITE que contém o local, o número de retorno de chamada do chamador, a URL de notificação (opcional) e o número de retorno de chamada de conferência, é encaminhado para o Lync Server.

2.  O Lync Server corresponde o número de emergência e encaminha a chamada (com base no valor **Uso do PSTN** definido na política de local aplicável) para um Servidor de Mediação e dele para um gateway ELIN.

3.  O gateway ELIN encaminha a chamada para o PSTN através de um tronco CAMA ou ISDN.

4.  O PSTN identifica a chamada como uma chamada de emergência e a encaminha para um roteador E9-1-1 seletivo na rede. O roteador E9-1-1 seletivo pesquisa o número do chamador no banco de dados ALI para obter o local geográfico. O roteador E9-1-1 seletivo envia a chamada para o PSAP mais apropriado com base nas informações de local que foram recuperadas do banco de dados ALI.

5.  Se você tiver configurado a política de local para notificações, um ou mais funcionários de segurança da sua organização receberão uma mensagem instantânea de notificação de emergência especial do Lync. Essa mensagem sempre aparecerá na(s) tela(s) dos funcionários de segurança e contém o nome, o número de telefone, a hora e o local do chamador, permitindo que o pessoal de segurança atenda rapidamente o chamador de emergência usando uma mensagem instantânea ou voz.

6.  Se a chamada for interrompida prematuramente, o PSAP usará o ELIN para contatar diretamente o chamador. O gateway ELIN trocará o ELIN pelo DID do chamador.

