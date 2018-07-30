---
title: 'Lync Server 2013: Preparando Serviços de Domínio do Active Directory'
TOCTitle: Preparando Serviços de Domínio do Active Directory
ms:assetid: 7b0d9aa4-f1ab-4578-b22f-b802b6ed1530
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398607(v=OCS.15)
ms:contentKeyID: 49307207
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Preparando Serviços de Domínio do Active Directory no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

No  Lync Server 2013, você pode usar o Assistente de Implantação do Lync Server para preparar os Serviços de Domínio Active Directory ou pode usar cmdlets do Shell de Gerenciamento do Lync Server diretamente. Também pode usar a ferramenta de linha de comando ldifde.exe diretamente nos seus controladores de domínio, conforme descrito mais adiante neste tópico.

O Assistente de Implantação do Lync Server o orienta em cada tarefa de preparação do Active Directory. O Assistente de implantação executa os cmdlets Shell de Gerenciamento do Lync Server. Essa ferramenta é útil para ambientes com um único domínio e topologia de floresta, ou outra topologia semelhante.

> [!IMPORTANT]  
> Você pode implantar o Lync Server em uma floresta ou domínio nos quais os controladores de domínio executam versões de 32 bits de alguns sistemas operacionais (para obter detalhes, consulte <a href="lync-server-2013-active-directory-infrastructure-requirements.md">Requisitos de infraestrutura do Active Directory para Lync Server 2013</a>). No entanto, você não pode usar o Assistente de Implantação do Lync Server para executar a preparação de esquema, floresta e domínio nesses ambientes porque o Assistente de implantação e os arquivos de suporte são de 64 bits apenas. Em vez disso, você pode usar o Ldifde.exe e os arquivos .ldf associados em um controlador de domínio de 32 bits para preparar o esquema, a floresta e domínio. Consulte a seção &quot;Usando os Cmdlets e Ldifde.exe&quot; posteriormente neste tópico.

Você pode usar cmdlets Shell de Gerenciamento do Lync Server para executar tarefas remotamente ou em ambientes mais complexos.

## Pré-requisitos de preparação do Active Directory

Você deve executar as etapas de preparação do Active Directory em um computador executando Windows Server 2012, Windows Server 2012 R2 ou Windows Server 2008 R2 com SP1 (64 bits). A preparação do Active Directory requer Shell de Gerenciamento do Lync Server e OCSCore.

Os seguintes componentes são necessários para executar tarefas de preparação do Active Directory:

  - Lync Server Componentes principais (OCScore.msi)
    
    > [!NOTE]  
    > Se você planeja usar Shell de Gerenciamento do Lync Server para a preparação do Active Directory, você deve executar o Assistente de Implantação do Lync Server primeiro para instalar os componentes principais.

  - Microsoft.NET Framework 4.5
    
    > [!NOTE]  
    > Para o Windows Server 2012 e o Windows Server 2012 R2, instale e ative o .NET Framework 4.5 usando o Gerenciador de Servidores. Para obter detalhes, consulte &quot;Microsoft .NET Framework 4.5&quot; em <a href="lync-server-2013-additional-software-requirements.md">Requisitos adicionais de software para Lync Server 2013</a>. Para o Windows Server 2008 R2, baixe e instale o <a href="http://www.microsoft.com/en-us/download/details.aspx?id=30653">.Net Framework 4.5</a> do site da Microsoft.

  - Ferramentas de administração de servidor remoto (RSAT)
    
    > [!NOTE]  
    > Algumas ferramentas RSAT são necessárias se você for executar as etapas de preparação do Active Directory em um servidor membro em vez de em um controlador de domínio. Instale as ferramentas de linha de comando e snap-ins do AD DS e o módulo Active Directory para Windows PowerShell a partir do nó do AD DS e ferramentas AD LDS.

  - Pacote Microsoft Visual C++ 2008 Redistributable
    
    > [!NOTE]  
    > O programa de instalação solicita que você instale esse pré-requisito, se ele já não estiver instalado no computador. O pacote é fornecido para você e não terá que adquirí-lo separadamente.

  - Windows PowerShell 3.0 (64 bits)
    
    Para Windows Server 2012, Windows Server 2012 R2 e Windows PowerShell 3.0 deve ser incluído com a instalação Lync Server 2013. Para Windows Server 2008 R2, você precisa instalar ou atualizar para Windows PowerShell 3.0. Para detalhes, consulte [Instalando Windows PowerShell 3.0 para Lync Server 2013](lync-server-2013-installing-windows-powershell-3-0.md)

## Funções e direitos do administrador

A tabela a seguir mostra as funções e os direitos administrativos necessários para cada tarefa de preparação do Active Directory.

### Direitos de usuário necessários para a preparação do Active Directory

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Procedimento</th>
<th>Direitos ou funções</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Preparação do esquema</p></td>
<td><p>Membro do grupo Administradores de esquema para o domínio raiz da floresta e os direitos do administrador no mestre de esquema</p></td>
</tr>
<tr class="even">
<td><p>Preparação da floresta</p></td>
<td><p>Membro do grupo Administradores de empresa para a floresta</p></td>
</tr>
<tr class="odd">
<td><p>Preparação do domínio</p></td>
<td><p>Membro do grupo Administradores de empresa ou Administradores do domínio para o domínio especificado</p></td>
</tr>
</tbody>
</table>


