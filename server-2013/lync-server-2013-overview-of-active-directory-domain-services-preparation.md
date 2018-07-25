---
title: 'Lync Server 2013: Visão geral da preparação do Serviços de Domínio Active Directory'
TOCTitle: Visão geral da preparação do Serviços de Domínio Active Directory
ms:assetid: cdd2a652-6a0d-4728-9950-3fcaa7a80066
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398869(v=OCS.15)
ms:contentKeyID: 49308137
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Visão geral da preparação do Serviços de Domínio Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Para preparar os Serviços de Domínio Active Directory para a implantação do Lync Server 2013, execute três etapas em uma sequência específica.

A tabela a seguir descreve as etapas necessárias para preparar o AD DS para o Lync Server.

### Etapas da preparação do Active Directory

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>Etapa</th>
<th>Descrição</th>
<th>Onde executar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1.</p></td>
<td><p><a href="lync-server-2013-preparing-the-active-directory-schema.md">Preparando o esquema do Active Directory no Lync Server 2013</a></p></td>
<td><p>Estende o esquema do Active Directory adicionando novas classes e atributos que são usados pelo Lync Server.</p>
<p>Execute uma vez para cada floresta em sua implantação onde o Lync Server será implantado.</p></td>
<td><p>No esquema mestre no domínio raiz de cada floresta na qual o Lync Server será implantado.</p>

> [!NOTE]  
> Não é necessário executar essa etapa no domínio raiz se você tiver permissões no esquema mestre, mas é necessário ser membro do grupo Administradores de Esquema no domínio raiz e membro do grupo Administradores de Empresa no esquema mestre. Em uma topologia de floresta de recursos, execute esta etapa somente na floresta de recursos, e não nas florestas de usuários. Em uma topologia de floresta central, execute esta etapa somente na floresta central, e não nas florestas de usuários.

</td>
</tr>
<tr class="even">
<td><p>2.</p></td>
<td><p><a href="lync-server-2013-preparing-the-forest.md">Preparando a floresta para Lync Server 2013</a></p></td>
<td><p>Cria configurações globais e grupos universais que são usados pelo Lync Server.</p>
<p>Execute uma vez para cada floresta em sua implantação onde o Lync Server será implantado.</p></td>
<td><p>No domínio raiz de cada floresta na qual o Lync Server será implantado. Para executar essa etapa, você precisa ser membro do grupo Administradores de Empresa.</p>

> [!NOTE]  
> Em uma topologia de floresta de recursos, execute esta etapa somente na floresta de recursos, não em florestas de qualquer usuário. Em uma topologia de floresta central, execute esta etapa somente na floresta central, não em florestas de qualquer usuário.

</td>
</tr>
<tr class="odd">
<td><p>3.</p></td>
<td><p><a href="lync-server-2013-preparing-domains.md">Preparando domínios para Server 2013</a></p></td>
<td><p>Adiciona permissões sobre objetos a serem usados por membros de grupos universais.</p>
<p>Execute uma vez por domínio de usuário ou domínio de servidor.</p>

> [!NOTE]  
> Se você estiver migrando do Lync Server 2013 para o Lync Server 2010, o Assistente de Implantação poderá indicar que a preparação do domínio já está completa. Não é necessário executar a preparação do domínio novamente. As permissões não foram alteradas de Lync Server 2013 para Lync Server 2010.

</td>
<td><p>Em um servidor membro em cada domínio no qual o Lync Server será implantado. Para executar essa etapa, você precisa ser membro do grupo Administradores do Domínio.</p></td>
</tr>
</tbody>
</table>


No Lync Server 2013, assim como o Lync Server 2010, armazena grande parte da informação de configuração no Repositório de Gerenciamento Central ao invés do AD DS, como foi o caso em Office Communications Server 2007 R2. No entanto, a seguinte informação é armazenada no AD DS:

  - **Extensões de esquema**:
    
      - Extensões de objetos de usuário
    
      - Extensões para classes do Office Communications Server 2007 R2 para manter a compatibilidade inversa

<!-- end list -->

  - **Dados** (armazenados no esquema estendido do Lync Server e nas classes de esquema existentes):
    
      - URI (Uniform Resource Identifier) SIP do usuário e outras configurações de usuário
    
      - Objetos de contato para aplicativos, como Grupo de Respostas e Atendedor de Conferência
    
      - Um ponteiro para o Repositório de Gerenciamento Central
    
      - Conta de Autenticação Kerberos (um objeto computador opcional)

No Lync Server 2013, você delega administração e configuração concedendo permissões de configuração para o grupo universal RTCUniversalServerAdmins para que os membros deste grupo possam instalar e ativar o Lync Server 2013 em um servidor local (após o servidor ter sido adicionado à topologia, publicado e habilitado). Os usuários delegados devem ser administradores locais no computador onde estão instalando e ativando o Lync Server 2013, mas não precisam ser membros do grupo Administradores de Domínio. Também é possível conceder permissões para objetos nas unidades organizacionais (OU) especificadas para que os membros dos grupos universais criados durante a preparação da floresta possam acessar estes objetos sem ser membro do grupo Administradores de Domínio.

Para novas implantações do Lync Server 2013, as configurações globais devem ser armazenadas no recipiente de Configuração. Se sua organização está atualizando de uma versão anterior e ainda precisa ter configurações globais no recipiente Sistema, o recipiente Sistema ainda é suportado.

## Consulte Também

#### Conceitos

[Preparando o esquema do Active Directory no Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)  
[Extensões, classes e atributos do esquema do Active Directory usado pelo Lync Server 2013](lync-server-2013-active-directory-schema-extensions-classes-and-attributes-used-by-lync-server.md)  

#### Outros Recursos

[Preparando a floresta para Lync Server 2013](lync-server-2013-preparing-the-forest.md)  
[Preparando domínios para Server 2013](lync-server-2013-preparing-domains.md)

