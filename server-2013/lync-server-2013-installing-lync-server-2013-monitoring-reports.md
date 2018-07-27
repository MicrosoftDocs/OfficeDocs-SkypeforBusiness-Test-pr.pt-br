---
title: Instalando Relatórios de Monitoramento do Lync Server 2013
TOCTitle: Instalando Relatórios de Monitoramento do Lync Server 2013
ms:assetid: 6f417569-b100-442c-ad48-fdd794626cf7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204989(v=OCS.15)
ms:contentKeyID: 49307058
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Instalando Relatórios de Monitoramento do Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Os relatórios de monitoramento do Microsoft Lync Server 2013 fornecem diversas informações sobre a qualidade e quantidade de sessões de comunicação que ocorrem na organização. Porém, os relatórios de monitoramento não são instalados automaticamente quando você instala o Lync Server 2013; em vez disso, você deve instalar os relatórios de monitoramento separadamente, somente após a instalação do Lync Server no computador.

> [!NOTE]  
> Recomenda-se a instalação dos relatórios de monitoramento no mesmo computador em que o banco de dados de monitoramento está instalado. Isso simplifica o processo de atribuição de permissões para acessar os relatórios: a com a instalação dos relatórios de monitoramento no computador que hospeda o repositório de monitoramento, você não precisará configurar permissões que permitam que um banco de dados em um computador interaja com os Reporting Services em execução em outro computador.

Os relatórios de monitoramento do Lync Server incluem mais de 30 relatórios desenvolvidos para fornecer informações detalhadas sobre conferências, sessões de mensagens instantâneas ponto a ponto, registro de usuários, o aplicativo Grupo de Resposta e muito mais. Para a versão 2013, os relatórios de monitoramento do Lync Server incluem diversos aprimoramentos:

  - **Novos relatórios de qualidade de voz**. Esses novos relatórios incluem o [Relatório de comparação de qualidade de mídia](lync-server-2013-media-quality-comparison-report.md), que compara a qualidade entre diferentes tipos de chamadas (por exemplo, entre chamadas com fio e sem fio); e o [Relatório de hora de ingresso na conferência](lync-server-2013-conference-join-time-report.md), que fornece informações a respeito do tempo necessário para que os usuários ingressem em uma conferência.

  - **Relatórios aprimorados para analisar e solucionar problemas de sessões de vídeo e compartilhamento de aplicativos.** Com o [Relatório de Resumo de Qualidade de Mídia no Lync Server 2013](lync-server-2013-media-quality-summary-report.md), é possível analisar chamadas de vídeo e compartilhamento de aplicativos, enquanto o [Relatório de Desempenho do Servidor no Lync Server 2013](lync-server-2013-server-performance-report.md) detalha o desempenho dos servidores que geram essas chamadas. As métricas de vídeo e compartilhamento de aplicativos também são informadas pelo [Relatório de Detalhes de Sessão Ponto a Ponto no Lync Server 2013](lync-server-2013-peer-to-peer-session-detail-report.md) e pelo [Relatório de detalhes da conferência](lync-server-2013-conference-detail-report.md).

  - **Desempenho de relatórios aprimorado**. Inclui tempos menores de resposta e recuperação de dados, bem como navegação mais rápida e fácil pelos relatórios.

Encontre mais informações sobre os relatórios individuais na documentação dos relatórios de monitoramento.

> [!NOTE]  
> Há mais um novo relatório (sub-relatório de detalhes de chamada de QoE) que foi incluído no Lync Server 2013. Porém, seu uso é principalmente interno e o acesso a ele não pode ser feito diretamente.

Há dois modos de instalar os relatórios de monitoramento do Lync Server, você pode usar o Assistente de Implantação do Lync Server ou um script do Windows PowerShell incluído nos arquivos de instalação do Lync Server 2013. Independente do método usado para instalar os relatórios, primeiro você deve certificar-se de:

  - Ter o direito de adicionar uma função de banco de dados a uma conta de usuário no banco de dados de monitoramento.

  - Possuir a função Gerenciador de Conteúdo no SQL Server Reporting Services. Essa função concede o direito de implantar relatórios no SQL Server Reporting Services.

Para instalar os relatórios de monitoramento usando o Assistente de Implantação, siga as etapas a seguir:

1.  Clique em **Iniciar**, **Todos os Programas**, **Microsoft Lync Server 2013** e **Assistente de Implantação do Lync Server**.

2.  No Assistente de Implantação, clique em **Implantar Relatórios de Monitoramento** para iniciar o assistente Implantar Relatórios de Monitoramento.

3.  No assistente Implantar Relatórios de Monitoramento, na página **Especificar Banco de Dados de Monitoramento**, certifique-se de que o nome de domínio totalmente qualificado do computador que hospeda o repositório de monitoramento apareça na lista suspensa **Banco de dados de monitoramento** (caso tenha vários repositórios de monitoramento, será necessário selecionar o servidor correto na lista suspensa). Verifique se a instância correta do SQL Server aparece na caixa **Instância do SSRS (SQL Server Reporting Services)** (por exemplo, **atl-sql-001.litwareinc.com/archinst**) e clique em **Avançar**.

4.  Na página **Especificar Credenciais**, na caixa **Nome de usuário**, digite o nome de domínio e nome de usuário da conta a ser usada ao acessar os relatórios de monitoramento (por exemplo, **litwareinc\\kenmyer**). Se você não utilizar esse formato ocorrerá um erro.
    
    Digite a senha da conta do usuário na caixa **Senha** e, em seguida, clique em **Próximo**. Observe que não são necessários direitos especiais para esta conta. A conta receberá automaticamente o login necessário e as permissões do banco de dados quando a configuração for concluída.

