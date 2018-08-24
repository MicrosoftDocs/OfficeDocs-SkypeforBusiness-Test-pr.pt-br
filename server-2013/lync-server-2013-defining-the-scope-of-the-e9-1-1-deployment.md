---
title: 'Lync Server 2013: Definindo o escopo da implantação de E9-1-1'
TOCTitle: Definindo o escopo da implantação de E9-1-1
ms:assetid: 2c572dfd-e901-471d-b5a0-18bc8d1d5328
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425775(v=OCS.15)
ms:contentKeyID: 49306239
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Definindo o escopo da implantação de E9-1-1 no Lync Server 2013

 

_**Tópico modificado em:** 2012-06-06_

Antes de configurar o Microsoft Lync Server 2013 para E9-1-1, é necessário planejar sua implantação do E9-1-1. Algumas das questões a serem consideradas são:

  - **Qual é a política de sua organização e as obrigações locais com relação ao E9-1-1?**  
    Os requisitos legais de E9-1-1 para PBXs (chamados de Multi-line Telephone Systems, ou MLTS, no linguajar de E9-1-1) diferem de acordo com o estado. Consulte com sua equipe legal para entender as obrigações que podem ser aplicadas à sua implantação do Lync Server em suas geografias relevantes.

<!-- end list -->

  - **Quais áreas dentro de sua empresa precisam estar habilitadas para E9-1-1?**  
    É possível habilitar o E9-1-1 para toda a empresa ou para locais selecionados. Por exemplo, talvez você tenha requisitos variados de E9-1-1 para escritórios em estados diferentes ou queira excluir sites fora dos EUA.

<!-- end list -->

  - **Como você implantará o E9-1-1 em sites de filiais?**  
    A resiliência de voz é um conceito importante para compreender quando implantar o E9-1-1 no site local. Se você centralizou troncos SIP E-9-1-1 e uma interrupção WAN ocorre, os clientes conectando podem talvez não obter um local do Serviço de Informações de Local ou se conectar ao provedor de serviços de emergência. O Lync Server oferece várias estratégias para lidar com a resiliência de voz nos escritórios filiais, incluindo: ter redes de dados resilientes, implantar um tronco SIP em cada filial ou realizar chamadas de emergência para o gateway local durante interrupções. Para obter detalhes, consulte [Planejamento de resiliência de voz no site da filial no Lync Server 2013](lync-server-2013-planning-for-branch-site-voice-resiliency.md).

<!-- end list -->

  - **Você habilitará o E9-1-1 para usuários trabalhando fora da rede?**  
    A aquisição automática de local fica disponível somente para clientes localizados dentro da rede da organização, portanto, sua organização precisa decidir se suportará chamadas de E9-1-1 feitas de clientes Lync no local. Por exemplo, você habilitará usuários para fazer chamadas de emergência se eles estiverem trabalhando de cada ou no local de um cliente? Se um cliente estiver localizado fora da rede empresarial, ele poderá ser configurado para solicitar ao usuário um local. No entanto, como esses locais fornecidos pelo usuário não podem ser pré-validados com base no MSAG (Catálogo de Endereços Principal), o despachante do provedor de serviços de emergência necessitarão confirmar a validade do local verbalmente com o chamador antes de rotear a chamada para o PSAP (ponto de atendimento público seguro).
    
    > [!NOTE]  
    > Clientes Lync de usuários que se conectam à sua rede da organização utilizando o VPN podem escolher informações de endereço IP interno, mas como estes endereços não podem ser usados para identificar o local atual do usuário, é fundamental que as subredes VPN sejam excluídas do Serviço de Informações de Local.

<!-- end list -->

  - **Você deseja fornecer roteamento de chamada de emergência para sites fora dos EUA?**  
    Talvez você queira fornecer roteamento de emergência para áreas de sua empresa que não são atendidas por um provedor de serviços de emergência (por exemplo, locais internacionais). Para fazer isso, crie um novo site e atribua políticas de voz aos sites que se referem a um uso do PSTN que roteia a chamada pelo gateway PSTN local.

