---
title: 'Lync Server 2013: Llista de verificação de implantação para acesso de usuário externo'
TOCTitle: Llista de verificação de implantação para acesso de usuário externo
ms:assetid: 3f55f502-88a0-4315-8783-45a32a0b78ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425910(v=OCS.15)
ms:contentKeyID: 49306487
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Llista de verificação de implantação para acesso de usuário externo no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Antes de implantar a rede de perímetro e implementar o suporte para usuários externos, você já deve ter implantado os servidores internos do Microsoft Lync Server 2013, incluindo um Pool de Front-Ends ou um Servidor Standard Edition. Se você planeja implantar o Diretores opcional em sua rede interna, também deve implantá-los antes de implantar Servidores de Borda. Para obter detalhes sobre o processo de implantação do Diretor, consulte [Cenários para o Diretor no Lync Server 2013](lync-server-2013-scenarios-for-the-director.md) na documentação de Planejamento.

Microsoft Lync Server 2013 inclui ferramentas para facilitar o planejamento e implantação de ambos os servidores internos e de Borda. Depois que a topologia estiver concluída, publique a definição de topologia resultante no seu ambiente de produção. Para tal, você precisa ser membro do grupo de **Administradores de domínio** e do grupo **RTCUniversalServerAdmins**.

  - **Ferramenta de planejamento**    Office Communications Server 2007 R2 incluída uma Ferramenta de Planejamento e uma Ferramenta de Planejamento de Borda que podem ser utilizadas para auxiliar a guiar no projeto de topologia. Em Lync Server 2010, essas duas ferramentas eram combinadas em um único Ferramenta de Planejamento que possui recursos e funcionalidades adicionais, como coleta de contagem de usuário planejada, requisitos de voz, tipos de acesso de usuário externo e opções de federação. Além disso, você pode planejar os parâmetros de rede da infraestrutura, como o endereço IP, tipos de balanceadores de carga e outras considerações de rede de perímetro.

  - **Construtor de topologia**    Lync Server 2013  Construtor de Topologias auxilia na definição da topologia e componentes. Construtor de Topologias é essencial para implantar servidores executando o Lync Server 2013. Construtor de Topologias publica os resultados em um Repositório de Gerenciamento Central que costuma configurar todos os servidores que executam Lync Server 2013 na sua organização. Você não pode instalar o Lync Server 2013 em servidores sem utilizar o Construtor de Topologias.

Se você projetou a topologia de borda durante o processo de planejamento, incluindo o Construtor de Topologias em execução para definir a topologia de borda, você pode utilizar tais resultados para iniciar a implantação do seu Servidor de Borda. Se você não terminou de construir a topologia de borda antes ou deseja alterar a informação especificada anteriormente, deverá finalizar a execução de Construtor de Topologias antes de prosseguir em outra etapa de implantação. Para detalhes sobre como construir a topologia, consulte [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).

Para detalhes sobre a Ferramenta de Planejamento e o Construtor de Topologia, consulte [Iniciando o processo de planejamento para Lync Server 2013](lync-server-2013-beginning-the-planning-process.md) na documentação de Planejamento.

A tabela a seguir apresenta uma visão geral do processo de implantação do Servidor de Borda. Para revisar as decisões que precisam ser tomadas antes de implantar o acesso de usuário externo, consulte [Cenários de acesso de usuário externo no Lync Server 2013](lync-server-2013-scenarios-for-external-user-access.md).


> [!WARNING]
> As informações na tabela a seguir enfatizam uma nova implementação. Se você tiver implantado Servidores de Borda em um ambiente Lync Server 2010, Office Communications Server 2007 R2 ou Office Communications Server 2007, consulte <A href="migration.md">Migração</A> para obter detalhes sobre como migrar para o Lync Server 2013. Não há suporte para a migração em nenhuma versão anterior à Office Communications Server 2007 R2, incluindo Office Communications Server 2007, Live Communications Server 2005 e Live Communications Server 2003.



