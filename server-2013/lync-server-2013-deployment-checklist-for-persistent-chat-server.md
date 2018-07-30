---
title: 'Lync Server 2013: Lista de verificação de implantação para o Servidor de Chat Persistente'
TOCTitle: Lista de verificação de implantação para o Servidor de Chat Persistente
ms:assetid: b1108f8f-88a2-4660-8086-d25ba76f7239
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412851(v=OCS.15)
ms:contentKeyID: 49307817
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lista de verificação de implantação para o Servidor de Chat Persistente no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A implantação do Lync Server 2013, Servidor de Chat Persistente requer que você o implante na sequência correta e que conclua todas as etapas de implantação necessárias.

## Sequência de implantação

É possível implantar o Servidor de Chat Persistente após a implantação de sua topologia inicial, incluindo pelo menos um Lync Server 2013, Pool de Front-Ends ou um Lync Server 2013, Servidor Standard Edition. Este tópico descreve como implantar o Servidor de Chat Persistente adicionando-o a uma implantação existente.

## Processo de implantação

A tabela a seguir lista as etapas básicas para implantar o Servidor de Chat Persistente e fornece links para mais informações.

### Processo de implantação do Servidor de Chat Persistente

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Tarefa</th>
<th>Etapas</th>
<th>Funções exigidas e associações em grupo</th>
<th>Tópicos relacionados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Instalar os pré-requisitos de hardware e software</strong></p></td>
<td><p>No hardware que atender aos requisitos do sistema, instale o seguinte:</p><ul><li><p>No Servidor de Chat PersistenteServidores Front-End:</p></li></ul><ul><li><p>Um sistema operacional que atenda aos requisitos do sistema</p></li><li><p>Pré-requisitos de software para computadores executando o Lync Server 2013</p></li><li><p>SQL Server no servidor que hospedará o banco de dados Servidor de Chat Persistente.</p></li></ul>
<p>Se a conformidade com Servidor de Chat Persistente for necessária:</p><ul><li><p>SQL Server no servidor que hospedará os bancos de dados de conformidade do Servidor de Chat Persistente</p></li></ul></td>
<td><p>Qualquer usuário que seja membro do grupo Administradores locais.</p></td>
<td><p><a href="lync-server-2013-supported-hardware.md">Hardware suportado para Lync Server 2013</a> na documentação Suporte</p>
<p><a href="lync-server-2013-server-software-and-infrastructure-support.md">Suporte a software e à infraestrutura de servidor no Lync Server 2013</a> na documentação Suporte</p>
<p><a href="lync-server-2013-determining-your-system-requirements.md">Determinando seus requisitos de sistema para Lync Server 2013</a></p>
<p><a href="lync-server-2013-technical-requirements-for-persistent-chat-server.md">Requisitos técnicos do Servidor de Chat Persistente no Lync Server 2013</a></p></td>
</tr>
<tr class="even">
<td><p><strong>Crie a topologia interna apropriada para suportar o Servidor de Chat Persistente (e, opcionalmente, a compatibilidade com Chat Persistente)</strong></p></td>
<td><p>Execute a Construtor de Topologias para adicionar o Pool de Servidor de Chat Persistente a sua topologia:</p><ul><li><p>Adicione os componentes do Servidor de Chat Persistente à topologia</p></li><li><p>Crie um banco de dados do SQL Server para o repositório do Servidor de Chat Persistente (e um backup do SQL Server para a recuperação de desastres)</p></li><li><p>Defina um novo Repositório de arquivos do Lync ou use um Repositório de arquivos Lync existente para Servidor de Chat Persistente files</p></li><li><p>Associe o pool do Lync Server 2013 que pode rotear solicitações ao Pool de Servidor de Chat Persistente</p></li></ul>
<p>Se a conformidade com Chat Persistente for necessária:</p><ul><li><p>Adicione o repositório de conformidade do Chat Persistente</p></li><li><p>Clique na caixa de seleção de definição do Pool de Servidor de Chat Persistente para habilitar a conformidade</p></li><li><p>Publicar a topologia</p></li></ul>
<p>Se você instalar o Servidor de Chat Persistente no Standard Edition, o nome de domínio totalmente qualificado (FQDN) do Pool de Servidor de Chat Persistente deve corresponder ao Servidor Standard Edition e aos bancos de dados do SQL Server são colocados na instância do SQL Server Express no Servidor Standard Edition</p></td>
<td><p>Para definir uma topologia, uma canta membro do grupo de usuários local</p>
<p>Para publicar a topologia, uma conta membro do grupo de Administradores do domínio e do grupo RTCUniversalServerAdmins, bem como o usuário deve ter controle completo sobre as permissões (ler/gravar/modificar) no Repositório de arquivos do Lync para arquivos do Servidor de Chat Persistente (para que o Construtor de topologia possa configurar os DACLs necessários).</p></td>
<td><p><a href="lync-server-2013-adding-persistent-chat-server-to-your-deployment.md">Adicionando Servidor de Chat Persistente em sua implantação no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="odd">
<td><p><strong>Implantar Servidor de Chat Persistente</strong></p></td>
<td><p>Execute a configuração do Lync Server em todos os computadores executando o Servidor de Chat Persistente. A configuração do Servidor de Chat Persistente é integrada ao Assistente de implantação do Lync Server 2013 que fornece as seguintes instruções:</p><ul><li><p>Implantar repositório de gerenciamento local</p></li><li><p>Instalar os serviços do Servidor de Chat Persistente.</p></li><li><p>Solicitar e assinar certificados</p></li><li><p>Executar e iniciar os serviços</p></li></ul></td>
<td><p>Qualquer usuário que seja membro do grupo Administradores locais.</p></td>
<td><p><a href="lync-server-2013-deploying-persistent-chat-server.md">Implantando Servidor de Chat Persistente no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="even">
<td><p><strong>Criar um banco de dados do Chat Persistente.</strong></p></td>
<td><p>Adicionar usuários ao grupo de segurança CsPersistentChatAdministrator.</p></td>
<td><p>Qualquer usuário que seja membro dos administradores de domínio</p></td>
<td><p><a href="lync-server-2013-adding-a-persistent-chat-administrator.md">Adicionando um administrador de Chat Persistente no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
<tr class="odd">
<td><p><strong>Configurar o Servidor de Chat Persistente</strong></p></td>
<td><p>Configurar usuários:</p><ul><li><p>O usuário deve ser habilitado pela política de acesso do Servidor de Chat Persistente. Por padrão, a política está desativada para todos os usuários e pode ser definida nos escopos global/site/pool/usuário.</p></li><li><p>Definir configurações</p></li></ul></td>
<td><p>O usuário deve ser membro do CsPersistentChatAdministrator. Para alterar a política, o usuário deve estar no CsUserAdministrator, no mínimo.</p></td>
<td><p><a href="lync-server-2013-configuring-persistent-chat-server.md">Configurando o Servidor de Chat Persistente no Lync Server 2013</a> na documentação de Implantação</p></td>
</tr>
</tbody>
</table>


> [!IMPORTANT]  
> Você pode implantar um ou mais Pools de Servidor de Chat Persistente. Nós oferecemos suporte a vários Pools de Servidor de Chat Persistente por motivos regulatórios pelos quais os dados gerados em determinada região são parte dessa região. Por exemplo, se você implantar um Pool de Servidor de Chat Persistente em Chicago e outro em Zurique para que sejam compatíveis com os regulamentos de dados na Suíça, os usuários podem se conectar a salas em ambos os Pools de Servidor de Chat Persistente, considerando que tenham acesso.
