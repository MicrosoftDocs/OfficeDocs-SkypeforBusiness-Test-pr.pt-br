---
title: Integrando um aplicativo de colaboração de terceiros com o Lync
TOCTitle: Integrando um aplicativo de colaboração de terceiros com o Lync
ms:assetid: 00b9312c-b0c8-4f79-8b76-05b2d820e197
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg398068(v=OCS.15)
ms:contentKeyID: 52057543
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Integrando um aplicativo de colaboração de terceiros com o Lync

 

_**Tópico modificado em:** 2015-03-09_

Você pode integrar o Lync 2013 com qualquer plicativo de colaboração online de terceiro ao adicionar informação sobre o aplicativo no registro. Você pode usar o Lync 2013 para iniciar sessões de conferência de dados hospedadas em um servidor local, em um serviço baseado em Internet, ou ambos. A colaboração ou sessão de conferência de dados pode ser iniciada a partir da lista de Contatos de uma sessão de IM, voz ou vídeo existente. O Lync 2013 age apenas como o veículo para o iniciar o aplicativo. Quais conversações de Lync 2013 existentes permanecem ativas após o início da sessão de colaboração on-line.

As seções a seguir descrevem como integrar o Lync 2013 com aplicativos de colaboração baseados em Internet e servidor.

## Integrando um Aplicativo de colaboração baseado em Internet ao Lync 2013

Normalmente, as etapas envolvidas na integração de um aplicativo de colaboração de terceiros são as seguintes:

1.  Informações sobre o aplicativo são adicionadas ao registro.

2.  O organizador ingressa no Lync 2013 e selecione contatos para compartilhamento de dados e colaboração. O organizador pode também já estar em uma conversa e decide adicionar conferência de dados.

3.  Lync 2013 lê o registro, inicia o aplicativo de colaboração e então envia uma mensagem SIP personalizada —um appINVITE—aos participantes selecionados.

4.  Os participantes aceitam o convite e o aplicativo de colaboração é inicializado no computador de cada pessoa. Lync 2013 utiliza o registro para determinar que aplicativo de colaboração usar e então inicializa aquele aplicativo, usando os parâmetros incluídos na mensagem appINVITE.

A tabela a seguir descreve as entradas de registro necessárias para integrar um aplicativo de colaboração baseado em internet com o Lync 2013. Essas entradas estão localizadas no registro nos locais a seguir:

  - HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps\\Parameters

### Entradas de Registro para um Aplicativo de Colaboração baseado em Internet

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Tipo</th>
<th>Dados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome</p></td>
<td><p>REG_SZ</p></td>
<td><p>O nome de aplicativo para menus Lync 2013.</p></td>
</tr>
<tr class="even">
<td><p>SmallIcon</p></td>
<td><p>REG_SZ</p></td>
<td><p>Caminho de um ícone com 16 pixels x 16 pixels, BMP ou PNG.</p></td>
</tr>
<tr class="odd">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>Caminho de participante para iniciar o aplicativo de colaboração on-line.</p></td>
</tr>
<tr class="even">
<td><p>OriginatorPath</p></td>
<td><p>REG_SZ</p></td>
<td><p>Caminho de organizador para iniciar o aplicativo de colaboração on-line. Este caminho pode conter um ou mais parâmetros personalizados, como definidos na sub-chave Parâmetros. Por exemplo, <code>https://meetserv.adatum.com/cc/%param1%/join?id=%param2%&amp;role=present&amp;pw=%param3%</code></p></td>
</tr>
<tr class="odd">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = Sessão local. O aplicativo é iniciado no computador local.</p>
<p>1 = Sessão de duas partes (padrão). Lync 2013 inicia o aplicativo localmente e então envia uma notificação de sistema ao outro usuário. O outro usuário clica na notificação e inicia o aplicativo especificado em seu computador.</p>
<p>2 = Sessão de múltiplas partes. Lync 2013 inicia o aplicativo localmente e então envia notificações de sistema aos outros usuários, avisando-os para iniciar o aplicativo especificado em seus computadores.</p></td>
</tr>
<tr class="even">
<td><p>ExensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>Uma lista de menus onde este comando aparecerá, separados por pontos-e-vírgulas. Os valores possíveis são:</p>
<ul>
<li><p>MainWindowActions</p></li>
<li><p>MainWindowRightClick</p></li>
<li><p>ConversationWindowActions</p></li>
<li><p>ConversationWindowButton</p></li>
<li><p>ConversationWindowRightClick</p></li>
</ul>
<p>Se ExtensibleMenu não estiver definido, os valores padrão de MainWindowRightClick e ConversationWindowActions serão usados.</p></td>
</tr>
</tbody>
</table>


A tabela a seguir descreve as entradas de registro para os parâmetros. Estas entradas estão em HKEY\_CURRENT\_USER\\Software\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps\\Parameters.

