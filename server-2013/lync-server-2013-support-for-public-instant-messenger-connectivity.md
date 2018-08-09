---
title: "Suporte p/ conectiv. a redes públicas de m. instantâneas no Lync Server 2013"
TOCTitle: "Suporte p/ conectiv. a redes públicas de m. instantâneas no Lync Server 2013"
ms:assetid: 9c6eb500-647b-4ccd-a00e-2b8dd7c44a76
ms:mtpsurl: https://technet.microsoft.com/pt-br/library/Dn458579(v=OCS.15)
ms:contentKeyID: 59602783
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Suporte para conectividade a redes públicas de mensagens instantâneas no Lync Server 2013

 

_**Tópico modificado em:** 2016-12-08_

## Suporte para conectividade a redes públicas de mensagens instantâneas

Este artigo fornece informações sobre o suporte para Conectividade de IM público (PIC). PIC é um recurso do Microsoft Lync que permite às organizações habilitar seus usuários do Lync à conexão com os usuários de determinados serviços públicos de mensagens instantâneas (IM) através de seus clientes Lync e identidades.

Os usuários finais se beneficiam da capacidade de se conectar com os clientes, parceiros e fornecedores de acordo com suas próprias condições. A TI se beneficia do suporte de um único cliente de comunicações em tempo real, mantendo o controle, conformidade e recursos de arquivamento do Lync. A conectividade do Lync com o Skype, [disponível publicamente em maio de 2013](http://blogs.technet.com/b/lync/archive/2013/05/23/lync-skype-connectivity-available-today.aspx), baseia-se na herança que o Lync/Office Communications Server (OCS)/Live Communications Server (LCS) estabeleceu primeiro com o PIC ao se conectar com o MSN/Windows Live, AOL e Yahoo.  Para obter mais informações sobre a conectividade do Lync com o Skype, consulte [conectividade do Lync com o Skype](http://office.microsoft.com/pt-br/lync/lync-skype-connectivity-fx103789635.aspx). A federação com Windows Live, AOL e Yahoo está prestes a atingir o fim da vida útil. Esta página documenta o status de cada serviço.

Para usar o PIC, os clientes precisam ativar o serviço para cada provedor público de serviços de mensagens instantâneas. Os requisitos e os detalhes de como fazer isso dependem do provedor de serviços de mensagens instantâneas e do programa de licenciamento subjacente do cliente.

## Windows Live Messenger

A Microsoft uniu o Windows Live Messenger e o Skype. Em abril de 2013, os usuários do Messenger foram migrados para o Skype após o logon. Os clientes do Lync baseados na federação com o Messenger ainda conseguirão se comunicar com seus contatos do Messenger, mesmo após a atualização desses contatos para o Skype. Não há nada que os administradores do Lync ou usuários finais Lync precisem fazer para manter a continuidade do serviço e o gerenciamento desta capacidade no Lync permanece o mesmo que já é feito para comunicações com Messenger. 

Quando os usuários do Messenger entram no Skype usando suas contas da Microsoft (ou seja, as mesmas credenciais usadas para Messenger), todos os seus contatos do Messenger - incluindo contatos federados do Lync - são migrados para o Skype. O compartilhamento da presença e as mensagens instantâneas entre o Skype e o Lync para esses contatos estão disponíveis. 

Conectividade do Lync com o Skype - a adição de contato, o compartilhamento de presença, as mensagens instantâneas e as chamadas de áudio entre os usuários do Lync e Skype - também já está disponível para todos os clientes do Lync.

## Mensagens Instantâneas Yahoo\! e AOL

A federação com o Yahoo\! e AOL está prestes a atingir o fim de vida para os clientes do Lync (e Office Communications Server). A capacidade de a Microsoft fornecer estes serviços está determinada por condições de suporte do Yahoo\! e AOL, e os acordos subjacentes destes serviços estão acabando. Os serviços do Yahoo\! e AOL continuarão até junho de 2014.

  - **Yahoo** - O serviço continuará até junho de 2014 e os clientes ainda precisam da licença "Lync Public IM Connectivity Licença de Assinatura de Usuário Microsoft" ("PIC USL").  A partir de 01 de setembro de 2012, a PIC USL não está mais disponível para compra para novos acordos ou de renovação.  Os clientes com licenças adquiridas antes desta data poderão continuar a federar com o Yahoo\! até a data de desativação do serviço ou até a expiração da licença. Consulte [o anúncio](http://blogs.technet.com/b/lync/archive/2012/11/26/lync-and-yahoo-federation-end-of-life.aspx) no blog da Equipe do Lync . Os clientes que tiverem licenças PIC em contratos válidos após o dia 30 de junho de 2014 receberão um crédito proporcional ao montante dos pagamentos que cobriria o período após o dia 30 de junho de 2014.

  - **AOL** - No dia 30 de junho de 2014, o serviço de conectividade de IM do Lync ("PIC") não estará mais disponível.  A fim de limitar a interrupção do cliente quando o serviço terminar, interrompemos o provisionamento de domínios de cliente adicionais. Até 30 de junho de 2014, os clientes não precisam tomar nenhuma iniciativa para continuar a oferecer suporte às comunicações federadas com AIM. Após esta data (ou para clientes que gostariam de fornecer domínios adicionais no meio tempo), um serviço  substituto está disponível diretamente do AOL. Para mais informações sobre o novo serviço do AOL , consulte [Estabelecer federação direta com o AIM](http://aimenterprise.aol.com/pic.php)  (abre uma nova página no AOL.com).  

## Resumo do Provedor de IM Público

A tabela a seguir apresenta um resumo dos provedores públicos de serviços de mensagens instantâneas, capacidades de federação com o Lync e requisitos de licenciamento.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Provedor de serviço de IM Público</th>
<th>Capacidades federadas</th>
<th>Requisitos de Licenciamento</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Skype</p></td>
<td><p>IM, Presença, Áudio</p></td>
<td><p>Licenças de acesso do cliente do Lync Server , Plano do Lync Online 1/2/3</p></td>
</tr>
<tr class="even">
<td><p>Windows Live Messenger</p></td>
<td><p>IM, Presença, Áudio/Vídeo</p></td>
<td><p>Licenças de acesso do cliente do Lync Server  (suportado contanto que WLM esteja no mercado)</p></td>
</tr>
<tr class="odd">
<td><p>AOL</p></td>
<td><p>IM, Presença</p></td>
<td><p>Licenças de acesso do cliente do Lync Server ; suportado até junho de 2014 para clientes existentes.</p></td>
</tr>
<tr class="even">
<td><p>Yahoo!</p></td>
<td><p>IM, Presença</p></td>
<td><p>Requer uma Microsoft Lync Public IM Connectivity User Subscription License (“PIC USL”) adicional, além de licenças de acesso de cliente do Lync Server. A partir da lista de preços de setembro de 2012, a PIC USL já não estará mais disponível para compra. Os clientes com licenças ativas poderão continuar a federação com o Yahoo! Messenger até a data de desativação do serviço no dia 30 de junho de 2014.</p></td>
</tr>
</tbody>
</table>

