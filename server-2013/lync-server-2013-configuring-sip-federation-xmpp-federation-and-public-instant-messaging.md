---
title: 'Lync Server 2013: Configurando federação SIP, federação XMPP e sistema de mensagens instântaneas público'
TOCTitle: Configurando federação SIP, federação XMPP e sistema de mensagens instântaneas público
ms:assetid: a6d04f0b-5cb8-4084-a3a2-d501938971f9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205134(v=OCS.15)
ms:contentKeyID: 49307702
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configurando federação SIP, federação XMPP e sistema de mensagens instântaneas público no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Federação, conectividade de mensagem instantânea pública e protocolo XMPP (Extensible Messaging and Presence Protocol) definem uma classe diferente de usuários externos - os usuários federados. Os usuários de uma implantação federada do Lync Server ou implantação XMPP têm um conjunto de serviços limitados e são autenticados pela implantação externa. Usuários remotos são membros da sua implantação do Lync Server e têm acesso a todos os serviços oferecidos por sua implantação.

> [!NOTE]  
> A data de fim de vida de junho de 2014 para o AOL e o Yahoo! foi anunciada. Para detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.

A conectividade de mensagem instantânea pública é um tipo especial de federação que permite que um cliente Lync Server acesse parceiros configurados de mensagem instantânea pública usando o Lync 2013. Os parceiros atuais de conectividade de mensagem instantânea pública são:

   America Online

   Windows Live

   Yahoo\!

Uma configuração de conectividade de mensagem instantânea pública permite que os usuários do Lync acessem usuários de conectividade de mensagem instantânea pública através de:

  - IM e presença

  - Visibilidade de contatos de conectividade de mensagem instantânea pública no cliente Lync

  - Conversas entre duas pessoas com os contatos

  - Chamadas de áudio e vídeo com usuários do Windows Live

A federação do Lync Server define um acordo entre sua implantação do Lync Server e outras implantações do Office Communications Server 2007 R2 ou Lync Server. Uma configuração federada do Lync Server permite acesso dos usuários do Lync aos usuários federados através de:

  - IM e presença

  - Criação de contatos federados no cliente Lync

A federação XMPP define uma implantação externa baseada no protocolo XMPP (eXtensible Messaging and Presence Protocol). Uma configuração de XMPP permite o acesso dos usuários do Lync aos usuários de domínio XMPP através de:

  - IM e presença - apenas entre duas pessoas

  - Criação de contatos federados XMPP no cliente Lync

> [!IMPORTANT]  
> O recurso XMPP do Lync Server 2013 é testado pela Microsoft e ela oferece suporte para federação de mensagens instantâneas com o Google Talk. Para quaisquer outros sistemas XMPP, entre em contato com o fornecedor do mesmo para verificar se eles suportam federação com o Lync Server 2013, e para quaisquer recomendações de implantação ou solução de problemas.

