---
title: 'Lync Server 2013: Projetando o tronco SIP para E9-1-1'
TOCTitle: Projetando o tronco SIP para E9-1-1
ms:assetid: 4f93b974-b460-45c7-a4a8-6f38e34840f5
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398323(v=OCS.15)
ms:contentKeyID: 49306684
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Projetando o tronco SIP para E9-1-1 no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server usa troncos SIP para conectar uma chamada de emergência ao provedor de serviços E9-1-1. Você pode configurar os troncos SIP do serviço de emergência para E9-1-1 em um local central, em vários locais centrais ou em cada filial. No entanto, se o link da WAN entre o local do chamador e o local que hospeda o tronco SIP do serviço de emergência não estiver disponível, uma chamada colocada por um usuário no site desconectado precisará de um registro de uso de telefone especial na política de voz do usuário que roteará a chamada ao ECRC por meio do gateway da PSTN (Rede Telefônica Pública Comutada) local. O mesmo é verdadeiro se os limites de chamadas simultâneas do serviço de controle de admissão chamada estão em vigor.


> [!NOTE]  
> Existem basicamente duas maneiras de implementar um tronco SIP em um ambiente do Lync Server:<ul><li><p>Use Servidor de Mediação de hospedagem múltipla que use as interfaces roteadas publicamente direcionadas para o exterior para se comunicar com o provedor do tronco SIP.</p></li><li><p>Use um SBC (Controlador de Borda de Sessão) no local para fornecer um ponto de demarcação seguro entre o Servidor de Mediação e os serviços do provedor de tronco SIP.</p></li></ul>
> Se você escolher o último método, certifique-se de que a marca e o modelo do SBC escolhidos foram certificados e oferecem suporte à transmissão de dados de localização PIDF-LO (objeto Local de formato de dados de informação de presença) como parte de seu SIP INVITE. Caso contrário, as chamadas chegarão ao provedor de serviços de emergência retirado das suas informações de localização. Para obter detalhes sobre SBCs certificados, consulte &quot;Infraestrutura qualificada para Microsoft Lync&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=248425">http://go.microsoft.com/fwlink/p/?LinkId=248425</a>.<br />Os provedores de serviços E9-1-1 fornecem acesso a um par de SBCs para redundância. É necessário tomar várias decisões sobre a configuração de topologia e roteamento de chamada do Servidor de Mediação. Você tratará os SBCs como pares iguais e utilizará o roteamento em rodízio para chamadas entre eles ou designará um SBC como primário e outro secundário?


Para obter detalhes sobre como implantar um tronco SIP no Lync Server, consulte [Como implementar tronco SIP no Lync Server 2013?](lync-server-2013-how-do-i-implement-sip-trunking.md). As seguintes perguntas ajudaram você a implantar troncos SIP para E9-1-1.

  - **Você deve implantar o tronco SIP em uma conexão de concessão dedicada ou uma conexão compartilhada com a Internet?**  
    É importante que as chamadas de emergência sejam sempre conectadas. Uma linha dedicada fornece uma conexão que não será garantida por outro tráfego na rede e permite que você implemente a QoS (Qualidade de Serviço). Lembre-se de que, se você estiver se conectando a provedores de serviços de emergência por meio da Internet pública, será preciso garantir a confidencialidade das chamadas de emergência, a criptografia IPSec será necessária.

<!-- end list -->

  - **Sua implantação de E9-1-1 foi projetada ser tolerante a desastres?**  
    Como esta é uma solução de emergência, a resiliência é importante. Implante a Servidor de Mediação primária e secundária e os troncos SIP em locais tolerantes a desastres. É uma boa ideia implantar a Servidor de Mediação primária mais próximo aos usuários aceitos e rotear as chamadas de failover por meio da Servidor de Mediação secundário (localizada em um local geográfico diferente).

<!-- end list -->

  - **Você deve implantar um tronco SIP separado para cada filial?**  
    O Lync Server fornece diversas estratégias para manipular a resiliência de Voz em filiais incluindo: ter redes de dados resistentes, implantar um tronco SIP em cada filial ou enviar por push chamadas para o gateway local durante interrupções do serviço. Para obter detalhes, consulte [Tronco SIP do site da filial no Lync Server 2013](lync-server-2013-branch-site-sip-trunking.md).

<!-- end list -->

  - **O CAC (serviço de controle de admissão de chamada) está habilitado?**  
    O Lync Server não manipula as chamadas de emergência de forma diferente de uma chamada comum. Por essa razão, o gerenciamento de largura de banda ou o CAC (serviço de controle de admissão de chamada) pode ter um impacto negativo em uma configuração de E9-1-1. As chamadas de emergência serão bloqueadas ou roteadas para o gateway PSTN local se um CAC estiver habilitado e for excedido o limite configurado em um link no qual as chamadas de emergência estão sendo roteadas. Como acima, tais chamadas não terão dados de localização e devem ser direcionadas manualmente para o ECRC.

