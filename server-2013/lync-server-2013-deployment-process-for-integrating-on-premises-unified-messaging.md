---
title: 'Lync Server 2013: Processo de implantação para integração de Unificação de Mensagens local'
TOCTitle: Processo de implantação para integração de Unificação de Mensagens local com Lync Server
ms:assetid: 269a4436-f09f-415b-96ab-49a64370a385
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg425737(v=OCS.15)
ms:contentKeyID: 49306185
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Processo de implantação para integração de Unificação de Mensagens local com Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Se você deseja integrar o Unificação de Mensagens (UM) do Exchange com o Lync Server 2013, deve realizar as tarefas descritas neste tópico. Certifique-se de revisar as práticas recomendadas de planejamento e implantação descritas no [Orientações para integração de Unificação de Mensagens local e Lync Server 2013](lync-server-2013-guidelines-for-integrating-on-premises-unified-messaging.md). Este tópico assume que você implantou o Lync Server 2013 com um Servidor de Mediação posicionado e você ter habilitado os usuários para Lync Server 2013, mas não necessariamente que você realizou todas as etapas de implantação e configuração para habilitar o Enterprise Voice, conforme descrito no [Implantando o Enterprise Voice no Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md) na documentação de Implantação.

## Processo de integração do Unified Messaging

> [!IMPORTANT]  
> É importante que você coordene com os administradores do Exchange da sua organização para confirmar as tarefas que cada um executará para garantir uma integração tranquila e bem-sucedida.


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
<th>Grupos e funções necessários</th>
<th>Documentação de implantação</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Implante um dos seguintes:</p><ul><li><p>Microsoft Exchange Server 2007 Service Pack 1 (SP2) ou service pack mais recente</p></li><li><p>Microsoft Exchange Server 2010 ou o service pack mais recente</p></li><li><p>Microsoft Exchange Server 2013</p></li></ul></td>
<td><p>Se você estiver usando o Microsoft Exchange Server 2013, instale as seguintes funções do Exchange Server na mesma floresta ou uma floresta diferente como o Lync Server 2013:</p><ul><li><p>Acesso do Cliente</p></li><li><p>Caixa de Correio</p></li></ul>
<p>Se o Microsoft Exchange Server 2013 e o Unificação de Mensagens (UM) do Exchange estão instalados em florestas diferentes, configure cada floresta do Exchange para confiar na floresta do Lync Server 2013.</p>
<p>Se você estiver usando o Exchange 2010, instale as seguintes funções do Exchange Server na mesma floresta ou uma floresta diferente como o Lync Server 2013:</p><ul><li><p>Unified Messaging</p></li><li><p>Transporte de hub</p></li><li><p>Acesso do Cliente</p></li><li><p>Caixa de Correio</p></li></ul>
<p>Se o Lync Server 2013 e o Unificação de Mensagens (UM) do Exchange estão instalados em florestas diferentes, configure cada floresta do Exchange para confiar na floresta do Lync Server 2013.</p></td>
<td><p>Administradores de empresa (se esta for o primeiro Exchange Server na organização)</p>
<p>- OU -</p>
<p>Administrador da organização do Exchange (se este não for o primeiro Exchange Server na organização)</p></td>
<td><p>Consulte a documentação apropriada para sua versão do Exchange Server:</p>
<dl>
<dt><span></span></dt>
<dd><p>Documentação de implantação do Exchange Server 2007 em <a href="http://go.microsoft.com/fwlink/p/?linkid=268694">http://go.microsoft.com/fwlink/p/?LinkId=268694</a>.</p>
</dd>
<dt><span></span></dt>
<dd><p>Documentação de implantação do Exchange Server 2010 ou service pack mais recente em <a href="http://go.microsoft.com/fwlink/p/?linkid=268695">http://go.microsoft.com/fwlink/p/?LinkId=268695</a>.</p>
</dd>
<dt><span></span></dt>
<dd><p>Planejamento e implantação do Microsoft Exchange Server 2013 em <a href="http://go.microsoft.com/fwlink/p/?linkid=266569">http://go.microsoft.com/fwlink/p/?LinkId=266569</a>.</p>
</dd>
</dl></td>
</tr>
<tr class="even">
<td><p>Instalar certificados.</p></td>
<td><p>Baixar e instalar certificados para cada servidor do UM do Exchange de uma CA de raiz confiável. Os certificados são exibidos para MTLS entre os servidores executando o UM do Exchange e Lync Server 2013.</p></td>
<td><p>Administradores</p></td>
<td><p><a href="lync-server-2013-configure-certificates-on-the-server-running-microsoft-exchange-server-unified-messaging.md">Configurar certificados no servidor executando o Unified Messaging do Microsoft Exchange Server</a></p></td>
</tr>
<tr class="odd">
<td><p>Criar e configurar um plano de discagem SIP do UM do Exchange.</p></td>
<td><p>No servidor do UM do Exchange, crie um plano de discagem SIP com base nos requisitos de implantação específicos da sua organização.</p></td>
<td><p>Administrador da organização do Exchange</p></td>
<td><p>Para Exchange 2007 SP1 ou service pack mais recente, consulte &quot;Como criar um plano de discagem URI de SIP de Unificação de Mensagens&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268632">http://go.microsoft.com/fwlink/p/?linkId=268632</a>.</p>
<p>Para Exchange 2010 ou service pack mais recente, consulte &quot;Criar um Plano de Discagem da UM&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268674">http://go.microsoft.com/fwlink/p/?linkId=268674</a>.</p>
<p>Para Exchange 2013, consulte Unificação de Mensagens em <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="even">
<td><p>Configurações de segurança para o plano de discagem SIP do UM do Exchange.</p></td>
<td><p>Para criptografar o tráfego do Enterprise Voice, defina as configurações de segurança no plano de discagem SIP do UM do Exchange como <strong>Protegido por SIP</strong> ou <strong>Seguro</strong>. Esta é uma etapa importante especialmente se você implantou ou planeja implantar dispositivos do Lync Phone Editionem seu ambiente. Para os dispositivos do Lync Phone Edition funcionarem em um ambiente com integração do UM do Exchange, as configurações de criptografia do Lync Server devem alinhar com as configurações de segurança do plano de discagem do UM do Exchange. Para obter detalhes, consulte a documentação de Implantação.</p></td>
<td><p>Administrador da organização do Exchange</p></td>
<td><p><a href="lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md">Configurar o Unified Messaging no Microsoft Exchange para Lync Server 2013</a></p>
<p>Para Exchange 2007 SP1 ou service pack mais recente, consulte também:</p>
<p>&quot;Como Configurar a Segurança em um Plano de Discagem de Unificação de Mensagens&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268696">http://go.microsoft.com/fwlink/p/?LinkId=268696</a>.</p>
<p></p>
<p>Para o Exchange 2010 ou service pack mais recente, consulte também:</p>
<p>&quot;Configurar a segurança VoIP em um plano de discagem de UM&quot; <a href="http://go.microsoft.com/fwlink/p/?linkid=268697">http://go.microsoft.com/fwlink/p/?LinkId=268697</a>.</p>
<p></p>
<p>Para Exchange 2013, consulte Unificação de Mensagens em <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Adicionar servidores do Unified Messaging para o plano de discagem SIP do UM do Exchange.</p></td>
<td><p>Para habilitar um servidor do Unified Messaging recentemente instalado a responder e processar chamadas de entrada, você deve adicionar o servidor do Unified Messaging para um plano de discagem do UM. Nesse caso, adicione o servidor para plano de discagem SIP do UM do Exchange.</p></td>
<td><p>Administradores</p>
<p>Administradores do Exchange Server</p></td>
<td><p>Para Exchange 2007 SP1 ou service pack mais recente, consulte &quot;Como adicionar um servidor de Unificação de Mensagens a um plano de discagem&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268681">http://go.microsoft.com/fwlink/p/?linkId=268681</a>.</p>
<p>Para Exchange 2010 ou service pack mais recente, consulte &quot;Exibir ou configurar as propriedades de um servidor UM&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268682">http://go.microsoft.com/fwlink/p/?linkId=268682</a>.</p>
<p></p>
<p>Para Exchange 2013, consulte Unificação de Mensagens em <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="even">
<td><p>Configurar caixas de correio com endereços SIP.</p></td>
<td><p>Atribuir endereços SIP às caixas de correio de usuários do Enterprise Voice que estarão usando os recursos do UM do Exchange.</p></td>
<td><p>Administrador do Lync Server 2013</p>
<p>Administrador de destinatários do Exchange</p></td>
<td><p>Para Exchange 2007 SP1 ou service pack mais recente, consulte &quot;Como adicionar, remover ou modificar um endereço SIP para um usuário habilitado para UM&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268698">http://go.microsoft.com/fwlink/p/?LinkId=268698</a>.</p>
<p>Para Exchange 2010 ou service pack mais recente, consulte &quot;Modificar um endereço SIP para um usuário habilitado para UM&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268699">http://go.microsoft.com/fwlink/p/?LinkId=268699</a>.</p>
<p></p>
<p>Para Exchange 2013, consulte Unificação de Mensagens em <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Execute o script exchucutil.ps1.</p></td>
<td><p>No servidor executando os serviços do UM do Exchange, abra o Shell de Gerenciamento do Exchange e execute o script exchucutil.ps1, que faz o seguinte:</p><ul><li><p>Concede permissões ao Lync Server 2013 para ler o objetos do UM do Exchange  Serviços de Domínio Active Directory, especificamente, os planos de discagem SIP criados na tarefa anterior.</p></li><li><p>Cria um objeto de gateway IP do Unified Messaging no Active Directory para cada pool do Lync Server 2013 Enterprise Edition ou servidor do Standard Edition que hospeda os usuários habilitados para o Enterprise Voice.</p></li><li><p>Cria um grupo de busca do UM do Exchange para cada gateway. O identificador piloto do grupo de busca será o nome do plano de discagem associado ao gateway correspondente. Eles precisam ser mapeados individualmente se houver mais de um plano de discagem.</p></li></ul></td>
<td><p>Administrador da organização do Exchange</p>
<p>Administrador de destinatários do Exchange</p></td>
<td><p><a href="lync-server-2013-configure-unified-messaging-on-microsoft-exchange.md">Configurar o Unified Messaging no Microsoft Exchange para Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p>Configure planos de discagem do Lync Server 2013.</p></td>
<td><p>Se você estiver integrando com o Exchange 2007 SP1 ou service pack mais recente ou Exchange 2010, crie um novo plano de discagem Enterprise Voice com um nome que corresponde o FQDN do plano de discagem de UM do Exchange.</p>
<div class="alert">
> [!NOTE]  
> Você precisará fazer isso para cada plano de discagem UM.
</div>
<p>Se você estiver integrando com o Exchange 2010 SP1, certifique-se de que os planos de discagem de nível local/global ou nível do pool do Enterprise Voice foram configurados.</p>
<div class="alert">
> [!NOTE]  
> Se você estiver integrando com o Exchange 2010 SP1, o plano de discagem do Lync Server e os nomes do plano de discagem do UM do Exchange não precisam corresponder.
</div></td>
<td><p>RTCUniversalServerAdmins</p></td>
<td><p><a href="lync-server-2013-configuring-dial-plans.md">Configurando planos de discagem no Lync Server 2013</a></p></td>
</tr>
<tr class="odd">
<td><p>Execute a ferramenta de Integração do UM do Exchange.</p></td>
<td><p>No Lync Server 2013, execute <strong>ocsumutil.exe</strong>, que:</p><ul><li><p>Cria objetos de contato do Acesso do Assinante e Atendedor Automático.</p></li><li><p>Valida que há um plano de discagem do Enterprise Voice com um nome que corresponde ao FQDN do plano de discagem do UM Exchange. Se você estiver executando o Exchange 2010 SP1 ou posterior, os nomes do plano de discagem não precisam corresponder e é possível ignorar o aviso da ferramenta sobre isso.</p></li></ul>
<p>Essa ferramenta funciona pela verificação do Active Directory para configurações do UM do Exchange e permite o administrador do Lync Server 2013 exibir, criar e editar objetos de contato.</p></td>
<td><p>RTCUniversalServerAdmins <em>e</em> RTCUniversalUserAdmins</p>
<div class="alert">
> [!IMPORTANT]  
> Para executar com êxito o ocsumutil.exe, o usuário deve pertencer aos dois grupos.
</div>
<div class="alert">
> [!NOTE]  
> Para criar objetos de Contato, o usuário que executa ocsumutil.exe deve ter a permissão correta para a unidade organizacional (OU) do Active Directory onde novos objetos de contato são armazenados. Esta permissão pode ser concedida executando o cmdlet <strong>Grant-CsOUPermission</strong>. Para obter detalhes, consulte a documentação do Shell de Gerenciamento do Lync Server.
</div></td>
<td><p><a href="lync-server-2013-configure-lync-server-2013-to-work-with-unified-messaging-on-microsoft-exchange-server.md">Configurar o Lync Server 2013 para trabalhar com a Unificação de Mensagens no Microsoft Exchange Server</a></p></td>
</tr>
<tr class="even">
<td><p>Se necessário, realize outras etapas de configuração do Enterprise Voice.</p></td>
<td><p>Se você ainda não definiu as configurações do Enterprise Voice nos seus servidores ou usuários, faça um ou mais dos seguintes:</p><ul><li><p>Implantar e configurar</p>
<p>Gateways PSTN e Servidores de Mediação</p></li><li><p>Defina as políticas de voz, os registros de uso PSTN e os roteamentos de chamada de saída.</p></li><li><p>Habilite usuários para o Enterprise Voice.</p></li><li><p>Opcionalmente, configure usuários específicos com planos de discagem.</p></li></ul>
<p>Outras etapas de configuração podem ser necessárias dependendo dos recursos do Enterprise Voice que você habilitar.</p></td>
<td><p>RTCUniversalServerAdmins</p>
<p>RTCUniversalUserAdmins</p></td>
<td><p>Consulte os tópicos nas seções a seguir:</p><ul><li><p><a href="lync-server-2013-configuring-voice-policies-pstn-usage-records-and-voice-routes.md">Configurando políticas de voz, registros de uso de PSTN e rotas de voz no Lync Server 2013</a></p></li><li><p><a href="lync-server-2013-deploying-enterprise-voice.md">Implantando o Enterprise Voice no Lync Server 2013</a></p></li></ul></td>
</tr>
<tr class="odd">
<td><p>Habilitar usuários Enterprise Voice para UM do Exchange.</p></td>
<td><p>No servidor do UM do Exchange, certifique-se de que uma política de caixa de correio do Unified Messaging foi criada e que cada usuário tenha uma atribuição de número exclusivo de extensão e habilitar o usuário para o Unified Messaging.</p></td>
<td><p>Administrador de destinatários do Exchange</p></td>
<td><p>Para Exchange 2007 SP1 ou service pack mais recente, consulte &quot;Como habilitar um usuário para Unificação de Mensagens&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268700">http://go.microsoft.com/fwlink/p/?LinkId=268700</a>.</p>
<p>Para Exchange 2010 ou service pack mais recente, consulte &quot;Habilitar um usuário para Unificação de Mensagens&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=268701">http://go.microsoft.com/fwlink/p/?LinkId=268701</a>.</p>
<p></p>
<p>Para Exchange 2013, consulte Unificação de Mensagens em <a href="http://go.microsoft.com/fwlink/p/?linkid=266579">http://go.microsoft.com/fwlink/p/?LinkId=266579</a>.</p></td>
</tr>
</tbody>
</table>

