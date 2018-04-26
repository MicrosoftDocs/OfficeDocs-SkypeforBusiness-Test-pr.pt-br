---
title: Verificar configurações
TOCTitle: Verificar configurações
ms:assetid: 51c2d1d9-63f7-43ab-88ca-b8913da7cede
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204885(v=OCS.15)
ms:contentKeyID: 49306702
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar configurações

 

_**Tópico modificado em:** 2012-09-06_

É possível validar a replicação de informações de configuração para o Servidor de Borda executando o cmdlet Lync Server 2013**Get-CsManagementStoreReplicationStatus** no computador interno no qual o Repositório de Gerenciamento Central está localizado (ou qualquer domínio participando do computador no qual os Componentes Principais do Lync Server 2013 (OcsCore.msi) estão instalados.

Os resultados iniciais podem indicar o status como "Falso" em vez de "Verdadeiro" para a replicação. Se isso acontecer, execute o cmdlet **Invoke-CsManagementStoreReplication** e dê tempo para a replicação ser concluída antes de executar o **Get-CsManagementStoreReplicationStatus** novamente.