## Federação externa de servidor de borda, conectividade de mensagem instantânea pública e processo de implantação de usuários XMPP


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Fase</th>
<th>Etapas</th>
<th>Permissões</th>
<th>Documentação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Determina as opções para adicionar à implantação de borda existente</p></td>
<td><p>Execute a Construtor de Topologias para editar as configurações do Servidor de Borda e criar e publica a topologia. Sua topologia de borda existente irá replicar as alterações do Repositório de Gerenciamento Central no Servidor de Borda.</p></td>
<td><p>Grupo de administradores de domínio e grupo RTCUniversalServerAdmins</p>
<div class="alert">
> [!NOTE]  
> Você pode editar uma topologia usando uma conta que é membro do grupo de usuários locais, mas publicar uma topologia exige uma conta que seja membro de um grupo de administradores de domínio e do grupo RTCUniversalServerAdmins
</div></td>
<td><p><a href="lync-server-2013-building-an-edge-and-director-topology.md">Criando uma topologia de borda e de diretor no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Preparar para instalação</p></td>
<td><ol><li><p>Garanta que os pré-requisitos do sistema sejam atendidos.</p></li><li><p>Configure registros DNS internos e externos para suportar conectividade de mensagens instantâneas públicas, federação Lync e federação XMPP</p></li><li><p>Configure portas e protocolos no firewall para suportar os tipos de federação que você está implantando</p></li><li><p>Obtenha e instale certificados públicos. O tempo necessário para obter certificados depende de qual autoridade de certificação (CA) emite o certificado. Esta etapa é opcional neste ponto da implantação. Se você não executar essa etapa nesse momento, será necessário fazê-lo durante a configuração do Servidor de Borda. O serviço de Servidor de Borda não pode ser iniciado até que o certificado seja obtido</p></li></ol>
<p></p></td>
<td><p>Conforme for apropriado para sua organização, pois essas funções são geralmente divididas entre vários grupos de trabalho</p></td>
<td><p><a href="lync-server-2013-planning-for-sip-xmpp-federation-and-public-instant-messaging.md">Planejamento para SIP, federação XMPP e mensagens instantâneas públicas no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Configure os Servidores de Borda para cenários de federação</p></td>
<td><ol><li><p>Transporte o arquivo de configuração de topologia exportado para cada Servidor de Borda ou permita que a replicação seja concluída</p></li><li><p>Execute novamente o Assistente de Implantação para instalar componentes de suporte para federação</p></li><li><p>Configura os Servidores de Borda</p></li><li><p>Solicite e instale certificados para cada Servidor de Borda</p></li><li><p>Reinicie os serviços dos Servidores de Borda</p></li></ol></td>
<td><p>Grupo Administradores</p></td>
<td><p><a href="lync-server-2013-setting-up-lync-federation.md">Configuração de federação do Lync no Lync Server 2013</a></p>
<p><a href="lync-server-2013-setting-up-public-instant-messaging-connectivity.md">Configurar conectividade de mensagens instantâneas públicas no Lync Server 2013</a></p>
<p><a href="lync-server-2013-setting-up-xmpp-federation.md">Configurando federação de XMPP no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configurar suporte para acesso de usuário externo.</p></td>
<td><ol><li><p>Use o acesso de usuários externos do Painel de Controle do Lync Server</p></li><li><p>Configure a Política de Acesso Externo para permitir comunicação com usuários federados ou usuários públicos</p></li><li><p>Configure domínios federados SIP para permitir ou bloquear domínios</p></li><li><p>Habilite provedores federados SIP para provedores de conectividade de mensagens instantâneas</p></li><li><p>Configure os parceiros federados XMPP por domínio XMPP</p></li></ol></td>
<td><p>Grupo RTCUniversalServerAdmins ou conta de usuário que é atribuído à função CSAdministrator</p></td>
<td><p><a href="lync-server-2013-configuring-support-for-external-user-access.md">Configurando suporte para acesso de usuário externo no Lync Server 2013</a></p>
<p><a href="lync-server-2013-configure-media-encryption-for-public-providers.md">Configurar criptografia de mídia para fornecedores públicos no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Verifique sua configuração do Servidor de Borda</p></td>
<td><p>Verifique a conectividade de servidor e replicação de dados de configuração de servidores internos</p></td>
<td><p>Para verificar a replicação, o grupo RTCUniversalServerAdmins ou conta do usuário que é atribuído à função CSAdministrator. Para verificação da conectividade do usuário, um usuário para cada tipo de usuário federado</p></td>
<td><p><a href="lync-server-2013-verifying-your-edge-deployment.md">Verificando a implantação de borda no Lync Server 2013</a></p>
<p><a href="lync-server-2013-example-xmpp-configuration-–-xmpp-federation-with-google-talk.md">Exemplo de configuração de XMPP no Lync Server 2013 – federação XMPP com Google Talk</a></p></td>
</tr>
</tbody>
</table>

