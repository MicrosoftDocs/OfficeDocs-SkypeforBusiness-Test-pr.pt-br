---
title: "Mover Mover Diretórios de confer. do Lync Server 2010 p/ o Lync Server 2013"
TOCTitle: Mover Diretórios de Conferência
ms:assetid: 659867e0-ce91-4a95-9787-b1c1566460a8
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn727126(v=OCS.15)
ms:contentKeyID: 62388593
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover Diretórios de Conferência

 

_**Tópico modificado em:** 2016-12-08_

Antes de encerrar um pool você deve realizar o procedimento a seguir para cada diretório de conferência no pool de Lync Server 2010.

## Para mover um diretório de conferência para o Lync Server 2013

1.  Abra o Shell de Gerenciamento do Lync Server.

2.  Para obter a identidade dos diretórios de conferência na sua organização, execute o comando a seguir:
    
        Get-CsConferenceDirectory
    
    O comando anterior retorna todos os diretórios de conferência na sua organização. Antes disso, pode ser necessário limitar os resultados ao pool sendo encerrado. Por exemplo, se você estiver encerrando o pool com o FQDN (nome de domínio totalmente qualificado) pool01.contoso.net, use este comando para limitar os dados retornados aos diretórios de conferência do pool:
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"}
    
    Este comando retorna somente os diretórios de conferência em que a propriedade do ServiceID contém o FQDN pool01.contoso.net.

3.  Para mover os diretórios de conferência, execute o comando a seguir para cada diretório de conferência no pool:
    
        Move-CsConferenceDirectory -Identity <Numeric identity of conference directory> -TargetPool <FQDN of pool where ownership is to be transitioned>
    
    Por exemplo, para mover o diretório de conferência 3 use este comando, especificando um pool de Lync Server 2013 como TargetPool:
    
        Move-CsConferenceDirectory -Identity 3 -TargetPool "pool02.contoso.net"
    
    Se você desejar mover todos os diretórios de conferência em um pool, use um dos comandos similares a seguir:
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"} | Move-CsConferenceDirectory -TargetPool "pool02.contoso.net"

Consulte o documento "Desinstalando o Microsoft Lync Server 2010 e Removendo as Funções do Servidor" (que pode ser baixado em [http://go.microsoft.com/fwlink/p/?linkId=246227](http://go.microsoft.com/fwlink/p/?linkid=246227)) para instruções abrangentes e etapa por etapa ao encerrar os pools do Lync 2010.

Ao mover os diretórios de conferência talvez você encontre o erro a seguir:

    WARNING: Move operation failed for conference directory with ID "5". Cannot perform a rollback because data migration might have already started. Retry the operation.
    WARNING: Before using the -Force parameter, ensure that you have exported the conference directory data using DBImpExp.exe and imported the data on the target pool. Refer to the DBImpExp-Readme.htm file for more information.
    Move-CsConferenceDirectory : Unable to cast COM object of type 'System._ComObject' to interface type 'Microsoft.Rtc.Interop.User.IRtcConfDirManagement'. 
    This operation failed because the QueryInterface call on the COM component for the interface with SID '{4262B886-503F-4BEA-868C-04E8DF562CEB}' failed due to the following error: The specified module could not be found.

Este erro normalmente ocorre quando o Shell de Gerenciamento do Lync Server requer um conjunto atualizado das permissões do Active Directory para concluir a tarefa. Para resolver o problema, feche a instância atual do Shell de Gerenciamento, e abra uma nova instância do shell e execute novamente o comando para mover o diretório de conferência.

