---
title: 'Lync Server 2013: Configurando a Unificação de Mensagens no Microsoft Exchange Server para funcionar com o Lync Server'
TOCTitle: Configurando a Unificação de Mensagens no Microsoft Exchange Server para funcionar com o Lync Server 2013
ms:assetid: 058da9c4-23af-4ddb-9f63-70133a8aafc6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398106(v=OCS.15)
ms:contentKeyID: 49305734
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando a Unificação de Mensagens no Microsoft Exchange Server para funcionar com o Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

> [!IMPORTANT]  
> Se você quer usar a Unificação de Mensagens (UM) do Exchange para fornecer atendimento de chamadas, Outlook Voice Access ou serviços de atendedor automático para usuários do Enterprise Voice, leia as informações em <a href="lync-server-2013-planning-for-exchange-unified-messaging-integration.md">Planejamento para integração de Unificação de Mensagens do Exchange no Lync Server 2013</a> na documentação do Planejamento e siga as instruções desta seção.

Para configurar o Unificação de Mensagens (UM) do Exchange a fim de funcionar com o Enterprise Voice, será necessário executar as seguintes tarefas:

  - Configurar certificados no servidor que executa os serviços do Unificação de Mensagens (UM) do Exchange
    
    > [!NOTE]  
    > Adicionar todos os servidores de Acesso ao cliente e de Caixa postal a todos os planos de discagem UM SIP URI. Caso contrário, o roteamento de chamada de saída não funcionará conforme o esperado.

  - Criar um ou mais planos de discagem SIP URI da UM, juntamente com seus número de telefone de acesso do assinante, conforme necessário, e criar planos de discagem de Lync Server correspondentes

  - Usar o script do **exchucutil.ps1** para:
    
      - Criar gateways IP da UM.
    
      - Criar grupos de busca da UM.
    
      - Conceder ao Lync Server 2013 permissão para ler objetos Serviços de Domínio Active Directory da UM.

  - Criar um atendedor automático da UM.

  - Criar um objeto de acesso do assinante.

  - Criar um SIP URI para cada usuário e para os usuários associados usando um plano de discagem SIP URI da UM

## Requisitos e recomendações

Antes de iniciar, a documentação desta seção presume que as seguintes funções do Exchange 2013 tenham sido implementadas: Client Access e Mailbox. No Microsoft Exchange Server 2013, o UM do Exchange é executado como um serviço nesses servidores.

Para obter detalhes sobre a implantação do Exchange 2013, consulte a Exchange 2013 Biblioteca do TechNet em [http://go.microsoft.com/fwlink/p/?LinkId=266637](http://go.microsoft.com/fwlink/p/?linkid=266637)

Também observe o seguinte:

  - Se o UM do Exchange estiver instalado em várias florestas, as etapas de integração do Exchange devem ser realizadas para cada floresta da UM. Além disso, a floresta da UM deve estar configurada para confiar na floresta na qual o Lync Server 2013 está implantado, e essa floresta do Lync Server 2013 deve ser configurada para confiar em cada floreta da UM.

  - As etapas de integração são realizadas em ambas as funções do Exchange Server nas quais os serviços de Unificação de Mensagens estão em execução e no servidor que executa o Lync Server 2013, sendo que as primeiras devem ser realizadas antes das etapas de integração do Lync Server 2013.
    
    > [!NOTE]  
    > Para visualizar quais etapas de integração são realizadas, em quais servidores e por quais funções de administrador, consulte <a href="lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md">Processo de implantação para integração de Unificação de Mensagens local com Lync Server 2013</a>.

As ferramentas a seguir devem estar disponíveis em cada servidor que execute o UM do Exchange:

  - Shell de Gerenciamento do Exchange

  - O script **exchucutil.ps1**, o qual realiza as tarefas a seguir:
    
      - Cria um gateway IP da UM para cada Lync Server 2013.
    
      - Cria um grupo de busca para cada gateway, e o identificador piloto de cada grupo especifica o plano de discagem SIP URI da UM usado pelo Pool de Front-Ends ou pelo Servidor Standard Edition que está associado ao gateway.
    
      - Concede permissão ao Lync Server 2013 para ler objetos UM do Exchange no Serviços de Domínio Active Directory.

## Nesta seção

  - [Configurar certificados no servidor executando o Unified Messaging do Microsoft Exchange Server](lync-server-2013-configure-certificates-on-the-server-running-microsoft-exchange-server-unified-messaging.md)

  - [Configurar o Unified Messaging no Microsoft Exchange para Lync Server 2013](lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md)

