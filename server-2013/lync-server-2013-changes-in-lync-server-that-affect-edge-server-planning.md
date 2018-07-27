---
title: 'Lync Server 2013: Alterações no Lync Server que afetam o planejamento do Servidor de Borda'
TOCTitle: Alterações no Lync Server 2013 que afetam o planejamento do Servidor de Borda
ms:assetid: 66305160-c9b8-4bc4-9f24-8ee8d9a294f7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204965(v=OCS.15)
ms:contentKeyID: 49306947
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Alterações no Lync Server 2013 que afetam o planejamento do Servidor de Borda

 

_**Tópico modificado em:** 2012-10-22_

O Lync Server 2013 apresenta novos recursos que ampliam os métodos de comunicação e os recursos para seus usuários. Além disso, o Lync Server 2013 introduz alterações a serviços existentes para integrar e estender melhor os serviços disponíveis em sua organização. A seguir, encontra-se um resumo das alterações que podem afetar seu planejamento e implantação dos serviços do Lync Server 2013  Servidor de Borda.

## Suporte ao endereçamento IPv6

O Lync Server 2013 oferece suporte ao endereçamento IPv6 para todos os serviços do Servidor de Borda. Se você tiver fornecido endereços IPv6 para as interfaces por meio da configuração do Windows Server, poderá usar endereços IPv6 em sua configuração do Servidor de Borda por meio da configuração de IP do Construtor de Topologias. Além disso, o protocolo XMPP oferece suporte ao IPv6. Não é necessária configuração adicional. Se o IPv6 estiver configurado na topologia, o XMPP o usará (quando necessário).

Um novo requisito para oferecer suporte ao IPv6 no Lync Server 2013 é criar registros DNS (Sistema de Nomes de Domínio) para registros que precisam ser descobertos e resolvidos como um endereço IPv6. O DNS IPv6 usa registros de host que são definidos como **AAAA** e chamados de “quad-A” (A quádruplo). Outros tipos de registro são consistentes com seus equivalentes em IPv4.

## Suporte à implantação do protocolo XMPP

O Servidor de Borda introduz um proxy XMPP totalmente integrado (implantado nos Servidores de Borda) e um gateway XMPP (implantado em seus Servidores Front-End). Você pode implantar a federação XMPP como um componente opcional. Ao adicionar e configurar o proxy e o gateway XMPP, você pode permitir que seus usuários do Microsoft Lync 2013 adicionem contatos de parceiros XMPP para IM (mensagens instantâneas) e presença.

> [!NOTE]  
> No momento, os serviços XMPP do Servidor de Borda só fornecem IM e presença entre clientes do Lync Server e contatos XMPP. Além disso, o XMPP é hospedado somente em um site.

> [!IMPORTANT]  
> O recurso XMPP do Lync Server 2013 é testado pela Microsoft e ela oferece suporte para federação de mensagens instantâneas com o Google Talk. Para quaisquer outros sistemas XMPP, entre em contato com o fornecedor do mesmo para verificar se eles suportam federação com o Lync Server 2013, e para quaisquer recomendações de implantação ou solução de problemas.

## Suporte a certificados de autenticação servidor a servidor e autenticação de áudio/vídeo

Um certificado é usado para gerar tokens que são emitidos para os clientes e outros consumidores do serviço de autenticação A/V e para autenticação servidor a servidor. O certificado de autenticação de áudio/vídeo é do tipo *AudioVideoAuthentication* e o certificado de autenticação servidor a servidor é do tipo *OAuthTokenIssuer* .

Para a autenticação de áudio/vídeo, tokens são usados para autenticar solicitações de alocação de porta e são armazenados em cache por até oito horas (a vida útil padrão do token). Em operação normal, esse é um método muito confiável de criar e distribuir material de autenticação para os consumidores de áudio e vídeo. No entanto, os certificados têm uma vida útil finita e expiram em uma data e hora predefinidas (com base na data de criação e nas políticas aplicadas na autoridade de certificação que criou o certificado - geralmente dois anos para esse tipo de certificado). Quando um certificado expira, todos os tokens criados por ele e armazenados em cache pelos consumidores se tornam inválidos. Uma tentativa de usar um token criado com um certificado expirado resultaria na falha de alocações do Media Relay, bem como na falha de qualquer sessão atual de áudio/vídeo. O cliente precisaria adquirir um novo token criado por um certificado válido para retomar a funcionalidade normal de áudio e vídeo.

A autenticação servidor a servidor é gerenciada por um certificado global que é solicitado e aplicado a todos os servidores da implantação. O certificado é responsável por autenticar servidores no Lync Server 2013, bem como realizar a autenticação no Exchange 2013 e no Microsoft SharePoint Server 2013. Para obter mais informações sobre como a autenticação servidor a servidor funciona, consulte [Gerenciando autenticação de servidor para servidor (Oauth) e inscrições de parceiros no Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md). Uma diferença muito importante entre o processo de autenticação de áudio/vídeo e do processo de autenticação servidor a servidor é a vida útil da autenticação ou dos tokens. Para a autenticação de áudio/vídeo, a autenticação expira após oito horas. A autenticação servidor a servidor tem uma vida útil de 24 horas. Leve isso em consideração ao planejar o uso de cada tipo de certificado.

