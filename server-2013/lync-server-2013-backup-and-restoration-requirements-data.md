---
title: 'Requisitos de backup e restauração: dados'
TOCTitle: 'Requisitos de backup e restauração: dados'
ms:assetid: ecfb8e4d-cb4f-476d-9772-4486bd683c04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202194(v=OCS.15)
ms:contentKeyID: 52057752
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Requisitos de backup e restauração: dados

 

_**Tópico modificado em:** 2016-12-08_

O Lync Server usa definições e informações de configuração armazenadas em bancos de dados e dados armazenados em banco de dados e repositórios de arquivo. Este tópico descreve os dados que precisam de backup para que você possa restaurar o serviço, caso sua organização enfrente uma falha ou interrupção, e também identifica os dados e componentes usados pelo Lync Server, cujo backup precisa ser feito separadamente.

## Requisitos de definição e configuração

Este tópico contém procedimentos para backup e restauração das definições e informações de configuração necessárias para a recuperação do serviço Lync Server. Essas informações estão localizadas no Repositório de Gerenciamento Central ou em outro banco de dados back-end do Servidor Standard Edition.

A tabela a seguir identifica as definições e informações de configuração necessárias para o backup e a restauração.

### Dados de definição e configuração

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipos de dados</th>
<th>Onde estão armazenados</th>
<th>Descrição/Quando fazer backup</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Informações de configuração da topologia</p></td>
<td><p>Repositório de Gerenciamento Central (banco de dados: Xds.mdf)</p></td>
<td><p>Definições de topologia, política e configuração.</p>
<p>Faça o backup com seus backups regulares e depois de usar o Painel de Controle do Lync Server ou cmdlets para modificar sua configuração ou políticas.</p></td>
</tr>
<tr class="even">
<td><p>Informações sobre o local</p></td>
<td><p>Repositório de Gerenciamento Central (banco de dados: Lis.mdf)</p></td>
<td><p>Informações de configuração do Enterprise Voice Enhanced 9-1-1 (E9-1-1). Essas informações são normalmente estáticas.</p>
<p>Faça o backup com seus backups regulares.</p></td>
</tr>
<tr class="odd">
<td><p>Informações de configuração do Grupo de resposta</p></td>
<td><p>Servidor Back-End ou Servidor Standard Edition (banco de dados: RgsConfig.mdf)</p></td>
<td><p>Grupos de agente, filas e fluxos de trabalho do Grupo de Resposta.</p>
<p>Fazer backup com seus backups regulares e após adicionar ou alterar grupos de agente, filas ou fluxos de trabalho.</p></td>
</tr>
</tbody>
</table>


## Requisitos de dados

Veja aqui uma lista dos dados do Lync Server que precisam de backup para que você possa restaurar o serviço Lync Server em um evento de falha.

Observe que alguns tipos de dados não são exigidos para a recuperação. Este tópico não contém procedimentos para o backup desses tipos de dados, que abrangem os seguintes:

  - Dados de usuário transitório, como pontos de extremidade e assinaturas, servidores de conferência ativa e estados de conferência transitórios (banco de dados: RtcDyn.mdf)

  - Dados do catálogo de endereços (bancos de dados: Rtcab.mdf e Rtcab1.mdf). O banco de dados do catálogo de endereços é regenerado automaticamente a partir do Serviços de Domínio Active Directory.

  - Informações dinâmicas para o Aplicativo de Estacionamento de Chamada (banco de dados: CpsDyn.mdf)

  - Dados do Grupo de Resposta transitórios, como estado de login do operador e informações de chamada em espera (banco de dados: RgsDyn.mdf)

  - O banco de dados de conformidade do Chat Persistente (banco de dados: MgcComp.mdf). Se você tiver a conformidade com chat persistente habilitada, as informações do banco de dados de conformidade do Chat Persistente serão transitórias desde que você tenha um adaptador configurado para ler as informações do banco de dados e convertê-las em um formato alternativo. Assim, o banco de dados de conformidade do Chat Persistente é considerado transitório.
    
    O Servidor de Chat Persistente do Lync Server 2013 é fornecido com um adaptador XML. Você também pode instalar adaptadores personalizados que pegam esses dados e os movem para outras fontes, como os Exchange Hosted Archives.

