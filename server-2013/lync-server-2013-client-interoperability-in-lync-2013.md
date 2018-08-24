---
title: 'Lync Server 2013: Interoperabilidade do Cliente no Lync 2013'
TOCTitle: Interoperabilidade do Cliente no Lync 2013
ms:assetid: 0f126571-91a2-45d5-855c-1e4ddb45fc04
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/JJ204672(v=OCS.15)
ms:contentKeyID: 49305891
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Interoperabilidade do Cliente no Lync 2013

 

_**Tópico modificado em:** 2016-03-04_

Este tópico discute a habilidade de clientes do Microsoft Lync Server 2013 de coexistir e interagir com clientes de versões anteriores do Lync Server e do Office Communications Server.

## Compatibilidade de servidor e cliente

A tabela a seguir exibe as combinações com suporte de versões de cliente e de servidor. Esta tabela indica se há suporte à assinatura quando o cliente tenta se conectar ao servidor indicado. O Lync Server 2013 suporta a versão de cliente anterior. Além disso, diferente das versões anteriores, o Lync Server 2010 suporta clientes do novo Lync 2013. Isso permite que organizações que estejam atualizando a partir do Lync Server 2010 usem novos clientes independente das atualizações do Lync Server.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Cliente</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte5</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App 2013</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Attendant</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Chat de Grupo do Lync 2010</p></td>
<td><p>Com suporte1</p></td>
<td><p>Com suporte2</p></td>
<td><p>Não aplicável</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App 2010</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendee</p></td>
<td><p>Sem suporte3</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>Interoperável4</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="even">
<td><p>Microsoft Office Communications Server 2007 R2 Attendant</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="even">
<td><p>Office Live Meeting 2007</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
<tr class="odd">
<td><p>Aplicativo Lync Windows Store</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
</tbody>
</table>


1Para maiores detalhes, consulte [Migração do Lync Server 2010, Chat em Grupo ou Office Communications Server 2007 R2 Group Chat para Lync Server 2013, Servidor de Chat Persistente](migration-from-lync-server-2010-group-chat-or-office-communications-server-2007-r2-group-chat-to-lync-server-2013-persistent-chat-server.md).

2No Microsoft Lync Server 2010, a funcionalidade de chat em grupo era possível com o Servidor de chat de grupo, um aplicativo confiável de terceiro para Lync Server 2010. Clientes do Lync 2013 não são compatíveis com o Lync Server 2010, Chat de Grupo.

3O Lync Web App 2013 agora fornece uma experiência de reuniões completa, incluindo áudio e vídeo do computador, e é considerado o substituto do Lync 2010 Attendee. O Lync 2010 Attendee irá conectar-se ao Lync Server 2013 somente quando você estiver usando um navegador com suporte (Internet Explorer 6 ou Internet Explorer 7) e o Windows XP.

4A presença e os recursos de IM do Office Communicator 2007 R2 são compatíveis com Lync Server 2013, mas os recursos de conferência não são. Durante a migração do Office Communications Server 2007 R2, o Office Communicator 2007 R2 é adequado para a interoperabilidade o IM e presença, mas os usuários devem usar o Lync Web App 2013 para participar de reuniões do Lync Server 2013.

5 Para conhecer as limitações, consulte "Suporte ao recurso de conferências de clientes Lync 2013 em reuniões do Lync Server 2010" posteriormente neste tópico.

## Interoperabilidade entre clientes

Com a versão do Lync Server 2013, várias versões de cliente podem interagir diretamente, em ambos os cenários, ponto a ponto e de conferências. Esta seção discute a disponibilidade de recursos quando os usuários interagem com outros usuários, que estejam usando versões diferentes de clientes e servidores.

## Suporte ao recurso ponto a ponto