Para aprimorar o desempenho e a segurança do Servidor de Borda e para facilitar a implantação, aplique as melhores práticas a seguir ao implantar sua rede de perímetro e Servidores de Borda:

  - Implante Servidores de Borda apenas após ter testado e verificado a operação do Lync Server 2013 dentro da organização.

  - Recomendamos que você implante os Servidores de Borda em um grupo de trabalho em vez de um domínio. Fazer isso simplifica a instalação e mantém os Serviços de Domínio de Diretório Ativo (AD DS) fora da rede de perímetro. Localizar os AD DS na rede de perímetro podem apresentar um risco à segurança significante.

  - Reunir um Servidor de Borda a um domínio localizado totalmente na rede de perímetro é suportado, mas não recomendado. Um servidor de Borda como parte de um domínio interno viola os limites de rede confiáveis, onde a Internet é o menos confiável, e o perímetro de rede é mais confiável que a Internet e a rede interna a mais confiável. Um servidor de Borda como membro do domínio é automaticamente uma parte da rede mais confiável, mas reside em uma rede menos confiável (o perímetro).

## Processo de implantação para Servidores de Borda


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
<td><p>Criar a topologia de borda apropriada e determinar os componentes apropriados.</p></td>
<td><ul>
<li><p>Execute o Construtor de Topologias para definir as configurações do Servidor de Borda e criar e publicar a topologia. Em seguida, use o Shell de Gerenciamento do Lync Server para exportar o arquivo de configuração de topologia.</p></li>
</ul>
<p></p></td>
<td><p>Grupo <strong>Admins. do Domínio</strong> e grupo <strong>RTCUniversalServerAdmins</strong> ou <strong>CsAdmins</strong></p>

> [!NOTE]  
> Você pode definir uma topologia usando uma conta que seja membro do grupo de usuários locais, mas a publicação de uma topologia requer uma conta que seja membro do grupo <strong>Admins. do Domínio</strong> e do grupo <strong>RTCUniversalServerAdmins</strong>.

</td>
<td><p><a href="lync-server-2013-building-an-edge-and-director-topology.md">Criando uma topologia de borda e de diretor no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="even">
<td><p>Preparar para instalação.</p></td>
<td><ol>
<li><p>Garanta que os pré-requisitos do sistema sejam atendidos.</p></li>
<li><p>Configure endereços IP (IPv4 e IPv6, se utilizados) para interfaces de rede internas e públicas em cada Servidor de Borda.</p></li>
<li><p>Configure registros DNS internos e externos (host A e AAAA para IPv4 e IPv6), incluindo a configuração do sufixo DNS no computador para ser implantado como um Servidor de Borda.</p></li>
<li><p>(Opcional) Crie e instale certificados públicos. O tempo necessário para obter certificados depende de qual CA (autoridade de certificação) emite o certificado. Se você não executar essa etapa neste ponto, você deverá fazê-lo durante a instalação do Servidor de Borda. O serviço de Servidor de Borda não pode ser iniciado enquanto os certificados não forem obtidos e instalados.</p></li>
<li><p>Forneça suporte para conectividade de IM pública, se a sua implantação for dar suporte a comunicações com usuários do Windows Live, AOL ou Yahoo!.</p>

> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que está sendo encerrado.</p></li>
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync para atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>

