---
title: 'Lync Server 2013: Componentes VoIP do Servidor Front-End'
TOCTitle: Componentes VoIP do Servidor Front-End
ms:assetid: 310e81a7-da45-47d4-95d0-92837e386502
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425812(v=OCS.15)
ms:contentKeyID: 49306290
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Componentes VoIP do Servidor Front-End para Lync Server 2013

 

_**Tópico modificado em:** 2012-10-01_

Os componentes VoIP localizados no Servidores Front-End são os seguintes:

  - Serviço de Conversão

  - Componente de Roteamento de Entrada

  - Componente de Roteamento de Saída

  - Componente de Roteamento da UM do Exchange

  - Componente de roteamento entre clusters

  - [Componente do Servidor de Mediação no Lync Server 2013](lync-server-2013-mediation-server-component.md)

## Serviço de Conversão

O Serviço de Conversão é o componente de servidor responsável pela conversão de um número discado no formato E.164 ou em outro formato, de acordo com as regras de normalização definidas pelo administrador. Esse serviço pode fazer a conversão para formatos que não sejam o E.164, caso a sua organização use um sistema de numeração particular ou um gateway ou PBX que não dê suporte a E.164.

## Componente de Roteamento de Entrada

O componente de Roteamento de Entrada lida com chamadas em entrada de acordo com as preferências especificadas pelos usuários em seus clientes do Enterprise Voice. Também facilita a delegação de chamada e chamada simultânea, se configurada pelo usuário. Por exemplo, os usuários especificam se as chamadas não atendidas são encaminhadas ou simplesmente conectadas para notificação. Se o encaminhamento de chamada está habilitado, os usuários podem especificar se as chamadas não respondidas devem ser encaminhadas para outro número ou para um servidor do UM do Exchange que foi configurado para oferecer resposta de chamada. O componente de Roteamento de Entrada é instalado por padrão em todos os Servidor Standard Edition e Servidores Front-End.

## Componente de Roteamento de Saída

O componente de Roteamento de Saída direciona as chamadas para destinos do PBX ou PSTN. Aplica regras de autorização de chamada, conforme definido pela política de voz do usuário, para ligadores e determina o melhor gateway PSTN para roteamento de cada chamada. O componente de Roteamento de Saída é instalado por padrão em todos os Servidor Standard Edition e Servidores Front-End.

A lógica de roteamento usada pelo Componente de Roteamento de Saída é, em grande parte, configurada pelos administradores de rede e de telefonia, de acordo com os requisitos das organizações.

## Componente de Roteamento da UM do Exchange

O componente de roteamento do UM do Exchange lida com o roteamento entre o Lync Server e servidores executando o Unificação de Mensagens (UM) do Exchange, para integrar o Lync Server com os recursos do Unified Messaging.

O componente de roteamento do UM do Exchange também trata o re-roteamento de caixa postal sobre o PSTN se os servidores do UM do Exchange não estão disponíveis. Se você possui usuários do Enterprise Voice em sites locais que não possuem um link WAN resiliente para o local central, o Aparelho de Filial Persistente implantado no site local oferece a sobrevivência da caixa postal para usuários de lote durante uma interrupção WAN. Quando o link WAN não está disponível, o Aparelho de Filial Persistente faz o seguinte:

  - faz um novo roteamento de chamadas não respondidas sobre o PSTN para o servidor de Unificação de Mensagens do Exchange no site central

  - fornece ao usuário a capacidade de recuperar mensagens de caixa postal sobre o PSTN

  - coloca em fila notificações de chamada perdida e as carrega no servidor de UM do Exchange quando o link de WAN for restaurado.

Para habilitar o re-roteamento da caixa postal, recomendamos que seu administrador do Exchange configure o Atendedor Automático do UM do Exchange (AA) para aceitar apenas mensagens.

Para obter detalhes sobre esses recursos, consulte [Planejamento para integração de Unificação de Mensagens do Exchange no Lync Server 2013](lync-server-2013-planning-for-exchange-unified-messaging-integration.md) e [Planejamento para resiliência do Enterprise Voice no Lync Server 2013](lync-server-2013-planning-for-enterprise-voice-resiliency.md), respectivamente.

## Componente de roteamento entre clusters

O componente de roteamento entre clusters é responsável por rotear chamadas ao pool de registradores principal do chamador. Se essa opção não estiver disponível, o componente roteará a chamada para o pool de registradores de backup de quem recebe a chamada. Se os pools de registradores principal e de backup de quem recebe a chamada não puderem ser acessados pela rede IP, o componente de roteamento entre clusters roteará novamente a chamada sobre o PSTN para o número de telefone do usuário.

## Outros componentes de Servidor Front-End necessários ao VoIP

Outros componentes residindo no Servidor Front-End ou Diretor que oferece suporte fundamental para VoIP, mas não são componentes VoIP, incluem o seguinte:

  - **Serviços do Usuário.** Realiza a pesquisa de número inverso no telefone de destino para cada chamada de entrada e corresponde esse número ao URI SIP do usuário de destino. Usando esta informação o componente de Roteamento de Entrada distribui a chamada para os pontos de extremidade SIP registrados do usuário. Os Serviços do Usuário é um componente principal em todos os Servidores Front-End e Diretores.

  - **Replicador do Usuário.** Extrai números telefônicos do Serviços de Domínio Active Directory e grava-os em tabelas no banco de dados RTC, onde eles estão disponíveis para os Serviços do Usuário e Servidor do Catálogo de Endereços. O Replicador do Usuário é um componente principal em todos os Servidores Front-End.

  - **Servidor do Catálogo de Endereço.** Oferece informações da lista de endereço global do Serviços de Domínio Active Directory para clientes do Lync Server. Também recupera a informação de contato e do usuário do banco de dados RTC, grava a informação nos arquivos do Catálogo de Endereços e armazena os arquivos em uma pasta compartilhada onde eles são baixados por clientes do Lync. O Servidor do Catálogo de Endereços grava a informação no banco de dados do RTCAb, que é usado pelo Serviço de Consulta à Web do Catálogo de Endereços para responder as consultas de pesquisa do usuário do Microsoft Lync 2010 Mobile. Opcionalmente, normaliza os números de telefone do usuário empresarial que são gravados no banco de dados RTC para fins de provisionamento dos contatos do usuário no Lync. O serviço do Catálogo de Endereços é instalado por padrão em todos os Servidores Front-End. O Serviço de Consulta à Web do Catálogo de Endereços é instalado por padrão com os serviços da Web em cada Servidores Front-End.