Recursos ponto a ponto são suportados para usuários que estão hospedados em versões diferentes do servidor e que estejam usando versões de cliente diferentes. A experiência do usuário final e os recursos disponíveis são consistentes com os recursos do cliente do usuário e a versão do servidor em que o usuário entrou. Em outras palavras:

  - Se um usuário entrou em Lync Server 2013 com um cliente mais antigo, ele terá a mesma experiência com a qual está acostumado. Nenhum dos novos recursos apresentados em Lync Server 2013 estará disponível até que o cliente do usuário seja atualizado. Exemplos incluem exibição da galeria de fotos, vídeo em HD, compartilhamento de PowerPoint e a opção de ativar Mudo do áudio e vídeo dos participantes ao entrar na reunião. Os novos recursos são descritos em [Novos recursos de conferência no Lync Server 2013](lync-server-2013-new-conferencing-features.md) e [Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

  - Se o usuário entrou no Lync Server 2010 com um cliente do Lync 2013 quaisquer recursos novos não suportados pelo Lync Server 2010 estarão indisponíveis até que o usuário mude para o Lync Server 2013.

A tabela a seguir compara a disponibilidade de recursos em sessões ponto a ponto onde o cliente entrou no Lync Server 2013 ou no Lync Server 2010.

> [!NOTE]  
> O Lync Web App e o Lync 2010 Attendee são clientes somente para reuniões e não estão incluídos nesta tabela.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th>Cliente</th>
<th>Sistema de Mensagens Instantâneas</th>
<th>Presença</th>
<th>Voz</th>
<th>Vídeo</th>
<th>Compartilhamento de Aplicativos</th>
<th>Transferência de Arquivos</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010 Attendant</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Lync 2010 Mobile</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="even">
<td><p>Lync Phone Edition</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R2</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim1</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="even">
<td><p>Rede pública de IM (AOL, Yahoo!)</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
<tr class="odd">
<td><p>Rede pública de IM (MSN, Windows Live Messenger)</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


> [!IMPORTANT]  
> <ul>
> <li><p>A partir de 1º de setembro de 2012, a Licença de Assinatura do Usuário para conectividade a redes públicas de IM do Microsoft Lync (&quot;PIC USL&quot;) não estará mais disponível para a compra de novos contratos ou para renovação. Os clientes com licenças ativas poderão continuar a federar com o Yahoo! Messenger até a data do encerramento do serviço. Foi anunciada a data de fim de vida útil em junho de 2014 para a AOL e o Yahoo!. Para obter detalhes, consulte <a href="lync-server-2013-support-for-public-instant-messenger-connectivity.md">Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013</a>.</p></li>
> 
> <li><p>A PIC USL é uma licença de assinatura por mês e por usuário que é necessária para o Lync Server ou o Office Communications Server federar com o Yahoo! Messenger. A capacidade da Microsoft de fornecer este serviço depende do suporte do Yahoo!, o contrato subjacente que não será renovado.</p></li>
> 
> 
> <li><p>Mais do que nunca, o Lync é uma ferramenta poderosa para a conexão entre as organizações e com pessoas de todo o mundo. A federação com o Windows Live Messenger não requer licenças de usuário/dispositivo adicionais além do CAL padrão do Lync. A federação do Skype será adicionada a esta lista, permitindo que os usuários do Lync atinjam centenas de milhões de pessoas com mensagens instantâneas e de voz.</p></li></ul>


1 No Office Communicator 2007 R2, somente o compartilhamento de área de trabalho (e não o compartilhamento de programas) está disponível.

## Suporte ao recurso de conferências de clientes do Lync 2013 em reuniões do Lync Server 2010

Quando os usuários participam de reuniões do Lync Server 2010 com um cliente do Lync 2013, eles têm acesso aos recursos de cliente do Lync 2013 com as seguintes exceções:

  - Nas opções de gerenciamento de **Participantes**, que o usuário pode acessar apontando para o ícone de pessoas na janela de reunião, a opção **Sem Mensagens Instantâneas na Reunião** não funciona.

  - O Modo de Exibição da Galeria não funciona em videoconferências. O usuário visualiza apenas o orador ativo, em vez de todos os oradores. Na lista de opções **Selecionar um Layout**, o **Modo de Exibição de Galeria** está indisponível

  - Por padrão, a lista de participantes é exibida nas videoconferências

  - As opções de gerenciamento de participantes **Bloquear Destaque de Vídeo** e **Fixar na Galeria** não estão disponíveis quando você clica com o botão direito do mouse na lista de participantes.

## Suporte ao recurso de conferências em reuniões do Lync Server 2013

Lync Server 2013 oferece novos recursos de conferência que são disponibilizados aos usuários depois que suas contas são movidas para Lync Server 2013 e eles entrarem com o cliente de Lync 2013. Exemplos incluem exibição da galeria de vídeos, vídeo em HD, compartilhamento de PowerPoint e a opção de ativar Mudo do áudio e vídeo dos participantes ao entrar na reunião. Os novos recursos são descritos em [Novos recursos de conferência no Lync Server 2013](lync-server-2013-new-conferencing-features.md) e [Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md).

Em reuniões em Lync Server 2013, certos recursos de conferência são suportados para usuários que estão hospedados em versões diferentes do servidor e que estão usando clientes e versões de cliente diferentes. Quando os clientes entram em uma reunião em Lync Server 2013, os usuários têm acesso aos recursos exibidos nesta tabela.


<table style="width:100%;">
<colgroup>
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 11%" />
</colgroup>
<thead>
<tr class="header">
<th>Cliente</th>
<th>Mensagens instantâneas ponto a ponto</th>
<th>Voz</th>
<th>Vídeo</th>
<th>Compartilhamento de Aplicativos</th>
<th>PowerPoint</th>
<th>Transferência de arquivos</th>
<th>Quadro de comunicações</th>
<th>Sondagem</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Lync 2013</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="even">
<td><p>Lync 2013 Basic</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="odd">
<td><p>Lync Web App</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim2</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="even">
<td><p>Lync 2010</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim3</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
<td><p>Sim</p></td>
</tr>
<tr class="odd">
<td><p>Office Communicator 2007 R24</p></td>
<td><p>Sim</p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
<td><p></p></td>
</tr>
</tbody>
</table>


1 No Office Communicator 2007 R2, somente o compartilhamento de área de trabalho (e não o compartilhamento de programas) está disponível.

2 O Lync Server 2013 usa um mecanismo atualizado para carregar arquivos do PowerPoint. Usuários do Lync Web App que entram em uma reunião que foi originalmente agendada no Lync Server 2010 podem exibir e navegar em apresentações do PowerPoint, mas não podem carregar arquivos do PowerPoint.

3 Se a reunião for agendada no Lync Server 2013 e a apresentação em PowerPoint for carregada por um cliente do Lync 2013, os usuários do Lync 2010 só terão acesso para exibição. De modo contrário, se a apresentação em PowerPoint for carregada por um usuário do Lync 2010, os usuários do Lync Server 2013 poderão visualizar os slides e, se o Office Web Apps Server estiver configurado, poderão acessar novos recursos como exibições em alta resolução, animações, transições de slide e vídeos integrados. Para obter mais informações consulte [Configurando a integração com servidor de Office Web Apps e Lync Server 2013](lync-server-2013-enabling-office-web-apps-server-and-lync-server-2013.md).

4A aparência e os recursos de IM no Office Communicator 2007 R2 são compatíveis com o Lync Server 2013, mas os recursos de conferência não são. Durante a migração do Office Communications Server 2007 R2, o Office Communicator 2007 R2 é ideal para a aparência e interoperabilidade de IM, mas os usuários devem usar o Lync Web App 2013 para fazer parte das reuniões do Lync Server 2013.

## Suporte a suplemento de agendamento

O suporte do servidor a vários suplementos de agendamento é consistente com a compatibilidade de versão do servidor e cliente. Em geral, os suplementos de agendamento a seguir são suportados no Lync Server 2013. No entanto, versões anteriores de suplementos não fornecem novos recursos de suplemento do Lync 2013, como a opção de ativar o mudo para o áudio e vídeo de todos os participantes na entrada da reunião.

  - **Suplemento de Reunião Online para Lync 2013**   Fornece os mesmos recursos do Suplemento de Reunião Online para o Lync 2010, além de controles de ativação de mudo dos participantes, o que permite que organizadores de reunião agendem conferências que possuem o áudio e vídeo dos participantes em mudo por padrão. Administradores também podem personalizar convites de reunião da organização incluindo um logotipo personalizado, uma URL da equipe de suporte, uma URL de aviso de isenção legal ou um texto de rodapé personalizado.

  - **Suplemento Reunião Online para Lync 2010**   Fornece agendamento para reuniões do Lync e remove a capacidade de agendar conferências do Office Live Meeting.

  - **Suplemento de Conferência do Office Communicator 2007 R2**   Fornece agendamento para conferências do Office Live Meeting e do Office Communicator 2007 R2. 

> [!NOTE]  
> Conferências do Live Meeting não podem ser agendadas no Lync Server 2013.


<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th>Cliente de agendamento</th>
<th>Lync Server 2013</th>
<th>Lync Server 2010</th>
<th>Office Communications Server 2007 R2</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Suplemento de Reunião Online para Lync 2013 (pode ser usado com o Office 2013, o Outlook 2010 e o Outlook 2007)</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte (novos recursos de suplemento não disponíveis)</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Agendador Web do Lync 2013</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="odd">
<td><p>Suplemento Reunião Online para Lync 2010</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Sem suporte</p></td>
</tr>
<tr class="even">
<td><p>Suplemento de Conferência do Office Communicator 2007 R2</p></td>
<td><p>Sem suporte</p></td>
<td><p>Com suporte</p></td>
<td><p>Com suporte</p></td>
</tr>
</tbody>
</table>


## Suporte para entrar em reuniões

Todos os clientes suportados pelo Lync Server 2013 têm permissão para entrar em reuniões do Lync 2013. Como o Lync Web App é um componente web do servidor, em casos em que o Lync Web App é usado para entrar em uma reunião do Lync Server 2013, a versão mais recente do Lync Web App sempre é usada.

Clientes do Lync 2013 podem entrar em reuniões hospedadas no Lync 2010 e no Office Communications Server 2007 R2 com funcionalidades reduzidas. Recursos em reuniões são limitados pela versão do servidor em que a reunião está hospedada.

## Consulte Também

#### Conceitos

[Requisitos do Aplicativo Lync da Windows Store para Lync Server 2013](lync-server-2013-lync-windows-store-app-requirements.md)  
[Novos recursos de conferência no Lync Server 2013](lync-server-2013-new-conferencing-features.md)  
[Novidades para clientes no Lync Server 2013](lync-server-2013-what-s-new-for-clients.md)

