---
title: 'Lync Server 2013: Requisitos de associação ao grupo'
TOCTitle: Requisitos de associação em grupo
ms:assetid: 01876843-8717-4e72-baf5-866ac8cceee6
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204623(v=OCS.15)
ms:contentKeyID: 49305671
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de associação ao grupo para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

A tabela a seguir resume o grupo ou grupos que uma pessoa deve pertencer para instalar, gerenciar e solucionar problemas com êxito do Lync Server 2013.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Executável Lync Server 2013</th>
<th>Participação no grupo necessária</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Setup.exe</strong> - Executável que inicia a instalação das ferramentas administrativas do Lync Server 2013.</p></td>
<td><p>Membro do grupo de Administradores Locais no computador o qual o executável está em execução. Membro do grupo Usuários do Domínio para ler informações no Serviços de Domínio Active Directory. Este nível de permissão é necessário porque a instalação automática dos pacotes MSI necessários no computador local requer privilégios que permitam ler e gravar dos recursos do computador local protegido, como diretórios de Arquivos de Programas e registros protegidos, como a ramificação da Máquina Local.</p>
<div class="alert">

> [!TIP]
> Você também pode delegar permissões de instalação para usuários e grupos os quais não deseja fornecer participação no grupo de Administradores de Domínio. Para detalhes, consulte <A href="lync-server-2013-granting-setup-permissions.md">Concedendo permissões de configuração no Lync Server 2013</A> na documentação de Implantação


</div></td>
</tr>
<tr class="even">
<td><p><strong>Deploy.exe</strong> - Chamado pelo setup.exe, o deploy.exe é responsável pela implantação dos componentes de software para funções do servidor.</p></td>
<td><p>Membros do grupo de Administradores Locais no computador o qual o executável está executando. Membros do grupo de Usuários de Domínio para ler informações no AD DS. Este nível de permissão é necessário porque a instalação automática dos pacotes MSI necessários no computador local precisam de privilégios que permitam a leitura e gravação nos recursos do computador local protegido, como Arquivos de Programas e registros protegidos, como a ramificação da Máquina Local. A participação no grupo RtcUniversalReadOnlyAdmins é necessária para ler o Repositório de Gerenciamento Central.</p>

> [!NOTE]  
> Se você está executando o Sistema operacional Windows Vista ou Sistema operacional Windows 7, será solicitado pelo Controle de Conta de Usuário (UAC) para prosseguir com a instalação. Se você estiver logado em uma conta de usuário padrão, precisará de alguém que seja membro do grupo de Administradores Locais para fornecer as credenciais quando solicitado para uma conta com permissões de instalar software.

</td>
</tr>
<tr class="odd">
<td><p><strong>Bootstrapper.exe</strong> - Chamado pelo setup.exe, o bootstrapper.exe é responsável pela implantação e configuração das funções do servidor.</p></td>
<td><p>Membros do grupo de Administradores Locais no computador o qual o executável está sendo executado. Membro do grupo RTCUniversalServerAdmins para executar o Bootstrapper.exe. Membro do grupo de Usuários do Domínio para ler informações no AD DS. Este nível de permissão é necessário porque a instalação automática dos pacotes MSI necessários no computador local precisam de privilégios que permitam a leitura e gravação nos recursos do computador local protegido, como diretórios de Arquivos de Programas e registros protegidos, como a ramificação da Máquina Local.</p></td>
</tr>
<tr class="even">
<td><p><strong>TopologyBuilder</strong> - Interface guiada pelo assistente para criar, visualizar, ajustar e validar topologias Lync Server 2013.</p></td>
<td><p>Membros do grupo de Administradores Locais o qual o executável está sendo executado para visualizar a topologia. Membros do grupo RTCUniversalServerAdmins para alterar as definições de configuração. Membros do grupo RTCUniversalServerAdmins e grupo de Administradores de Domínio ou membros do grupo RTCUniversalServerAdmins (somente se o grupo possuir permissões de instalação delegadas) para publicar a topologia. Para detalhes sobre a delegação de permissões de instalação para permitir que membros do grupo RTCUniversalServerAdmins publiquem a topologia sem serem membros do grupo de Administradores de Domínio, consulte <a href="lync-server-2013-granting-setup-permissions.md">Concedendo permissões de configuração no Lync Server 2013</a> na documentação de Implantação.</p></td>
</tr>
<tr class="odd">
<td><p><strong>AdminUIHost</strong> - Interface de usuário gráfico com base na Web para gerenciamento do Lync Server 2013.</p></td>
<td><p>Membro do grupo ou outra função RBAC o qual a tarefa administrativa específica é atribuída. As implementações do Painel de Controle do Lync Server 2013 são alteradas ao executar cmdlets Shell de Gerenciamento do Lync Server 2013. Para uma lista de funções predefinidas e membros de cmdlets que podem ser executados, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de Planejamento.</p></td>
</tr>
<tr class="even">
<td><p><strong>PowerShell.exe com o módulo Lync Server 2013 carregado</strong> - Ferramenta administrativa de linha de comando com cmdlets específicos para gerenciar o Lync Server 2013.</p></td>
<td><p>Membro do grupo CsAdministrator ou membro de outra função do RBAC o qual o cmdlet específico foi atribuído. Para uma lista de funções predefinidas e membros cmdlets que podem ser executados, consulte <a href="lync-server-2013-planning-for-role-based-access-control.md">Planejamento de controle de acesso baseado em função no Lync Server 2013</a> na documentação de Planejamento.</p>
<p>Ou, membro de um ou mais dos seguintes grupos, dependendo do cmdlet:</p>
<ul>
<li><p>RTCUniversalServerAdmins</p></li>
<li><p>RTCUniversalUserAdmins</p></li>
<li><p>RTCUniversalReadOnlyAdmins</p></li>
</ul></td>
</tr>
</tbody>
</table>

