---
title: Adicionando comandos aos menus do Lync
TOCTitle: Adicionando comandos aos menus do Lync
ms:assetid: a8443bc2-e234-4022-870a-00700f38b1ea
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Gg412788(v=OCS.15)
ms:contentKeyID: 52057680
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Adicionando comandos aos menus do Lync

 

_**Tópico modificado em:** 2016-04-11_

Você pode adicionar comandos personalizados aos menus do Lync 2013 e passar o URI (Uniform Resource Identifier) do SIP do usuário atual e dos contatos selecionados para o aplicativo iniciado pelo comando personalizado.

Os comandos adicionados podem aparecer em um ou mais dos seguintes menus:

  - O menu Ferramentas, na barra de menus da janela principal do Lync

  - O menu de atalho para contatos na lista de Contatos

  - O menu Mais Opções, na barra de ferramentas, na janela de Conversas

  - O menu de atalho para pessoas na lista de participantes na janela de Conversas

  - O menu de opções em um cartão de visitas

Você pode definir comandos personalizados para dois tipos de aplicativos — aqueles que:

  - Aplicam-se somente ao usuário atual e são iniciados no computador local.

  - Envolvem usuários adicionais, como programas de colaboração online, e devem ser iniciados no computador de cada usuário.

O comando personalizado pode ser chamado das seguintes formas:

  - Selecione um ou mais usuários e escolha o comando personalizado.

  - Inicie uma conversa com dois ou vários participantes e escolha o comando personalizado.

## Para adicionar um comando personalizado

Use as configurações de registro na tabela a seguir para adicionar um comando aos menus. Essas entradas estão localizadas no registro em:

HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Office\\15.0\\Lync\\CustomCommands

### Entradas de Registro de Comandos Personalizados

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
<td><p>0 = Executável (padrão)</p>

> [!NOTE]  
> Requer ApplicationInstallPath.


<p>1 = Protocolo</p></td>
</tr>
<tr class="odd">
<td><p>ApplicationInstallPath</p></td>
<td><p>REG_SZ</p></td>
<td><p>Caminho completo do executável.</p>

> [!NOTE]  
> Deve ser especificado se o Tipo de Aplicativo for 0 (Executável).

</td>
</tr>
<tr class="even">
<td><p>Path</p></td>
<td><p>REG_SZ</p></td>
<td><p>Caminho completo a ser iniciado junto com quaisquer parâmetros, incluindo os parâmetros padrão <em>%user-id%</em> e <em>%contact-id%</em>.</p></td>
</tr>
<tr class="odd">
<td><p>SessionType</p></td>
<td><p>DWORD</p></td>
<td><p>0 = Sessão local. O aplicativo é iniciado no computador local.</p>
<p>1 = Sessão de dois participantes (padrão). O Lync 2013 inicia o aplicativo localmente e envia notificações na área de trabalho para o outro usuários. Os demais usuários clicam na notificação para iniciar o aplicativo em seu computador.</p>
<p>2 = Sessão de diversos participantes. O Lync 2013 inicia o aplicativo localmente e envia uma notificação na área de trabalho para os outros usuários. O outro usuário clica na notificação para iniciar o aplicativo especificado em seu computador.</p></td>
</tr>
<tr class="even">
<td><p>ExtensibleMenu</p></td>
<td><p>REG_SZ</p></td>
<td><p>Uma lista de menus em que esse comando aparecerá, separada por ponto e vírgula. Os valores possíveis são:</p>
<p>MainWindowActions</p>
<p>MainWindowRightClick</p>
<p>ConversationWindowActions</p>
<p>ConversationWindowRightClick</p>
<p>ContactCardMenu</p>
<p>Se ExtensibleMenu não estiver definido, os valores padrão de MainWindowRightClick e ConversationWindowActions são usados.</p></td>
</tr>
</tbody>
</table>


Por exemplo, o arquivo do Editor do Registro (.REG) a seguir mostra os resultados de adicionar o item Gerente de Contatos de Vendas da Contoso ao menu Ações na janela de Conversas:

    Windows Registry Editor Version 5.00
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\15.0\Lync\CustomCommands\{1F9F07C6-7E0B-462B-AAD7-98C6DBEA8F69}]
    "Name"="Contoso Sales Contact Manager"
    "HelpMessage"="The Contoso Sales Contact Manager is not installed. Contact the Help Desk for more information."
    "ApplicationType"=dword:00000000
    "ApplicationInstallPath"="C:\\cscm.exe"
    "Path"="C:\\cscm.exe %user-id% %contact-id%"
    "SessionType"=dword:00000001
    "ExtensibleMenu"="ConversationWindowActions;MainWindowRightClick"

## Para acessar um comando personalizado

Para acessar um comando personalizado depois de ele ter sido adicionado, execute um dos procedimentos a seguir, dependendo dos valores de ExtensibleMenu definidos:

  - **MainWindowActions**   Na janela principal do Lync, clique em **Ferramentas** e então no seu comando personalizado.

  - MainWindowRightClick   Na janela principal do Lync, clique com o botão direito em um contato e clique em seu comando personalizado.

  - **ConversationWindowActions**   Na janela de Conversas, clique no ícone **Mais Opções** e então no seu comando personalizado.

  - **ConversationWindowRightClick**   Na janela de Conversas, clique com o botão direito em um nome de contato e clique em seu comando personalizado.

  - **ContactCardMenu**   No cartão de visitas de uma pessoa, clique no ícone de opções e então no seu comando personalizado.