</li>
<li><p>Fornecimento de suporte para XMPP e suporte de federação para parceiros Office Communications Server 2007, Office Communications Server 2007 R2, Lync Server 2010caso a sua implantação utilize-os</p></li>
<li><p>Configure firewalls.</p></li>
</ol></td>
<td><p>Conforme apropriado para sua organização</p></td>
<td><p><a href="lync-server-2013-preparing-for-installation-of-servers-in-the-perimeter-network.md">Preparando para instalação de servidores na rede de perímetro para Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="odd">
<td><p>Configurar proxy reverso.</p></td>
<td><ul>
<li><p>Configure o proxy inverso (por exemplo, para o Microsoft Forefront Threat Management Gateway 2010 ou o Microsoft Internet Security and Acceleration (ISA) Server com Service Pack 1) na rede de perímetro, obtenha os certificados públicos necessários e configure as regras de publicação na Web no servidor proxy reverso.</p>
<p>Prepare o proxy reverso para serviços de Mobilidade se você tiver planejado para Mobilidade e está implantando serviços de Mobilidade no pool de Front End ou no servidor Standard Edition.</p></li>
</ul></td>
<td><p>Grupo <strong>Administrators</strong> ou administrador de Proxy Reversa</p></td>
<td><p></p>
<p><a href="lync-server-2013-setting-up-reverse-proxy-servers.md">Configurando servidores de proxy reverso para o Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="even">
<td><p>Configurar um Diretor (opcional).</p></td>
<td><ul>
<li><p>(Opcional) Instale e configure um ou mais Diretores na rede interna.</p></li>
</ul></td>
<td><p>Grupo <strong>Administradores</strong></p></td>
<td><p><a href="lync-server-2013-setting-up-the-director.md">Configurando o Diretor no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="odd">
<td><p>Configurar os Servidores de Borda.</p></td>
<td><ol>
<li><p>Instalar o software de pré-requisito</p></li>
<li><p>Transporte o arquivo de configuração de topologia exportado para cada Servidor de Borda.</p></li>
<li><p>Instale o software Lync Server 2013 em cada Servidor de Borda.</p></li>
<li><p>Configure os Servidores de Borda.</p></li>
<li><p>Solicite e instale certificados para cada Servidor de Borda.</p></li>
<li><p>Inicie os serviços dos Servidores de Borda.</p></li>
</ol></td>
<td><p>Grupo <strong>Administradores</strong></p></td>
<td><p><a href="lync-server-2013-setting-up-edge-servers.md">Configurando os servidores de borda no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="even">
<td><p>Configuração de implantação para acesso de usuário externo.</p></td>
<td><ol>
<li><p>Use o Painel de Controle do Lync Serverpara configurar o suporte para cada uma das seguintes (conforme aplicável):</p>
<ul>
<li><p>Retransmissão de mídia</p></li>
<li><p>Rota de federação</p></li>
<li><p>Acesso de usuários remotos</p></li>
<li><p>Federação com Lync Server, Office Communications Server e Live Communications Server</p></li>
<li><p>Conectividade a redes públicas de mensagens instantâneas</p></li>
<li><p>Federação XMPP</p></li>
<li><p>Usuários anônimos</p></li>
</ul></li>
<li><p>Configure contas de usuário para acesso de usuário remoto, federação, conectividade pública de IM, XMPP e suporte de usuário anônimo (conforme aplicável).</p></li>
</ol></td>
<td><p>Grupo <strong>RTCUniversalServerAdmins</strong> ou conta de usuário que é atribuído à função <strong>CSAdministrator</strong></p>
<p></p></td>
<td><p><a href="lync-server-2013-configuring-support-for-external-user-access.md">Configurando suporte para acesso de usuário externo no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="odd">
<td><p>Verificar sua configuração do Servidor de Borda.</p></td>
<td><ol>
<li><p>Verifique a conectividade de servidor e replicação de dados de configuração de servidores internos.</p></li>
<li><p>Verifique se os usuários externos podem se conectar, incluindo usuários remotos, usuários em domínios federados, usuários públicos de mensagens instantâneas e usuários anônimos, conforme apropriado para sua implantação.</p></li>
<li><p>Verifique a configuração e comunicação utilizando o Lync Server Remote Connectivity Analyzer <a href="https://www.testocsconnectivity.com" class="uri">https://www.testocsconnectivity.com</a></p></li>
<li><p>Solução de problemas de dificuldades de configuração e comunicação</p></li>
</ol></td>
<td><p>Para verificação de replicação, o grupo <strong>RTCUniversalServerAdmins</strong> ou a conta de usuário que é atribuída à função <strong>CSAdministrator</strong></p>
<p>Para a verificação de conectividade de usuário, um usuário para cada tipo de acesso de usuário externo que você dê suporte.</p>
<p>Usuários remotos</p></td>
<td><p><a href="lync-server-2013-verifying-your-edge-deployment.md">Verificando a implantação de borda no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
</tbody>
</table>

