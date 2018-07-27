---
title: 'Lync Server 2013: Posicionamento de dados do Servidor SQL e do arquivo de log'
TOCTitle: Posicionamento de dados do Servidor SQL e do arquivo de log
ms:assetid: 67aa525b-8aa3-474f-827e-8e1d4697f30f
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398479(v=OCS.15)
ms:contentKeyID: 49306962
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Posicionamento de dados do Servidor SQL e do arquivo de log para Lync Server 2013

 

_**Tópico modificado em:** 2015-03-09_

Durante o planejamento e a implantação do Microsoft SQL Server 2012 ou do Microsoft SQL Server 2008 R2 SP1 para o seu Lync Server 2013  Pool de Front-Ends, uma importante consideração é a colocação de dados e de arquivos de log em discos rígidos físicos para obter desempenho. A configuração de disco recomendada é implementar o conjunto RAID 1+0 usando 6 eixos. Colocar todos os arquivos de banco de dados e de log que são usados pelo Pool de Front-Ends e as funções e serviços de servidor associados (isto é, Servidor de Arquivamento e Monitoramento, Serviço Grupo de Resposta do Lync Server, Serviço de Estacionamento de Chamada do Lync Server) no conjunto de unidade RAID utilizando o Assistente de Implantação do Lync Server resultará em uma configuração que foi testada para bom desempenho. Os arquivos de banco de dados e suas responsabilidades são detalhados na tabela seguinte.

> [!NOTE]  
> Se suas políticas e configurações do SQL Server precisarem de uma instalação especializada, os arquivos de banco de dados e de log podem ser instalados em qualquer local pré-definido usando o Shell de Gerenciamento do Lync Server. Consulte <a href="lync-server-2013-database-installation-using-lync-server-management-shell.md">Instalação de banco de dados usando o Shell de Gerenciamento do Lync Server no Lync Server 2013</a> para obter mais detalhes.

### Arquivos de dados e de log para o Repositório de Gerenciamento Central

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Arquivos do banco de dados do Repositório de Gerenciamento Central</th>
<th>Objetivo do arquivo de dados ou log</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Xds.ldf</p></td>
<td><p>Arquivo de log de transação para o Repositório de Gerenciamento Central</p></td>
</tr>
<tr class="even">
<td><p>Xds.mdf</p></td>
<td><p>Mantém a configuração da topologia atual do Lync Server 2013, conforme definido e publicado pelo Construtor de Topologias</p></td>
</tr>
<tr class="odd">
<td><p>Lis.mdf</p></td>
<td><p>Arquivo de dados do Serviço de Informações de Local</p></td>
</tr>
<tr class="even">
<td><p>Lis.ldf</p></td>
<td><p>Log de transação para o arquivo de dados do Serviço de Informações de Local</p></td>
</tr>
</tbody>
</table>


### Arquivos de dados e de log de Usuário, Conferência e Catálogo de Endereços

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Arquivos do banco de dados principal do Lync Server 2013</th>
<th>Objetivo do arquivo de dados ou log</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Rtc.mdf</p></td>
<td><p>Dados do usuário persistente (por exemplo, as ACLs (listas de controle de acesso), contatos, conferências programadas)</p></td>
</tr>
<tr class="even">
<td><p>Rtc.ldf</p></td>
<td><p>Log de transação dos dados do Rtc</p></td>
</tr>
<tr class="odd">
<td><p>Rtcdyn.mdf</p></td>
<td><p>Mantenha os dados dos usuários temporários (dados de tempo de execução de presença)</p></td>
</tr>
<tr class="even">
<td><p>Rtcdyn.ldf</p></td>
<td><p>Log de transação para dados Rtcdyn.</p></td>
</tr>
<tr class="odd">
<td><p>Rtcab.mdf</p></td>
<td><p>O banco de dados do catálogo de endereços RTC (comunicação em tempo real) é o repositório do SQL Server onde as informações do serviço de Catálogo de Endereços são armazenadas</p></td>
</tr>
<tr class="even">
<td><p>Rtcab.ldf</p></td>
<td><p>Log de transação para o serviço Catálogo de Endereços</p></td>
</tr>
<tr class="odd">
<td><p>Rtclocal.mdb</p></td>
<td><p>Hospeda o diretório de conferências</p></td>
</tr>
<tr class="even">
<td><p>Rtcxds.mdf</p></td>
<td><p>Mantém o backup dos dados do usuário</p></td>
</tr>
<tr class="odd">
<td><p>Rtcxds.ldf</p></td>
<td><p>Log de transação dos dados Rtcxds</p></td>
</tr>
</tbody>
</table>


