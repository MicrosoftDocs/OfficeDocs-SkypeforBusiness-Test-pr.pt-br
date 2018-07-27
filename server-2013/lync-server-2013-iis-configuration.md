---
title: 'Lync Server 2013: Configuração de IIS'
TOCTitle: Configuração de IIS
ms:assetid: b458babf-bf64-43f0-8a8e-612f5096b63c
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412871(v=OCS.15)
ms:contentKeyID: 49307843
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Configuração de IIS no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para concluir este procedimento com êxito, você deve estar conectado ao servidor no mínimo como um administrador local e como um usuário do domínio.

Antes de configurar e instalar o Servidor Front-End para Lync Server 2013, Standard Edition ou o primeiro Servidor Front-End em um pool, instale e configure a função de servidor e Serviços Web para IIS (Serviços de Informações da Internet).

> [!IMPORTANT]  
> Se sua organização exigir que o IIS e todos os serviços Web sejam colocados em uma unidade diferente da unidade do sistema, você poderá alterar o caminho do local de instalação para os arquivos do Lync Server 2013 na caixa de diálogo Configuração ao instalar inicialmente as ferramentas Administrativas do Lync Server 2013. Instale as ferramentas Administrativas antes de instalar o IIS. Se você instalar os arquivos de Configuração nesse caminho, incluindo o OCSCore.msi, o restante dos arquivos do Lync Server 2013 serão implantados nessa unidade também. Para obter informações detalhadas, consulte <a href="lync-server-2013-install-lync-server-administrative-tools.md">Instalar ferramentas administrativas do Lync Server 2013</a>. Para obter detalhes sobre como realocar o INETPUB implantado pelo Windows Server Manager durante a instalação do IIS, consulte <a href="http://go.microsoft.com/fwlink/?linkid=216888" class="uri">http://go.microsoft.com/fwlink/?linkid=216888</a>.

A tabela a seguir indica os serviços de função do IIS 7.5 necessário.

### Serviços de função IIS 7.5

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cabeçalho da função</th>
<th>Serviço de função</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Recursos HTTP comuns instalados</p></td>
<td><p>Conteúdo estático</p></td>
</tr>
<tr class="even">
<td><p>Recursos HTTP comuns instalados</p></td>
<td><p>Documento padrão</p></td>
</tr>
<tr class="odd">
<td><p>Recursos HTTP comuns instalados</p></td>
<td><p>Erros HTTP</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento de aplicativos</p></td>
<td><p>ASP.NET</p>
<p>O Windows Server 2012 também requer o ASP.NET4.5</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento de aplicativos</p></td>
<td><p>Extensibilidade .NET</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento de aplicativos</p></td>
<td><p>Extensões Internet Server API (ISAPI)</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento de aplicativos</p></td>
<td><p>Filtros ISAPI</p></td>
</tr>
<tr class="even">
<td><p>Integridade e diagnósticos</p></td>
<td><p>Log de HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Integridade e diagnósticos</p></td>
<td><p>Ferramentas de log</p></td>
</tr>
<tr class="even">
<td><p>Integridade e diagnósticos</p></td>
<td><p>Rastreamento</p></td>
</tr>
<tr class="odd">
<td><p>Segurança</p></td>
<td><p>Autenticação anônima (instalada e habilitada por padrão)</p></td>
</tr>
<tr class="even">
<td><p>Segurança</p></td>
<td><p>Autenticação do Windows</p></td>
</tr>
<tr class="odd">
<td><p>Segurança</p></td>
<td><p>Autenticação de mapeamento de certificado de cliente</p></td>
</tr>
<tr class="even">
<td><p>Segurança</p></td>
<td><p>Filtragem de solicitação</p></td>
</tr>
<tr class="odd">
<td><p>Desempenho</p></td>
<td><p>Compactação de conteúdo estático</p>
<p>Compressão de conteúdo dinâmico</p></td>
</tr>
<tr class="even">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Console de gerenciamento IIS</p></td>
</tr>
<tr class="odd">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Ferramentas e scripts de gerenciamento IIS</p></td>
</tr>
</tbody>
</table>


