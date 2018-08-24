---
title: Modificar as configurações dos arquivos de log de atualizações de dispositivo
TOCTitle: Modificar as configurações dos arquivos de log de atualizações de dispositivo
ms:assetid: 9b57f126-1853-43b3-bbd4-06401e6498bd
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg182554(v=OCS.15)
ms:contentKeyID: 49307583
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Modificar as configurações dos arquivos de log de atualizações de dispositivo

 

_**Tópico modificado em:** 2015-03-09_

Você pode alterar as configurações de como as informações do dispositivo são registradas em sua organização utilizando o Painel de Controle do Lync Server ou Shell de Gerenciamento do Lync Server. A tabela a seguir mostra quais configurações podem ser modificadas, e qual ferramenta(s) você utilizará para modificar as configurações.

Configurações de log podem ser alteradas e aplicadas globalmente ou por site.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Para alterar</th>
<th>Utilizar</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>O tamanho máximo (em bytes) para um arquivo de log</p></td>
<td><p>Painel de Controle do Lync Server</p>
<p>-ou-</p>
<p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
<tr class="even">
<td><p>A quantidade máxima de informações (em bytes) que pode ser mantida em cache</p></td>
<td><p>Painel de Controle do Lync Server</p>
<p>-ou-</p>
<p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
<tr class="odd">
<td><p>Com que frequência (em minutos) gravar informações do cache para o arquivo de log</p></td>
<td><p>Painel de Controle do Lync Server</p>
<p>-ou-</p>
<p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
<tr class="even">
<td><p>Por quanto tempo (em dias) manter os arquivos de log</p></td>
<td><p>Painel de Controle do Lync Server</p>
<p>-ou-</p>
<p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
<tr class="odd">
<td><p>Quando (horário) verificar se há arquivos expirados que devam ser deletados</p></td>
<td><p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
<tr class="even">
<td><p>Quais extensões de arquivo de log permitir</p></td>
<td><p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
<tr class="odd">
<td><p>Quais tipos de arquivos de log reter</p></td>
<td><p>Shell de Gerenciamento do Lync Server</p></td>
</tr>
</tbody>
</table>


## Para alterar configurações de log utilizando Painel de Controle do Lync Server

1.  Abra uma janela do navegador e insira a URL do Administrador para abrir o Painel de Controle do Lync Server. Para obter detalhes sobre os diferentes métodos que você pode usar para iniciar o Painel de Controle do Lync Server, consulte [Abrir ferramentas administrativas do Lync Server](lync-server-2013-open-lync-server-administrative-tools.md).

2.  Na barra de navegação à esquerda, clique em **Clientes** e em **Configuração de Log do Dispositivo**.

3.  Na página **Configuração de Log do Dispositivo**, dê duplo clique na configuração que deseja alterar.

4.  Na caixa de diálogo **Editar Configuração de Log**, altere qualquer uma das configurações a seguir:
    
      - **Tamanho máximo do arquivo (bytes)**   Especifica o tamanho máximo que um arquivo de log pode alcançar antes de ser excluído. O padrão é 1.024.000 bytes (1 MB).
    
      - **Tamanho máximo do cache (bytes)**   Especifica a quantidade máxima de informação (em bytes) que pode ser armazenada no cache do arquivo de log antes que o cache seja excluído e que os dados sejam gravados em um arquivo de log. O padrão é 512.000 bytes (0,5 MB).
    
      - **Número de minutos para liberar o cache (1-60)**   Indica com que frequência a informação armazenada no cache do arquivo de log é gravada no arquivo de log real. Depois que o dado é registrado em log, o cache é liberado. O padrão é cinco minutos.
    
      - **Número de dias para manter arquivos de log (1-365)**   Especifica o número de dias durante os quais os arquivos de log são mantidos antes de serem excluídos. O padrão é 10 dias.

5.  Clique em **Confirmar**.

## Para alterar configurações de registro utilizando Cmdlets Windows PowerShell

As definições de arquivo de log de atualização de dispositivo podem ser modificadas usando o Windows PowerShell e o cmdlet **Set-CsDeviceUpdateConfiguration**. Este cmdlet pode ser executado a partir do Shell de Gerenciamento do Lync Server 2013 ou de uma sessão remota do Windows PowerShell.

> [!NOTE]  
> Para obter detalhes sobre como usar o Windows PowerShell remoto para conectar ao Lync Server, consulte o artigo de blog do Lync Server Windows PowerShell, &quot;Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell&quot; em <a href="http://go.microsoft.com/fwlink/p/?linkid=255876">http://go.microsoft.com/fwlink/p/?linkId=255876 (em inglês)</a>.

Os exemplos a seguir mostram dois modos em que você pode utilizar o **Set-CsDeviceUpdateConfiguration** para modificar as configurações.

## Para modificar o tamanho máximo de arquivo de log e o intervalo de limpeza do log

  - O comando a seguir modifica as configurações de log de atualização do dispositivo aplicadas ao site Redmond. Neste exemplo, o tamanho máximo do arquivo de log está configurado como 204.800 bytes, enquanto o intervalo de limpeza de log está definido como 14 dias.
    
        Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -MaxLogFileSize 204800 -LogCleanUpInterval 14.00:00:00

## Para modificar o horário em que realizar a limpeza do log

  - Esse comando define o horário para limpeza do log para o site Redmond como 3:00h.
    
        Set-CsDeviceUpdateConfiguration -Identity "site:Redmond" -LogCleanupTimeOfDay 03:00

Para detalhes, veja o tópico Ajuda para o cmdlet [Set-CsDeviceUpdateConfiguration](https://docs.microsoft.com/en-us/powershell/module/skype/Set-CsDeviceUpdateConfiguration).

