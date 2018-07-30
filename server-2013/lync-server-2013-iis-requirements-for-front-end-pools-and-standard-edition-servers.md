---
title: 'Lync Server 2013: Requisitos de IIS para pools Front-End pools e servidores Standard Edition'
TOCTitle: Requisitos de IIS para pools Front-End pools e servidores Standard Edition
ms:assetid: e8a6c7ac-b6d5-4c7e-abe9-d8ea5eedbc62
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg399038(v=OCS.15)
ms:contentKeyID: 49308466
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de IIS para pools Front-End pools e servidores Standard Edition no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

Para os servidores Standard Edition, Servidores Front-End e Diretores, o instalador do Lync Server 2013 cria diretórios virtuais no IIS (Serviços de Informações da Internet) para os seguintes propósitos:

  - Para permitir que usuários baixem arquivos do Serviço de Catálogo de Endereços

  - Para permitir que os clientes obtenham atualizações

  - Para habilitar a conferência

  - Para permitir que usuários baixem o conteúdo das reuniões

  - Para permitir que usuários expandam grupos de distribuição

  - Para habilitar a conferência telefônica

  - Para habilitar recursos do grupo de resposta

Além disso, o instalador da atualização cumulativa para Lync Server 2010: novembro de 2011 cria diretórios virtuais no IIS para as seguintes finalidades:

  - No Servidores Front-End ou servidores Standard Edition para suportar a funcionalidade de mobilidade, como IM (mensagem instantânea) e presença, em dispositivos móveis

  - No Servidores Front-End ou servidores Standard Edition e em Diretores a fim de permitir que os dispositivos móveis descubram automaticamente os recursos de mobilidade

> [!NOTE]  
> Se você estiver implantando a mobilidade, recomendamos o uso do IIS 7.5. O instalador do Serviço de Mobilidade do Lync Server define alguns sinalizadores ASP.NET a fim de aprimorar o desempenho. O IIS 7.5 é instalado por padrão no Windows Server 2008 R2 e o instalador do Serviço de Mobilidade altera automaticamente as configurações do ASP.NET. Se você usar o IIS 7.0 no Windows Server 2008, será necessário alterar manualmente essas configurações.

O Lync Server exige a instalação dos seguintes módulos de IIS:

> [!IMPORTANT]  
> Se sua organização exigir que você coloque o IIS e todos os Serviços da Web em uma unidade que não seja a unidade do sistema, será possível alterar o caminho do local de instalação para os arquivos do Lync Server na caixa de diálogo Configuração. Se você instalar os arquivos de Configuração nesse caminho, incluindo OCSCore.msi, o restante dos arquivos do Lync Server serão implantados nessa unidade também. Para obter detalhes sobre como realocar o INETPUB implantado pelo Windows Server Manager durante a instalação do IIS, consulte <a href="http://go.microsoft.com/fwlink/?linkid=216888" class="uri">http://go.microsoft.com/fwlink/?linkid=216888</a>.

  - Conteúdo estático

  - Documento padrão

  - Erros HTTP

  - ASP.NET

  - Extensibilidade .NET

  - Extensões Internet Server API (ISAPI)

  - Filtros ISAPI

  - Log HTTP

  - Ferramentas de log

  - Rastreamento

  - Autenticação do Windows

  - Requisição de filtro

  - Compressão de conteúdo estático

  - Compactação de conteúdo dinâmico

  - Console de gerenciamento IIS

  - Ferramentas e scripts de gerenciamento IIS

  - Autenticação anônima (instalada por padrão quando o IIS é instalado)

  - Autenticação de mapeamento de certificado de cliente

A tabela a seguir relaciona os URIs dos diretórios virtuais para acesso interno e os recursos do sistema de arquivos a que se referem.

### Diretórios virtuais para acesso interno

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Recurso</th>
<th>URI de diretório virtual</th>
<th>Refere-se a</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Servidor de Catálogo de Endereços</p></td>
<td><p>https:// <em>&lt;FQDN interno&gt;</em> /ABS/int/Handler</p></td>
<td><p>Localização de arquivos de download do Serviço de Catálogo de Endereços para usuários internos.</p></td>
</tr>
<tr class="even">
<td><p>Serviço de descoberta automática</p></td>
<td><p>https:// <em>&lt;FQDN interno&gt;</em> /Autodiscover</p></td>
<td><p>Local do serviço Descoberta Automática do Lync Server que localiza os recursos de mobilidade para usuários de dispositivo móvel internos.</p></td>
</tr>
<tr class="odd">
<td><p>Atualizações de cliente</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /AutoUpdate/Int</p></td>
<td><p>Localização de arquivos de atualização para clientes baseados em computador interno.</p></td>
</tr>
<tr class="even">
<td><p>Conf</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /Conf/Int</p></td>
<td><p>Localização de recursos de conferência para usuários internos.</p></td>
</tr>
<tr class="odd">
<td><p>Atualizações de dispositivos</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /DeviceUpdateFiles_Int</p></td>
<td><p>Localização de arquivos de atualização de dispositivo de UC para dispositivos internos de UC.</p></td>
</tr>
<tr class="even">
<td><p>Reunião</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /etc/place/null</p></td>
<td><p>Localização do conteúdo de reunião para usuários internos.</p></td>
</tr>
<tr class="odd">
<td><p>Serviço de Mobilidade</p></td>
<td><p>https:// <em>&lt;FQDN interno&gt;</em> /Mcx</p></td>
<td><p>Localização dos recursos do Serviço de Mobilidade para usuários de dispositivo móvel internos.</p></td>
</tr>
<tr class="even">
<td><p>Serviço de Consulta na Web ao Catálogo de Endereços e Expansão de Grupo</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /GroupExpansion/int/service.asmx</p></td>
<td><p>Localização do serviço web que permite a expansão de grupos para usuários internos. Além disso, o local do serviço Address Book Web Query que fornece informações sobre a lista de endereços globais aos clientes internos do Lync Mobile. Microsoft Lync 2010 Mobile</p></td>
</tr>
<tr class="odd">
<td><p>Conferência por telefone</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /PhoneConferencing/Int</p></td>
<td><p>Localização de dados de conferência por telefone para usuários internos.</p></td>
</tr>
<tr class="even">
<td><p>Atualizações de dispositivos</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /RequestHandler</p></td>
<td><p>Localização do Manipulador de Solicitações do Serviço Web de Atualização de Dispositivo que permite aos dispositivos de UC internos carregar logs e verificar a existência de atualizações.</p></td>
</tr>
<tr class="odd">
<td><p>Aplicativo Grupo de Resposta</p></td>
<td><p>http:// <em>&lt;FQDN interno&gt;</em> /RgsConfig</p>
<p>http:// <em>&lt;FQDN interno&gt;</em> /RgsClients</p></td>
<td><p>Localização da Ferramenta de Configuração de Grupo de Resposta.</p></td>
</tr>
</tbody>
</table>


> [!NOTE]  
> Para o Pools de Front-Ends em uma configuração consolidada, é necessário implantar o IIS antes de poder adicionar servidores ao pool.

> [!security]  
> Você deve usar o snap-in administrativo do IIS para atribuir o certificado usado pelo servidor de componente da web do IIS.
