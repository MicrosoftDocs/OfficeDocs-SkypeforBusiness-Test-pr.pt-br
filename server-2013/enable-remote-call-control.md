---
title: Habilitar o controle de chamada remota
TOCTitle: Habilitar o controle de chamada remota
ms:assetid: 0b91d418-e6ed-4556-97af-e8523e01f249
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204664(v=OCS.15)
ms:contentKeyID: 49305844
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Habilitar o controle de chamada remota

 

_**Tópico modificado em:** 2012-10-02_

O controle de chamadas remotas possibilita que os usuários controlem os telefones de sua central privada de comutação telefônica (PBX) usando Lync Server 2013. Caso tenha implementado o controle de chamada remota em seu ambiente herdado e queira migrá-lo Lync Server 2013, é necessário realizar as seguintes tarefas:

1.  Instalar um gateway SIP/CSTA e configura-lo para comunicar-se com sua PBX. É necessparui realizar esta etapa quando ao impplantar seu pool piloto Lync Server 2013.

2.  Após unir sua topologia e migrar suas políticas e configurações, configure Lync Server 2013 para encaminhar as solicitaçõe CSTA aogateway SIP/CSTA. Esta etapa pe uma etapa manual que segue a migração automatizada. Para configurar o encaminhamento de solicitações CSTA, faço o seguinte:
    
      - Remova as entradas host herdadas (conhecidas como *entradas do servidor confiáveis* em Lync Server 2013). Caso esteja migrado usuários de seu ambiente herdado, certifique que tenha removido todas as entradas host existentes autorizadas que você criou para o gateway SIP/CSTA gateway antes de configurar novas entradas confiáveis da aplicação no Lync Server 2013 pool piloto. Para mais detalhes sobre como remover entradas host autorizadas herdadas, consulte [Remover uma entrada de host autorizada](remove-an-authorized-host-entry.md).
    
      - Configure uma rota estática para o controle de chamadas remotas. Você pode configurar uma rota estática para pool individuais que você queira que de suporte ao controle de chamadas remotas ou você pode configurar uma rota estática global, assim cada pool que não estiver configurado com a rota estática a nível de pool usa a rota estática globa. Para detalhes sobre como configurar a rota estática, consulte [Configurar uma rota estática para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-static-route-for-remote-call-control.md) in the Deployment documentation.
    
      - Configure uma entrada de aplicação confiável para ocontrol de chamadas remotas em cada pool para aqueles que você queira que suporte o controle de chamadas remotas. Para detalhes sobre como configurar entrada de aplicação confiável, consulte [Configurar uma entrada de aplicativo confiável para controle de chamada remota no Lync Server 2013](lync-server-2013-configure-a-trusted-application-entry-for-remote-call-control.md) na documentação de Implementação.

3.  Se você implementou um gateway SIP/CSTAque usa o Protocolo de Controle de Transmissão (TCP) para conectar ao Lync Server 2013,defina o endereço de IP do gateway no Construtor de Topologias. Para detalhes sobre como definir o endereço de IP, consulte [Definir um endereço SIP de gateway SIP/CSTA no Lync Server 2013](lync-server-2013-define-a-sip-csta-gateway-ip-address.md) na documentação de Implementação.

4.  Configure os usuários Lync 2013 para o controle de chamadas remotas habilitando o controle de chamadas remotas e designando um Identificador de Recurso Uniforme (URI) do servidor de linha e um URI de linha. Ao migrar os usuários de sua implementação herdada para Lync Server 2013, as configurações do controle de chamadas remotas são migradas juntamente com as configurações do ususário.

5.  Se você personalizou a regras na sua implementação herdada, é necessário realizar algumas terefas manuais após a migração automatizada das políticas e configuração esteja concluída para migrar as regras personalizadas. Caso não tenha personalizado as regras, o Catálogo de Endereços é migrado juntamente com sua topologia. Para mais detalhes sobre como migrar manualmente as regras, consulte [Migrar catálogo de endereços](migrate-address-book_1.md).

