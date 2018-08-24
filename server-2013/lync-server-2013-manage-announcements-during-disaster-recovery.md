---
title: 'Lync Server 2013: Gerenciar comunicados durante recuperação de desastre'
TOCTitle: Gerenciar comunicados durante recuperação de desastre
ms:assetid: c33e51ea-421f-42d2-826b-b73968f6bd5b
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ721874(v=OCS.15)
ms:contentKeyID: 49886394
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Gerenciar comunicados durante recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2013-02-23_

O Lync Server 2013 suporta anúncios para chamadas de números não atribuídos durante interrupções. Restaurar a funcionalidade de anúncio durante uma interrupção é opcional. Se você escolher restaurar anúncios durante uma interrupção, é necessário recriar sua configuração de anúncio no pool de backup. Esta seção descreve o que você precisa fazer se escolher restaurar anúncios durante a recuperação de desastres.

Esta seção se aplica a um intervalo de números não atribuídos que usam o Aplicativo Comunicado. Esta seção não se aplica ao intervalo de números não atribuídos que usam o Atendedor Automático do Exchange Unified Messaging (UM).

## Antes de uma interrupção

Independente se você escolher usar anúncios durante interrupções, você deve realizar backups separados de qualquer arquivo de áudio personalizado configurado para o Aplicativo Comunicado. Os anúncios personalizados não são armazenados como parte do processo de recuperação de desastres do Lync Server. Se você não realizar backups separados dos arquivos e os arquivos que você carregou ao servidor ou pool estão danificados, corrompidos ou apagados, os arquivos serão perdidos.

Se você não fez cópias de backup de arquivos de áudio personalizado e os arquivos de áudio original não estiverem mais disponíveis, é possível encontrar os arquivos de áudio configurados para um Aplicativo Comunicado procurando no Repositório de Arquivos para o servidor ou pool onde você importou originalmente os arquivos. É possível copiar todos os arquivos de áudio configurados para o Aplicativo Comunicado do Repositório de Arquivos.

**Para copiar arquivos de áudio do repositório de arquivos**

1.  Na linha de comando, execute:
    
        Xcopy <Source: Pool Announcement Service File Store path> <Destination>
    
    Por exemplo:
    
        Xcopy "<Pool File Store Path>\X-ApplicationServer-X\AppServerFiles\RGS\AS" "<Destination: Backup location>"
    
    Onde X-ApplicationServer-X refere-se à ID de serviço do Servidor de Aplicativos do pool (por exemplo, 1-ApplicationServer-1")


## Durante uma interrupção

Para usar o Aplicativo Comunicado durante uma interrupção, é necessário recriar a configuração de anúncio no pool de backup realizando as tarefas descritas nesta seção.

> [!NOTE]  
> Recomendamos realizar estas tarefas se você falhar no pool de backup, porque assim que você realizar a etapa 2, o pool de backup tem propriedade dos intervalos de número não atribuídos.

> [!NOTE]  
> Estas etapas não são necessárias para intervalos de número que usam um número de telefone do Atendedor Automático do Exchange UM.

**Para recriar a configuração de comunicado no pool de backup**

1.  Recrie os anúncios que você implantou no pool primário no pool de backup fazendo o seguinte:
    
    1.  Importe qualquer arquivo de áudio usado no pool primário para o pool de backup usando o cmdlet **Import-CsAnnouncementFile** e especificando o pool de backup para o parâmetro Parent.
    
    2.  Recriar cada anúncio usando o cmdlet **New-CsAnnouncement** e especificando o pool de backup para o parâmetro Parent.
    
    > [!NOTE]  
    > Para obter detalhes sobre o uso destes parâmetros para criar anúncios no pool de backup, consulte <a href="lync-server-2013-create-an-announcement.md">Criar um comunicado no Lync Server 2013</a>.

2.  Após todos os anúncios serem recriados no pool de backup, redirecione todos os intervalos de número não atribuídos que usam anúncios no pool primário para os anúncios recriados no pool de backup.
    
    Para cada intervalo de número não atribuído que usa um anúncio no pool primário, execute o seguinte:
    
        Set-CsUnassignedNumber -Identity "<name of number range>" -AnnouncementService "<FQDN of backup pool>" -AnnouncementName "<announcement name in backup pool>"

## Após a interrupção

Quando o pool primário se torna disponível, você precisa redirecionar os intervalos de número não atribuídos que você alterou para a interrupção de volta para o pool primário.

> [!NOTE]  
> Estas etapas não são necessárias para intervalos de número que usam um número de telefone do Atendedor Automático do Exchange UM.

**Para restaurar comunicados no pool primário**

1.  Se você precisa reconstruir o pool primário durante a recuperação, é necessário recriar os anúncios no pool primário importando os arquivos de áudio e criando anúncios, assim como você faria no pool de backup, exceto que você especifica o pool primário para o parâmetro Parent. Para obter detalhes, consulte "Durante uma interrupção" anteriormente neste tópico.

2.  Para cada intervalo de número não atribuído que você alterou para a interrupção, execute o seguinte:
    
        Set-CsUnassignedNumber [-Identity "<name of number range>"] -AnnouncementService "<FQDN of primary pool>" -AnnouncementName "<announcement name in primary pool>"

3.  Opcionalmente, remova os anúncios recriados no pool de backup. Obtenha uma lista de anúncios para o pool de backup do Aplicativo Comunicado. Na linha de comando, execute:
    
        Get-CsAnnouncement -Identity "<Service:service ID>"
    
    Por exemplo:
    
        Get-CsAnnouncement -Identity "ApplicationServer:redmond.contoso.com
    
    Na lista resultante, localize os anúncios que deseja remover e copie os GUIDs. Para cada anúncio que deseja remover, execute:
    
        Remove-CsAnnouncement -Identity "<Service:service ID/guid>"
    
    Por exemplo:
    
        Remove-CsAnnouncement -Identity "ApplicationServer:redmond.contoso.com/1951f734-c80f-4fb2-965d-51807c792b90"