A tabela a seguir identifica os dados que precisam de backup e restauração.

### Dados armazenados em bancos de dados

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipos de dados</th>
<th>Onde estão armazenados</th>
<th>Descrição/Quando fazer backup</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Dados persistentes de usuário</p></td>
<td><p>Servidor back-end ou Servidor Standard Edition (banco de dados: RTCXDS.mdf)</p></td>
<td><p>Direitos do usuário, listas de contatos do usuário, dados do servidor ou do pool, conferências agendadas e assim por diante. Esses dados do usuário não abrangem o conteúdo carregado para uma conferência.</p>
<p>Faça o backup com seus backups regulares. Essas informações são dinâmicas, mas a perda de atualizações não será catastrófica para o Lync Server se você precisar restaurar seu backup regular mais recente. Se as Listas de contato forem fundamentais para sua organização, faça backup desses dados com mais frequência.</p></td>
</tr>
<tr class="even">
<td><p>Arquivamento de dados</p></td>
<td><p>Arquivamento de banco de dados (banco de dados: LcsLog.mdf)</p>
<p>Esses dados poderão ser armazenados no Exchange 2013 se você tiver habilitado a opção de integração com o Microsoft Exchange. Caso contrário, esses dados serão mantidos em um banco de dados de arquivamento do Lync Server, que pode ser colocado com outro banco de dados do Lync Server ou permanecer autônomo e um servidor de banco de dados separado.</p></td>
<td><p>IM (Mensagem instantânea) e conteúdo de reunião.</p>
<p>Esses dados não são fundamentais para o Lync Server, mas podem ser para sua organização para fins normativos. Determine sua agenda de backups adequadamente.</p>
<p>O Lync Server oferece suporte apenas ao modelo de recuperação simples dos bancos de dados de arquivamento. Com esse modelo, os bancos de dados são recuperados no ponto do último backup completo, o que significa que você não pode restaurar um banco de dados para o ponto de uma falha ou um ponto específico no tempo.</p></td>
</tr>
<tr class="odd">
<td><p>Dados de monitoramento</p></td>
<td><p>Bancos de dados de monitoramento (LcsCDR.mdf e QoeMetrics.mdf)</p>
<p>Esses bancos de dados podem ser colocados com outro banco de dados do Lync Server ou permanecer autônomos em um servidor de banco de dados separado.</p></td>
<td><p>Registros de detalhes da chamada (LcsCDR.mdf) e métricas de QoE (qualidade da experiência) (QoeMetrics.mdf).</p>
<p>Os registros de detalhes de chamada são dinâmicos e podem ser essenciais para seus negócios. Determine sua agenda de backups considerando se você precisa desses registros por razões normativas.</p>
<p>As informações de Qualidade de experiência são dinâmicas. A perda de dados de QoE não é fundamental para a operação do Lync Server, mas pode ser para seu negócio. Determine sua agenda de backups com base na importância que essas informações têm para sua organização.</p>
<p>O Lync Server oferece suporte apenas ao modelo de recuperação simples dos bancos de dados de monitoramento. Com esse modelo, os bancos de dados são recuperados no ponto do último backup completo, o que significa que você não pode restaurar um banco de dados para o ponto de uma falha ou um ponto específico no tempo.</p></td>
</tr>
<tr class="even">
<td><p>Dados do chat persistente</p></td>
<td><p>Banco de dados do chat persistente (mgd.mdf).</p>
<p>Esse banco de dados pode ser colocado com outro banco de dados do Lync Server ou permanecer autônomo em um servidor de banco de dados separado.</p></td>
<td><p>Os dados do chat persistente são o conteúdo real do chat que está sendo publicado nas salas de chat. Esses dados são sempre críticos aos negócios.</p>
<p>Você pode optar por usar o backup do SQL Server ou exportar o banco de dados usando o cmdlet <strong>Export-CsPersistentChatData</strong> fornecido no Lync Server. Para a recuperação dos dados, você pode importar e restaurar o banco de dados para o ponto do último backup completo, o que significa que você não poderá restaurar o banco de dados para o ponto de falha.</p></td>
</tr>
</tbody>
</table>


## Requisitos de dados do repositório de arquivos