Uma novidade no Lync Server 2013 é a capacidade de preparar certificados substitutos de autenticação de áudio/vídeo e autenticação servidor a servidor previamente à expiração do certificado atual. O novo certificado é então usado para gerar novos tokens ou novas solicitações de autenticação, mas mantém o certificado antigo para confirmar as sessões e autenticações atuais. Isso permite efetivamente impedir praticamente todas as falhas decorrentes da expiração de tokens ou certificados. Para obter detalhes sobre esse recurso e como configurá-lo, consulte [Adaptando Certificados AV e OAuth Usando no Lync Server 2013 -Roll in Set-CsCertificate](lync-server-2013-staging-av-and-oauth-certificates-using-roll-in-https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsCertificate).

## Menor dependência da afinidade com base em cookies

Em versões anteriores do Lync Server e do Office Communications Server, a afinidade com base em cookies era usada pelos serviços Web para garantir que o estado da sessão do cliente e dos serviços Web fosse mantido. Os serviços Web do Lync Server 2013 usam um mecanismo de afinidade interno que elimina em grande parte a necessidade da afinidade com base em cookies.


> [!WARNING]
> O cliente do Microsoft Lync 2010 Mobile ainda precisa usar a afinidade com base em cookies e ela precisará ser configurada até que todos os clientes sejam migrados para o futuro cliente do Microsoft Lync Mobile (a data do lançamento ainda não foi determinada).



Para obter detalhes sobre a afinidade com base em cookies no Lync Server 2013, consulte [Componentes obrigatórios para acesso de usuário externo no Lync Server 2013](lync-server-2013-components-required-for-external-user-access.md).

## Melhorias da Descoberta Automática

O recurso Descoberta Automática do Lync Server 2013 permite que os clientes localizem recursos adicionais disponibilizados para comunicação. A Descoberta Automática foi introduzida na atualização cumulativa do Lync Server 2010 de novembro de 2011 para mobilidade e Microsoft Lync 2010 Mobile. O recurso Descoberta Automática (também conhecido pelos nomes de registro DNS LyncDiscover e LyncDiscoverInternal) permite que os clientes localizem e usem serviços de mobilidade (para clientes do Microsoft Lync 2010 Mobile), o Microsoft Lync Web App e o Lync Web Scheduler, bem como comunicações com o Microsoft Exchange Server e o SharePoint Server. A Descoberta Automática é instalada como parte normal da instalação e da implantação de sua infraestrutura e seus servidores do Lync Server 2013. O Construtor de Topologias e o Assistente de Implantação do Lync Server eliminam a maioria das tarefas de configuração que eram necessárias na atualização cumulativa do Lync Server 2010 de novembro de 2011.

## Planejamento para clientes móveis

Introduzidos na atualização cumulativa do Lync Server 2010 de novembro de 2011, os serviços de mobilidade do Lync Server 2013 permitem que celulares que executam o Lync Mobile, dispositivos tablet que usam os sistemas Apple iOS, Android e Windows Phone com suporte ou dispositivos móveis Nokia realizem atividades como enviar e receber mensagens instantâneas ou exibir contatos e presença. Além disso, os dispositivos móveis oferecem suporte a alguns recursos do Enterprise Voice, como clicar para ingressar em uma conferência, Telefonar via Trabalho, acesso por único número, caixa postal e notificação de chamadas perdidas.

> [!NOTE]  
> Os serviços de mobilidade usam o proxy reverso e os serviços publicados implantados em seus Servidores Front-End. Nenhuma alteração é necessária nos Servidores de Borda. No mínimo, você precisa de SIP/TCP/5061 de saída do servidor que executa o Serviço de Borda de Acesso do Lync Server.

## A função Diretor é opcional

A função do servidor Diretor na topologia do Lync Server 2013 não mudou. Ela ainda hospeda os serviços Web, pré-autentica as solicitações de usuário de entrada e direciona usuários externos para seu pool primário. Ao alterar o Diretor de uma função recomendada para uma função opcional, a Microsoft não pretende diminuir o valor do Diretor. A intenção é reduzir o número de servidores e outros requisitos de hardware (por exemplo, balanceadores de carga de hardware para o Diretor) sem comprometer os recursos e a funcionalidade. Como os Servidores Front-End podem executar a mesma função que o Diretor sem impacto nos serviços fornecidos, você pode implantar Diretores se desejar. Você pode excluir o Diretor com a confiança de que os Servidores Front-End fornecerão os mesmos serviços no lugar de um Diretor.