## Cmdlets de preparação do Active Directory

A tabela a seguir compara os cmdlets Shell de Gerenciamento do Lync Server usados para preparar o AD DS para comandos LcsCmd, usado para preparar o AD DS em Microsoft Office Communications Server 2007 R2.

### Cmdlets comparados a LcsCmd

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cmdlets</th>
<th>LcsCmd</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Install-CsAdServerSchema</p></td>
<td><p>Lcscmd /forest /action:SchemaPrep /SchemaType:Server</p></td>
</tr>
<tr class="even">
<td><p>Get-CsAdServerSchema</p></td>
<td><p>Lcscmd /forest /action:CheckSchemaPrepState</p></td>
</tr>
<tr class="odd">
<td><p>Enable-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:ForestPrep</p></td>
</tr>
<tr class="even">
<td><p>Disable-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:ForestUnprep</p></td>
</tr>
<tr class="odd">
<td><p>Get-CsAdForest</p></td>
<td><p>Lcscmd /forest /action:CheckForestPrepState</p></td>
</tr>
<tr class="even">
<td><p>Enable-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action:DomainPrep</p></td>
</tr>
<tr class="odd">
<td><p>Disable-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action: DomainUnprep</p></td>
</tr>
<tr class="even">
<td><p>Get-CsAdDomain</p></td>
<td><p>Lcscmd /domain /action:CheckDomainPrepState</p></td>
</tr>
</tbody>
</table>


## Requisitos do Active Directory bloqueado

Se a herança das permissões estiver desabilitada ou as permissões de usuário autenticadas tiverem que ser desabilitadas na organização, execute etapas adicionais durante a preparação do domínio. Para obter detalhes, consulte [Preparando Serviços de Domínio Active Directory bloqueado no Lync Server 2013](lync-server-2013-preparing-a-locked-down-active-directory-domain-services.md).

## Permissões de contêiner personalizadas

Se sua organização usa contêineres personalizados em vez de três contêineres internos (controladores de usuários, computadores e domínio), você deve conceder o acesso de leitura aos contêineres personalizados para o grupo Usuários autenticados. O acesso de leitura aos contêineres é necessário para a preparação do domínio. Para obter detalhes, consulte [Preparando domínios para Server 2013](lync-server-2013-preparing-domains.md).

## Usando Cmdlets e Ldifde.exe

A etapa **Preparar esquema** em Assistente de Implantação do Lync Server e o cmdlet **Install-CsAdServerSchema** estendem o esquema do Active Directory em controladores de domínio executando um sistema operacional de 64 bits. Se você precisa estender o esquema do Active Directory em um controlador de domínio executando um sistema operacional de 32 bits, execute o cmdlet **Install-CsAdServerSchema** remotamente a partir de um servidor membro (abordagem recomendada). No entanto, se for necessário executar a preparação do esquema diretamente no controlador de domínio, você pode usar a ferramenta Ldifde.exe para importar os arquivos de esquema. A ferramenta Ldifde.exe é fornecida com a maioria das versões do sistema operacional Windows.

Se você usar o Ldifde.exe para importar os arquivos de esquema, importe todos os quatro arquivos independentemente de estar migrando de uma versão anterior ou executando uma instalação limpa. Você deve importá-los na seguinte seqüência:

1.  ExternalSchema.ldf

2.  ServerSchema.ldf

3.  BackCompatSchema.ldf

4.  VersionSchema.ldf

> [!NOTE]  
> Os quatro arquivos .ldf estão localizados em \Suporte\ diretório de esquema na mídia de instalação ou download.

Para usar o Ldifde.exe na importação dos arquivos de quatro esquemas em um controlador de domínio que é o mestre de esquema, use o seguinte formato:

    ldifde -i -v -k -s <DCName> -f <Schema filename> -c DC=X <defaultNamingContext> -j logFilePath -b <administrator account> <logon domain> <password>

Por exemplo:

    ldifde -i -v -k -s DC1 -f ServerSchema.ldf -c DC=X "DC=contoso,DC=com" -j C:\BatchImportLogFile -b Administrator contoso password

> [!NOTE]  
> Use o parâmetro b somente se estiver conectado como um usuário diferente. Para obter detalhes sobre os direitos necessários, consulte a seção &quot;Direitos e funções do administrador&quot; anteriormente neste tópico.

Para usar o Ldifde.exe na importação dos arquivos de quatro esquemas em um controlador de domínio que não é o mestre de esquema, use o seguinte formato:

    ldifde -i -v -k -s <SchemaMasterFQDN> -f <Schema filename> -c DC=X <rootDomainNamingContext> -j logFilePath -b <administrator account> <domain> <password>

Para obter detalhes sobre como usar o Ldifde, consulte o artigo 237677 da Microsoft Knowledge Base, "Usando o LDIFDE para importar e exportar objetos de diretório para o Active Directory", em [http://go.microsoft.com/fwlink/?linkid=132204](http://go.microsoft.com/fwlink/?linkid=132204%26clcid=0x416).

## Nesta seção

  - [Preparando o esquema do Active Directory no Lync Server 2013](lync-server-2013-preparing-the-active-directory-schema.md)

  - [Preparando a floresta para Lync Server 2013](lync-server-2013-preparing-the-forest.md)

  - [Preparando domínios para Server 2013](lync-server-2013-preparing-domains.md)

