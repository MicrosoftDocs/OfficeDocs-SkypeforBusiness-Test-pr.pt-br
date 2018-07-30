---
title: Mover diretórios de conferência
TOCTitle: Mover diretórios de conferência
ms:assetid: 71a28308-1f3b-4717-b535-2f4bfe3499a1
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204994(v=OCS.15)
ms:contentKeyID: 49307083
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Mover diretórios de conferência

 

_**Tópico modificado em:** 2012-10-04_

Antes de encerrar um pool, é necessário realizar o seguinte procedimento para cada diretório de conferência no pool do Office Communications Server 2007 R2.

## Para mover um diretório de conferência para o Lync Server 2013

1.  Abra o Shell de Gerenciamento do Lync Server.

2.  Para obter a identidade dos diretórios de conferência de sua organização, execute os seguintes comandos:
    
        Get-CsConferenceDirectory
    
    Como este cmdlet retorna todos os diretórios de conferência da organização, convém limitar os resultados apenas ao pool que deseja encerrar. Por exemplo, caso deseje encerrar um pool com o FQDN (nome de domínio totalmente qualificado) pool01.contoso.net:
    
        Get-CsConferenceDirectory | Where-Object {$_.ServiceID -match "pool01.contoso.net"}
    
    Este cmdlet retorna todos os diretórios de conferência cujos IDs de serviço contêm o FQDN pool01.contoso.net.

3.  Para mover diretórios de conferência, execute o seguinte comando para cada diretório de conferência no pool:
    
        Move-CsConferenceDirectory -Identity <Numeric identity of conference directory> -TargetPool <FQDN of pool where ownership is to be transitioned>
    
    Por exemplo:
    
        Move-CsConferenceDirectory -Identity 3 -TargetPool pool02.contoso.net

> [!NOTE]  
> Talvez ocorra um erro (mostrado a seguir) causado pelo Shell de Gerenciamento do Lync Server ao exigir um conjunto atualizado de permissões do Active Directory. Para solucionar esse erro, fecha a janela atual, abra um novo Shell de Gerenciamento do Lync Server e execute o comando novamente.

![Saída de erro Move-CsConferenceDirectory](images/JJ204994.4748b9e8-9651-4527-afe1-cbdc6d5ce4a8(OCS.15).jpg "Saída de erro Move-CsConferenceDirectory")

