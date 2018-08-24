---
title: "Lync Server 2013: Verif. conectiv. entre servidores int. e Servidores de Borda"
TOCTitle: 'Verificar conectividade entre servidores internos e Servidores de Borda '
ms:assetid: 219f706e-2b8a-46c5-b394-c384240eef50
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398292(v=OCS.15)
ms:contentKeyID: 49306124
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Verificar conectividade entre servidores internos e Servidores de Borda no Lync Server 2013

 

_**Tópico modificado em:** 2012-09-08_

No Lync Server 2013, um assistente de validação separado estava disponível para ajudar a validar a conectividade entre os Servidores de Borda e os servidores internos. No Lync Server 2013, a validação da conectividade é realizada automaticamente ao instalar os Servidores de Borda.

É possível validar a replicação de informações de configuração para a borda executando o cmdlet Windows PowerShell**Get-CsManagementStoreReplicationStatus** no computador interno no qual o Repositório de Gerenciamento Central está localizado (ou qualquer domínio participando do computador no qual os Componentes Principais do Lync Server 2013 (OcsCore.msi) estão instalados. Os resultados iniciais podem indicar o status como "Falso" em vez de "Verdadeiro" para replicação. Se assim, execute o cmdlet **Invoke-CsManagementStoreReplication** e permita que o tempo necessário para a replicação seja concluído antes de executar o **Get-CsManagementStoreReplicationStatus** novamente.

É possível verificar a conectividade de usuário externo separadamente, inclusive o uso do Analisador de Conectividade Remota do Office Communications Server para verificar a conectividade de usuários remotos. Para obter detalhes, consulte [Verificar conectividade para usuários externos no Lync Server 2013](lync-server-2013-verify-connectivity-for-external-users.md).

