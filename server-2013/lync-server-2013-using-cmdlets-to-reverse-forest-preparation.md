---
title: 'Lync Server 2013: Usando cmdlets para reverter preparação da floresta'
TOCTitle: Usando cmdlets para reverter preparação da floresta
ms:assetid: f48c7eb3-ccb0-48e6-ac79-ab7c7062b9d3
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg413024(v=OCS.15)
ms:contentKeyID: 49308604
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Usando cmdlets para reverter preparação da floresta no Lync Server 2013

 

_**Tópico modificado em:** 2013-06-19_

Use o cmdlet **Disable-CsAdForest** para reverter a etapa de preparação da floresta.


> [!WARNING]  
> Se você executar o cmdlet <STRONG>Disable-CsAdForest</STRONG> em um ambiente onde você já tinha uma versão anterior do Lync Server implantada, as configurações globais da versão anterior também serão excluídas.



## Para usar cmdlets para reverter a preparação da floresta

1.  Faça o login em um computador que faz parte de um domínio como membro do grupo Administradores de Domínio no domínio raiz da floresta.

2.  Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

3.  Execute:
    
        Disable-CsAdForest [-Force] [-GroupDomain <FQDN of the domain in which universal groups were created>]
    
    Por exemplo:
    
        Disable-CsAdForest -Force -GroupDomain contoso.net
    
    O parâmetro Force especifica se deve forçar a execução da tarefa. Se este parâmetro não está presente, o comando não funcionará, mesmo se um domínio na floresta ainda está preparado para o Lync Server 2013. Se o parâmetro Force é especificado, a ação continuará independente do estado dos outros domínios na floresta.
    
    Se você não especificar o parâmetro GroupDomain, o valor padrão é o domínio local.

## Consulte Também

#### Tarefas

[Executando preparação de floresta para Lync Server 2013](lync-server-2013-running-forest-preparation.md)  

#### Outros Recursos

[Preparando a floresta para Lync Server 2013](lync-server-2013-preparing-the-forest.md)