### Entradas de Registro para um Aplicativo de Colaboração baseado em Internet

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Tipo</th>
<th>Dados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Param1</p></td>
<td><p>REG_SZ</p></td>
<td><p>Utilizado em formato de token (<code>%Parm1%</code>) para adicionar valores específicos do usuário à chave de registro OriginatorPath.</p></td>
</tr>
<tr class="even">
<td><p>Param2</p></td>
<td><p>REG_SZ</p></td>
<td><p>Consulte Param1.</p></td>
</tr>
<tr class="odd">
<td><p>Param3</p></td>
<td><p>REG_SZ</p></td>
<td><p>Consulte Param1.</p></td>
</tr>
</tbody>
</table>


O exemplo de definições de registro a seguir integra o ADatum Collaboration Client com Lync 2013:

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{C3F6E17A-855F-44a0-B90D-C0B92D38E5F1}]
    "Path"="https://meetingservice.adatum.com/cc/%param1%/meet/%param2%"
    "OriginatorPath"="https://meetserv.adatum.com/cc/%param1%/join?id=%param2%&role=present&pw=%param3%"
    "SessionType"=dword:00000002
    "ApplicationType"=dword:00000001
    "LiveServerIntegration"=dword:00000000
    "Name"="ADatum Online Collaboration Service"
    "Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowRightClick"
    
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters]
    [HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Lync\SessionManager\Apps\Parameters\{C3F6E17A-855F-44a0-B90D-C0B92D38E5F1}]
    "Param1"="meetserv"
    "Param2"="admin"
    "Param3"="abcdefg123"

## Integrando um Aplicativo de Colaboração baseado em Servidor com o Lync 2013

As definições para adicionar comandos para iniciar um aplicativo baseado em servidor a partir do Lync 2013 são similares às descritas na seção anterior, Integrando um Aplicativo de colaboração baseado em Internet com o Lync 2013. No entanto, o OriginatorPath não é exigido e alguns valores são diferentes. As entradas de registro são colocadas nos seguintes locais:

  - HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Office\\15.0\\Lync\\SessionManager\\Apps\\Parameters

### Entradas de Registro de um Aplicativo de Colaboração baseado em Servidor

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Nome</th>
<th>Tipo</th>
<th>Dados</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Nome</p></td>
<td><p>REG_SZ</p></td>
<td><p>Nome do aplicativo conforme aparece no menu.</p></td>
</tr>
<tr class="even">
<td><p>ApplicationType</p></td>
<td><p>DWORD</p></td>
<td><p>Valor = 1. Define o tipo de aplicativo como protocolo. Os outros valores possíveis não se aplicam neste caso. Caso não esteja presente, ApplicationType é definido como 0 (executável).</p></td>
</tr>
<tr class="odd">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>Protocolo usado para iniciar o aplicativo de colaboração. Para Live Meeting 2007o valor de Path é definido como <code>meet:%conf-uri%</code>.</p></td>
</tr>
<tr class="even">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = Sessão local. O aplicativo é iniciado no computador local.</p>
<p>1 = Sessão de duas partes (padrão). Lync 2013 inicia o aplicativo localmente e então envia uma notificação de sistema ao outro usuário. O outro usuário clica na notificação e inicia o aplicativo especificado em seu computador.</p>
<p>2 = Sessão de múltiplas partes. Lync 2013 inicia o aplicativo localmente e então envia notificações de sistema aos outros usuários, avisando-os para iniciar o aplicativo especificado em seus computadores.</p></td>
</tr>
<tr class="odd">
<td><p>MCUType</p></td>
<td><p>REG_SZ</p></td>
<td><p>DATA = O tipo de servidor.</p></td>
</tr>
<tr class="even">
<td><p>ExtensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>Uma lista dos menus onde este comando aparecerá, separados por ponto-e-vírgula. Os valores possíveis são:</p>
<ul>
<li><p>MainWindowActions</p></li>
<li><p>MainWindowRightClick</p></li>
<li><p>ConversationWindowActions</p></li>
<li><p>ConversationWindowButton</p></li>
<li><p>ConversationWindowRightClick</p></li>
</ul>
<p>Se ExtensibleMenu não estiver definido, os valores padrão de MainWindowRightClick e ConversationWindowActions serão usados.</p></td>
</tr>
</tbody>
</table>


O exemplo a seguir adiciona comandos para iniciar o ADatum Collaboration Client a partir do Lync 2013:

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps]
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\SessionManager\Apps\{27877e66-615c-4582-ab88-0cb2ca05d951}]
    "Path"="meet:%conf-uri%"
    "SessionType"=dword:00000002
    "LiveServerIntegration"=dword:00000001
    "ApplicationType"=dword:00000001
    "Name"="ADatum Collaboration Client"
    "MCUType"="Data"
    "Extensiblemenu"="MainWindowActions;MainWindowRightClick;ConversationWindowActions;ConversationWindowRightClick"

