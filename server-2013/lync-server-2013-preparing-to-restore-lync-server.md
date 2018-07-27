---
title: Preparando para restaurar o Lync Server
TOCTitle: Preparando para restaurar o Lync Server
ms:assetid: 857e4e02-908e-433a-96c6-be1795a9cb61
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202179(v=OCS.15)
ms:contentKeyID: 52057643
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando para restaurar o Lync Server

 

_**Tópico modificado em:** 2015-03-09_

Antes de começar a restauração de servidores e bancos de dados após uma falha, você precisa determinar o seguinte:

  - O que precisa ser restaurado.

  - O hardware, o software, as ferramentas e os dados necessários para restauração.

## Determinando o quê restaurar

Este tópico descreve como restaurar paralisações do Lync Server que ocorrem em nível do servidor, pool ou do Repositório de Gerenciamento Central. Se o Repositório de Gerenciamento Central falhar, a sua implantação do Lync Server continua a funcionar, mas você não pode fazer alterações na configuração. Se um servidor Standard Edition ou de Back-End falhar, o pool de usuário para de funcionar. Se qualquer outro servidor falhar, a magnitude da falha depende da função de servidor que o servidor está executando e de se o servidor hospeda um ou mais bancos de dados.

### O que restaurar

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Se isto falhou</th>
<th>Consulte esta seção:</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor Standard Edition</p></td>
<td><p><a href="lync-server-2013-restoring-a-standard-edition-server.md">Restaurando um servidor do Standard Edition</a></p></td>
</tr>
<tr class="even">
<td><p>Repositório de Gerenciamento Central</p></td>
<td><p><a href="lync-server-2013-restoring-the-server-hosting-the-central-management-store.md">Restaurar o servidor que hospeda o Repositório de Gerenciamento Central</a></p></td>
</tr>
<tr class="odd">
<td><p>Back-end do Enterprise Edition</p></td>
<td><p><a href="lync-server-2013-restoring-an-enterprise-edition-back-end-server.md">Restaurando um servidor de back-end do Enterprise Edition</a></p></td>
</tr>
<tr class="even">
<td><p>Servidor Back-End Principal Espelhado do Enterprise Edition</p></td>
<td><p><a href="lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-primary.md">Restaurando um servidor back-end Enterprise Edition espelhado – primário</a></p></td>
</tr>
<tr class="odd">
<td><p>Servidor Back-End secundário Espelhado do Enterprise Edition</p></td>
<td><p><a href="lync-server-2013-restoring-a-mirrored-enterprise-edition-back-end-server-mirror.md">Restaurando um servidor back-end Enterprise Edition espelhado – espelho</a></p></td>
</tr>
<tr class="even">
<td><p>Qualquer servidor Enterprise Edition executando uma função de servidor, como um Servidor Front-End, Servidor de Borda, Diretor, Servidor de Mediação ou Servidor de Chat Persistente.</p></td>
<td><p><a href="lync-server-2013-restoring-an-enterprise-edition-member-server.md">Restaurando um servidor membro do Enterprise Edition</a></p></td>
</tr>
<tr class="odd">
<td><p>Um pool inteiro de Lync Server</p></td>
<td><p><a href="lync-server-2013-restoring-a-lync-server-pool.md">Restaurando um pool do Lync Server</a></p></td>
</tr>
<tr class="even">
<td><p>Repositório de Arquivos Enterprise Edition</p></td>
<td><p><a href="lync-server-2013-restoring-a-file-store.md">Restaurando um repositório de arquivos</a></p></td>
</tr>
<tr class="odd">
<td><p>Um banco de dados de Monitoramento ou banco de dados de Arquivamento autônomo</p></td>
<td><p><a href="lync-server-2013-restoring-monitoring-or-archiving-data.md">Restauração de monitoramento ou arquivamento de dados</a></p></td>
</tr>
<tr class="even">
<td><p>Um banco de dados de Chat Persistente autônomo</p></td>
<td><p><a href="lync-server-2013-restoring-persistent-chat-data.md">Restaurando dados do chat persistente</a></p></td>
</tr>
</tbody>
</table>


