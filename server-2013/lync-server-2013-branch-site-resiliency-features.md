---
title: 'Lync Server 2013: Recursos de resiliência do site de filial'
TOCTitle: Recursos de resiliência do site de filial
ms:assetid: 8e3feda5-9a38-4e3c-b808-af29f19c5eb9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398715(v=OCS.15)
ms:contentKeyID: 49307412
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Recursos de resiliência do site de filial no Lync Server 2013

 

_**Tópico modificado em:** 2014-02-10_

Se você fornecer resiliência de site de filial, se a conexão WAN de um site de filial com um site central falhar ou se o site central estiver inacessível, os seguintes recursos de voz deverão continuar disponíveis:


  - Chamadas de rede de telefonia pública comutada (PSTN) de entrada e saída

  - Chamadas corporativas entre usuários em ambos, o mesmo site e entre dois sites diferentes

  - Manipulação básica de chamadas, incluindo espera, recuperação e transferência de chamadas

  - Mensagens instantâneas de dois participantes

  - Encaminhamento de chamadas, toque simultâneo de pontos de extremidade, delegação de chamadas e serviços de chamada de equipe, mas somente se o delegante e o delegado (por exemplo, um gerente e o administrador do gerente) ou todos os membros da equipe estiverem configurados no mesmo site

  - Registros de detalhes de chamadas (CDRs)

  - Conferência de discagem PSTN com Atendedor Automático de Conferência

  - Recursos de caixa postal, se forem configuradas definições de reroteamento de caixa postal (para detalhes, consulte [Requisitos de resiliência do site da filial para Lync Server 2013](lync-server-2013-branch-site-resiliency-requirements.md)).

  - Autenticação e autorização de usuário

Os recursos a seguir estarão disponíveis somente se sua solução de resiliência for uma implantação do Lync Server em escala completa no site de filial:

  - Conferências de IM, webconferências e conferências de A/V

  - Presença e roteamento baseado em Não Incomodar (DND), onde as chamadas não tocam em extensões com o DND ativado

  - Atualização de configurações de encaminhamento de chamadas

  - Aplicativo Grupo de Resposta e Aplicativo de Estacionamento de Chamada

  - Provisionamento de novos telefones e clientes, mas somente se o Serviços de Domínio Active Directory estiver presente no site de filial.

  - 9-1-1 Avançado (E9-1-1)
    
    Se o E9-1-1 estiver implantado e o tronco SIP no site central não estiver disponível porque o link WAN está offline, o Aparelho de Filial Persistente roteará chamadas E9-1-1 para o gateway da filial local. Para habilitar este recurso, as políticas de voz dos usuários do site de filial devem rotear chamadas para o gateway local, em caso da falha da WAN.

> [!NOTE]  
> O SBA (aparelho de filial persistente) não tem suporte no XMPP. Os usuários hospedados em configurações de SBA não poderão enviar mensagens instantâneas, nem visualizar a presença com contatos de XMPP.
