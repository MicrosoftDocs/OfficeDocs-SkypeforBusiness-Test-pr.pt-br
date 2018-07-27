---
title: Visão geral de conferência discada no Lync Server 2013
TOCTitle: Visão geral de conferência discada no Lync Server 2013
ms:assetid: 6e581cef-960a-4730-8b22-91b2129d34e3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398524(v=OCS.15)
ms:contentKeyID: 49307048
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral de conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-30_

Se sua organização tem usuários que precisam participar de conferências locais do Lync Server 2013 quando estão fora do escritório ou quando não têm acesso a um computador, você pode implantar a conferência discada para que eles possam participar da conferência usando um telefone PSTN.

A conferência de discagem é um recurso opcional que você pode configurar ao implantar a conferência do Lync Server 2013. Embora a conferência de discagem use alguns dos mesmo componentes do Lync Server 2013 utilizados pelo Enterprise Voice, você pode implantar a conferência de discagem mesmo sem implantar o Enterprise Voice.

> [!NOTE]  
> Se você implantar a conferência de discagem, será necessário implantá-lo em cada pool onde você implantar a conferência do Lync Server 2013. Não é necessário atribuir números de acesso em cada pool, mas você deve implantar o recurso de discagem em todos os pools. Esse requisito oferece suporte ao recurso de nome gravado quando um usuário chama um número de acesso de um pool para unir-se a uma conferência de Lync Server 2013 em um pool diferente.

As conferências devem ser habilitadas para o acesso de discagem na poítica da reunião. Por padrão, as conferências que estão ativadas para o acesso de discagem incluem as seguintes informações na solicitação de conferência:

  - Uma ID numérica de conferência que identifica a conferência.

  - Um ou mais números de acesso PSTN.

  - Um link para uma Página Configurações de Conferência Discada, que contém uma lista completa dos números de acesso com os seus idiomas associados; um lugar para criar, redefinir ou desbloquear os números de identificação pessoal (PINs); e outras informações, como controles de multifrequência de tom dual (DTMF).

A conferência de discagem suporta aos usuários corporativos e anônimos. Os usuários corporativos possuem credenciais de Serviços de Domínio Active Directory e contas do Lync Server 2013 em sua organização. Os usuários anônimos não têm credenciais da empresa dentro de sua organização. No contexto de conferência de discagem, um usuário em uma organização de um parceiro federado que usa o PSTN para se conectar a uma conferência é tratado como usuário anônimo. Diferentemente de em outros contextos, para a conferência discagem os usuários federados não são autenticados.

Os usuários corporativos ou líderes de conferência que ingressam em uma conferência estão habilitados para o acesso de discagem discam um dos números de acesso de conferência e, em seguida, são solicitados a inserir o ID de conferência. Se um líder ainda não ingressou na reunião, os usuários podem digitar a sua extensão de comunicações unificadas (UC) (ou número de telefone completo) e PIN ou aguardar para ser admitidos pelo líder. Os organizadores de reuniões podem ingressar na reunião como líderes apenas digitando o seu PIN. O Servidor Front-End usa a combinação do número completo ou extensão de telefone e o PIN, para mapear exclusivamente os usuários corporativos para as credenciais do Active Directory. Como resultado, os usuários corporativos são autenticados e identificados pelo nome da conferência. Os usuários corporativos também podem assumir um papel de conferência predefinido pelo organizador.

> [!NOTE]  
> Os usuários corporativos que discam de um telefone IP do escritório, de Lync Server 2013 ou de Lync 2010 Attendant, não têm os seus número de telefone solicitados porque eles já estão autenticados.

Os usuários anônimos que desejem ingressar em uma conferência de discagem discam um dos números de acesso de conferência e, em seguida, são solicitado a inserir o ID de conferência. Os usuários anônimos não autenticados também têm que registrar o seu nome. O nome gravado identifica os usuários não autenticados na conferência. Os usuários anônimos não são admitidos na conferência até que pelo menos um líder ou usuário autenticado ingresse e não é possível atribuir uma função predefinida.

> [!NOTE]  
> Os usuários corporativos que optam por não inserir o número de telefone e o PIN não são autenticados. Eles serão solicitados a registrar seu nome e são tratados como usuários anônimos na conferência.

No momento do agendamento o organizador da reunião pode optar por restringir o acesso à reunião, fazendo reunião fechada ou bloqueada. Nesse caso, é solicitado que os usuários de discagem façam a autenticação. Se os usuários de discagem falham ou optam por não autenticar, são transferidos para o lobby, onde eles aguardam até que um líder os aceita ou rejeita, ou o tempo limite é alcançado e eles são desconectados. Os usuários de discagem ouvem música se estão aguardando para ser admitidos na conferência. Depois que eles são admitidos em uma conferência, os usuários de discagem podem participar na parte de áudio da conferência e exercer comandos de multifrequência de tom dual (DTMF) usando o teclado do telefone. Os líderes da discagem podem exercer os comandos DTMF para habilitar ou desabilitar a capacidade dos participantes para ativar ou desativar o mudo, bloquear ou desbloquear a conferência, admitir pessoas do lobby e ativar ou desativar a entrada e saída de comunicados. Os líderes também podem usar um comando DTMF admitir a todos do lobby, o que altera as permissões da reunião para permitir qualquer pessoa que se una posteriormente. Todos os participantes de discagem podem exercer os comandos DTMF para ouvir a ajuda, a lista de conferência e ativar o mudo.

Os participantes de discagem (se eles discam ou não do PSTN) ouvem comunicados pessoais durante a conferência, como, por exemplo, se tiveram o mudo ativado ou desativado, se a reunião está sendo gravada ou alguém está aguardando no lobby.

> [!NOTE]  
> Os participantes que ingressam na conferência clicando em um link, em vez de discando, não ouvem os comunicados pessoais.
