---
title: 'Lync Server 2013: Teste de recuperação de desastre'
TOCTitle: Teste de recuperação de desastre
ms:assetid: 04f5e747-d837-4350-9fc0-8605dbf025a7
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn747887(v=OCS.15)
ms:contentKeyID: 62293580
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Teste de recuperação de desastre no Lync Server 2013

 

_**Tópico modificado em:** 2015-01-26_

Execute uma recuperação do sistema para um servidor de pools do Lync Server 2013 para testar seu processo de recuperação de desastre documentado. Esse teste simulará uma falha completa de hardware de um servidor e ajudará a garantir que os recursos, os planos e os dados estejam disponíveis para recuperação. Tente alternar o foco do teste mensalmente para que sua organização teste sempre a falha de um servidor diferente ou de outro equipamento.

Observe que o cronograma de execução do teste de Recuperação de Desastre pelas organizações variará. É muito importante que o teste de recuperação de desastre não seja ignorado ou negligenciado.


Exporte a topologia, as políticas e os parâmetros de configuração do Lync Server 2013 para um arquivo. O arquivo poderá ser usado, entre outras coisas, para restaurar essas informações para o Repositório de Gerenciamento Central após uma atualização, uma falha de hardware ou outro problema que resulte em perda de dados.

Importe a topologia, as políticas e os parâmetros de configuração do Lync Server 2013 para o Repositório de Gerenciamento Central ou para o computador local, conforme mostrado nos seguintes comandos:

`Import-CsConfiguration -ByteInput <Byte[]> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

`Import-CsConfiguration -FileName <String> [-Force <SwitchParameter>] [-LocalStore <SwitchParameter>]`

Para fazer backup dos dados de produção do Lync Server 2013:

  - Faça backup dos bancos de dados RTC e LCSLog usando o processo de backup SQL Server padrão e despeje o banco de dados em um arquivo ou em um dispositivo de fita de despejo.

  - Use um aplicativo de backup terceirizado para fazer backup dos dados para um arquivo ou uma fita.

  - Use o cmdlet Export-CsUserData para criar uma exportação XML de todo o banco de dados RTC.

  - Use o backup do sistema de arquivos ou de terceiros para fazer backup do conteúdo de reuniões e de logs de conformidade.

  - Use a ferramenta de linha de comando Export-CsConfiguration para fazer backup das configurações do Lync Server 2013.

A primeira etapa do procedimento de failover inclui um movimento forçado dos usuários do pool de produção para o pool de Recuperação de Desastre.

O movimento será forçado, pois o pool de produção não estará disponível para aceitar a realocação do usuário.

O processo de movimentação do usuário do Lync Server 2013 é efetivamente uma alteração para um atributo no objeto de conta do usuário, além de uma atualização de registro no banco de dados SQL RTC.

Esses dados podem ser restaurados por meio destes dois processos:

  - O banco de dados RTC pode ser restaurado do dispositivo de despejo de backup original do SQL Server de produção usando o processo de restauração SQL Server padrão ou um utilitário de backup/restauração terceirizado.

  - Os dados de contato do usuário podem ser restaurados por meio do utilitário DBIMPEXP.exe, usando o arquivo XML criado a partir da exportação do SQL Server de produção.

Após a restauração desses dados, os usuários poderão ser conectar efetivamente ao pool do Lync Server 2013 de Recuperação de Desastre e operar normalmente.

Para permitir que os usuários se conectem ao pool do Lync Server 2013 de Recuperação de Desastre, será necessária uma alteração do registro DNS.

O pool do Lync Server 2013 de produção será referenciado pelos clientes usando a configuração automática e os registros SRV DNS de:

  - SRV: \_sip.\_tls.\<domain\> /CNAME: SIP.\<domain\>

  - CNAME: SIP.\<domain\> /cvc-pool-1.\<domain\>

Para facilitar o failover, esse registro CNAME deve ser atualizado para referenciar o FQDN DROCSPool:

  - CNAME: SIP.\<domain\> /DROCSPool.\<domain\>

  - Sip.\<domain\>

  - AV.\<domain\>

  - webconf.\<domain\>

  - OCSServices.\<domain\>

> [!IMPORTANT]  
> Para obter os procedimentos detalhados de administração e gerenciamento, consulte <a href="lync-server-2013-backing-up-and-restoring-lync-server.md">Fazendo backup e restaurando o Lync Server 2013</a>.

## Consulte Também

#### Conceitos

[Planejamento para alta disponibilidade e recuperação de desastre no Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md)  
[Cmdlets de Backup e Alta Disponibilidade](https://docs.microsoft.com/en-us/powershell/module/skype/?view=skype-ps)  

#### Outros Recursos

[Import-CsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Import-CsConfiguration)  
[Fazendo backup e restaurando o Lync Server 2013](lync-server-2013-backing-up-and-restoring-lync-server.md)  
[Gerenciando recuperação de desastre, alta disponibilidade e Serviço de Backup do Lync Server 2013](lync-server-2013-managing-lync-server-disaster-recovery-high-availability-and-backup-service.md)

