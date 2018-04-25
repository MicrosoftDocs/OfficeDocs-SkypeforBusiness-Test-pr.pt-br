---
title: Associando relatórios de monitoramento a um banco de dados espelho
TOCTitle: Associando relatórios de monitoramento a um banco de dados espelho
ms:assetid: 42b797c6-8db8-4ad7-886e-8ddf8deb06f9
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945624(v=OCS.15)
ms:contentKeyID: 52057590
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Associando relatórios de monitoramento a um banco de dados espelho

 

_**Tópico modificado em:** 2014-02-07_

Se você configurar um espelho para o seu banco de dados de monitoramento, esse banco de dados espelho assumirá como o banco de dados primário se ocorrer um failover. No entanto, se você usar os Relatórios de Monitoramento do Lync Server e ocorrer um failover, talvez você ache que seus Relatórios de Monitoramento não estão se conectando ao banco de dados espelho. Isso ocorre porque, quando instala os Relatórios de Monitoramento, você especifica apenas o local do banco de dados primário; não é necessário especificar o local do banco de dados espelho.

Para que os Relatórios de Monitoramento executem o failover automático do banco de dados espelho, adicione esse banco de dados como um "parceiro de failover" aos dois bancos de dados usados pelos Relatórios de Monitoramento (um banco de dados para dados de Registro de Detalhe de Chamada e o outro para dados de QoE (Qualidade da Experiência)). (Observe que essa etapa deve ser executada após a instalação de Relatórios de Monitoramento.) Você pode adicionar as informações de parceiro de failover editando manualmente os valores de cadeia de conexão usados por esses dois bancos de dados. Para fazer isso, siga este procedimento:

1.  Use o Internet Explorer para abrir a home page do **SQL Server Reporting Services**. A URL dessa home page inclui:
    
      - O prefixo **http:**.
    
      - O FQDN (nome de domínio totalmente qualificado) do computador em que o Reporting Services está instalado (por exemplo, **atl-sql-001.litwareinc.com**).
    
      - A cadeia de caracteres **/Reports\_**.
    
      - O nome da instância de banco de dados em que os Relatórios de Monitoramento estão instalados (por exemplo, **archinst**).
    
    Por exemplo, se o SQL Server Reporting Services for instalado no computador atl-sql-001.litwareinc.com e os Relatórios de Monitoramento usarem a instância de banco de dados archinst, a URL da home page será parecida com esta:
    
    **http://atl-sql-001.litwareinc.com/Reports\_archinst**

2.  Depois que você acessar a home page do Reporting Services, clique em **LyncServerReports** e em **Reports\_Content**. Isso o levará para a página **Reports\_Content** de Relatórios de Monitoramento do Lync Server.

3.  Na página **Reports\_Content**, clique na fonte de dados **CDRDB**.

4.  Na página **CDRDB**, na guia **Propriedades**, procure a caixa de texto chamada **Cadeia de conexão**. A cadeia de conexão atual será semelhante a esta:
    
    **Data source=(local)\\archinst;initial catalog=LcsCDR**

5.  Edite a cadeia de conexão para incluir o nome do servidor e a instância de banco de dados do banco de dados espelho. Por exemplo, se o servidor se chamar atl-mirror-001 e o banco de dados espelho estiver na instância archinst, será necessário especificar o banco de dados espelho usando esta sintaxe:
    
    **Failover Partner=atl-mirror-001\\archinst**
    
    A cadeia de conexão editada será parecida com esta:
    
    **Data source=(local)\\archinst;Failover Partner=atl-mirror-001\\archinst;initial catalog=LcsCDR**

6.  Após a atualização da cadeia de conexão, clique em **Aplicar**.

7.  Na página **CDRDB**, clique no link **Reports\_Content**. Clique na fonte de dados **QMSDB** e edite a cadeia de conexão do banco de dados de QoE. Por exemplo:
    
    **Data source=(local)\\archinst;Failover Partner=atl-mirror-001\\archinst;initial catalog=QoEMetrics**

8.  Clique em **Aplicar**.

## Consulte Também

#### Conceitos

[Instalando Relatórios de Monitoramento do Lync Server 2013](lync-server-2013-installing-lync-server-2013-monitoring-reports.md)  
[Usando Relatórios de Monitoramento no Lync Server 2013](lync-server-2013-using-monitoring-reports.md)

