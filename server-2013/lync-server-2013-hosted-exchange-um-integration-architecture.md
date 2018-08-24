---
title: 'Lync Server 2013: Arquitetura de integração do UM do Exchange hospedado'
TOCTitle: Arquitetura de integração do UM do Exchange hospedado
ms:assetid: 0094d5dc-1836-441c-b6e2-f88e35203a8d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398067(v=OCS.15)
ms:contentKeyID: 49305664
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Arquitetura de integração do UM do Exchange hospedado no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-25_

O aplicativo ExUM Routing do Lync Server 2013 dá suporte à integração com uma implantação do Unificação de Mensagens (UM) do Exchange local, com o UM do Exchange hospedado por um provedor de serviços, ou com uma combinação dos dois. O diagrama abaixo mostra todas as três possibilidades.

**Integração com implantação de UM do Exchange local e dois provedores Exchange hospedados**

![Implantação UM do Lync Server Exchange local](images/Gg398821.d6498eb9-87ee-40f3-8ecd-852f91546590(OCS.15).jpg "Implantação UM do Lync Server Exchange local")

Os modos a seguir são suportados:

  - **Implantação local :** Lync Server 2013 e UM do Exchange são ambos implantados em servidores locais dentro de sua empresa.

  - **Implantação entre instalações :** Lync Server 2013 é implantado em servidos locais dentro de sua empresa e UM do Exchange é hospedado nas instalações de um provedor de serviço on-line, como um data center Microsoft Exchange Online.

  - **Implantação mista :** Sua implantação Lync Server 2013 tem algumas caixas de entradas de usuários hospedadas em servidores Exchange locais dentro de sua empresa e algumas hospedadas em um data center de serviço Exchange hospedado.
    
    > [!NOTE]  
    > A implantação mista pode ser usada como uma solução de transição durante a avaliação e migração em fases de usuários ao UM do Exchange hospedado, ou uma solução permanente caso você opte por manter alguns serviços de UM do Exchange dos usuários no local, após transferir outros.

## Espaço de Endereçamento SIP Compartilhado

Para integrar Lync Server 2013 à uma implantação UM do Exchange local, você concede permissão ao Lync Server 2013 para ler objetos UM do Exchange de Serviços de Domínio Active Directory. Esta abordagem, no entanto, não funciona para a integração com UM do Exchange hospedado pois Lync Server 2013 e o UM do Exchange estão instalados em florestas separadas sem confiança entre elas.

Para integrar Lync Server 2013 ao UM do Exchange hospedado, você deve configurar um *espaço de endereçamento SIP compartilhado* . Nesta configuração, o mesmo espaço de endereçamento SIP compartilhado está disponível para ambos Lync Server 2013 e o provedor de serviço UM do Exchange hospedado.

> [!NOTE]  
> O uso de espaço de endereço SIP compartilhado é similar à abordagem utilizada em um ambiente Lync Server 2013 entre instalações, no qual alguns usuários estão hospedados na implantação local e outros na implantação hospedada (como Lync Online). O domínio SIP está dividido entre eles. Quando você integrar Lync Server 2013 com UM do Exchange hospedado, assegure-se de incluir um provedor de serviço UM do Exchange no espaço de endereço SIP compartilhado.

Para configurar o espaço de endereço SIP compartilhado para integrar-se com um provedor de serviço UM do Exchange, você deve configurar seu Servidor de Borda como exemplificado a seguir:

1.  Configure o Servidor de Borda para federação, executando o cmdlet **Set-CsAccessEdgeConfiguration** para definir os seguintes parâmetros:
    
      - **UseDnsSrvRouting** especifica se os Servidores de Borda dependerão dos registros DNS SRV ao enviar e receber solicitações de federação.
    
      - **AllowFederatedUsers** especifica se os usuários internos têm permissão para se comunicar com usuários de domínios federados. Essa propriedade também determina se os usuários internos podem se comunicar com usuários em uma situação de divisão de domínios.
    
      - **EnablePartnerDiscovery** especifica se Lync Server 2013 utilizará registros DNS para tentar descobrir domínios de parceiros que não estão listados na lista de domínios permitidos do Active Directory. Se Falso, Lync Server 2013 irá federar apenas com domínios que são encontrados na lista de domínios permitidos. Esse parâmetro é obrigatório caso se esteja utilizando o roteamento de serviço de DNS. Na maioria das implantações, o valor é definido como falso para evitar a abertura de federação para todos os parceiros.

2.  Replique o Repositório de Gerenciamento Central para o Servidor de Borda e verifique a replicação. Para maiores detalhes, consulte [Exportar sua topologia do Lync Server 2013 e copiá-la na mídia externa para instalação de borda](lync-server-2013-export-your-topology-and-copy-it-to-external-media-for-edge-installation.md) na documentação de Implantação.

3.  Configure um *provedor de hospedagem* no Servidor de Borda, executando o cmdlet **New-CsHostingProvider** para configurar os seguintes parâmetros:
    
      - **Identidade** especifica um identificador de valor de string único para o provedor de hospedagem que você está criando, por exemplo, **UM do Exchange Hospedado** .
    
      - **Ativado** indica se a conexão de rede entre o seu domínio e o provedor de hospedagem está ativa. Deve ser **Verdadeiro** .
    
      - **EnabledSharedAddressSpace**indica se o provedor de hospedagem será usado no cenário de espaço de endereçamento SIP compartilhado. Deve ser **Verdadeiro** .
    
      - **HostsOCSUsers** indica se o provedor de hospedagem é usado para hospedar contas Lync Server 2013. Deve ser **Falso** .
    
      - **ProxyFQDN** especifica o FQDN (nome de domínio totalmente qualificado) para o servidor proxy usado pelo provedor de hospedagem, por exemplo, **proxyserver.fabrikam.com** . Entre em contato com seu provedor de hospedagem por esta informação. Este valor não pode ser modificado. Se o provedor de hospedagem mudar seu servidor proxy, você precisará excluir e então recriar o registro para aquele provedor.
    
      - **IsLocal** indica se o servidor proxy usado pelo provedor de hospedagem está contido dentro da topologia Lync Server 2013. Deve ser **Falso**.