Em uma implantação do Enterprise Edition, o repositório de arquivos do Lync Server está geralmente localizado em um servidor de arquivos. Em uma implantação do Standard Edition, o repositório de arquivos do Lync Server está localizado por padrão no Servidor Standard Edition. Normalmente, há um repositório de arquivos do Lync Server compartilhado para um site. O repositório de arquivos do Chat Persistente usa o mesmo compartilhamento de arquivos do repositório de arquivos do Lync Server.

Os locais de repositório de arquivos são identificados como \\\\servidor\\nome do compartilhamento. Para encontrar os locais específicos de seus repositórios de arquivo, abra o Construtor de Topologias e analise o nó **Repositórios de arquivo**.

A tabela a seguir identifica os repositórios de arquivo necessários para backup e restauração.

### Repositórios de arquivo

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Tipos de dados</th>
<th>Onde estão armazenados</th>
<th>Descrição/Quando fazer backup</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Repositório de arquivos do Lync Server</p></td>
<td><p>Normalmente em um servidor de arquivos, cluster de arquivos ou um Servidor Standard Edition</p></td>
<td><p>Conteúdo da reunião, metadados do conteúdo da reunião, logs de conformidade da reunião, arquivos de dados de aplicativo, arquivos de atualizações de dispositivo, arquivos de áudio do Grupo de Resposta, Estacionamento de Chamada, aplicativos Comunicados e arquivos postados em salas de chat persistente.</p>
<p>Faça o backup com seus backups regulares.</p></td>
</tr>
</tbody>
</table>


## Requisitos adicionais de backup