## Coletando hardware, software e ferramentas

Quando você restaura um servidor, é precisso iniciar com um computador novo ou limpo. Você deve ter os seguintes hardware e software disponíveis:

  - Um servidor novo ou limpo com o mesmoFQDN (nome de domínio totalmente qualificado) do servidor que falhou.
    
    > [!IMPORTANT]  
    > Ao instalar o sistema operacional, verifique se não foi excluída a conta de computador no Serviços de Domínio Active Directory e se as permissões de grupo da conta estão retidas.

  - Software de instalação para o sistema operacional. Para instalar o sistema operacional, use as configurações de implantação do servidor e procedimentos estabelecidos pela organização. Você deve ter esses procedimentos e requisitos de configuração disponíveis quando restaurar o serviço.

  - Software de instalação para o SQL Server 2012 ou o SQL Server 2008 R2. Para instalar um servidor de banco de dados, use a versão adequada do SQL Server e os procedimentos de implantação do servidor de banco de dados e configurações estabelecidos pela sua organização. Você deve ter esses procedimentos e requisitos de configuração disponíveis quando restaurar o serviço.
    
    > [!NOTE]  
    > O Assistente de Instalação do Lync Server instala automaticamente o SQL Server 2012 Express em cada Servidor Standard Edition e em qualquer outro servidor do Lync Server, quando é instalado um armazenamento de configuração local, a menos que você tenha o SQL Server 2012 ou o SQL Server 2008 R2 pré-instalado no servidor.

  - Software para fazer imagens de sistema.
    

    > [!TIP]
    > Recomendamos que você faça uma cópia da imagem do sistema depois de instalar o sistema operacional e o SQL Server e antes de iniciar a restauração para que você possa usar essa imagem como um ponto de reversão, caso algo dê errado durante a restauração.



  - Software de instalação do Lync Server 2013. O Assistente de Implantação do Lync Server está localizado na pasta de instalação do Lync Server ou mídia em \\setup\\amd64\\Setup.exe.

Durante a restauração, você pode usar as seguintes ferramentas:

  - Cmdlets do Shell de Gerenciamento do Lync Server

  - Import-CsUserData

  - Ferramentas para restaurar as pastas do Windows

  - Construtor de Topologias

  - Utilitários de banco de dados de SQL Server, como o SQL Server Management Studio

## Preparação para restaurar um servidor

Antes de restaurar o servidor, você deverá executar as seguintes etapas:

1.  Instale o sistema operacional.

2.  Se o servidor for um Servidor Back-End, instale o SQL Server 2012 ou o SQL Server 2008 R2.

3.  Restaure ou registre seus certificados novamente. Para obter detalhes sobre certificados, consulte "Requisitos adicionais de backup" em [Requisitos de backup e restauração: dados](lync-server-2013-backup-and-restoration-requirements-data.md).

4.  Faça uma captura de imagem do sistema antes de iniciar a restauração para usar como um ponto de reversão caso algo dê errado durante a restauração.

> [!NOTE]  
> O Assistente de Implantação e os cmdlets do Lync Server descritos nos procedimentos neste tópico, e tópicos relacionados, definem todas as listas de controle do acesso (ACLs) necessárias.

Verificar se o hardware e o software que você precisa para os componentes que pretende restaurar estão disponíveis antes de iniciar a restauração. Depois de instalar o sistema operacional e o SQL Server, a maioria das etapas nos procedimentos de restauração a seguir pode ser executada remotamente. As exceções estão indicadas nos procedimentos.

Você também deve ter o backup da sua organização e o plano de restauração e as informações do seu último backup, como, por exemplo, as informações nas planilhas neste documento (para obter detalhes, consulte [Planilhas de backup e restauração](lync-server-2013-backup-and-restoration-worksheets.md)), disponível antes de iniciar a restauração.

