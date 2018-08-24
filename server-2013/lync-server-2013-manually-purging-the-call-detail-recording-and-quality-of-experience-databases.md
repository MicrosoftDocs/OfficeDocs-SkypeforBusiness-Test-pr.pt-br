---
title: "Excluir manualm. o reg. de det. de chama e b. de dados de qual. de exper. Databases"
TOCTitle: "Excluir manualm. o reg. de det. de chama e b. de dados de qual. de exper. Databases"
ms:assetid: 3a3a965b-b861-41a4-b9a8-27184d622c17
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204812(v=OCS.15)
ms:contentKeyID: 49306439
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Excluir manualmente o registro de detalhes de chama e bancos de dados de qualidade de experiência Databases

 

_**Tópico modificado em:** 2014-07-07_

Conforme observado na seção anterior, os administradores podem configurar os bancos de dados de CDR (registro de detalhes das chamadas) e/ou QoE (qualidade da experiência) para que limpem automaticamente os registros antigos do banco de dados; isso ocorrerá se a limpeza for habilitada para o banco de dados especificado (CDR ou QoE) e se houver qualquer registro que esteja no banco de dados a mais tempo do que o período especificado. Por exemplo, os administradores podem configurar o sistema para que todos os dias, às 13:00, os registros de QoE com mais de 60 dias sejam excluídos do banco de dados de QoE.

Além da limpeza automática, dois novos cmdlets – Invoke-CsCdrDatabasePurge e Invoke-CsQoEDatbasePurge – foram adicionados ao Microsoft Lync Server 2013; esses cmdlets permitem que os administradores limpem registros manualmente dos bancos de dados de CDR ou QoE a qualquer momento. Por exemplo, para limpar manualmente todos os registros com mais de 10 dias do banco de dados de CDR, é possível usar um comando semelhante a este:

    Invoke-CsCdrDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10

No comando anterior, os registros de detalhes da chamada e os registros de dados diagnósticos com mais de 10 dias eram excluídos do banco de dados de monitoramento em atl-sql-001.litwareinc.com. (Os registros de detalhes da chamada são relatórios de usuário/sessão. Os registros de dados diagnósticos são logs diagnósticos carregados pelos aplicativos clientes, como o Lync 2013.)

Como mostrado acima, quando o cmdlet Invoke-CsCdrDatabasePurge é executado, os parâmetros PurgeCallDetaiDataOlderThanDays e PurgeDiagnosticDataOlderThanDays devem ser incluídos. No entanto, esses parâmetros não precisam ser definidos com o mesmo valor. Por exemplo, é possível limpar registros de detalhes da chamada com mais de 10 dias e ao mesmo tempo deixar todos os registros de dados diagnósticos no banco de dados. Para isso, defina PurgeCallDetailDataOlderThanDays como 10 e PurgeDiagnosticDataOlderThanDays como 0. Por exemplo:

    Invoke-CsCdrDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 0

Por padrão, sempre que o Invoke-CsCdrDatabasePurge é executado, um aviso semelhante a esse é exibido para cada tabela de banco de dados que deve ser limpo:

    Confirm
    Are you sure you want to perform this action?
    Performing operation "Stored procedure: RtcCleanupDiag" on Target "Target SQL Server:atl-sql-001.litwareinc.com\archinst Database: lcscdr".
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All [S] Suspend  [?] Help (default is "Y"):

É preciso digitar S (Sim) ou T (Sim para Todos) antes que a limpeza do banco de dados verdadeiramente ocorra. Se você preferir suprimir esse avisos de confirmação, adicione o seguinte parâmetro ao final de sua chamada como Invoke-CsCdrDatabasePurge:

    -Confirm:$False

Por exemplo:

    Invoke-CsCdrDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeCallDetailDataOlderThanDays 10 -PurgeDiagnosticDataOlderThanDays 10 -Confirm:$False

Se fizer isso, os avisos de confirmação não serão exibidos e a limpeza do banco de dados será realizada imediatamente.

Para limpar o banco de dados de QoE, use o cmdlet Invoke-CsQoEDatabasePurge e especifique a idade (em dias) dos registros a serem excluídos:

    Invoke-CsQoEDatabasePurge -Identity MonitoringDatabase:atl-sql-001.litwareinc.com -PurgeQoEDataOlderThanDays 10