No sistema operacional x64 do Windows Server 2008 R2 SP1, é possível usar o Windows PowerShell 2.0. Primeiro é necessário importar o módulo ServerManager e, em seguida, instalar a função e os serviços de função IIS 7.5.

```
    Import-Module ServerManager
```
```
    Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Scripting-Tools, Web-Windows-Auth, Web-Asp-Net, Web-Log-Libraries, Web-Http-Tracing, Web-Stat-Compression, Web-Dyn-Compression, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Errors, Web-Http-Logging, Web-Net-Ext, Web-Client-Auth, Web-Filtering, Web-Mgmt-Console
```

> [!NOTE]  
> A autenticação anônima é instalada por padrão com a função de servidor do IIS. É possível gerenciar a autenticação anônima após a instalação do IIS. Para obter detalhes, consulte “Habilitar autenticação Anônima (IIS 7)“ em <a href="http://go.microsoft.com/fwlink/?linkid=203935" class="uri">http://go.microsoft.com/fwlink/?linkid=203935</a>.

A tabela a seguir indica os serviços de função IIS 8.0 e e IIS 8.5 para o Windows Server 2012 e Windows Server 2012 R2.

> [!NOTE]  
> Para o Windows Server 2012 e o Windows Server 2012 R2, o cmdlet Add-WindowsFeature foi substituído pelo cmdlet Install-WindowsFeature. Para obter detalhes, consulte <a href="http://go.microsoft.com/fwlink/p/?linkid=392274">Install-WindowsFeature</a>.

### Serviços de função IIS 8.0 e IIS 8.5

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Cabeçalho da função</th>
<th>Serviço de função</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor Web (IIS)</p></td>
<td><p>Servidor Web</p></td>
</tr>
<tr class="even">
<td><p>Recursos HTTP Comuns</p></td>
<td><p>Documento padrão</p></td>
</tr>
<tr class="odd">
<td><p>Recursos HTTP Comuns</p></td>
<td><p>Pesquisa de diretório</p></td>
</tr>
<tr class="even">
<td><p>Recursos HTTP Comuns</p></td>
<td><p>Erros HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Recursos HTTP Comuns</p></td>
<td><p>Conteúdo estático</p></td>
</tr>
<tr class="even">
<td><p>Recursos HTTP Comuns</p></td>
<td><p>Redirecionamento HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Integridade e Diagnósticos</p></td>
<td><p>Log HTTP</p></td>
</tr>
<tr class="even">
<td><p>Integridade e Diagnósticos</p></td>
<td><p>Ferramentas de log</p></td>
</tr>
<tr class="odd">
<td><p>Integridade e Diagnósticos</p></td>
<td><p>Monitor de solicitações</p></td>
</tr>
<tr class="even">
<td><p>Integridade e Diagnósticos</p></td>
<td><p>Rastreamento</p></td>
</tr>
<tr class="odd">
<td><p>Segurança</p></td>
<td><p>Requisição de filtro</p></td>
</tr>
<tr class="even">
<td><p>Segurança</p></td>
<td><p>Autenticação básica</p></td>
</tr>
<tr class="odd">
<td><p>Segurança</p></td>
<td><p>Autenticação de mapeamento de certificado de cliente</p></td>
</tr>
<tr class="even">
<td><p>Segurança</p></td>
<td><p>Autenticação do Windows</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Extensibilidade .NET 3,5</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Extensibilidade .NET 4.5</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>ASP.Net 3,5</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>ASP.Net 4.5</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Extensões ISAPI</p></td>
</tr>
<tr class="even">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>Filtros ISAPI</p></td>
</tr>
<tr class="odd">
<td><p>Desenvolvimento do aplicativo</p></td>
<td><p>A ponta do servidor inclui</p></td>
</tr>
<tr class="even">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Console de gerenciamento IIS</p></td>
</tr>
<tr class="odd">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Compatibilidade com Metabase IIS 6</p></td>
</tr>
<tr class="even">
<td><p>Ferramentas de gerenciamento</p></td>
<td><p>Ferramentas e scripts de gerenciamento IIS</p></td>
</tr>
<tr class="odd">
<td><p>Recursos do .Net Framework 3,5</p></td>
<td><p>.Net Framework 3.5</p></td>
</tr>
<tr class="even">
<td><p>Recursos do .Net Framework 4.5</p></td>
<td><p>.Net Framework 4.5</p></td>
</tr>
<tr class="odd">
<td><p>Recursos do .Net Framework 4.5</p></td>
<td><p>ASP.Net 4.5</p></td>
</tr>
<tr class="even">
<td><p>Recursos do .Net Framework 4.5</p></td>
<td><p>Ativação HTTP</p></td>
</tr>
<tr class="odd">
<td><p>Recursos do .Net Framework 4.5</p></td>
<td><p>Compartilhamento de porta TCP</p></td>
</tr>
<tr class="even">
<td><p>Serviço de transferência inteligente de plano de fundo</p></td>
<td><p>Extensões de servidor IIS</p></td>
</tr>
<tr class="odd">
<td><p>Serviços de tinta e manuscrito</p></td>
<td><p>Serviços de tinta e manuscrito</p></td>
</tr>
<tr class="even">
<td><p>Media Foundation</p></td>
<td><p>Media Foundation</p></td>
</tr>
<tr class="odd">
<td><p>Infraestrutura e interfaces de usuário</p></td>
<td><p>Infraestrutura e ferramentas gráficas de gerenciamento</p></td>
</tr>
<tr class="even">
<td><p>Infraestrutura e interfaces de usuário</p></td>
<td><p>Desktop Experience</p></td>
</tr>
<tr class="odd">
<td><p>Infraestrutura e interfaces de usuário</p></td>
<td><p>Shell gráfico do servidor</p></td>
</tr>
<tr class="even">
<td><p>Windows Identity Foundation 3.5</p></td>
<td><p>Windows Identity Foundation 3.5</p></td>
</tr>
<tr class="odd">
<td><p>Serviço de ativação de processo do Windows</p></td>
<td><p>Modelo de processo</p></td>
</tr>
<tr class="even">
<td><p>Serviço de ativação de processo do Windows</p></td>
<td><p>APIs de configuração</p></td>
</tr>
</tbody>
</table>


