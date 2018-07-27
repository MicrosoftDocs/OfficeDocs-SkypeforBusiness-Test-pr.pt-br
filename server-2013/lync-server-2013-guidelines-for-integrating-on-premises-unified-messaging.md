---
title: 'Lync Server 2013: Orientações para integração de Unificação de Mensagens local e Lync Server'
TOCTitle: Orientações para integração de Unificação de Mensagens local e Lync Server
ms:assetid: 829ac017-6907-40f9-be22-787a28eae0ac
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398656(v=OCS.15)
ms:contentKeyID: 49307303
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Orientações para integração de Unificação de Mensagens local e Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

As diretrizes e práticas recomendadas abaixo devem ser levadas em consideração ao implantar o Enterprise Voice:

> [!IMPORTANT]  
> Unificação de Mensagens (UM) do Exchange suporta IPv6 somente se você estiver usando UCMA 4.

  - Implantar um servidor Standard Edition do Lync Server 2013 ou um Pool de Front-Ends. Para obter detalhes sobre a instalação, consulte [Implantando o Lync Server 2013](lync-server-2013-deploying-lync-server.md) na documentação de implantação.

  - Trabalhar com os administradores do Exchange para confirmar que tarefas cada um executará para garantir uma integração tranqüila e bem-sucedida.

  - Implantar as funções de servidor Caixa de Correio do Exchange em cada floresta do Unificação de Mensagens (UM) do Exchange onde você deseja habilitar usuários para o UM do Exchange. Para obter detalhes sobre como instalar as funções de servidor do Exchange, consulte a documentação de Microsoft Exchange Server 2013.
    
    > [!IMPORTANT]  
    > Quando o Unificação de Mensagens (UM) do Exchange é instalado, é configurado para usar um certificado auto-assinado.<br />    O certificado auto-assinado, no entanto, não permite a confiança entre o Lync Server 2013 e o UM do Exchange, motivo pelo qual é necessário solicitar um certificado separado de uma autoridade de certificação no qual ambos os servidores confiem.

  - Se o Lync Server 2013 e o UM do Exchange são instalados em diferentes florestas, configure cada floresta do Exchange para confiar na floresta do Lync Server 2013 e a floresta do Lync Server 2013 para confiar em cada floresta do Exchange. Além disso, defina as configurações dos usuários do UM do Exchange em objetos de usuário na floresta do Lync Server 2013, normalmente usando um script ou uma ferramenta entre florestas, como o Identity Lifecycle Manager (ILM).

  - Se necessário, instale o Console de Gerenciamento do Exchange para gerenciar os servidores de Unificação de mensagens.

  - Obtenha números de telefone válidos para o Outlook Voice Access e o atendedor automático.

  - Se você estiver usando uma versão do UM do Exchange anterior ao Service Pack 1 (SP1) do Microsoft Exchange Server 2010, coordene nomes para os planos de discagem URI do SIP e os planos de discagem do Enterprise Voice do UM do Exchange.

## Implantando Servidores Redundantes UM do Exchange

> [!IMPORTANT]  
> Recomendamos que você implante um mínimo de dois servidores UM do Exchange para cada plano de discagem de URI do SIP do UM do Exchange que você configurar para sua organização. Além de oferecer capacidade expandida, a implantação de servidores redundantes fornece alta disponibilidade. No caso de uma falha de servidor UM do Exchange, o Lync Server 2013 pode ser configurado para fazer failover a outro servidor.

As seguintes configurações de exemplo fornecem resiliência de UM do Exchange.

**Exemplo 1: resiliência de UM do Exchange**

![Exchange UM Exemplo 1](images/Gg398656.3644b847-0847-4550-a989-e3fc51de5c4b(OCS.15).jpg "Exchange UM Exemplo 1")

No exemplo 1, os servidores UM 1 e 2 do Exchange são ativados no data center de Tukwila e os servidores UM 3 e 4 do Exchange são ativados no data center de Dublin. No caso de uma paralisação UM do Exchange em Tukwila, os registros DNS (Sistema de Nomes de Domínio) para os servidores de 1 e 2 devem ser configurados para apontar aos servidores 3 e 4, respectivamente. No caso de uma paralisação UM do Exchange em Dublin, os registros DNS para os servidores 3 e 4 devem ser configurados para apontar aos servidores 1 e 2 respectivamente.

> [!NOTE]  
> Para o exemplo 1, você deve também atribuir um dos seguintes certificados em cada servidor UM do Exchange:<ul>
> 
> <li><p>Use um certificado com um caractere curinga no nome de alternativo da entidade (SAN).</p></li>
> 
> 
> <li><p>Coloque o FQDN (nome de domínio totalmente qualificado) de cada um dos quatro servidores UM do Exchange no SAN.</p></li></ul>


**Exemplo 2: resiliência de UM do Exchange**

![Exchange UM Exemplo 2](images/Gg398656.15754273-306e-448d-b258-84bc2936a2e8(OCS.15).jpg "Exchange UM Exemplo 2")

No exemplo 2, sob condições operacionais comuns, os servidores UM 1 e 2 do Exchange são ativados no data center de Tukwila e os servidores UM 3 e 4 do Exchange são ativados no data center de Dublin. Os quatro servidores estão incluídos no plano de discagem de URI do SIP dos usuários de Tukwila; no entanto, os servidores 3 e 4 estão desativados. No caso de uma paralisação UM Exchange em Tukwila, por exemplo, os servidores UM 1 e 2 do Exchange devem ser desativados e os servidores UM 3 e 4 do Exchange devem ser habilitados para que o tráfego UM do Exchange de Tukwila seja roteado para os servidores em Dublin.

Para obter detalhes sobre como habilitar ou desabilitar a Unificação de Mensagens no Exchange 2013, consulte “Integrar a UM do Exchange 2013 com o Lync Server” em [http://go.microsoft.com/fwlink/p/?LinkId=265372](http://go.microsoft.com/fwlink/p/?linkid=265372).

Para detalhes sobre como habilitar ou desabilitar o Unified Messaging em Microsoft Exchange Server 2010, consulte:

  - "Habilitar a Unificação de Mensagens no Exchange 2010" em [http://go.microsoft.com/fwlink/p/?LinkId=204418](http://go.microsoft.com/fwlink/p/?linkid=204418).

  - "Desabilitar a Unificação de Mensagens no Exchange 2010" em [http://go.microsoft.com/fwlink/p/?LinkId=204416](http://go.microsoft.com/fwlink/p/?linkid=204416).

## Consulte Também

#### Conceitos

[Processo de implantação para integração de Unificação de Mensagens local com Lync Server 2013](lync-server-2013-deployment-process-for-integrating-on-premises-unified-messaging.md)