5.  Na página **Especificar Grupo Somente Leitura**, informe o nome de um grupo de segurança ao qual será concedido acesso somente leitura ao SQL Server Reporting Services na caixa Grupo de usuários. Por exemplo, para conceder aos administradores acesso somente leitura aos relatórios, digite **RTCUniversalReadOnlyAdmins**. Clique em **Avançar**.

6.  Na página **Executando Comandos**, clique em **Concluir**.

Os relatórios de monitoramento também podem ser instalados no Shell de Gerenciamento do Lync Server executando o script DeployReports.ps1; esse script do Windows PowerShell pode ser encontrado na mídia de instalação do Lync Server na pasta \\Setup\\ReportingSetup. Para instalar os relatórios de monitoramento usando DeployReports.ps1, digite um comando semelhante a este no prompt do Shell de Gerenciamento:

    D:\Setup\AMD64\Setp\ReportingSetup\DeployReports.ps1 -storedUserName "litwareinc\kenmyer" -storedPassword "p@ssw0rd" -readOnlyGroupName "RTCUniversalReadOnlyAdmins" -reportServerSqlInstance "atl-sql-001.litwareinc.com" -monitoringDatabaseId "MonitoringDatabase:atl-sql-001.litwareinc.com"

Os parâmetros usados no comando anterior são descritos na tabela a seguir:


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome do parâmetro</th>
<th>Obrigatório</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>storedUserName</p></td>
<td><p>Sim</p></td>
<td><p>Conta de usuário (no formato domínio\nome_de_usuário) usada para acessar o repositório de monitoramento; por exemplo:</p>
<pre><code>-storedUserName &quot;litwareinc\kenmyer&quot;</code></pre>
<p>Essa conta deve ter permissões do SQL Server e SQL Server Reporting Services especificadas previamente. Caso contrário, o script falhará.</p></td>
</tr>
<tr class="even">
<td><p>storedPassword</p></td>
<td><p>Sim</p></td>
<td><p>Senha da conta de usuário usada para acessar o repositório de monitoramento.</p></td>
</tr>
<tr class="odd">
<td><p>readOnlyGroupName</p></td>
<td><p>Não</p></td>
<td><p>Grupo de segurança local ou domínio cujos membros receberão acesso somente leitura aos relatórios de monitoramento. Observe que o script falhará se o grupo especificado não existir. Caso decida revogar as permissões posteriormente ou se decidir conceder permissão de acesso a outros usuários ou grupos, faça isso usando o gerenciador de relatórios do SQL Server Reporting Services.</p></td>
</tr>
<tr class="even">
<td><p>reportSqlServerInstance</p></td>
<td><p>Não</p></td>
<td><p>Instância do SQL Server que hospeda o Reporting Service. A instância de relatório deve ser especificada usando o nome de domínio totalmente qualificado do servidor de relatório. Por exemplo:</p>
<pre><code>-reportServerSqlInstance atl-sql-001.litwareinc.com</code></pre>
<p>Se este parâmetro não for incluído, o script partirá do pressuposto de que o Reporting Services é hospedado pela mesma instância do SQL Server que hospeda o banco de dados de monitoramento.</p></td>
</tr>
<tr class="odd">
<td><p>monitoringDatabaseId</p></td>
<td><p>Não</p></td>
<td><p>Identidade de serviço do banco de dados de monitoramento. Você pode retornar as identidades dos bancos de dados de monitoramento executando este comando:</p>
<pre><code>Get-CsService -MonitoringDatabase</code></pre></td>
</tr>
</tbody>
</table>


Após a instalação do relatórios de monitoramento, você deve usar o cmdlet Set-CsReportingConfiguration para configurar o URL usado para acessar esses relatórios. Essa tarefa pode ser executada no Shell de Gerenciamento do Lync Server pela execução do comando de Windows PowerShell a seguir. Observe que, apesar de recomendado, não é obrigatório usar o protocolo HTTPS ao configurar o URL do relatório:

    Set-CsReportingConfiguration -Identity "MonitoringDatabase:atl-sql-001.litwareinc.com" -ReportingURL "https://atl-sql-001.litwareinc.com:443/Reports_ARCHINST"

No comando anterior, a propriedade ReportingUrl deve ser definida como o URL do Gerenciador de Relatórios usado pelo SQL Server 2008 R2 Reporting Services. Você pode determinar o URL do Gerenciador de Relatórios concluindo as etapas a seguir no computador onde o SQL Server Reporting Services foi instalado:

1.  Clique em Iniciar, Todos os Programas, Microsoft SQL Server 2008 R2, Ferramentas de Configuração e Gerenciador de Configuração do Reporting Services.

2.  Na caixa de diálogo Conexão de Configuração do Reporting Services, certifique-se de que o nome do computador do Reporting Services apareça na caixa Nome do Servidor. Selecione a instância do SQL Server na lista suspensa Instância do Servidor de Relatório e clique em Conectar.

3.  no Gerenciador de Configuração do Reporting Services, clique em URL do Gerenciador de Relatório. Um ou mais URLs devem aparecer no painel URL do Gerenciador de Relatório. Todos esses URLs podem ser usados como URL de relatório, embora, mais uma vez, seja recomendado que ReportingUrl use o protocolo HTTPS.

Se você tiver configurado um banco de dados de espelho para monitoramento do banco de dados, você também deverá associar os Relatórios de Monitoramento com o banco de dados de espelho. Consulte o artigo [Associando relatórios de monitoramento a um banco de dados espelho](lync-server-2013-associating-monitoring-reports-with-a-mirror-database.md) para maiores detalhes.