No Windows Server 2012 e Windows Server 2012 R2, você pode usar o Windows PowerShell 3.0 para instalar os requisitos do IIS. Usando o módulo ServerManager no Windows PowerShell 3.0, digite:

```
    Import-Module ServerManager
```
```
    Add-WindowsFeature Web-Server, Web-Static-Content, Web-Default-Doc, Web-Http-Errors, Web-Asp-Net, Web-Net-Ext, Web-ISAPI-Ext, Web-ISAPI-Filter, Web-Http-Logging, Web-Log-Libraries, Web-Request-Monitor, Web-Http-Tracing, Web-Basic-Auth, Web-Windows-Auth, Web-Client-Auth, Web-Filtering, Web-Stat-Compression, Web-Dyn-Compression, NET-Framework-45-Core, NET-WCF-HTTP-Activation45, Web-Asp-Net45, Web-Mgmt-Tools, Web-Scripting-Tools, Web-Mgmt-Console, Web-Mgmt-Compat, Windows-Identity-Foundation, Server-Media-Foundation, BITS -Source D:\sources\sxs
```

> [!IMPORTANT]  
> Novidade no Windows Server 2012 é o parâmetro -Origem que define onde a mídia de origem Windows Server 2012 pode ser encontrada. A mídia pode ser definida como unidade de DVD (por exemplo, D:\Sources\Sxs), ou como compartilhamento em rede para a qual os arquivos de mídia foram copiados (por exemplo, \\fileserver\windows2012\sources\Sxs).

## Consulte Também

#### Conceitos

[Requisitos de IIS para pools Front-End pools e servidores Standard Edition no Lync Server 2013](lync-server-2013-iis-requirements-for-front-end-pools-and-standard-edition-servers.md)

