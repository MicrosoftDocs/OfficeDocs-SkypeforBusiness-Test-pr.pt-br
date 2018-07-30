---
title: Pré-requisitos de backup para failover do pool ABC
TOCTitle: Pré-requisitos de backup para failover do pool ABC
ms:assetid: 652046f5-6086-4592-902d-d5789581977d
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ945634(v=OCS.15)
ms:contentKeyID: 52057647
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Pré-requisitos de backup para failover do pool ABC

 

_**Tópico modificado em:** 2013-03-26_

Para obter o máximo benefício de usar o procedimento de failover do pool ABC, você deve executar determinados backups antes do desastre e da falha acontecerem:

  - Você deve constantemente fazer o backup dos dados de configuração do LIS (serviço de informações de local) a partir do pool A usando o cmdlet **Export-CsLISConfiguration**.
    
        Export-csLisConfiguration -FileName <C:\LISExportPrimary.zip>

  - Você deve constantemente fazer o backup dos dados de configuração do Grupo de Resposta no pool A usando o cmdlet **Export-CsRgsConfiguration**.
    
        Export-CsRgsConfiguration -Source "service:ApplicationServer:<Pool A FQDN>" -FileName "C:\RgsExportPrimary.zip"
    
    No geral, recomendamos que você execute backups diários, mas caso possua um volume alto de alterações, você pode querer programar backups mais frequentes. a quantidade de informações que você pode perder em caso de desastre depende da frequência de seus backups, como também da frequência e volume de alterações.
    
    O aplicativo Grupo de Resposta pode armazenar somente um conjunto de configurações no nível de aplicativo por pool. Essas configurações podem ser acessadas pelos cmdlets **Get-CsRgsConfiguration**. As configurações incluem a configuração de música em espera padrão, o arquivo de áudio de música em espera padrão, o período de espera do agente e a configuração de contexto da chamada. Essas configurações podem ser transferidas de um pool para outro por meio do cmdlet **Import-CsRgsConfiguration** usando o parâmetro **ReplaceExistingSettings**, mas essa operação sobrescreverá quaisquer configurações no nível de aplicativo no pool de destino.
    

    > [!TIP]
    > Em um local separado, mantenha uma cópia de backup de todos os arquivos de áudio originais que você usou para configurar o aplicativo Grupo de Resposta (ou seja, quaisquer arquivos de gravação ou de músicas em espera).

    
    Se os arquivos de música em espera personalizados tiverem sido carregados para o Estacionamento de Chamada em um pool, você deve manter uma cópia deles em outro local. O backup desses arquivos não faz parte do processo de recuperação de desastres do Lync Server 2013 e eles serão perdidos se os arquivos carregados para o pool forem danificados, corrompidos ou apagados.
    
        Xcopy  <Source: Pool A CPS File Store Path>  <Destination>
        Example: Xcopy  "<Pool A File Store Path>\LyncFileStore\coX-ApplicationServer-X\AppServerFiles\CPS\"  "<Destination:  Backup location 1>"
    
    > [!NOTE]  
    > O aplicativo Estacionamento de Chamada pode armazenar somente um conjunto de configurações e um arquivo de áudio de música em espera personalizado por pool. Essas configurações podem ser acessados pelo cmdlet <strong>Get-CsCpsConfiguration</strong>. Como o mecanismo de recuperação de desastres do Estacionamento de Chamada se baseia no aplicativo Estacionamento de Chamada do pool de backup, o backup das configurações do pool primário não é feito nem preservado se um desastre ocorrer. Se o pool primário for perdido, essas configurações não poderão ser recuperadas e quando um novo pool for implantado para substituir o pool primário, as configurações do Estacionamento de Chamada e qualquer arquivo de áudio de música em espera personalizado precisará ser configurado novamente.

  - Se você configurar qualquer comunicado como parte do Recurso de Voz com Número Não Atribuído, recomendamos que você tenha em outro local uma cópia de qualquer arquivo de áudio original usado durante a configuração inicial. Se você não fizer isso, é possível obter uma cópia dos arquivos de áudio configurados no armazenamento de arquivos do servidor ou do pool para o qual os arquivos de áudio foram importados. O backup desses arquivos não é feito como parte do processo de recuperação de desastres do Lync Server 2013 e eles serão perdidos se os arquivos carregados para o pool forem danificados, corrompidos ou apagados. Para copiar todos os arquivos de áudio utilizados para configurar o Recurso de Voz com Número Não Atribuído a partir do armazenamento de arquivos de um servidor ou de um pool, use:
    
        Use: Xcopy  <Source: Pool A Announcement Service File Store Path>  <Destination>
        Example Usage:  Xcopy  "<Pool A File Store Path>\X-ApplicationServer-X\AppServerFiles\RGS\AS"  "<Destination: Backup location>"

  - Se você possuir bancos de dados de Monitoramento e Arquivamento em um pool, é necessário usar as ferramentas de gerenciamento do SQL Server para fazer backup deles. No procedimento de failover do ABC, os bancos de dados de Monitoramento e Arquivamento não são preservados se eles são colocados em um pool A, porque o backup desses bancos de dados não é feito pelo Serviço de Backup do Lync Server.