### Arquivos de dados e log para o Estacionamento de Chamada e o Grupo de Resposta

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Banco de dados de aplicativos</th>
<th>Objetivo do arquivo de dados ou log</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Cpsdyn.mdf</p></td>
<td><p>Banco de dados de informações dinâmicas para o Aplicativo de Estacionamento de Chamada</p></td>
</tr>
<tr class="even">
<td><p>Cpsdyn.ldf</p></td>
<td><p>Log de transações do arquivo de dados do Aplicativo de Estacionamento de Chamada</p></td>
</tr>
<tr class="odd">
<td><p>Rgsconfig.mdf</p></td>
<td><p>Arquivo de dados do serviço Grupo de Resposta do Lync Server para a configuração dos serviços</p></td>
</tr>
<tr class="even">
<td><p>Rgsconfig.ldf</p></td>
<td><p>Arquivo de log de transação para a configuração do Aplicativo Grupo de Resposta</p></td>
</tr>
<tr class="odd">
<td><p>Rgsdyn.mdf</p></td>
<td><p>Arquivo de dados do serviço Grupo de Resposta para operações de tempo de execução</p></td>
</tr>
<tr class="even">
<td><p>Rgsdyn.ldf</p></td>
<td><p>Log de transação do arquivo de dados de tempo de execução do serviço Grupo de Resposta</p></td>
</tr>
</tbody>
</table>


### Arquivos de dados e de log para o Servidor de Arquivamento e o Monitoring Server

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Arquivos de banco de dados de Arquivamento e Monitoramento</th>
<th>Objetivo do arquivo de dados ou log</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>LcsCdr.mdf</p></td>
<td><p>Repositório de dados do processo CDR (registro de detalhes da chamada) do Servidor de Monitoramento</p></td>
</tr>
<tr class="even">
<td><p>LcsCdr.ldf</p></td>
<td><p>Log de transação dos dados CDR (registro de detalhes da chamada)</p></td>
</tr>
<tr class="odd">
<td><p>QoEMetrics.mdf</p></td>
<td><p>Arquivo de dados de Qualidade da Experiência armazenado do Servidor de Monitoramento</p></td>
</tr>
<tr class="even">
<td><p>QoEMetrics.ldf</p></td>
<td><p>Log de transação dos dados de Monitoramento</p></td>
</tr>
<tr class="odd">
<td><p>Lcslog.mdf</p></td>
<td><p>Arquivo de dados para a retenção de dados de conferência e mensagens instantâneas em um Servidor de Arquivamento</p></td>
</tr>
<tr class="even">
<td><p>Lcslog.ldf</p></td>
<td><p>Log de transação dos dados de Arquivamento</p></td>
</tr>
</tbody>
</table>


Neste tópico, são feitas referências ao disco e ao conjunto RAID. Observe que na configuração de recursos do SQL Server, referir-se a um disco significa um dispositivo de hardware único. Um disco rígido com duas partições, uma que mantém os arquivos de log e a outra partição que contém os arquivos de dados, não é o mesmo que dois discos, cada um dedicado a arquivos de log ou de dados.

Em referência aos conjuntos RAID, há diversas tecnologias RAID diferentes de vários fornecedores. Além disso, com a proliferação de redes SAN, os conjuntos RAID dedicados a um único sistema estão mais raros. Você deve consultar seu fornecedor de RAID ou SAN para determinar qual é a melhor configuração para seu layout de disco ao configurar o desempenho do SQL Server com o Lync Server 2013.

Observe também que nem todas as unidades de disco são criadas igualmente; algumas têm melhor desempenho melhor que outras. Mesmo as unidades do mesmo fabricante podem variar em desempenho devido a velocidade de rotação, tamanho do cache de hardware e outros fatores.

