---
title: Entendendo as configurações do serviço de registro em log centralizado
TOCTitle: Entendendo as configurações do serviço de registro em log centralizado
ms:assetid: 3c34e600-0b91-43dc-b4cc-90b6a70ee12e
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ688029(v=OCS.15)
ms:contentKeyID: 49886181
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Entendendo as configurações do serviço de registro em log centralizado

 

_**Tópico modificado em:** 2015-03-09_

O Serviço de Log Centralizado é configurado para definir o que o serviço de log deve coletar, como ele coleta, de onde ele irá coletar e quais são as configurações do log. Você define essas configurações para global (isto é, toda a implantação) ou local (isto é, o local nomeado na sua implantação).Qualquer log que você definir utilizará as configurações adequadas para a identidade que você utiliza para os comandos para iniciar, parar, liberar e buscar logs.

## Para exibir a configuração Serviço de Log Centralizado atual

Inicie o Shell de Gerenciamento do Lync Server: clique em **Iniciar**, em **Todos os Programas**, em **Microsoft Lync Server 2013** e em **Shell de Gerenciamento do Lync Server**.

Digite o seguinte em uma linha de comando do promt:

    Get-CsClsConfiguration


> [!TIP]
> Você pode diminuir ou ampliar o escopo das definições das configurações que retornam ao definir <CODE>-Identity</CODE> e um escopo, como “Site:Redmond”, para retornar apenas o CsClsConfiguration para o Redmond local. Caso deseje detalhes sobre uma dada parte da configuração, você pode canalizar a saída em outro cmdlet Windows PowerShell. Por exemplo, para obter detalhes sobre os cenários definidos na configuração para o "Redmond" loca, digite: <CODE>Get-CsClsConfiguration -Identity "site:Redmond" | Select-Object -ExpandPropery Scenarios</CODE>



![Amostra de saída do Get-CsClsConfiguration.](images/JJ688138.23f98ddc-fc48-499a-b6c5-752611f2a0b0(OCS.15).jpg "Amostra de saída do Get-CsClsConfiguration.")

O resultado do cmdlet exibe a configuração atual do Serviço de Log Centralizado.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Definição da Configuração</th>
<th>Descrição</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Identidade</strong></p></td>
<td><p>Identifica o escopo e o nome para esta configuração. Há apenas uma configuração global e uma configuração por local.</p></td>
</tr>
<tr class="even">
<td><p><strong>Cenários</strong></p></td>
<td><p>Lista de todos os cenários que são definidos para esta configuração.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Termos de busca</strong></p></td>
<td><p>Termos de busca definidos para a configuração. Office 365, não implantações locais.</p></td>
</tr>
<tr class="even">
<td><p><strong>SecurityGroups</strong></p></td>
<td><p>Grupos de segurança definidos que controlam quem (isto é, membros dos grupos de segurança) podem ver computadores com base no local que estão. Local, neste contexto, é o local como definido em Construtor de Topologias.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Regiões</strong></p></td>
<td><p>Regiões definidas são utilizadas para coletar SecurityGroups em uma região, por exemplo EMEA.</p></td>
</tr>
<tr class="even">
<td><p><strong>EtlFileFolder</strong></p></td>
<td><p>Caminho definido para a localização onde os arquivos de log são gravados nos computadores. O CLSAgent grava os arquivos de log e executa sob o contexto do Serviço de Rede. Neste caso, %TEMP% expande-se para %WINDIR%\ServiceProfiles\NetworkService\AppData\Local</p></td>
</tr>
<tr class="odd">
<td><p><strong>EtlFileRolloverSizeMB</strong></p></td>
<td><p>O parâmetro indica o tamanho máximo do arquivo de log antes que um log de rastreio de evento (.etl) novo seja criado. Um novo arquivo de log é criado quando o tamanho definido é atingido, mesmo se o tempo máximo definido no EtlFileRolloverMinutes não tiver sido atingido ainda.</p></td>
</tr>
<tr class="even">
<td><p><strong>EtlFileRolloverMinutes</strong></p></td>
<td><p>Quantidade de tempo máxima definida, em minutos, que um log pode decorrer antes de um novo arquivo .etl ser criado. Um novo arquivo de log é criado quando o cronômetro expira, mesmo que o tamanho máximo definido em EtlFileRolloverSizeMB não tenha sido atingido ainda.</p></td>
</tr>
<tr class="odd">
<td><p><strong>TmfFileSearchPath</strong></p></td>
<td><p>Local para buscar por arquivos de formato de mensagens de rastreio. Os arquivos de formato de mensagem são utilizados para converter os arquivos binários em um formato humanamente legível.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheFileLocalFolders</strong></p></td>
<td><p>Caminho definido para o local onde os arquivos de cache são gravados nos computadores. O CLSAgent grava os arquivos de cache e executa sob o contexto do Serviço de Rede. Neste caso, %TEMP% expande-se para %WINDIR%\ServiceProfiles\NetworkService\AppData\Local. Por padrão, os arquivos de log e cache são gravados no mesmo diretório.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheFileNetworkFolder</strong></p></td>
<td><p>Você pode definir um caminho de convenção de nomenclatura universal (UNC) para receber os arquivos de cache durante operações de log.</p></td>
</tr>
<tr class="even">
<td><p><strong>CacheFileLocalRetentionPeriod</strong></p></td>
<td><p>Definido como o tempo máximo em dias que os arquivos de cache são retidos.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CacheFileMaxDiskUsage</strong></p></td>
<td><p>Definido como a porcentagem de espaço em disco que pode ser utilizado pelos arquivos de cache.</p></td>
</tr>
<tr class="even">
<td><p><strong>ComponentThrottleLimit</strong></p></td>
<td><p>Definido como o número máximo de rastreios por segundo que um componente pode produzir antes de o limitador de aceleração automática é acionado.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ComponentThrottleSample</strong></p></td>
<td><p>Número de vezes em 60 segundos em que o ComponentThrottleLimit pode ser excedido.</p></td>
</tr>
<tr class="even">
<td><p><strong>MinimumClsAgentServiceVersion</strong></p></td>
<td><p>A versão mínima do CLSAgent que pode ser executada. Este elemento é destinado a Office 365.</p></td>
</tr>
</tbody>
</table>


## Consulte Também

#### Conceitos

[Visão Geral do Serviço de Registro em Log](lync-server-2013-overview-of-the-centralized-logging-service.md)  

#### Outros Recursos

[Set-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsClsConfiguration)  
[Remove-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Remove-CsClsConfiguration)  
[New-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/New-CsClsConfiguration)  
[Get-CsClsConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Get-CsClsConfiguration)

