---
title: Restaurando um repositório de arquivos
TOCTitle: Restaurando um repositório de arquivos
ms:assetid: 89916fc6-31d3-4c7f-9eaf-c02584761ef4
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Hh202180(v=OCS.15)
ms:contentKeyID: 52057672
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Restaurando um repositório de arquivos

 

_**Tópico modificado em:** 2013-02-18_

Os Repositórios de Arquivo para o Standard Edition estão normalmente localizados na Servidor Standard Edition. Os Repositórios de Arquivo para o Enterprise Edition estão normalmente localizados em um cluster ou servidor de arquivos. O procedimento seguinte descreve como restaurar uma Repositório de Arquivos.

## Para restaurar um Re positório de arquivo

1.  Se um Repositório de Arquivos falhar, copie o Repositório de Arquivos adequado de $Backup\\ ao local do Repositório de Arquivos no servidor de arquivos ou Servidor Standard Edition e compartilhe a pasta.
    
    > [!IMPORTANT]  
    > O caminho e o nome do arquivo para o Repositório de Arquivos restaurado devem ser exatamente o mesmo que os do Repositório de Arquivos armazenado para que os componentes que usam os arquivos possam acessá-los.

2.  Se necessário, defina as listas do controle de acesso (ACLs) para o Repositório de Arquivos. Na linha de comando, digite:
    
        Enable-CsTopology
    
    > [!NOTE]  
    > É necessário executar esta etapa somente se você não executou a Construtor de Topologias durante o processo de restauração.