Para ajudar a assegurar sua capacidade de restaurar os serviços do Lync Server em um evento de falha, você deve fazer backup de alguns componentes necessários que não fazem parte do próprio Lync Server. Os seguintes componentes não têm o backup feito nem são restaurados como parte do processo de backup e restauração do Lync Server descrito neste documento:

  - **Serviços de Domínio Active Directory**   Você precisa fazer backup do AD DS (Serviços de Domínio Active Directory) usando as ferramentas do Active Directory ao mesmo tempo em que faz o backup do Lync Server. É importante manter os AD DS sincronizados com o Lync Server para evitar problemas que podem ocorrer quando o Lync Server espera contatar objetos que não correspondem aos dos AD DS. Os AD DS armazenam as seguintes configurações usadas pelo Lync Server:
    
      - URI (Uniform Resource Identifier) do SIP do usuário e outras configurações do usuário.
    
      - Objetos de contato para aplicativos, como Grupo de Resposta e Atendedor de Conferência.
    
      - Um indicador para o Repositório de Gerenciamento Central
    
      - Conta de autenticação Kerberos (um objeto de computador opcional) e grupos de segurança do Lync Server.
    
    Para obter detalhes sobre o backup e a restauração dos AD DS no Windows Server 2008, consulte "Guia passo a passo de backup e recuperação dos AD DS" em <http://go.microsoft.com/fwlink/?linkid=209105>.

  - **Autoridade de certificação e certificados**   Use a política de sua organização para fazer backup de sua CA (autoridade de certificação) e certificados. Se você usar chaves privadas exportáveis, poderá fazer o backup do certificado e da chave privada e exportá-los se usar os procedimentos neste documento para restaurar o Lync Server. Se você usar um CA interno, poderá se reinscrever, caso precise restaurar o Lync Server. É importante que você mantenha a chave privada em um local seguro onde ficará disponível caso um computador falhe.

  - **System Center Operations Manager**   Se você usar o Microsoft System Center Operations Manager (anteriormente Microsoft Operations Manager) para monitorar sua implantação do Lync Server, poderá, como opção, fazer o backup dos dados que ele cria enquanto monitora o Lync Server. Use seu processo de backup padrão do SQL Server para fazer backup de arquivos do System Center Operations Manager. Esses arquivos não são restaurados durante a recuperação.

  - **Configuração do gateway PSTN (Rede de Telefonia Pública Comutada)**   Se você usar o Enterprise Voice ou Aparelhos de Filial Persistente, será necessário fazer o backup da configuração do gateway PSTN. Consulte seu fornecedor para obter detalhes sobre como fazer backup e restaurar as configurações do gateway PSTN.

  - **Versões coexistentes do Lync Server ou do Office Communications Server**  Se sua implantação do Lync Server 2013 coexistir com o Lync Server 2010 ou uma versão anterior do Office Communications Server, você não poderá usar os procedimentos deste documento para fazer backup e restaurar a versão anterior. Em vez disso, você deverá usar os procedimentos de backup e restauração documentados especificamente para a versão anterior. Para obter detalhes sobre o backup e a restauração do Lync Server 2010, consulte <http://go.microsoft.com/fwlink/?linkid=265417> . Para obter detalhes sobre o backup e a restauração do Microsoft Office Communications Server 2007 R2, consulte <http://go.microsoft.com/fwlink/?linkid=168162>.

  - **Informações de infraestrutura**   Você deve fazer backup das informações sobre sua infraestrutura, como a configuração de seu firewall, configuração de balanceamento de carga, configuração de ISS (Serviços de Informações da Internet), registros DNS (Sistema de Nomes de Domínio), endereços IP e configuração de DHCP (Dynamic Host Configuration Protocol). Para obter detalhes sobre o backup desses componentes, consulte os respectivos fornecedores.

  - **Microsoft Exchange e UM (Unificação de Mensagens) do Exchange**   Faça backup e restaure o Microsoft Exchange e o UM do Exchange conforme descrito na documentação do Microsoft Exchange. Para obter detalhes sobre o backup e a restauração do Exchange Server 2013, consulte <http://go.microsoft.com/fwlink/?linkid=285384>. Para obter detalhes sobre o backup e a restauração do Exchange Server 2010, consulte <http://go.microsoft.com/fwlink/?linkid=209179>.
    
    Observe que o Lync Server 2013 apresenta a capacidade de ter listas de contatos do usuário, fotos de usuário em alta definição e dados de arquivamento armazenados no Exchange 2013. Consulte a seguinte lista para saber como fazer o backup desses tipos de dados:
    
      - O backup das **fotos em alta definição** faz parte do backup do Exchange Server.
    
      - O **repositório de contatos unificado** foi introduzido no Lync Server 2013. O repositório de contatos unificado permite que os usuários mantenham todas as informações de contato no Exchange 2013.
        
        Você deve assegurar que os backups estejam atualizados para os usuários verificando se os contatos de cada usuário estão armazenados no repositório de contatos unificado ou no servidor back-end do Lync. Os cenários a seguir ilustram quando a migração dos contatos do usuário para o repositório de contatos unificado pode causar problemas para o processo de backup e restauração.
        
        **Cenário 1:** os contatos do usuário são migrados para o repositório de contatos unificado e uma restauração é realizada a partir de um backup do Lync Server feito antes da migração dos contatos do usuário. Neste cenário, o usuário terá um estado de contatos desatualizados por até um dia até que as tarefas de migração do Lync Server comecem a migrar os contatos do usuário para o Exchange. (Observe que, em virtude de os contatos do usuário terem sido migrados anteriormente para o repositório de contatos unificado, as informações de contato do Exchange serão usadas). Nenhuma intervenção do administrador é necessária neste cenário.
        
        **Cenário 2:** os contatos do usuário foram armazenados anteriormente no repositório de contatos unificado, mas depois foram revertidos. Uma restauração é realizada a partir de um backup do Lync Server feito quando os contatos do usuário estavam armazenados no repositório de contatos unificado. Neste cenário, a mensagem de erro `Error: Incorrect Exchange Version` no cliente ou logs do servidor Lyss pode indicar um problema. O usuário poderá acessar a lista de contatos do Lync 2013 diretamente do Exchange, mas o estado do cliente não corresponderá ao estado do Lync Server. Para resolver isso, um administrador deverá executar os cmdlets **Invoke-CsUCSRollback** para os usuários afetados.
    
      - Os **dados de arquivamento** podem ser armazenados no Exchange 2013. Esses dados não são críticos ao Lync Server, mas poderão ser críticos à sua organização para fins regulatórios. Se os dados de arquivamento forem armazenados no Exchange e forem críticos à sua organização, siga os procedimentos de backup e restauração do Exchange. Observe que os dados de arquivamento armazenados no Exchange não podem ser movidos de volta para o Lync Server. Além disso, não há como mover os dados já armazenados no banco de dados de arquivamento do Lync para o Exchange.

