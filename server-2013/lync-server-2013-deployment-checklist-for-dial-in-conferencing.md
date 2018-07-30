---
title: 'Lync Server 2013: Lista de verificação de implantação para conferência discada'
TOCTitle: Lista de verificação de implantação para conferência discada
ms:assetid: 9c8d3ebe-0d70-4a61-9bd0-522286cddd9a
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412726(v=OCS.15)
ms:contentKeyID: 49307594
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação de implantação para conferência discada no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os componentes necessários para conferência discada são implantados quando a carga de trabalho de conferência é implantada. Antes de configurar a conferência discada, você precisa implantar o Enterprise Voice ou um Servidor de Mediação e um gateway PSTN (rede telefônica comutada pública).

Todas as etapas na tabela a seguir devem ser executadas antes que os usuários possam discar a partir do PSTN para entrar em uma conferência de áudio/vídeo.

> [!NOTE]  
> Se estiver migrando do Office Communications Server 2007 R2, você deve aplicar a atualização mais recente do ambiente Office Communications Server 2007 R2 antes de implantar a conferência discada.

### Processo de implantação da conferência discada

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
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Crie uma topologia que inclua a carga de trabalho das Conferências, incluindo um Servidor de Mediação e o gateway PSTN e implante o Pool de Front-Ends ou Servidor Standard Edition</strong></p></td>
<td><ol><li><p>Execute o Construtor de Topologias para configurar sua topologia. Enquanto a configuração da topologia é executada, selecione a opção de conferência discada.</p></li><li><p>Publique a topologia e implante o Pool de Front-Ends ou Servidor Standard Edition.</p></li><li><p>Se necessário, crie um Servidor de Mediação autônomo e o associe a um gateway PSTN.</p>
<div class="alert">
> [!NOTE]  
> Esta etapa é necessária somente se você não implantar o Enterprise Voice e não colocar o Servidor de Mediação com o Enterprise EditionServidor Front-End ou Servidor Standard Edition. Se o Enterprise Voice for implantado, instale e configure o Servidor de Mediação e gateways PSTN como parte da implantação do Enterprise Voice. Se o Servidor de Mediação for colocado, instale e configure o Servidor de Mediação como parte da implantação do Pool de Front-Ends ou Servidor Standard Edition.
</div></li></ol></td>
<td><p>Admins. do Domínio</p>
<p>RTCUniversalServerAdmins</p>
<p>Administrador</p></td>
<td><ul><li><p><a href="lync-server-2013-deploying-lync-server.md">Implantando o Lync Server 2013</a></p></li><li><p>Para criar um Pool do servidor de mediação autônomo: <a href="lync-server-2013-deploying-mediation-servers-and-defining-peers.md">Implantando Servidores de Mediação e definindo pares no Lync Server 2013</a></p></li></ul></td>
</tr>
<tr class="even">
<td><p><strong>Configure planos de discagem</strong></p></td>
<td><p>Um plano de discagem é um conjunto de regras de normalização de número de telefone que traduzem números discados de um local específico para um padrão de formato único (E.164), para fins de autorização do telefone e roteamento de chamadas. O mesmo número de telefone discado a partir de locais diferentes pode, com base nos respectivos planos de discagem, resolver para diferentes números E.164, conforme o que for mais adequado para cada local. Se você implantar Enterprise Voice, serão configurados planos de discagem como parte dessa implantação, e será necessário verificar se os planos de discagem também acomodam conferência discada. Se você não implantar Enterprise Voice, será necessário configurar planos de discagem para conferência discada.</p>
<p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para configurar planos de discagem da seguinte forma:</p><ol><li><p>Crie um ou mais planos de discagem para rotear números de telefone de acesso de discagem.</p></li><li><p>Atribua um plano de discagem padrão para cada pool. Defina a <strong>Região da conferência discada</strong> à localização geográfica à qual o plano de discagem se aplica. A região associa o plano de discagem aos números de acesso discado.</p></li></ol></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-dial-plans-for-dial-in-conferencing.md">Configurar planos de discagem para conferência discada no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Verifique se os planos de discagem possuem regiões atribuídas</strong></p></td>
<td><p>Execute os cmdlets <strong>Get-CsDialPlan</strong> e <strong>Set-CsDialPlan</strong> para verificar se todos os planos de discagem possuem uma região atribuída.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsVoiceAdministrator</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-make-sure-dial-plans-have-assigned-regions.md">Certifique-se de que os planos de discagem do Lync Server 2013 têm opções atribuídas</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Opcional) Verifique ou modifique os requisitos do número de identificação pessoal (PIN) do usuário.</strong></p></td>
<td><p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para visualizar ou modificar a <strong>Política de PIN</strong> de Conferência. Você pode especificar o comprimento mínimo do PIN, o número máximo de tentativas de logon, a expiração do PIN e se padrões comuns são permissíveis.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-verify-pin-policy-settings.md">(Opcional) Verificar configurações de política de PIN no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Configure a política de conferência para suportar conferências discadas.</strong></p></td>
<td><p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para configurar as definições da <strong>Política de Conferência</strong> . Especifique se:</p><ul>
> <li><p>A discagem de conferência PSTN está habilitada.</p></li>
> 
> <li><p>Usuários podem convidar participantes anônimos.</p></li>
> 
> 
> <li><p>Usuários não autenticados podem participar de uma conferência usando discagem de saída. Com a discagem de saída, o servidor de conferência faz uma chamada para o usuário e o usuário atende o telefone para entrar na conferência.</p></li></ul></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-conferencing-policy-for-dial-in.md">Configurar política de conferência para discagem no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Configure números de acesso de discagem</strong></p></td>
<td><p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para configurar números de acesso de discagem para os quais os usuários ligarão para entrar em uma conferência discada e especifique as regiões que associam o número de aceso aos planos de discagem apropriados. Os três primeiros números de acesso para a região especificada pelo plano de discagem do organizador são incluídos no convite da conferência. Todos os números de acesso estão disponíveis em Página Configurações de Conferência Discada.</p>
<div class="alert">
> [!NOTE]  
> Depois de criar números de acesso de discagem, você pode usar o cmdlet <strong>Set-CsDialInConferencingAccessNumber</strong> para modificar o nome de exibição dos objetos de contato do Active Directory, de forma que os usuários possam identificar mais facilmente o número de acesso correto.
</div></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-dial-in-conferencing-access-numbers.md">Configurar número de acesso da conferência discada no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>(Opcional) Verifique as configurações da conferência discada</strong></p></td>
<td><p>Use o cmdlet <strong>Get-CsDialinConferencingAccessNumber</strong> para pesquisar planos de discagem que tenham uma região de conferência discada que não seja usada por qualquer número de acesso e números de acesso que não possuam região atribuída.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p>
<p>CsViewOnlyAdministrator</p>
<p>CsHelpDesk</p></td>
<td><p><a href="lync-server-2013-optional-verify-dial-in-conferencing-settings.md">(Opcional) Verificar configurações de conferência discada no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Opcional) Modifique o mapeamento de teclas dos comandos DTMF</strong></p></td>
<td><p>Use o cmdlet <strong>Set-CsDialinConferencingDtmfConfiguration</strong> para modificar as teclas usadas para comandos DTMF que os participantes podem usar para controlar as configurações da conferência (como silenciar e ativar ou travar e destravar).</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-modify-key-mapping-for-dtmf-commands.md">(Opcional) Modificar mapeamento principal de comandos DTMF no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>(Opcional) Modifique o comportamento do anúncio de entrada e saída da conferência</strong></p></td>
<td><p>Use o cmdlet <strong>Set-CsDialinConferencingConfiguration</strong> para alterar como os anúncios funcionam quando participantes entram e saem das conferências.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-enable-and-disable-conference-join-and-leave-announcements.md">(Opcional) Habilitar e desabilitar comunicados de ingresso e saída de conferência no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Opcional) Verifique a conferência discada</strong></p></td>
<td><p>Use o cmdlet <strong>Test-CsDialInConferencing</strong> para testar se os números de acesso para o pool especificado estão funcionando corretamente.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsServerAdministrator</p>
<p>CsAdministrator</p></td>
<td><p><a href="lync-server-2013-optional-verify-dial-in-conferencing.md">(Opcional) Verificar conferência discada no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p><strong>Implante o Suplemento de Reunião Online para Lync 2013</strong></p></td>
<td><p>Implante o Suplemento de Reunião Online para Lync 2013 para que os usuários possam agendar conferências que suportam conferências discadas. O Suplemento de Reunião Online para Lync 2013 é instalado automaticamente quando o Lync 2013 é instalado.</p></td>
<td><p>Administradores</p></td>
<td><p><a href="lync-server-2013-deploy-the-online-meeting-add-in-for-lync-2013.md">Implantar suplemento Online Meeting para Lync 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Defina as configurações da conta do usuário</strong></p></td>
<td><p>Use o Painel de Controle do Lync Server 2013 ou Shell de Gerenciamento do Lync Server para configurar a <strong>URI de Linha</strong> de telefonia como um número de telefone normalizado único (por exemplo, tel:+14255550200).</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>CsAdministrator</p>
<p>CsUserAdministrator</p></td>
<td><p><a href="lync-server-2013-configure-user-account-settings.md">Definir configurações de conta do usuário no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>(Recomendado) Configurar diretórios de conferência</p></td>
<td><p>Use o cmdlet <strong>New-CsConferenceDirectory</strong> para criar um diretório de conferência para cada 999 usuários no pool.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-dial-in-conferencing-requirements.md">Exigências da conferência discada no Lync Server 2013</a> <a href="recommended-create-conference-directories.md">(Recomendado) Criar diretórios de conferência</a></p></td>
</tr>
<tr class="even">
<td><p><strong>(Opcional) Receba os usuários em conferências discadas e defina o PIN inicial</strong></p></td>
<td><p>Use o script <strong>Set-CsPinSendCAWelcomeMail</strong> para definir o PIN inicial dos usuários e envie um e-mail de boas vindas com o PIN inicial e um link para a Página Configurações de Conferência Discada.</p></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-optional-welcome-users-to-dial-in-conferencing.md">(Opcional) Dar as boas-vindas aos usuários na conferência discada no Lync Server 2013</a></p></td>
</tr>
</tbody>
</table>

