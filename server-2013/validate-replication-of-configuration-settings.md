---
title: Validar replicação de configurações
TOCTitle: Validar replicação de configurações
ms:assetid: 81a3c21d-b28a-4287-adac-11791e8db56d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ205042(v=OCS.15)
ms:contentKeyID: 49307285
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Validar replicação de configurações

 

_**Tópico modificado em:** 2012-10-19_

É possível validar a replicação de informações de configuração para o Servidor de Borda executando o cmdlet Lync Server 2013**Get-CsManagementStoreReplicationStatus** no computador interno no qual o Repositório de Gerenciamento Central está localizado ou qualquer domínio participando do computador no qual os Componentes principais Lync Server 2013 estão instalados.

Os resultados iniciais podem indicar o status como "Falso" e não "Verdadeiro" para replicação. Se for o caso, execute o cmdlet **Invoke-CsManagementStoreReplication** e permita que a replicação seja concluída antes de executar o cmdlet **Get-CsManagementStoreReplicationStatus** novamente.

